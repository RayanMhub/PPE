---
title: Projet 5 — Conception réseau complète pour une PME multi-sites

---

**1. Création de la topologie**
PC1 et PC2->Switch1->R1->R2<-Switch2<-PC3 et PC4
![image](https://hackmd.io/_uploads/SkzrBPk2Ge.png)

**2. Configuration des interfaces**

**Configuration interfaces routeurs**
R2
![Capture d'écran 2026-10-16 104843](https://hackmd.io/_uploads/rJClHwJnMl.png)
R1
![Capture d'écran 2026-10-16 104816](https://hackmd.io/_uploads/H1NWSDk3Gg.png)

**Configuration interfaces VPCS**
PC1
![Capture d'écran 2026-10-16 101347](https://hackmd.io/_uploads/H1a96Ly3Gx.png)
PC2
![Capture d'écran 2026-10-16 101708](https://hackmd.io/_uploads/rJkip8k2zl.png)

**Teste de ping**
![image](https://hackmd.io/_uploads/r1qkvPk3fe.png)
![image](https://hackmd.io/_uploads/rJYMPvk2Gl.png)
Les deux tests ont réussi

**3. Configuration du VPN site-à-site**

**Vérification d'abord que les 2 routeurs peuvent communiquer**

Depuis R1: ping 192.0.2.2
![image](https://hackmd.io/_uploads/S19jtDyhfg.png)
Test réussi

Depuis R2: ping 192.0.2.1
![image](https://hackmd.io/_uploads/HkxRFwk2zx.png)
Test réussi

**Configuration des VPN sur les routeurs**
R1
![image](https://hackmd.io/_uploads/SJZwpw13fg.png)

R2
![image](https://hackmd.io/_uploads/S1r56vk2Me.png)

**4. Vérification du tunnel VPN**
![image](https://hackmd.io/_uploads/HyX4oKJhzx.png)

**5. Ajouts des VLAN sur les routeurs**
R1
![Capture d'écran 2026-10-16 134441](https://hackmd.io/_uploads/BJtTCKkhzx.png)
R2
![Capture d'écran 2026-10-16 134616](https://hackmd.io/_uploads/H11AAFk3zl.png)

**6. Adaptation du VPN pour transporter tous les VLAN**
R2
![Capture d'écran 2026-10-16 135223](https://hackmd.io/_uploads/rkW_G5J3fx.png)
R1
![Capture d'écran 2026-10-16 135159](https://hackmd.io/_uploads/ryI_zqy2Gg.png)

**7. Teste de la configuration**
![Capture d'écran 2026-10-16 140002](https://hackmd.io/_uploads/SJcjfqk2ze.png)
