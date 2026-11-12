---
title: MARQUIS_Rayan_TPFinal_Virtualisation_Partie_1

---

# **PARTIE 1 — Audit de connaissances**

**A. Histoire et concepts fondamentaux**
1. Quelle entreprise a créé les premières machines virtuelles dans les années 1960, et sur quel type d'ordinateur ?
IBM, avec les ordinateurs IBM System/360, dans les années 1960.
2. Pourquoi la virtualisation a-t-elle perdu de son intérêt entre 1980 et 2000 ?
Entre 1980 et 2000, les ordinateurs sont devenus moins chers et plus puissants, tandis que les systèmes x86 étaient moins adaptés à une virtualisation efficace. L'intérêt économique de virtualiser était donc plus faible.
3. Quel produit, sorti en 2001, a permis de virtualiser des processeurs x86 standards ?
VMware Workstation, sorti en 1999, puis VMware GSX Server/ESX ont popularisé la virtualisation x86. Si le cours vise précisément 2001, il s'agit généralement de VMware ESX Server, qui a permis une virtualisation x86 de niveau entreprise.
4. Définissez la virtualisation en une phrase.
La virtualisation consiste à créer une représentation logicielle d'une ressource informatique physique afin de faire fonctionner plusieurs environnements isolés sur le même matériel.
5. Quelle est la différence entre un hôte (host) et un invité (guest) ?
Host (hôte) : machine physique qui fournit les ressources. Guest (invité) : machine virtuelle qui utilise ces ressources.
6. Qu'est-ce qu'un template de VM et à quoi sert-il ?
Un template est une image modèle d'une VM préconfigurée. Il sert à déployer rapidement plusieurs VMs identiques.
7. Un snapshot peut-il remplacer une sauvegarde ? Justifiez.
Non. Un snapshot conserve l'état d'une VM à un instant donné, mais dépend généralement du disque d'origine et n'est pas conçu pour protéger contre toutes les pertes de données ou la destruction du stockage.
8. Citez trois bénéfices concrets de la virtualisation pour une entreprise.
meilleure utilisation du matériel, réduction des coûts matériels et énergétiques,
déploiement, migration et administration plus rapides.
9. Qu'est-ce que l'overhead en virtualisation ?
L'overhead est la consommation supplémentaire de CPU, RAM, I/O, etc. nécessaire au fonctionnement de la couche de virtualisation.
10. Pourquoi un serveur hôte isolé constitue-t-il un SPOF (point de défaillance unique) ?
Si l'unique serveur hôte tombe en panne, toutes les VMs qui y résident deviennent indisponibles : c'est donc un Single Point of Failure (SPOF).

**B. Matériel et extensions de virtualisation**

11. Quel est le nom de l'extension de virtualisation matérielle chez Intel ? Chez AMD ?
Chez Intel : VT-x. Chez AMD : AMD-V.
12. Quel est le rôle des technologies Intel EPT et AMD RVI ?
Intel EPT et AMD RVI/NPT accélèrent la traduction des adresses mémoire des VMs grâce à une traduction matérielle de second niveau (SLAT).
13. Quelle commande Linux permet de vérifier le support de la virtualisation ? Que signifient vmx et svm ?
La commande est la suivante: "grep -E 'vmx|svm' /proc/cpuinfo". vmx = Intel VT-x, svm = AMD-V.
14. Où vérifier sous Windows que la virtualisation est activée ?
Sous Windows : Gestionnaire des tâches -> Performances -> Processeur -> Virtualisation.
15. Dans quel environnement faut-il activer VT-x / AMD-V s'il est désactivé ?
Dans le BIOS/UEFI du serveur ou du PC.
16. Qu'est-ce que la contention d'E/S (I/O contention) ?
a I/O contention se produit lorsque plusieurs VMs utilisent simultanément les mêmes ressources d'entrée/sortie et se disputent la bande passante ou les IOPS.
17. Pourquoi privilégie-t-on des disques NVMe plutôt que des HDD pour héberger des VMs ?
Les NVMe offrent généralement beaucoup plus d'IOPS, une latence plus faible et de meilleurs débits que les HDD, ce qui est particulièrement utile avec de nombreuses VMs.
18. À quoi sert le SR-IOV ?
SR-IOV permet à un périphérique PCIe, notamment une carte réseau, de fournir plusieurs fonctions virtuelles directement aux VMs, avec moins d'overhead.
19. Qu'est-ce que la virtualisation imbriquée (nested virtualization) et pourquoi est-elle utile dans un lab ?
La nested virtualization consiste à exécuter un hyperviseur à l'intérieur d'une VM. Elle est utile pour créer des labs, tester des clusters ou apprendre la virtualisation sans plusieurs serveurs physiques.
20. Pourquoi un hôte de virtualisation a-t-il besoin de plus de bande passante réseau qu'un serveur physique classique ?
Un hôte transporte le trafic de plusieurs VMs : trafic utilisateur, stockage, management, migration, cluster et sauvegardes.

**C. Types de virtualisation**

21. Qu'est-ce que la VDI ? Citez une solution du marché.
VDI (Virtual Desktop Infrastructure) : bureaux utilisateurs hébergés sur des serveurs et accessibles à distance. Exemple : VMware Horizon.
22. Qu'est-ce que le SDN ? Citez une solution du marché.
SDN (Software-Defined Networking) : séparation du contrôle réseau de la transmission des paquets afin de programmer et centraliser le réseau. Exemple : VMware NSX.
23. Qu'est-ce que la virtualisation de stockage ? Citez deux solutions.
La virtualisation du stockage regroupe ou abstrait plusieurs ressources physiques derrière une couche logique. Exemples : Ceph et VMware vSAN.
24. Quel problème résout la virtualisation applicative ?
Elle permet d'exécuter une application dans un environnement isolé ou compatible sans devoir modifier profondément le système d'exploitation hôte.
25. Quelle est la différence fondamentale entre une VM et un conteneur ?
Une VM virtualise une machine complète, avec son propre OS ; un conteneur partage le noyau de l'OS hôte et isole principalement les processus.
26. Pourquoi un conteneur démarre-t-il beaucoup plus vite qu'une VM ?
Parce qu'un conteneur ne démarre pas un OS complet : il lance essentiellement les processus nécessaires en partageant le noyau de l'hôte.
27. Une entreprise veut que 150 employés accèdent à leur bureau Windows depuis n'importe quel appareil. Quel type de virtualisation recommandez-vous ?
VDI, par exemple avec une infrastructure de bureaux Windows virtuels accessibles à distance.
28. Dans Proxmox VE, que sont les LXC ?
Les LXC sont des conteneurs système Linux proposés par Proxmox VE. Ils partagent le noyau Linux de l'hôte, contrairement aux VMs KVM.

**D. Acteurs du marché**

29. Qui a racheté VMware, et en quelle année ?
Broadcom a racheté VMware en 2023, acquisition finalisée le 22 novembre 202
30. Quelle a été la conséquence principale de ce rachat pour les clients ?
Une conséquence majeure a été l'évolution du modèle commercial vers des offres par abonnement et une restructuration du portefeuille VMware. Broadcom a également modifié les portails, licences et modalités de support.
31. Sur quelle technologie de virtualisation repose Proxmox VE ?
Proxmox VE repose principalement sur KVM pour les VMs et LXC pour les conteneurs.
32. Quel est l'hyperviseur de Microsoft et dans quels produits est-il intégré ?
L'hyperviseur Microsoft est Hyper-V. Il est intégré à Windows Server et disponible comme fonctionnalité dans certaines éditions de Windows.
33. Citez deux fournisseurs cloud européens ou suisses répondant à un besoin de souveraineté des données.
Exemples : Infomaniak (Suisse) et Exoscale (Suisse/Europe).
34. Quel est le rôle de Kubernetes ?
Kubernetes orchestre des conteneurs : déploiement, réplication, réseau, équilibrage, montée/descente en charge et redémarrage automatique.
35. Sur quel hyperviseur historique repose XCP-ng ?
XCP-ng repose historiquement sur Xen.

**E. Processeurs et dimensionnement**

36. Quelle est la différence entre l'architecture x86-64 et l'architecture ARM ?
x86-64 et ARM sont deux architectures d'instructions différentes. Elles ont notamment des jeux d'instructions et des mécanismes matériels différents.
37. Pourquoi une VM Windows Server x86 ne peut-elle pas être exécutée sur un hôte à processeur ARM (ex. Ampere Altra) ?
Une VM Windows Server x86 contient du code destiné aux instructions x86-64. Un processeur ARM ne peut pas exécuter directement ces instructions ; il faudrait une émulation/traduction adaptée, avec des contraintes de compatibilité et de performances.
38. Différenciez cœur physique, thread et vCPU.
Cœur physique : unité réelle de calcul du processeur.
Thread : flux d'exécution logique présenté par le CPU, notamment grâce au SMT/Hyper-Threading.
vCPU : processeur virtuel attribué à une VM.
39. Quel gain de performance approximatif apporte l'Hyper-Threading / SMT ?
Il n'y a pas de gain fixe. Selon la charge, le SMT/Hyper-Threading peut apporter typiquement environ 10 à 30 %, mais parfois beaucoup moins ou davantage.
40. Qu'est-ce que l'overcommit (surallocation) CPU ?
L'overcommit CPU consiste à attribuer aux VMs plus de vCPU que le nombre de threads physiques disponibles, en comptant sur le fait que toutes les VMs n'utiliseront pas leur CPU maximal simultanément.
41. Quel ratio d'overcommit CPU est raisonnable pour des charges générales ? Pour des charges critiques ?
Pour des charges générales : environ 2:1 à 4:1 peut être raisonnable selon la charge. Pour des charges critiques : souvent 1:1 à 2:1. Il faut surtout mesurer la contention réelle plutôt que suivre un ratio universel.
42. Calcul : un hôte possède 2 processeurs de 16 cœurs / 32 threads. Overcommit 4:1, VMs à 4 vCPU. Combien de VMs peut-il héberger au maximum ?
2 processeurs × 32 threads = 64 threads.
Avec un ratio 4:1 : 64 × 4 = 256 vCPU.
Chaque VM = 4 vCPU : 256 ÷ 4 = 64 VMs maximum théorique.
43. Calcul : 60 VMs à 2 vCPU, ratio 3:1. Combien de threads physiques faut-il au minimum ?
60 × 2 vCPU = 120 vCPU.
Avec 3:1 : 120 ÷ 3 = 40 threads physiques minimum.
44. Pourquoi évite-t-on l'overcommit de la RAM en production ?
La RAM ne se partage pas aussi facilement que le CPU. Une surallocation excessive peut provoquer du swapping, de la compression mémoire ou une forte dégradation des performances.
45. Que signifie TDP et pourquoi est-ce un critère business ?
TDP = Thermal Design Power. Il indique approximativement la puissance thermique que le système de refroidissement doit être capable de dissiper. C'est un critère business car il influence consommation électrique, refroidissement et coût d'exploitation.
46. Pour 40 petites VMs, privilégiez-vous la fréquence ou le nombre de cœurs ? Et pour une application monothread ?
Pour 40 petites VMs, on privilégie généralement le nombre de cœurs. Pour une application monothread, une fréquence et surtout une performance par cœur élevées sont plus importantes.
47. Qu'est-ce que le dimensionnement N+1 dans un cluster, et pourquoi est-il indispensable ?
N+1 signifie qu'un cluster possède suffisamment de capacité pour continuer à fonctionner même après la perte d'un nœud. C'est essentiel pour maintenir la disponibilité lors d'une panne.

**F. Hyperviseurs**

48. Définissez un hyperviseur.
Un hyperviseur est une couche logicielle qui permet de créer, exécuter et isoler plusieurs machines virtuelles sur un même matériel.
49. Quelle est la différence entre un hyperviseur de Type 1 et de Type 2 ?
Type 1 : s'exécute directement sur le matériel.
Type 2 : fonctionne au-dessus d'un système d'exploitation classique.
50. Citez trois hyperviseurs de Type 1.
VMware ESXi, Microsoft Hyper-V et Xen/XCP-ng.
51. Citez trois hyperviseurs de Type 2.
VMware Workstation, Oracle VirtualBox et Parallels Desktop.
52. Pourquoi un hyperviseur de Type 1 est-il préféré en production ?
Il offre généralement moins de couches intermédiaires, une meilleure maîtrise des ressources et une meilleure intégration aux infrastructures de production.
53. Quelles deux technologies de virtualisation Proxmox VE combine-t-il ?
KVM + LXC.
54. Dans un environnement 100 % Microsoft, quel hyperviseur est le plus cohérent ? Pourquoi ?
Hyper-V, car il est intégré à l'écosystème Microsoft : Windows Server, Active Directory, PowerShell et Failover Clustering.
55. Quel hyperviseur recommandez-vous pour une PME au budget serré souhaitant une solution open source ?
Proxmox VE, qui combine KVM et LXC et est disponible en open source.

**G. Proxmox VE**

56. Sur quel port est accessible l'interface web de Proxmox VE ?
L'interface web est accessible par défaut sur le port 8006, en HTTPS :
"https://adresse-du-serveur:8006"
57. Quel est le nom du pont réseau (bridge) créé par défaut ?
Le bridge créé par défaut est généralement vmbr0.
58. Quel est le rôle de ce pont réseau ?
vmbr0 relie les interfaces réseau des VMs au réseau physique via l'interface réseau de l'hôte.
59. Quel outil en ligne de commande réalise les sauvegardes de VMs sous Proxmox ?
vzdump
60. Quelle commande crée un cluster Proxmox ?
pvecm create NOM_DU_CLUSTER
61. Quelle commande permet à un nœud de rejoindre un cluster existant ?
pvecm add IP_DU_NOEUD_EXISTANT
62. Quelle commande affiche l'état du cluster et du quorum ?
pvecm status
63. Qu'est-ce que le quorum et pourquoi recommande-t-on au minimum 3 nœuds ?
Le quorum est le nombre minimal de votes nécessaires pour qu'un cluster puisse prendre des décisions. Trois nœuds permettent de conserver une majorité en cas de perte d'un nœud.
64. Quel service assure la communication entre les nœuds d'un cluster Proxmox ?
Corosync assure la communication et la gestion du membership/quorum du cluster.
65. Qu'est-ce que Ceph dans un contexte Proxmox ?
Ceph est une solution de stockage distribué permettant notamment de fournir du stockage partagé et redondant aux VMs Proxmox.

**H. VMware ESXi, Hyper-V, RHV**

66. Quelle est l'URL d'accès au client web d'un hôte ESXi ?
https://IP_DU_ESXI/ui
67. Quel est le rôle de vCenter Server ?
vCenter Server centralise la gestion de plusieurs hôtes ESXi et fournit notamment clustering, HA, DRS, vMotion, administration centralisée, etc.
68. Différenciez vSwitch et Port Group.
vSwitch : commutateur virtuel.
Port Group : ensemble logique de ports avec une configuration commune, par exemple un VLAN et des politiques réseau.
69. À quoi sert un port VMkernel ?
Un port VMkernel fournit une interface réseau à l'hyperviseur ESXi pour des fonctions comme management, vMotion, stockage ou vSAN.
70. Qu'est-ce que VMFS ?
VMFS (Virtual Machine File System) est le système de fichiers de VMware conçu notamment pour stocker les fichiers des VMs sur des datastores.
71. Différenciez un disque Thin et un disque Thick.
Thin : espace réellement consommé progressivement selon les besoins.
Thick : espace réservé/alloué à l'avance.
72. Quel est le format de disque virtuel chez VMware ? Chez Hyper-V ? Chez RHV ?
VMware : VMDK.
Hyper-V : VHD/VHDX.
RHV/oVirt : principalement QCOW2 ou RAW.
73. Citez les trois types de commutateurs virtuels Hyper-V et leur usage.
External : accès au réseau physique ;
Internal : communication entre hôte et VMs ;
Private : communication uniquement entre VMs.
74. Différenciez une VM Hyper-V de Génération 1 et de Génération 2.
Génération 1 : matériel virtuel traditionnel, BIOS et périphériques hérités.
Génération 2 : UEFI, Secure Boot et matériel virtuel plus moderne.
75. Différenciez un checkpoint standard et un checkpoint de production.
Checkpoint standard : capture l'état de la VM et de sa mémoire ; adapté aux tests.
Checkpoint de production : utilise les mécanismes de sauvegarde de l'OS invité pour obtenir un état cohérent, adapté aux environnements de production.
76. Comment s'appelle la migration à chaud chez VMware ? Chez Hyper-V ?
VMware : vMotion.
Hyper-V : Live Migration.
77. Quel est l'équivalent Hyper-V de vSphere HA ?
L'équivalent de vSphere HA chez Microsoft est Hyper-V Failover Clustering / Hyper-V Replica selon le besoin, mais pour le redémarrage automatique d'une VM sur un autre hôte, c'est principalement Failover Clustering.

**I. Réseau virtuel**

78. Qu'est-ce qu'un VLAN et quel est son intérêt en virtualisation ?
Un VLAN segmente logiquement un réseau physique. En virtualisation, il permet par exemple de séparer management, stockage, VMs et trafic cluster.
79. Quelle norme IEEE définit le marquage VLAN ?
IEEE 802.1Q.
80. À quoi sert l'agrégation de liens (LACP / bonding) sur un hôte ?
LACP/bonding agrège plusieurs interfaces réseau afin d'améliorer la disponibilité et, selon la configuration, la capacité réseau globale.
81. Pourquoi isoler le réseau de management sur un VLAN dédié ?
Pour isoler les interfaces d'administration du trafic utilisateur et réduire les risques d'accès non autorisé.
82. Pourquoi séparer les réseaux cluster, stockage et VMs ?
Pour éviter qu'un trafic important dans un domaine — par exemple le stockage — dégrade les performances d'un autre domaine, comme les VMs ou le management.
83. Deux VMs hébergées sur deux hyperviseurs différents doivent se pinguer. Citez trois conditions nécessaires.
une connectivité réseau entre les deux hyperviseurs, des VLAN/bridges correctement configurés, des adresses IP et règles firewall permettant le trafic ICMP.
84. Pourquoi un ping vers une VM Windows échoue-t-il souvent par défaut ? Comment le corriger proprement ?
Le pare-feu Windows bloque souvent les requêtes ICMP Echo par défaut selon le profil/configuration. Il faut autoriser proprement la règle ICMP Echo Request dans le pare-feu Windows plutôt que désactiver complètement le firewall.
85. Dans un lab imbriqué, quelle option doit être activée sur la VM qui héberge l'hyperviseur, côté hyperviseur « parent » ?
Il faut activer l'option de virtualisation imbriquée / nested virtualization sur la VM qui héberge l'hyperviseur.

**J. Stockage, haute disponibilité, sauvegarde**

86. Différenciez SAN et NAS.
SAN : fournit principalement du stockage bloc accessible par les serveurs.
NAS : fournit du stockage fichier, généralement via SMB/NFS.
87. Citez un protocole de stockage bloc et un protocole de stockage fichier.
Bloc : iSCSI ou Fibre Channel.
Fichier : NFS ou SMB.
88. Pourquoi un stockage partagé est-il indispensable à la migration à chaud ?
Avec un stockage partagé, les fichiers/disques de la VM restent accessibles depuis le nouvel hôte pendant la migration.
89. Différenciez migration à chaud et basculement HA.
Migration à chaud : déplacement planifié d'une VM en fonctionnement.
Basculement HA : réaction automatique à une panne d'un hôte pour redémarrer ou reprendre la VM ailleurs.
90. Qu'est-ce qu'un heartbeat dans un cluster ?
Le heartbeat est un signal périodique permettant aux nœuds de vérifier que les autres nœuds sont toujours actifs.
91. Énoncez la règle de sauvegarde 3-2-1.
3 copies des données, sur 2 supports différents et 1 copie hors site ou déconnectée.
92. Contre quoi protègent respectivement un snapshot, la HA et une sauvegarde ?
Snapshot : protège surtout contre une erreur ou modification récente.
HA : protège contre la panne d'un hôte.
Sauvegarde : protège contre la perte/corruption/destruction des données et permet une restauration.
93. Pourquoi ne faut-il pas laisser un snapshot actif trop longtemps ?
Parce qu'un snapshot peut augmenter les chaînes de disques, consommer beaucoup d'espace et dégrader les performances ; plus il reste longtemps, plus sa gestion peut devenir complexe.
94. Qu'est-ce qu'un split-brain et comment le quorum l'empêche-t-il ?
Split-brain : deux parties d'un cluster pensent chacune être la partie légitime et peuvent prendre des décisions contradictoires. Le quorum empêche normalement une partition minoritaire de continuer à fonctionner comme cluster actif.
95. Pourquoi un cluster de 2 nœuds sans stockage partagé ne fournit-il pas une vraie haute disponibilité ?
Avec deux nœuds sans stockage partagé, une panne d'un nœud peut laisser l'autre sans accès aux disques des VMs. Il faut donc au minimum une stratégie de stockage/réplication et de quorum adaptée pour obtenir une vraie HA.

**K. Sécurité et cloud**

96. Qu'est-ce qu'une VM Escape ?
Une VM Escape est une vulnérabilité permettant à un code exécuté dans une VM de sortir de son isolation et d'interagir avec l'hyperviseur ou le système hôte.
97. Citez trois mesures de durcissement (hardening) d'un hyperviseur.
appliquer régulièrement les correctifs de sécurité, limiter l'accès administratif et utiliser MFA et désactiver les services/périphériques inutiles et segmenter le réseau de management.
98. Pourquoi activer le MFA sur les consoles d'administration de virtualisation ?
Le MFA ajoute un deuxième facteur d'authentification. Il réduit fortement le risque qu'un mot de passe compromis suffise à prendre le contrôle de l'infrastructure.
99. Différenciez cloud hybride et multi-cloud.
Cloud hybride : combinaison d'un environnement privé/on-premise et d'un cloud public, avec des échanges entre eux. Multi-cloud : utilisation de plusieurs fournisseurs cloud différents.
100. Qu'est-ce que le vendor lock-in et comment la virtualisation multi-plateforme permet-elle de le limiter ?
Le vendor lock-in est la dépendance forte à un fournisseur, rendant difficile ou coûteux le changement de plateforme. Utiliser des technologies et formats compatibles avec plusieurs hyperviseurs, des standards ouverts et des outils multiplateformes permet de réduire cette dépendance.

