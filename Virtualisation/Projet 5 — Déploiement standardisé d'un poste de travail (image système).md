---
title: Projet 5 — Déploiement standardisé d'un poste de travail (image système)

---

Étape 1 — Définir le cahier des charges

Système d'exploitation : Windows 11 Pro.

Logiciels : navigateur, suite bureautique, lecteur PDF et outils utilisés par les stagiaires, 

Comptes utilisateurs : compte standard pour les stagiaires et éventuellement compte administrateur pour le technicien.

Paramètres réseau : DHCP ou adresse IP fixe, nom du réseau, paramètres DNS si nécessaire.

Paramètres système : langue, fuseau horaire, mises à jour, fond d'écran et paramètres de sécurité

Étape 2 — Préparer le poste de référence

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

Etape 3 - Installation du script

Pour cette étape nous allons utilisé un script trouvé sur Internet

1. Ouvrez Powershell en tant qu'administrateur et entrez le script

2. Attendez ensuite que le téléchargement se fasse
![Capture d'écran 2026-09-18 094110](https://hackmd.io/_uploads/Hy6VTDcYze.jpg)


3. Séléctionnez le mot de passe et le nom d'uilisateur pour le stagiare
![Capture d'écran 2026-09-18 085701](https://hackmd.io/_uploads/rJxeAv9Yzg.jpg)
![Capture d'écran 2026-09-18 085643](https://hackmd.io/_uploads/rkxeRDqYzg.jpg)

4. Séléctionnez pour redemarrez votre ordinateur

Temps d'installation: 7 minutes

Etape 4 - Test sur une seconde machine

1. Refaire l'étape 1, 2 et 3 et comparer le nouveau poste avec le cahier des charges

2. Calculer ensuite le temps pris
![Capture d'écran 2026-09-18 145154](https://hackmd.io/_uploads/HyNp8ncFMg.jpg)

![Capture d'écran 2026-09-18 150302](https://hackmd.io/_uploads/rkwyPn9FMl.jpg)

Ici 9 minutes

Temps pour la première machine: 7 minutes

Temps pour la deuxième machine: 9 minutes







