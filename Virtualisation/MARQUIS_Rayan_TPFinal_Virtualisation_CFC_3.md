---
title: MARQUIS_Rayan_TPFinal_Virtualisation_CFC_3

---

### 1. Choix de la solution — justification en 5 lignes

**Choix : Voie A — Proxmox VE**

Nous choisissons Proxmox VE car il est particulièrement adapté à un environnement de laboratoire disposant de ressources limitées.
Par rapport à VMware ESXi + vCenter, Proxmox nécessite moins de ressources matérielles et ne nécessite pas de serveur VCSA supplémentaire.
Le choix est cohérent avec le CDC 1 et le CDC 2, qui ont permis de définir les besoins en virtualisation, stockage et disponibilité.
Proxmox permet de mettre en place un cluster de trois nœuds, du stockage NFS partagé, la migration à chaud et la haute disponibilité.
Cette solution permet donc de reproduire les fonctionnalités demandées par le client tout en restant réaliste pour le laboratoire.

---

# 2. Architecture proposée

Les trois nœuds Proxmox disposent chacun de trois interfaces réseau :

| Machine       | MGMT          | CLUSTER     | STORAGE     |
| ------------- | ------------- | ----------- | ----------- |
| **pve-n1**    | 192.168.50.31 | 10.10.10.31 | 10.20.20.31 |
| **pve-n2**    | 192.168.50.32 | 10.10.10.32 | 10.20.20.32 |
| **pve-n3**    | 192.168.50.33 | 10.10.10.33 | 10.20.20.33 |
| **NAS-LAB01** | 192.168.50.50 | —           | 10.20.20.50 |
| **VM03-APP**  | 192.168.50.60 | —           | —           |

### Schéma

```text
                         ┌──────────────────────┐
                         │      NAS-LAB01       │
                         │                      │
                         │ MGMT:    192.168.50.50
                         │ STORAGE: 10.20.20.50 │
                         │                      │
                         │ /srv/nfs/ltl-vms     │
                         └──────────┬───────────┘
                                    │
                              STORAGE NFS
                           10.20.20.0/24
                                    │
          ┌─────────────────────────┼─────────────────────────┐
          │                         │                         │
   ┌──────▼──────┐           ┌──────▼──────┐           ┌──────▼──────┐
   │   pve-n1    │           │   pve-n2    │           │   pve-n3    │
   │             │           │             │           │             │
   │ MGMT .31    │           │ MGMT .32    │           │ MGMT .33    │
   │ CLUSTER .31 │◄─────────►│ CLUSTER .32 │◄─────────►│ CLUSTER .33 │
   │ STORAGE .31 │           │ STORAGE .32 │           │ STORAGE .33 │
   └──────┬──────┘           └──────┬──────┘           └──────┬──────┘
          │                         │                         │
          └─────────────────────────┼─────────────────────────┘
                                    │
                              CLUSTER / Corosync
                              10.10.10.0/24

                         MGMT : 192.168.50.0/24
                                    │
                                    ▼
                            ┌───────────────┐
                            │   VM03-APP    │
                            │ 192.168.50.60 │
                            │ 1 vCPU / 1 GB │
                            │    / 10 GB    │
                            └───────────────┘
```

---

# 3. Préparation des trois nœuds

Sur chaque serveur Proxmox, il faut commencer par vérifier le nom de machine.

### NODE1

```bash
hostnamectl set-hostname pve-n1
```

### NODE2

```bash
hostnamectl set-hostname pve-n2
```

### NODE3

```bash
hostnamectl set-hostname pve-n3
```

Ensuite, sur **les trois nœuds**, compléter `/etc/hosts` :

```text
192.168.50.31 pve-n1
192.168.50.32 pve-n2
192.168.50.33 pve-n3
192.168.50.50 nas-lab01
```

Tester :

```bash
ping -c 3 pve-n1
ping -c 3 pve-n2
ping -c 3 pve-n3
ping -c 3 nas-lab01
```

---

# 4. Vérification du réseau CLUSTER

Depuis chaque nœud :

```bash
ping -c 3 10.10.10.31
ping -c 3 10.10.10.32
ping -c 3 10.10.10.33
```

Il faut également vérifier le réseau STORAGE :

```bash
ping -c 3 10.20.20.50
```

### À mettre dans le rapport

**Capture d'écran :**

* configuration des interfaces ;
* ping entre les trois nœuds sur `10.10.10.0/24` ;
* ping du NAS sur `10.20.20.50`.

---

# 5. Synchronisation NTP

Sur les trois nœuds :

```bash
timedatectl
```

Vérifier notamment :

```text
System clock synchronized: yes
NTP service: active
```

Une synchronisation horaire correcte est importante pour le fonctionnement du cluster.

---

# 6. Création du cluster Proxmox

Sur **NODE1 uniquement** :

```bash
pvecm create CLUSTER-LTL --link0 10.10.10.31
```

Vérifier :

```bash
pvecm status
```

Puis :

```bash
pvecm nodes
```

À ce stade, NODE1 doit être présent.

---

# 7. Ajout de NODE2 et NODE3

Depuis NODE2 :

```bash
pvecm add 192.168.50.31 --link0 10.10.10.32
```

Puis depuis NODE3 :

```bash
pvecm add 192.168.50.31 --link0 10.10.10.33
```

Ensuite, sur NODE1 :

```bash
pvecm status
```

et :

```bash
pvecm nodes
```

Le résultat attendu est approximativement :

```text
Node  Sts   Votes
1     Online   1
2     Online   1
3     Online   1
```

Et le quorum doit être atteint.

### Preuve à mettre dans le rapport

```bash
pvecm status
```

**Capture d'écran montrant :**

* `CLUSTER-LTL`
* 3 nœuds
* quorum OK
* les nœuds Online.

---

# 8. Configuration du serveur NFS

Sur **NAS-LAB01**, installer NFS :

```bash
apt update
apt install nfs-kernel-server
```

Créer le répertoire :

```bash
mkdir -p /srv/nfs/ltl-vms
```

Configurer `/etc/exports` :

```text
/srv/nfs/ltl-vms 10.20.20.0/24(rw,sync,no_subtree_check)
```

Puis :

```bash
exportfs -ra
systemctl restart nfs-kernel-server
```

Vérifier :

```bash
exportfs -v
```

---

# 9. Ajouter le stockage NFS à Proxmox

Dans l'interface web :

**Datacenter → Storage → Add → NFS**

Configurer :

```text
ID : NFS-LTL
Server : 10.20.20.50
Export : /srv/nfs/ltl-vms
Content : Disk image, ISO image, Container
```

Le stockage doit apparaître comme disponible sur les **trois nœuds**.

On peut également vérifier depuis les nœuds :

```bash
mount | grep NFS-LTL
```

### Preuve demandée

Faire une capture de l'interface Proxmox montrant :

```text
NFS-LTL
pve-n1
pve-n2
pve-n3
```

---

# 10. Création de VM03-APP

Créer une VM :

```text
Nom       : VM03-APP
CPU       : 1 vCPU
RAM       : 1024 MB
Disque    : 10 GB
Stockage  : NFS-LTL
OS        : Ubuntu Server / Debian
IP        : 192.168.50.60
```

Depuis une autre machine, vérifier :

```bash
ping 192.168.50.60
```

---

# 11. Configuration de la haute disponibilité

Dans Proxmox :

**Datacenter → HA → Groups**

Créer :

```text
Nom : HA-LTL
Nœuds :
    pve-n1
    pve-n2
    pve-n3
```

Puis :

**Datacenter → HA → Resources**

Ajouter :

```text
VM03-APP
État : started
Groupe : HA-LTL
```

Vérifier avec :

```bash
ha-manager status
```

---

# 12. Test de migration à chaud

C'est une partie très importante du rapport.

La VM doit initialement être sur **NODE1**.

Depuis une autre machine :

```bash
ping 192.168.50.60
```

Laisser tourner le ping.

Pendant ce temps, dans Proxmox :

**VM03-APP → Migrate → pve-n2**

Choisir :

```text
Mode : Online
Target : pve-n2
```

Le ping continue pendant la migration.

### Exemple de résultat


```text
--- 192.168.50.60 ping statistics ---
100 packets transmitted
99 packets received
1 packets lost
```

Donc :

```text
Paquets perdus : 1
Taux de perte : 1 %
```

La migration à chaud ne redémarre normalement pas complètement la VM : Proxmox transfère son état vers l'autre nœud pendant qu'elle continue à fonctionner.

---

# 13. Test de panne HA

Une fois VM03-APP sur NODE2, vérifier :

```bash
ha-manager status
```

Puis lancer un ping continu :

```bash
ping 192.168.50.60
```

Maintenant, **éteindre brutalement NODE2**.

Par exemple, si c'est une machine virtuelle de laboratoire :

```bash
poweroff
```

ou utiliser l'arrêt brutal prévu par ton environnement de lab.

Mesurer le temps entre :

**A : dernière réponse avant la panne**

et

**B : première réponse après le redémarrage HA de VM03-APP.**

### Exemple de tableau

| Événement                    |    Heure |
| ---------------------------- | -------: |
| Dernière réponse avant panne | 14:32:10 |
| Première réponse après HA    | 14:32:42 |
| Temps de reprise             | **32 s** |
| Paquets perdus               |   **XX** |

Encore une fois, **ne mets pas 32 s dans ton rapport sauf si c'est réellement ton résultat**.

---

# 14. Différence migration à chaud / HA

Tu peux mettre cette explication dans ton rapport :

Lors d'une migration à chaud, la VM continue de fonctionner pendant que son état et sa mémoire sont transférés vers un autre nœud. La coupure réseau est donc très courte et le nombre de paquets perdus doit normalement rester faible.

Lors d'un basculement HA, le serveur qui hébergeait la VM est réellement en panne. La VM ne peut donc plus continuer son exécution sur ce serveur. Le gestionnaire HA détecte la panne, sélectionne un autre nœud disponible et redémarre la VM depuis le stockage partagé.

Le basculement HA entraîne donc une interruption plus importante que la migration à chaud. La durée observée dépend notamment du temps de détection de la panne, du redémarrage de la VM et du temps nécessaire au système invité pour redevenir opérationnel.

La migration à chaud correspond ainsi à un déplacement planifié et quasiment transparent, tandis que le HA correspond à une récupération après une panne.

---

# 15. Retour du nœud en panne

Redémarrer NODE2.

Vérifier :

```bash
pvecm status
```

Puis :

```bash
pvecm nodes
```

Le cluster doit de nouveau afficher les trois nœuds.

Vérifier également :

```bash
ha-manager status
```

### Preuve

Faire une capture montrant les trois nœuds après leur réintégration.

---

# 16. Sauvegarde

Dans Proxmox :

**Datacenter → Backup → Add**

Configurer par exemple :

```text
Node       : pve-n1
Storage    : NFS-LTL
VM         : VM03-APP
Schedule   : Daily
Mode       : Snapshot
```

Faire ensuite une sauvegarde manuelle.

On peut vérifier les fichiers présents sur le NFS :

```bash
ls -lh /srv/nfs/ltl-vms
```

### Preuves

Mettre dans le rapport :

1. capture de la tâche de sauvegarde planifiée ;
2. capture de la sauvegarde manuelle terminée ;
3. capture montrant le fichier de sauvegarde sur le NFS.

---

# 17. Analyse demandée — 3.5

## 3.5.1 Pourquoi 3 nœuds et pas 2 ?

Un cluster de trois nœuds permet d'obtenir une majorité claire pour le quorum.

Avec deux nœuds, si la liaison CLUSTER est coupée, chaque nœud peut potentiellement considérer l'autre comme indisponible. Il n'existe alors pas de majorité claire entre les deux parties.

Avec trois nœuds, une partition réseau peut laisser une partie avec deux nœuds et l'autre avec un seul. Le groupe possédant deux nœuds conserve la majorité.

Le quorum est donc particulièrement important pour éviter des décisions contradictoires et protéger l'intégrité des services et du cluster.

---

## 3.5.2 Pourquoi séparer MGMT, CLUSTER et STORAGE ?

| Réseau      | Fonction                                   |
| ----------- | ------------------------------------------ |
| **MGMT**    | Administration et communication de gestion |
| **CLUSTER** | Communication Corosync entre les nœuds     |
| **STORAGE** | Communication avec le serveur NFS          |

Cette séparation permet d'éviter que le trafic important du stockage ou de la gestion perturbe les communications du cluster.

Elle améliore également la sécurité et permet d'appliquer des règles réseau différentes à chaque type de trafic.

---

## 3.5.3 Migration à chaud contre basculement HA

|                                  | Migration à chaud         | Basculement HA           |
| -------------------------------- | ------------------------- | ------------------------ |
| Situation                        | Déplacement volontaire    | Panne d'un nœud          |
| VM continue son fonctionnement ? | Oui                       | Non pendant la panne     |
| Redémarrage VM                   | Non                       | Oui                      |
| Interruption                     | Très courte               | Plus importante          |
| Paquets perdus                   | Généralement très peu     | Généralement davantage   |
| Objectif                         | Maintenance / équilibrage | Récupération après panne |

Les valeurs exactes doivent être celles obtenues pendant les tests.

---

# 18. Point de défaillance unique

Dans cette architecture de lab, le principal point de défaillance unique est le **NAS-LAB01**.

Même si les trois nœuds Proxmox sont redondants, ils dépendent tous du même serveur NFS.

Si le NAS tombe, le stockage partagé peut devenir indisponible et les mécanismes de migration ou de redémarrage des VMs peuvent être fortement limités.

### Solution pour la production

Pour la production, on pourrait mettre en place un stockage redondant, par exemple :

* une solution de stockage avec plusieurs contrôleurs ;
* deux serveurs de stockage redondants ;
* du stockage distribué comme **Ceph** ;
* plusieurs chemins réseau vers le stockage.

L'objectif est que la panne d'un serveur de stockage ou d'un lien ne rende pas les VMs indisponibles.

---

# 19. Question 3.5.5 — capacité après perte d'un hôte

Pour cette question, il faut reprendre les chiffres du **CDC 1**, car ils ne sont pas présents dans ton message.

La logique est :

```text
Capacité disponible après panne
=
Capacité totale du cluster
-
Capacité du nœud perdu
```

Mais il faut également conserver une marge pour éviter de surcharger les deux nœuds restants.

### Exemple

Si le CDC 1 indique :

```text
Chaque hôte :
4 vCPU disponibles
8 Go RAM disponibles

3 hôtes :
12 vCPU
24 Go RAM
```

et qu'une VM LTL consomme :

```text
1 vCPU
1 Go RAM
```

alors, après la perte d'un hôte :

```text
2 hôtes disponibles
= 8 vCPU
= 16 Go RAM
```

Donc la capacité théorique serait :

```text
16 VMs
```

du point de vue de la RAM, mais il faut vérifier la contrainte CPU et la marge de sécurité.

**Pour donner le nombre exact demandé dans ton devoir, il me faut les chiffres du CDC 1.**

---

# 20. Checklist du livrable final

Tu peux organiser ton rapport comme ceci :

### CDC 3 — Cluster de virtualisation haute disponibilité

**1. Choix de la solution**

* Proxmox VE
* justification en 5 lignes

**2. Architecture**

* schéma des 3 réseaux
* 3 nœuds
* NAS
* VM03-APP

**3. Installation et configuration**

* hostname
* `/etc/hosts`
* NTP
* interfaces réseau

**4. Création du cluster**

* `pvecm create`
* `pvecm add`
* `pvecm status`
* `pvecm nodes`
* capture du quorum

**5. Stockage partagé**

* configuration NFS
* `NFS-LTL`
* capture sur les trois nœuds

**6. VM03-APP**

* 1 vCPU
* 1 Go RAM
* 10 Go
* IP `192.168.50.60`

**7. Migration à chaud**

* NODE1 → NODE2
* ping continu
* nombre de paquets perdus
* captures

**8. Haute disponibilité**

* groupe HA
* VM03-APP en `started`
* `ha-manager status`

**9. Simulation de panne**

* arrêt brutal du nœud
* ping
* temps de reprise
* nombre de paquets perdus
* captures

**10. Retour à la normale**

* redémarrage
* réintégration du nœud
* quorum à 3

**11. Sauvegarde**

* sauvegarde quotidienne
* sauvegarde manuelle
* stockage sur NFS
* captures

**12. Analyse**

* quorum à 3 nœuds
* séparation des réseaux
* migration vs HA
* SPOF du NAS
* capacité après perte d'un hôte

---
