---
title: Projet 2 — Snapshots et plan de reprise d'une VM critique

---

**Etape 1 - Créer une VM de test avec une application simple installée**
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

**Etape 2 - Prendre un snapshot avant une modification volontaire**
Avant de faire une snapshot de notre machine virtuelle  il faudra faire une modification à notre machine afin de voir si notre snapshot a vraiment marchée. Pour ça nous allons faire une mise à jour de notre machine
1. Aller dans les paramètre puis dans "windows update" afin de faire toute les mises à jours nécessaires.
![Capture d'écran 2026-10-06 133210](https://hackmd.io/_uploads/SyXWJdzjfg.png)
![Capture d'écran 2026-10-06 134407](https://hackmd.io/_uploads/Syq-1_ziGe.png)
2. Une fois cela  fait il faudra faire un clique droit sur votre machine virtuelle séléctionnez "Snapshot"->"Take Snapshot"
![Capture d'écran 2026-10-06 134914](https://hackmd.io/_uploads/S1GKk_zofg.jpg)
3. Puis nommez votre Snapshot
![Capture d'écran 2026-10-06 134928](https://hackmd.io/_uploads/SyKn1dGozx.jpg)


**Etape 3 - Simuler un incident**
Pour la simulation d'incident de la machine virtuelle il faudra ouvrir l'invite de commande en tant qu'administrateur et taapez la commande suivante: taskkill /IM svchost.exe /F
![Capture d'écran 2026-10-06 144804](https://hackmd.io/_uploads/rJuQg_zszg.png)
**Etape 4 - Restaurer la VM à partir du snapshot**
1. Après avoir "l'incindent" on éteindra la machine virtuelle puis il faudra faire un clique droit sur la machine virtuelle puis séléctionner "Snapshot"->"Revert to Sapshot"
![Capture d'écran 2026-10-06 144856](https://hackmd.io/_uploads/r13QeuMiMl.png)
2. Sur cette écran cliquez sur "Yes"
![Capture d'écran 2026-10-06 144905](https://hackmd.io/_uploads/HJ-EgOMoMl.png)
3. On peut ainsi vérifier que la machine virtuelle est à l'état au moment où nous avons fait notre snapshot
![Capture d'écran 2026-10-06 145041](https://hackmd.io/_uploads/r1rEeOfjzl.png)
**Etape 5 - Mesurer le temps de restauration**
Temps pour la restauration: 2 minutes