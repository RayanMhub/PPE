---
title: MARQUIS_Rayan_TPFinal_Virtualisation_CFC_1

---

# CDC 1 — Dimensionnement de la plateforme et choix du processeur

## 1. Besoin CPU

### 1.1 Total de vCPU

**VM critiques :**

* SRV-DC01 : 2 vCPU
* SRV-DC02 : 2 vCPU
* SRV-SQL01 : 8 vCPU
* SRV-ERP01 : 8 vCPU

**Total critiques :**

2 + 2 + 8 + 8 = **20 vCPU**

**VM standard :**

4 + 8 + 8 + 2 + 2 + 2 + 4 + 2 + 2 + 2 = **36 vCPU**

Correction : en reprenant toutes les VM standard du tableau :

* FILE01 : 4
* RDS01 : 8
* RDS02 : 8
* WEB01 : 2
* WEB02 : 2
* MON01 : 4
* BKP01 : 4
* PRINT01 : 2
* TEST01 : 2
* TEST02 : 2
* TEST03 : 2

Total standard :

4 + 8 + 8 + 2 + 2 + 4 + 4 + 2 + 2 + 2 + 2 = **40 vCPU**

### 1.2 Application de l'overcommit

Pour les VM critiques, le ratio est **1:1** :

20 / 1 = **20 threads physiques**

Pour les VM standard, le ratio est **3:1** :

40 / 3 = **13,33 threads physiques**

Besoin total avant croissance :

20 + 13,33 = **33,33 threads**

Avec une croissance de 30 % :

33,33 × 1,30 = **43,33 threads**

Arrondi à l'entier supérieur :

➡️ **44 threads physiques nécessaires au total**

---

# 2. Besoin RAM

RAM totale des VM :

8 + 8 + 64 + 32 + 16 + 48 + 48 + 4 + 4 + 8 + 16 + 4 + 4 + 4 + 4

= **272 Go**

Croissance de 30 % :

272 × 1,30 = **353,6 Go**

➡️ Besoin RAM prévu : **353,6 Go**

Il n'y a aucun overcommit RAM.

---

# 3. Besoin stockage

Disques des VM :

100 + 100 + 800 + 300 + 2000 + 300 + 300 + 80 + 80 + 200 + 200 + 80 + 60 + 60 + 60

= **4 720 Go**

Soit **4,72 To**.

Avec 30 % de croissance :

4 720 × 1,30 = **6 136 Go**

Soit **6,136 To** de données.

Le client demande de conserver **20 % d'espace libre**.

La capacité utile nécessaire est donc :

6 136 / 0,80 = **7 670 Go**

➡️ **Volume utile à prévoir : 7,67 To**

### RAID 10

En RAID 10, environ 50 % de la capacité brute est disponible.

Capacité brute :

7,67 × 2 = **15,34 To**

➡️ **Il faut acheter environ 15,34 To de capacité brute en RAID 10.**

En pratique, on choisirait une capacité commerciale légèrement supérieure à cette valeur.

---

# 4. Dimensionnement par hôte — N+1

Le cluster possède **3 hôtes** et doit continuer à fonctionner avec seulement **2 hôtes**.

Il faut donc répartir la charge totale prévue sur 2 hôtes.

### CPU

Besoin total : **44 threads**

44 / 2 = **22 threads par hôte**

Il faut ensuite ajouter la réserve hyperviseur :

* 2 cœurs
* soit 4 threads

22 + 4 = **26 threads par hôte**

➡️ **Minimum : 26 threads par hôte**

### RAM

Besoin total : **353,6 Go**

353,6 / 2 = **176,8 Go par hôte**

Réserve hyperviseur :

176,8 + 8 = **184,8 Go**

➡️ **Minimum : 184,8 Go de RAM par hôte**

---

# 5. Configuration RAM commerciale

Les barrettes disponibles sont de 32 ou 64 Go.

Il faut au minimum 184,8 Go.

Une configuration de :

**3 × 64 Go = 192 Go**

convient.

Chaque hôte aura donc :

➡️ **192 Go de RAM**

Vérification :

192 - 8 Go de réserve hyperviseur = **184 Go disponibles**

Pour deux hôtes :

184 × 2 = **368 Go**

368 Go > 353,6 Go nécessaires.

➡️ La configuration respecte donc le N+1.

---

# 6. Vérification de la plus grosse VM

La plus grosse VM est :

**SRV-SQL01**

* 8 vCPU
* 64 Go RAM
* 800 Go disque

Un hôte possède au minimum :

* 26 threads CPU
* 192 Go RAM

La VM SQL nécessite seulement :

* 8 vCPU < 26 threads
* 64 Go RAM < 192 Go

➡️ **La plus grosse VM peut donc fonctionner sur un seul hôte.**

---

# 7. Compatibilité des processeurs

| Processeur                 | Cœurs / threads | Compatible ? | Justification                                                                                                                                  |
| -------------------------- | --------------: | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **P1 Xeon Silver 4510**    |         12 / 24 | ❌ Non        | Seulement 24 threads, alors qu'il faut 26 threads par hôte                                                                                     |
| **P2 Xeon Gold 6526Y**     |         16 / 32 | ✅ Oui        | 32 threads disponibles, donc supérieur aux 26 requis                                                                                           |
| **P3 EPYC 9124**           |         16 / 32 | ✅ Oui        | 32 threads disponibles, suffisant pour le besoin                                                                                               |
| **P4 EPYC 9354**           |         32 / 64 | ✅ Oui        | 64 threads, largement suffisant                                                                                                                |
| **P5 Ampere Altra Q64-22** |         64 / 64 | ❌ Non        | Architecture ARM alors que les VM sont principalement x86-64 Windows Server 2022 ; incompatibilité avec la plateforme de virtualisation prévue |

### Remarque sur P5

Le problème du P5 n'est pas sa puissance brute. Il possède beaucoup de cœurs et un TDP faible.

Le problème principal est son **architecture ARM**. Les VM Windows Server 2022 et Ubuntu/Debian prévues sont basées sur une plateforme x86-64. Il faudrait vérifier une compatibilité ARM spécifique de l'hyperviseur et des systèmes invités, ce qui ne correspond pas au cahier des charges fourni.

---

# 8. Comparaison des processeurs compatibles

| Processeur         | Threads | Prix / hôte | Prix pour 3 hôtes |   TDP |
| ------------------ | ------: | ----------: | ----------------: | ----: |
| P2 Xeon Gold 6526Y |      32 |   3 100 CHF |     **9 300 CHF** | 195 W |
| P3 EPYC 9124       |      32 |   1 400 CHF |     **4 200 CHF** | 200 W |
| P4 EPYC 9354       |      64 |   3 400 CHF |    **10 200 CHF** | 280 W |

Le P1 est éliminé car il ne possède que 24 threads.

Le P5 est éliminé pour la compatibilité d'architecture.

Entre les processeurs compatibles, le **P3** fournit 32 threads par hôte, soit 6 threads de marge au-dessus du minimum de 26.

Sur 3 hôtes :

3 × 32 = **96 threads physiques**

Avec la réserve hyperviseur :

96 - (3 × 4) = **84 threads utilisables**

Le besoin après croissance est de 44 threads.

Il existe donc une marge importante.

Le P3 coûte également :

3 × 1 400 = **4 200 CHF**

contre 9 300 CHF pour le P2 et 10 200 CHF pour le P4.

Son TDP de 200 W reste proche du P2 (195 W) et nettement inférieur au P4 (280 W).

---

# 9. Configuration retenue

### Par hôte

* **1 × AMD EPYC 9124 (P3)**
* 16 cœurs / 32 threads
* **192 Go RAM**
* 1 seul socket
* Réserve hyperviseur : 4 threads + 8 Go RAM

### Cluster

* **3 hôtes identiques**
* 3 × P3
* 3 × 192 Go RAM
* **96 threads physiques au total**
* **576 Go RAM installée au total**

Le cluster respecte le fonctionnement N+1 : même avec la perte d'un hôte, les deux hôtes restants disposent de suffisamment de CPU et de RAM pour supporter la charge prévue.

---

# 10. Tableau récapitulatif

| Ressource             | Besoin total prévu | Besoin sur 2 hôtes |            Par hôte retenu |
| --------------------- | -----------------: | -----------------: | -------------------------: |
| CPU                   |         44 threads |       22 + réserve |             **32 threads** |
| RAM                   |           353,6 Go |    176,8 + réserve |                 **192 Go** |
| Stockage utile        |        **7,67 To** |   Stockage partagé |         **7,67 To utiles** |
| Stockage brut RAID 10 |       **15,34 To** |   Stockage partagé | **15,34 To bruts minimum** |

---

# 11. Recommandation finale

Le processeur recommandé est le **P3 — AMD EPYC 9124**.

Il fournit **32 threads par hôte**, alors que le besoin minimum est de 26 threads par hôte avec la réserve hyperviseur. Il conserve donc une marge de capacité.

Pour 3 hôtes, le coût des processeurs est de seulement **4 200 CHF**, contre 9 300 CHF pour le P2 et 10 200 CHF pour le P4.

Son TDP de **200 W** reste raisonnable et sa capacité est suffisante pour la charge prévue et la croissance de 30 %.

La configuration retenue est donc :

**3 × AMD EPYC 9124 + 192 Go RAM par hôte**, avec environ **7,67 To utiles** de stockage partagé en RAID 10, nécessitant environ **15,34 To bruts**.

---

# 12. Réponse au commercial concernant le P5

Le P5 possède effectivement 64 cœurs pour 1 600 CHF, mais le nombre de cœurs ne suffit pas à garantir sa compatibilité avec notre plateforme.
Notre infrastructure repose principalement sur des VM x86-64, notamment Windows Server 2022, alors que le P5 utilise l'architecture ARM.
Il faudrait donc vérifier la compatibilité de l'hyperviseur et des systèmes invités avant de pouvoir l'utiliser.
Le P3, en architecture x86-64, fournit déjà 32 threads par hôte, soit suffisamment pour notre besoin de 26 threads avec la réserve hyperviseur.
Nous retenons donc le P3, qui répond au cahier des charges tout en limitant le coût et la consommation.
