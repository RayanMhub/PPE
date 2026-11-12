---
title: Projet 3 — Réseau virtuel isolé (labo de test)

---

**Important !** Avant cette opération il faudra avoir créer et configurer au moins  2 machine virtuelle sur Vmware Worksation

---

**Etape 1 - Création un commutateur/réseau virtuel de type interne**

Pour créer un réseau virtuel il faudra aller dans Vmware Workstation cliquez sur "Edit"->"Virtual Network Editor". Une fois dans "Virtual Network Editor" cliquez sur "Change Settings" afin de pouvoir faire les modifications necéssaire. Cliquez sur "Add Network" afin d'ajouter un réseau et séléctionnez n'importe quel "Vmnet" disponible. Une fois cela fait  Séléctionnez ensuite "Host-only" et entrez l'adresse ip et un masque pour le sous-réseau
![Capture d'écran 2026-10-07 101938](https://hackmd.io/_uploads/ByEJbtmjzg.png)

**Etape 2 - Connection des 2 VM à ce réseau**

Pour conncter les 2 machines virtuelles faites un clique droit sur les machines virtuelles puis séléctionnez "Settings"->"Network Adapter" puis séléctionnez l'option "Custom" et séléctionnez le "Vmnet" que vous avez choisi lors de l'étape précédante
![Capture d'écran 2026-10-07 101957](https://hackmd.io/_uploads/HJOkWtXsMg.png)

**Etape 3 - Vérification qu'aucune de ces VM n'a accès à Internet ni au réseau physique**
Pour véfifier que les VM n'ont pas accès à Internet et réseau physique il faudra aller dans les paramètres réseau et internet de la VM. Deux messages s'afficheront: "Vous n'êtes conncté à aucun réseau" et "pas de connexion Internet"
![Capture d'écran 2026-10-07 110259](https://hackmd.io/_uploads/BkDsnF7ife.png)

**Etape 4 - Ajout d'une VM passerelle avec règles de filtrage**

---


Important ! Pour cette étape il faudra avoir avoir installer et configurer une VM ,de préference un système d'exploitation comme un linux léger comme Ubuntu ce que nous allons utiliser

---


Une fois dans Ubuntu faites un clique droit dans le bureau, séléctionnez "ouvrir un terminal" puis une fois dans le terminal entrez les commandes suivantes:

**Routage activé:**
sudo sysctl -w net.ipv4.ip_forward=1

**Autoriser le trafic sortant**
sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

**NAT pour masquer l’IP interne**
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

**Bloquer tout le reste**
sudo iptables -A FORWARD -j DROP

**Etape 5 - Tester la connectivité entre les VM du labo**

Il faudra verifier les adresses IP de chaque VM. Il faudra entrer les commandes suivantes.

Pour windows:
ipconfig
route print

Pour Ubuntu:
ip addr
ip route

Il faudra avoir comme résultat:
VM1 : 192.168.50.10/24
VM2 : 192.168.50.20/24
VM3 : 192.168.50.30/24
Passerelle : 192.168.50.1



