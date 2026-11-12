---
title: Projet 1 — Infrastructure virtuelle pour une PME

---

# Etape 1 - Intstallation de ESXI

1. Dans Vmware workstation cliquer sur "creat a new virtual machine" puis séléctionner l'option typical
![Capture d'écran 2026-09-16 141922](https://hackmd.io/_uploads/H1mFnl49Ge.png)
2. sur cette écran cliquez directement sur "next" si la dérnière version de workstation est séléctionné sinon séléctionnez-le
![Capture d'écran 2026-09-16 141938](https://hackmd.io/_uploads/HyuKnx4cfg.png)
3. Séléctionner ensuite l'ISO nécessaire pour cette installation, cliquer sur "browse"
![Capture d'écran 2026-09-25 144443](https://hackmd.io/_uploads/BynongE9zl.png)
4. Pour cette installation séléctionnez 8 Go de mémoire vive
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
16. Voilà l'installation terminée
![Capture d'écran 2026-09-25 160133](https://hackmd.io/_uploads/BJrykZEqze.png)


# Etape 2 - Création et configuration des trois machines virtuelles dans le site de ESXI

1. Une fois l'installation terminée entrée le lien https, vous aurez un message d'invertissement, il faudra cliquez sur paramètre avancé et entrer dans le site le nom d'utilisateur qui est "root" puis entrez votre mot de passe
![Capture d'écran 2026-10-05 095607](https://hackmd.io/_uploads/rkC1dfbozx.png)
![Capture d'écran 2026-10-05 095251](https://hackmd.io/_uploads/Syl-Yfbjzg.png)

2. Avant de commencer il faudra avoir au préalablement avoir créer un deuxième dans ESXI. 50 Go de taille de préférence.
![Capture d'écran 2026-10-05 110226](https://hackmd.io/_uploads/B1PGczWjfe.png)

3. Aller ensuite dans "machine virtuelle" et séléctionnez "Créer/Enregistrer une machine virtuelle"
![Capture d'écran 2026-10-05 110455](https://hackmd.io/_uploads/r1i1hG-oze.png)
4. Séléctionnez "Créer une machine virtuelle"
![Capture d'écran 2026-10-05 110512](https://hackmd.io/_uploads/ByNx2GWofe.png)
5. Séléctionnez le nom de la machine puis le système d'exploitation
![Capture d'écran 2026-10-05 110647](https://hackmd.io/_uploads/S1vg3zboMl.png)
6. Séléctionnez ensuite le disque que vous avez créer
![Capture d'écran 2026-10-05 110655](https://hackmd.io/_uploads/rkjxnGZozx.png)
7. Personnaliser ensuite les paramètre de la machine virtuelle
![Capture d'écran 2026-10-05 110746](https://hackmd.io/_uploads/HyJWhzZize.png)
8. Important, dans le "lecteur CD/DVD" séléctionnez le fichier ISO du système d'exploitation. Si il ne s'affiche pas cliquez sur "télécharger" et séléctionnez le fichier ISO (le téléchargement peut prendre du temps)
![Capture d'écran 2026-10-05 113755](https://hackmd.io/_uploads/BycWnz-ofe.png)
![Capture d'écran 2026-10-05 113632](https://hackmd.io/_uploads/rkHu1QWjzg.png)
9. Répétez cette opération pour les trois machines virtuelles
![Capture d'écran 2026-10-05 140038](https://hackmd.io/_uploads/BJnWnMZofe.png)
