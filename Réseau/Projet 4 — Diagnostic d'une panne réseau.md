---
title: Projet 4 — Diagnostic d'une panne réseau

---

**1. Scénarion de la  panne**

**Contexte**
Un utilisateur signale qu'il n'accède plus au réseau. Le formateur simule une panne (câble, IP, DNS, switch).

**Topologie**
Routeur->Switch->PC
![Capture d'écran 2026-10-15 093506](https://hackmd.io/_uploads/rypFQZAizg.png)

Réseau avant la panne: Le pc ping avec le routeur
![Capture d'écran 2026-10-15 093629](https://hackmd.io/_uploads/SJZqXZAofx.png)

Après la panne: Le pc ne ping plus avec le routeur
![image](https://hackmd.io/_uploads/Hktcib0jzl.png)

**2. Diagnostiquer couche par couche**

**Verfication du routeur**
Dans le routeur entrer "show ip interface brief"
![image](https://hackmd.io/_uploads/Sky90WCoMg.png)

**Verification du PC**
Dans le PC entrer "show ip"
![image](https://hackmd.io/_uploads/HJMLkGAoGx.png)

**3. Identification de la cause racine**

|Symptôme observé|	Cause possible|	Action corrective|
|--|--|--|
|Adresse IP incorrecte|	Mauvaise configuration IP|	Corriger IP et masque|

**4. Résolution de la panne**
Dans le PC il faut entrer la bonne addresse IP donc= "ip 192.168.1.10/24 192.168.1.1"
![image](https://hackmd.io/_uploads/r1yLbMRjGx.png)
