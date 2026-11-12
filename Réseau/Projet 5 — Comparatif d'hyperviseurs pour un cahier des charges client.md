---
title: Projet 5 — Comparatif d'hyperviseurs pour un cahier des charges client

---

**1. Comparaison des trois hyperviseurs**
Critère|Proxmox|VE VMware ESXi| VirtualBox
--|--|--|--
Coût|Gratuit avec abonnements facultatifs|Dépend de l’offre et de la licence| Gratuit pour le paquet de base
Licences| Open source, AGPLv3 principalement| Propriétaire| GPLv3 principalement pour le paquet de base
Administration| Interface Web centralisée, nombreuses fonctions| Outils d’administration orientés serveurs| Interface graphique simple
Performances| Potentiel élevé sur serveur dédié |Potentiel élevé sur serveur dédié| Dépend du système hôte et des ressources disponibles
Écosystème| Communauté open source, outils de stockage et de conteneurisation| Écosystème professionnel VMware Documentation| Oracle, extensions et communauté
 
**2. Installation de 2 superviseurs**

**ESXI**

1. Dans Vmware workstation cliquer sur "creat a new virtual machine" puis séléctionner l'option typical
![Capture d'écran 2026-09-16 141922](https://hackmd.io/_uploads/H1mFnl49Ge.png)
2. sur cette écran cliquez directement sur "next" si la dérnière version de workstation est séléctionné sinon séléctionnez-le
![Capture d'écran 2026-09-16 141938](https://hackmd.io/_uploads/HyuKnx4cfg.png)
3. Séléctionner ensuite l'ISO nécessaire pour cette installation, cliquer sur "browse"
![Capture d'écran 2026-09-25 144443](https://hackmd.io/_uploads/BynongE9zl.png)
4. Pour cette installation séléctionnez n'importe quel taille mémoire vive, minimum 4 Gb
![Capture d'écran 2026-09-25 144523](https://hackmd.io/_uploads/SkJh2eV5Gx.png)
5. Séléctionnez ensuite les options dans les images ci-dessous
![Capture d'écran 2026-09-25 144539](https://hackmd.io/_uploads/H1732x4cGl.png)
![Capture d'écran 2026-09-25 144545](https://hackmd.io/_uploads/ByS3he45fl.png)![Capture d'écran 2026-09-25 144550](https://hackmd.io/_uploads/BJYQQ-VqMg.png)
![Capture d'écran 2026-09-25 144558](https://hackmd.io/_uploads/HJg4mZN5zg.png)
(Pour la taille du disque il n'est pas nécessaire de prendre trop grand 50 Go peut suffir)
![Capture d'écran 2026-09-25 144606](https://hackmd.io/_uploads/HyHNXbV9Ml.png)
![Capture d'écran 2026-09-25 144612](https://hackmd.io/_uploads/SJBrX-E5Gl.png)
6. Cliquez enfin sur "finish"
![Capture d'écran 2026-09-25 144617](https://hackmd.io/_uploads/SJPnnxN9zl.png)
7. Avant de lancer la machine cliquez sur VM->Setting->Processors et assurez vous que la première option de "Virtualization engine" est décochée sinon la machine ne pourra pas se lançée
![Capture d'écran 2026-09-25 144634](https://hackmd.io/_uploads/Bk932gVqMg.png)
8. Attendez que l'installation se fasse puis sur cette faite cliquez sur "entrer"
![Capture d'écran 2026-09-25 145148](https://hackmd.io/_uploads/B1T33e49zx.png)
9. Sur cette écran cliquez sur F11
![Capture d'écran 2026-09-25 145209](https://hackmd.io/_uploads/SyyahgEqze.png)
10. Séléctionnez ensuite le disque que vous avez créer
![Capture d'écran 2026-09-25 150230](https://hackmd.io/_uploads/Hy-62x49Gl.png)
11. Séléctionnez la langue de votre clavier
![Capture d'écran 2026-09-25 150243](https://hackmd.io/_uploads/By4ahl45Ml.png)
12. Entrez un mot de passe
![Capture d'écran 2026-09-25 150315](https://hackmd.io/_uploads/r1gI63xEczg.png)
13. Sur cette écran cliquez sur "écran"
![Capture d'écran 2026-09-25 150327](https://hackmd.io/_uploads/B1OT2gE9fg.png)
14. Cliquez sur F11 pour installer la machine
![Capture d'écran 2026-09-25 150340](https://hackmd.io/_uploads/Byi6hxVczg.png)
15. Cliquez sur "entrer" pour le reboot de la machine afin de completer l'installation
![Capture d'écran 2026-09-25 150507](https://hackmd.io/_uploads/HkC6nxE9ze.png)
16. Attendez que l'installtion se fasse 
![Capture d'écran 2026-09-25 160133](https://hackmd.io/_uploads/BJrykZEqze.png)


**Proxmox**
1. Dans Vmware workstation cliquer sur "creat a new virtual machine" puis séléctionner l'option typical
![Capture d'écran 2026-09-25 112426](https://hackmd.io/_uploads/HJ2mTxE5Mx.png)
2. sur cette écran cliquez directement sur "next" si la dérnière version de workstation est séléctionné sinon séléctionnez-le
![Capture d'écran 2026-09-25 112431](https://hackmd.io/_uploads/HJR7peV9fg.png)
3. Séléctionner ensuite l'ISO nécessaire pour cette installation, cliquer sur "browse"
![Capture d'écran 2026-09-25 112445](https://hackmd.io/_uploads/Sy7EpxV5fg.png)
4. Pour la séléction du type de la machine virtuelle prenez "Linux"->"Debian 12.x 64-bit"
![Capture d'écran 2026-09-25 112524](https://hackmd.io/_uploads/SkPEaxEqMx.png)
5. Choisissez un nom pour votre machine
![Capture d'écran 2026-09-25 112548](https://hackmd.io/_uploads/BJtVag45Ml.png)
6. Choisissez ensuite le nombre de processeur pour la machine virtuelle
![Capture d'écran 2026-09-25 112742](https://hackmd.io/_uploads/B1iE6xV5zx.png)
7. Pour cette installation séléctionnez n'importe quel taille de mémore vive, minimum 4 Gb
![Capture d'écran 2026-09-25 112809](https://hackmd.io/_uploads/H1pV6eNcGg.png)
8. Séléctionnez ensuite les options dans les images ci-dessous
![Capture d'écran 2026-09-25 112837](https://hackmd.io/_uploads/B11HpxE9Ge.png)
![Capture d'écran 2026-09-25 112847](https://hackmd.io/_uploads/rk-BTgNcfe.png)
![Capture d'écran 2026-09-25 112853](https://hackmd.io/_uploads/SJXBaxVcMl.png)
![Capture d'écran 2026-09-25 112859](https://hackmd.io/_uploads/SJHH6gV5Mx.png)
(Pour la taille du disque il n'est pas nécessaire de prendre trop grand 50 Go peut suffir)
![Capture d'écran 2026-09-25 112911](https://hackmd.io/_uploads/rywBagV5Ml.png)
![Capture d'écran 2026-09-25 112916](https://hackmd.io/_uploads/Sy6SalV9zx.png)
9. Cliquez enfin sur "finish"
![Capture d'écran 2026-09-25 112920](https://hackmd.io/_uploads/r118TgNczx.png)
10. Une fois la machine virtuelle lancée cliquez sur "Install Proxmox VE (Graphical)"
![Capture d'écran 2026-09-25 115548](https://hackmd.io/_uploads/rybI6e45zl.png)
11. Une fois l'installation terminé vous aurez un notification qui apparaîtra, vous n'aurez qu'a cliquez sur "OK"
![Capture d'écran 2026-09-25 115707](https://hackmd.io/_uploads/B1HLaeEqGl.png)
12. Sur l'écran "END USER AGREEMENT (EULA)" cliquez sur "I Agree"
![Capture d'écran 2026-09-25 115737](https://hackmd.io/_uploads/rJD86eE9Me.png)
13. Sur l'écran "Proxmox Virtual Environment (PVE)" cliquez directement sur "Next"
![Capture d'écran 2026-09-25 115753](https://hackmd.io/_uploads/SJKIagE9fx.png)
14. Sur l'écran "Location and Time Zone selection" choisissez votre pays et la langue de votre clavier
![Capture d'écran 2026-09-25 115807](https://hackmd.io/_uploads/S1sLpgE5zl.png)
15. Entrez ensuite votre mot de passe et votre adresse email
![Capture d'écran 2026-09-25 115832](https://hackmd.io/_uploads/H1RUpeEcze.png)
16. Sur l'écran "Management Network Configuration" cliquez directement sur "Next"
![Capture d'écran 2026-09-25 120246](https://hackmd.io/_uploads/HJgDagN5Gx.png)
17. Enfin cliquez sur "Install" et attendez que l'installation se fasse
![Capture d'écran 2026-09-25 120300](https://hackmd.io/_uploads/ryLwaeVqfx.png)
18. Une fois l'installation terminée sur "pve login" entrez "root" et entrez votre mot de passe
![Capture d'écran 2026-09-25 130945](https://hackmd.io/_uploads/B1dwpgV9zg.png)

**3. Observation des différences notables**
On peut noter que que Proxmox et ESXI ont tout les deux une installation et une configuration simple mais qui peut prendre du temps à se a faire.

**4. Construction du tableau comparatif**
Critère|Proxmox|VE VMware ESXi
--|--|--
Coût|Gratuit avec abonnements facultatifs|Dépend de l’offre et de la licence
Licences| Open source, AGPLv3 principalement| Propriétaire
Administration| Interface Web centralisée, nombreuses fonctions| Outils d’administration orientés serveurs
Performances| Potentiel élevé sur serveur dédié |Potentiel élevé sur serveur dédié
Écosystème| Communauté open source, outils de stockage et de conteneurisation| Écosystème professionnel VMware Documentation| 
Temps d'installation | 1 à 2 heure | 1 à 2 heure