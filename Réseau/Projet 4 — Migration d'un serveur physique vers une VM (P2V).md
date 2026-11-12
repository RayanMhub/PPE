---
title: Projet 4 — Migration d'un serveur physique vers une VM (P2V)

---

## 1. Identification du serveur

Le serveur physique choisi pour la migration est un serveur **Windows Server 2022** ayant pour rôle de **serveur de fichiers**.

### Configuration avant migration

| Élément    | Configuration       |
| ---------- | ------------------- |
| Système    | Windows Server 2022 |
| Processeur | 4 cœurs             |
| RAM        | 8 Go                |
| Stockage   | 64 Go SSD          |
| Réseau     | 1 carte Ethernet    |
| Rôle       | Serveur de fichiers |
| Adresse IP | 192.168.1.10        |

![Capture d'écran 2026-10-08 101452](https://hackmd.io/_uploads/rk0jZ0Vsfx.png)


L'objectif est de reproduire ce serveur sous forme de **machine virtuelle avec VMware Workstation**.

## 2. Choix de l'outil

Pour cette migration, nous utilisons **VMware Workstation**.


Création d'une nouvelle VM dans VMware Workstation et **reconstruire le serveur** avec une configuration équivalente.

Pour un environnement pédagogique, la deuxième méthode est plus simple et permet de comparer clairement le serveur physique et son équivalent virtuel.

## 3. Création de la machine virtuelle

Dans VMware Workstation, nous créons une nouvelle machine virtuelle.

### Configuration de la VM

* **Nom :** SRV-FICHIERS-VM
* **Système :** Windows Server 2022
* **Processeurs :** 4 vCPU
* **Mémoire :** 8 Go RAM
* **Disque virtuel :** 64 Go
* **Réseau :** NAT ou Bridged selon l'environnement
* **Firmware :** UEFI

![Capture d'écran 2026-10-08 101700](https://hackmd.io/_uploads/HJKhbCVozl.png)


Nous installons ensuite Windows Server 2022 sur la machine virtuelle.

Après l'installation, nous configurons le serveur afin qu'il possède les mêmes fonctionnalités que le serveur physique :

1. Installation des mises à jour.
2. Configuration du réseau.
3. Configuration du nom du serveur.
4. Création des dossiers partagés.
5. Configuration des utilisateurs et permissions.
6. Vérification de l'accès aux fichiers.

## 4. Comparaison avant / après

| Élément   | Serveur physique        | VM VMware Workstation         |
| --------- | ----------------------- | ----------------------------- |
| Système   | Windows Server 2022     | Windows Server 2022           |
| CPU       | 4 cœurs                 | 4 vCPU                        |
| RAM       | 8 Go                    | 8 Go                          |
| Stockage  | 64 Go SSD              | 64 Go virtuels               |
| Réseau    | Carte Ethernet physique | Carte réseau virtuelle VMware |
| Rôle      | Serveur de fichiers     | Serveur de fichiers           |
| Partages  | Fonctionnels            | Fonctionnels                  |
| Démarrage | Matériel physique       | VMware Workstation            |
| Gestion   | Serveur physique        | Machine virtuelle             |

### Tests effectués

Après avoir démarré la VM, plusieurs tests sont réalisés :

* démarrage correct de Windows Server ;
* connexion avec un compte administrateur ;
* vérification de l'adresse IP ;
* test de la connexion réseau ;
* accès aux dossiers partagés ;
* lecture et écriture de fichiers ;
* vérification de l'utilisation du processeur et de la RAM.

**Résultat :** les fonctions principales du serveur sont disponibles sur la machine virtuelle.

## 5. Problèmes et risques

### Pilotes

Dans VMware Workstation, le matériel présenté à Windows est virtuel. Les pilotes du serveur physique ne sont donc pas nécessairement utilisés.

Il faut notamment vérifier que la carte réseau virtuelle et les autres périphériques fonctionnent correctement.

### Réseau

La configuration réseau doit être vérifiée après la migration.

Le mode **NAT** permet à la VM d'utiliser la connexion réseau de l'ordinateur hôte. Le mode **Bridged** permet à la VM d'apparaître comme une machine distincte sur le réseau local.

### Licences

La licence Windows Server doit être vérifiée. Le changement de matériel physique vers du matériel virtuel peut nécessiter une nouvelle activation selon le type de licence utilisé.

### Performances

Les performances de la VM dépendent directement des ressources disponibles sur l'ordinateur qui exécute VMware Workstation.

Par exemple, si l'ordinateur possède seulement 8 Go de RAM et que la VM utilise également 8 Go, le système hôte risque de manquer de mémoire.

### Sauvegarde

Avant toute migration, une sauvegarde des données doit être réalisée. Cela permet de restaurer le serveur original en cas de problème.

## 6. Rapport de migration

### Rapport de migration vers VMware Workstation

**Objectif :**
L'objectif de ce projet est de remplacer un serveur physique Windows Server 2022 par une machine virtuelle exécutée avec VMware Workstation.

**Configuration initiale :**
Le serveur physique possède 4 cœurs CPU, 8 Go de RAM et 100 Go de stockage. Il est utilisé comme serveur de fichiers.

**Méthode :**
Une machine virtuelle Windows Server 2022 a été créée dans VMware Workstation avec une configuration similaire au serveur physique. Les fonctionnalités du serveur, notamment les dossiers partagés et la configuration réseau, ont ensuite été reproduites dans la VM.

**Tests :**
Après l'installation et la configuration, la VM a été démarrée. Le réseau, les partages de fichiers, la lecture et l'écriture des données ont été testés.

**Résultat :**
La machine virtuelle fonctionne correctement et assure le même rôle que le serveur physique. La virtualisation permet notamment de déplacer et sauvegarder plus facilement le serveur.

**Limites :**

* Les performances dépendent de l'ordinateur hôte.
* La configuration réseau peut nécessiter des modifications.
* Certains logiciels peuvent nécessiter une nouvelle activation.
* Les performances du stockage virtuel peuvent être différentes du serveur physique.
* VMware Workstation est principalement adapté à un environnement de test ou de laboratoire plutôt qu'à une infrastructure serveur professionnelle.

**Risques identifiés :**

* Perte de données lors de la migration.
* Mauvaise configuration réseau.
* Manque de RAM ou de CPU sur l'ordinateur hôte.
* Problèmes de compatibilité avec certaines applications.
* Problèmes d'activation de Windows Server.
* Panne de l'ordinateur hôte entraînant l'indisponibilité de la VM.




