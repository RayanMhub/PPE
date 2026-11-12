---
title: Projet 3 - Migration et sauvegarde d'un poste existant

---

Etape 1 - Préparation de la machine virtuelle Windows 11

Important: Il faut avoir au préalablement installer et configurer Vmare Workstation et avoir l'iso windows 11

1. Sur Vmware workstation cliquez sur "create e new virtual machine" et séléctionnez l'option "Typical"
![Capture d'écran 2026-09-15 070247](https://hackmd.io/_uploads/HJfHfdUFGl.png)

2.  Cliquez sur "Browse" et séléctionnez l'iso Windows 11 que vous avez télécharger
![Capture d'écran 2026-09-15 070353](https://hackmd.io/_uploads/rJFBzuLKzx.png)

3. Séléctionnez ensuite la version windows 11
![Capture d'écran 2026-09-15 070412](https://hackmd.io/_uploads/BkCUfuIFfe.png)

4. Nommer la machine virtuelle selon votre choix
![Capture d'écran 2026-09-15 070453](https://hackmd.io/_uploads/HytDzuUtGe.png)

5. Dans "choose encryption type" chosissez la seconde option et generez ensuite un mot de passe
![Capture d'écran 2026-09-15 070507](https://hackmd.io/_uploads/S1x_fu8tzl.png)

6. Chosissez ensuite l'espace de stockage (64GB est recommendé) et séléctionnez "store virtual disk as a singke file"
![Capture d'écran 2026-09-15 070526](https://hackmd.io/_uploads/BJuOzu8FGx.png)

7. Si vous souhaitez faire d'autre modification de votre vous pouvez les faire dans "Customize hardware" sinon cliquez sur "Finish"
![Capture d'écran 2026-09-15 070602](https://hackmd.io/_uploads/H1kKMu8YGx.png)

8. Séléctionnez ensuite les options suivantes selon vos préférences
![Capture d'écran 2026-09-15 070747](https://hackmd.io/_uploads/r1NFf_8KMg.png)
![Capture d'écran 2026-09-15 070819](https://hackmd.io/_uploads/By3YG_Itzl.png)

9.  Cliquez sur "Installer Windows 11"
![Capture d'écran 2026-09-15 070837](https://hackmd.io/_uploads/H1Z9MdIKfe.png)
10. Entrez la clé de produit si vous l'avez, sinon cliquez "Je n'ainpas de clé de produit clé(Product Key)"
![Capture d'écran 2026-09-15 070856](https://hackmd.io/_uploads/SJuozuIKGl.png)

11. Séléctionnez ensuite k'image que vous souhaitez, dans notre cas se sera "windows 11 professionnel"
![Capture d'écran 2026-09-15 070936](https://hackmd.io/_uploads/r1TjG_UKGl.png)

12. Acceptez les conditions du contrat de licence
![Capture d'écran 2026-09-15 071000](https://hackmd.io/_uploads/B1QhfdLYGl.png)

13. Séléctionnez l'emplacement d'installation de Windows 11
![Capture d'écran 2026-09-15 071151](https://hackmd.io/_uploads/HJF3zdItGe.png)

14. Cliquez sur "Installer"
![Capture d'écran 2026-09-15 071216](https://hackmd.io/_uploads/SyX6z_ItMx.png)

15. Attendez que l'installation se fasse
![Capture d'écran 2026-09-15 071228](https://hackmd.io/_uploads/B196fdLFMe.png)

16. Séléctionnez ensuite les options suivantes selon votre choix
![Capture d'écran 2026-09-15 073123](https://hackmd.io/_uploads/BJmpT_IFMl.png)
![Capture d'écran 2026-09-15 073158](https://hackmd.io/_uploads/r1AT6dUKMl.png)
![Capture d'écran 2026-09-15 073210](https://hackmd.io/_uploads/B1HRpu8tze.png)
![Capture d'écran 2026-09-15 073803](https://hackmd.io/_uploads/SksCau8Fze.png)
![Capture d'écran 2026-09-15 074226](https://hackmd.io/_uploads/B1MyRu8Yfe.png)
![Capture d'écran 2026-09-15 074403](https://hackmd.io/_uploads/B1P1R_LFMl.png)
![Capture d'écran 2026-09-15 075536](https://hackmd.io/_uploads/rkokCdIYGl.png)
![Capture d'écran 2026-09-15 080204](https://hackmd.io/_uploads/rJWlCOLKGg.png)
![Capture d'écran 2026-09-15 080220](https://hackmd.io/_uploads/ByVxRu8FGx.png)
![Capture d'écran 2026-09-15 080232](https://hackmd.io/_uploads/ByixROUFfl.png)
![Capture d'écran 2026-09-15 080248](https://hackmd.io/_uploads/SkAlR_Itfl.png)
![Capture d'écran 2026-09-15 080304](https://hackmd.io/_uploads/Bk4WC_8YMg.png)
![Capture d'écran 2026-09-15 080318](https://hackmd.io/_uploads/HywbC_Itzx.png)
![Capture d'écran 2026-09-15 080835](https://hackmd.io/_uploads/ByefRd8tzl.png)
![Capture d'écran 2026-09-15 080915](https://hackmd.io/_uploads/rkVGRdIYfl.png)
![Capture d'écran 2026-09-15 080934](https://hackmd.io/_uploads/SJuMRuLKGe.png)
![Capture d'écran 2026-09-15 080948](https://hackmd.io/_uploads/HJhMC_8tzl.png)
![Capture d'écran 2026-09-15 081009](https://hackmd.io/_uploads/H1G7AOIYfl.png)
![Capture d'écran 2026-09-15 081029](https://hackmd.io/_uploads/H1smCOUtfx.png)
![Capture d'écran 2026-09-15 081040](https://hackmd.io/_uploads/SyfNA_UYzl.png)

17. Attendez que les téléchargements se fassent
![Capture d'écran 2026-09-15 081217](https://hackmd.io/_uploads/Sk5wC_UtMl.png)

18. Voilà Windows 11 installé
![Capture d'écran 2026-09-15 113539](https://hackmd.io/_uploads/S1xYbc8YMe.png)

Etape 2 - Création de données test

1. Créez trois fichiers distinc afin de les retrouver lors de la migration de données. Ici on a crée un fichier_test.txt, image_test.png et document_test.pdf
![Capture d'écran 2026-09-16 101028](https://hackmd.io/_uploads/SJX2f0DtMe.png)
![Capture d'écran 2026-09-16 102249](https://hackmd.io/_uploads/SJQ3fAPKMg.png)
![Capture d'écran 2026-09-16 101046](https://hackmd.io/_uploads/BJQhzCvtGg.png)

Etape 3 - Faire l'inventaire de la machine virtuelle

L'inventaire de la machine nous permettra de relever les informations de la machine virtuelle

1. Allez dans Paramètre->Système->Information du système
![Capture d'écran 2026-09-16 103053](https://hackmd.io/_uploads/HJ9ZN0DKfx.png)

Etape 4 - Sauvegarde des données

Afin de faire une sauvegarde  des données il faudra créer un autre disque virtuel et l'initialiser

1. Allez dans "gestion de disque" (clique droit sur le bouton windows)
![f72d398b-77a2-4c05-8b64-fabe8d6d0120](https://hackmd.io/_uploads/HJRfxy_tzg.jpg)
![Capture d'écran 2026-09-16 103932](https://hackmd.io/_uploads/SJzjZkOKMx.png)


2. Cliquez ensuite sur "action" puis sur "créer un disque dur virtuel" 
![Capture d'écran 2026-09-16 103932](https://hackmd.io/_uploads/Hyn7e1uKfx.png)

3. Créez ensuite votre second disque en séléctionnant l'emplacement, la taille, le format du disque virtuel et le type de disque dur virtuel
![Média](https://hackmd.io/_uploads/Sk-tQJ_Yzx.jpg)

4. Une fois le second disque virtuel créer fermer et entrer de nouveau dans "gestion de disque" un message apparaîtra pour initialiser le disque. Séléctionner le format GPT puis cliquez sur "OK"
![Capture d'écran 2026-09-16 114629](https://hackmd.io/_uploads/rJ8eOy_tMe.png)

5. Faite ensuite un clique droit sur le disque
![Capture d'écran 2026-09-16 114855](https://hackmd.io/_uploads/ByWC_kutGl.png)

6. Cliquez ensuite sur suivant
![Capture d'écran 2026-09-16 114919](https://hackmd.io/_uploads/Bk3mvluKzx.png)

7. Séléctionnez la taille du volume simple en Mo. Cela se fait automatiquement, tout la place du disque est pris
![Capture d'écran 2026-09-16 114931](https://hackmd.io/_uploads/B1XEweutzx.png)

8. Attribuer une lettre de lecteur de votre choix
![Capture d'écran 2026-09-16 115056](https://hackmd.io/_uploads/Bk54wldtGl.png)

9. Séléctionnez "Formater ce volume avec les paramètres suivant" puis choisissez pour "sytème de fichiers" l'option "NFTS", pour "taille d'unité d'allocation" séléctionnez "par défaut" et enfin nommez votre disque comme vous le souhaitez
![Capture d'écran 2026-09-16 115122](https://hackmd.io/_uploads/HJZnvedtfl.png)

10. Cliquer sur "Terminer" et votre disque est prêt pour la sauvegarde
![Capture d'écran 2026-09-16 115154](https://hackmd.io/_uploads/Hku3wxdtzl.png)

Etape 5 - Création du dossier de sauvegarde

1. Créer un dossier de sauvegarde dans le disque que vous avez crée
![Capture d'écran 2026-09-16 133020](https://hackmd.io/_uploads/S13iUWuKMg.png)

2. Ensuite allez dans "Ce PC"->"Disque local"->"Utilisateurs" puis copier-coller votre dossier dans le dossier de sauvgarde du disque 
![Capture d'écran 2026-09-16 133243](https://hackmd.io/_uploads/rkZnI-utMg.png)
![Capture d'écran 2026-09-16 140604](https://hackmd.io/_uploads/r1u3UZdYfx.png)

Etape 6 - Reinstallation de Windows 11

1. Créer un nouvelle machine virtuelle et séléctionner "custom"
![Capture d'écran 2026-09-16 141922](https://hackmd.io/_uploads/r1HsNMdtze.png)

2. Choisissez la dèrnière version de workstation et cliquez sur "suivant"
![Capture d'écran 2026-09-16 141938](https://hackmd.io/_uploads/BkooVzOYMe.png)

3. Séléctionnez l'iso de windows avec "browse"
![Capture d'écran 2026-09-16 142042](https://hackmd.io/_uploads/ByghNGdYMl.png)

4. Séléctionnez windows 11
![Capture d'écran 2026-09-16 142053](https://hackmd.io/_uploads/BJV2VGuKGg.png)

5. Nommez la machine virtuelle selon votre choix
![Capture d'écran 2026-09-16 142107](https://hackmd.io/_uploads/SJshVGuKMl.png)

6.  Séléctionnez la seconde option dans "Choose Encryption Type"
![Capture d'écran 2026-09-16 142120](https://hackmd.io/_uploads/S1XpEzdtMx.png)

7. Séléctoinnez "UEFI"
![Capture d'écran 2026-09-16 142132](https://hackmd.io/_uploads/r1KTEfOKMg.png)

8. Séléctionnez le nombre de procésseur et core souhaitez (l'option par défaut est recommendée)
![Capture d'écran 2026-09-16 142144](https://hackmd.io/_uploads/rJiAVGutfl.png)

9. Choisissez ensuite la mémoire vive selon votre choix
![Capture d'écran 2026-09-16 142154](https://hackmd.io/_uploads/ByEkSzdYGl.png)

10. Pour les options suivantes choisissez celles qui sont affichées sur les images suivantes
![Capture d'écran 2026-09-16 142207](https://hackmd.io/_uploads/SyjJHG_tMx.png)
![Capture d'écran 2026-09-16 142231](https://hackmd.io/_uploads/BkZxBMuFGl.png)
![Capture d'écran 2026-09-16 142241](https://hackmd.io/_uploads/HyLgHzdFfx.png)

11. Pour l'option du disque choisissez deuxième option "use an existing virtual disk"
![Capture d'écran 2026-09-16 142309](https://hackmd.io/_uploads/Hy2gBzuKzg.png)

12. Cliquez ensuite sur "browse" la machine virtuelle précédement utilisé
![Capture d'écran 2026-09-16 142524](https://hackmd.io/_uploads/ByfWSM_Yzx.png)
![Capture d'écran 2026-09-16 142551](https://hackmd.io/_uploads/rysWHMOKfl.png)

13. Changez les paramètres de la machine virtuelle si vous le souhaitez en cliquant sur "customize hardware"
![Capture d'écran 2026-09-16 142609](https://hackmd.io/_uploads/Hkbfrf_tfe.png)

14. Lancer ensuite la machine virtuelle et vous retrouverez les données de l'ancienne machine
![Média (1)](https://hackmd.io/_uploads/ryDXDMOtfl.jpg)









