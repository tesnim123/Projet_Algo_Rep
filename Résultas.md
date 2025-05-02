# Résultats d’Exécution

Ce fichier illustre les résultats de l’exécution de la simulation des horloges logiques en systèmes distribués, pour les implémentations en **langage C** et **langage Java**.

---

## Partie 1 : Résultats en Langage C

### 1. Horloge Scalaire (Lamport)

```plaintext
[Client 0] Iteration 1
Processus 0: Execution locale...
Resultat: 175
Horloge scalaire mise a jour: 1
Horloge scalaire mise a jour: 2
[Client 0] envoi -> 1: FROM 0 TO 1 | HORLOGE: S 2
[Client 0] recu de 3: FROM 3 TO 0 | HORLOGE: S 8
Horloge scalaire mise a jour: 9
valeur de received value 8:
Message recu : FROM 3 TO 0 | HORLOGE: S 8
[Client 0] Horloge scalaire apres fusion: 9
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 2
Processus 0: Execution locale...
Resultat: 34
Horloge scalaire mise a jour: 10
Horloge scalaire mise a jour: 11
[Client 0] envoi -> 2: FROM 0 TO 2 | HORLOGE: S 11
[Client 0] recu de 2: FROM 2 TO 0 | HORLOGE: S 13
Horloge scalaire mise a jour: 14
valeur de received value 13:
Message recu : FROM 2 TO 0 | HORLOGE: S 13
[Client 0] Horloge scalaire apres fusion: 14
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 3
Processus 0: Execution locale...
Resultat: 117
Horloge scalaire mise a jour: 15
Horloge scalaire mise a jour: 16
[Client 0] envoi -> 3: FROM 0 TO 3 | HORLOGE: S 16
[Client 0] recu de 1: FROM 1 TO 0 | HORLOGE: S 14
Horloge scalaire mise a jour: 17
valeur de received value 14:
Message recu : FROM 1 TO 0 | HORLOGE: S 14
[Client 0] Horloge scalaire apres fusion: 17
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 4
Processus 0: Execution locale...
Resultat: 194
Horloge scalaire mise a jour: 18
Horloge scalaire mise a jour: 19
[Client 0] envoi -> 1: FROM 0 TO 1 | HORLOGE: S 19
[Client 0] recu de 3: FROM 3 TO 0 | HORLOGE: S 25
Horloge scalaire mise a jour: 26
valeur de received value 25:
Message recu : FROM 3 TO 0 | HORLOGE: S 25
[Client 0] Horloge scalaire apres fusion: 26
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 5
Processus 0: Execution locale...
Resultat: 190
Horloge scalaire mise a jour: 27
```

### 2. Horloge Vectorielle

```plaintext
[Client 0] Iteration 1
Processus 0: Execution locale...
Resultat: 175
Horloge vectorielle mise a jour: [1,0,0,0]
Horloge vectorielle mise a jour: [2,0,0,0]
[Client 0] envoi -> 1: FROM 0 TO 1 | HORLOGE: V [2,0,0,0]
[Client 0] recu de 3: FROM 3 TO 0 | HORLOGE: V [2,3,3,3]
Horloge vectorielle mise a jour: [3,3,3,3]
[Client 0] Horloge vectorielle apres fusion: [3, 3, 3, 3]
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 2
Processus 0: Execution locale...
Resultat: 34
Horloge vectorielle mise a jour: [4,3,3,3]
Horloge vectorielle mise a jour: [5,3,3,3]
[Client 0] envoi -> 2: FROM 0 TO 2 | HORLOGE: V [5,3,3,3]
[Client 0] recu de 2: FROM 2 TO 0 | HORLOGE: V [5,3,6,3]
Horloge vectorielle mise a jour: [6,3,6,3]
[Client 0] Horloge vectorielle apres fusion: [6, 3, 6, 3]
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 3
Processus 0: Execution locale...
Resultat: 117
Horloge vectorielle mise a jour: [7,3,6,3]
Horloge vectorielle mise a jour: [8,3,6,3]
[Client 0] envoi -> 3: FROM 0 TO 3 | HORLOGE: V [8,3,6,3]
[Client 0] recu de 1: FROM 1 TO 0 | HORLOGE: V [2,8,3,6]
Horloge vectorielle mise a jour: [9,8,6,6]
[Client 0] Horloge vectorielle apres fusion: [9, 8, 6, 6]
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 4
Processus 0: Execution locale...
Resultat: 194
Horloge vectorielle mise a jour: [10,8,6,6]
Horloge vectorielle mise a jour: [11,8,6,6]
[Client 0] envoi -> 1: FROM 0 TO 1 | HORLOGE: V [11,8,6,6]
[Client 0] recu de 3: FROM 3 TO 0 | HORLOGE: V [11,12,12,12]
Horloge vectorielle mise a jour: [12,12,12,12]
[Client 0] Horloge vectorielle apres fusion: [12, 12, 12, 12]
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 5
Processus 0: Execution locale...
Resultat: 190
Horloge vectorielle mise a jour: [13,12,12,12]
```

### 3. Horloge Matricielle

```plaintext
[Client 0] Iteration 1
Processus 0: Execution locale...
Resultat: 175
Horloge matricielle mise a jour:
[1,0,0,0]
[0,0,0,0]
[0,0,0,0]
[0,0,0,0]

[Processus 0] Preparation de l'envoi vers P1
[Processus 0] Horloge apres envoi :
 2  1  0  0
 0  0  0  0
 0  0  0  0
 0  0  0  0
[Client 0] envoi -> 1: FROM 0 TO 1 | HORLOGE: M [2,1,0,0;0,0,0,0;0,0,0,0;0,0,0,0]
[Client 0] recu de 3: FROM 3 TO 0 | HORLOGE: M [2,1,0,0;1,3,1,0;0,1,3,1;1,0,1,3]

[Processus 0] Tentative de fusion avec message de P3 :
Message delivre. Mise a jour de l'horloge :
Mise ├á jour horloge[1][0] : 0 ÔåÆ 1
Mise ├á jour horloge[1][1] : 0 ÔåÆ 3
Mise ├á jour horloge[1][2] : 0 ÔåÆ 1
Mise ├á jour horloge[2][1] : 0 ÔåÆ 1
Mise ├á jour horloge[2][2] : 0 ÔåÆ 3
Mise ├á jour horloge[2][3] : 0 ÔåÆ 1
Mise ├á jour horloge[3][0] : 0 ÔåÆ 1
Mise ├á jour horloge[3][2] : 0 ÔåÆ 1
Mise ├á jour horloge[3][3] : 0 ÔåÆ 3
[Processus 0] Horloge matricielle apres fusion :
 3  1  0  1
 1  3  1  0
 0  1  3  1
 1  0  1  3
[Client 0] Horloge matricielle apres fusion :
3 1 0 1
1 3 1 0
0 1 3 1
1 0 1 3
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 2
Processus 0: Execution locale...
Resultat: 34
Horloge matricielle mise a jour:
[4,1,0,1]
[1,3,1,0]
[0,1,3,1]
[1,0,1,3]

[Processus 0] Preparation de l'envoi vers P2
[Processus 0] Horloge apres envoi :
 5  1  1  1
 1  3  1  0
 0  1  3  1
 1  0  1  3
[Client 0] envoi -> 2: FROM 0 TO 2 | HORLOGE: M [5,1,1,1;1,3,1,0;0,1,3,1;1,0,1,3]
[Client 0] recu de 2: FROM 2 TO 0 | HORLOGE: M [5,1,1,1;1,3,1,0;2,1,6,1;1,0,1,3]

[Processus 0] Tentative de fusion avec message de P2 :
Message delivre. Mise a jour de l'horloge :
Mise ├á jour horloge[2][0] : 0 ÔåÆ 2
Mise ├á jour horloge[2][2] : 3 ÔåÆ 6
[Processus 0] Horloge matricielle apres fusion :
 6  1  2  1
 1  3  1  0
 2  1  6  1
 1  0  1  3
[Client 0] Horloge matricielle apres fusion :
6 1 2 1
1 3 1 0
2 1 6 1
1 0 1 3
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 3
Processus 0: Execution locale...
Resultat: 117
Horloge matricielle mise a jour:
[7,1,2,1]
[1,3,1,0]
[2,1,6,1]
[1,0,1,3]

[Processus 0] Preparation de l'envoi vers P3
[Processus 0] Horloge apres envoi :
 8  1  2  2
 1  3  1  0
 2  1  6  1
 1  0  1  3
[Client 0] envoi -> 3: FROM 0 TO 3 | HORLOGE: M [8,1,2,2;1,3,1,0;2,1,6,1;1,0,1,3]
[Client 0] recu de 1: FROM 1 TO 0 | HORLOGE: M [2,1,0,0;2,8,1,2;0,1,3,1;1,2,1,6]

[Processus 0] Tentative de fusion avec message de P1 :
Message delivre. Mise a jour de l'horloge :
Mise ├á jour horloge[1][0] : 1 ÔåÆ 2
Mise ├á jour horloge[1][1] : 3 ÔåÆ 8
Mise ├á jour horloge[1][3] : 0 ÔåÆ 2
Mise ├á jour horloge[3][1] : 0 ÔåÆ 2
Mise ├á jour horloge[3][3] : 3 ÔåÆ 6
[Processus 0] Horloge matricielle apres fusion :
 9  2  2  2
 2  8  1  2
 2  1  6  1
 1  2  1  6
[Client 0] Horloge matricielle apres fusion :
9 2 2 2
2 8 1 2
2 1 6 1
1 2 1 6
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 4
Processus 0: Execution locale...
Resultat: 194
Horloge matricielle mise a jour:
[10,2,2,2]
[2,8,1,2]
[2,1,6,1]
[1,2,1,6]

[Processus 0] Preparation de l'envoi vers P1
[Processus 0] Horloge apres envoi :
11  3  2  2
 2  8  1  2
 2  1  6  1
 1  2  1  6
[Client 0] envoi -> 1: FROM 0 TO 1 | HORLOGE: M [11,3,2,2;2,8,1,2;2,1,6,1;1,2,1,6]
[Client 0] recu de 3: FROM 3 TO 0 | HORLOGE: M [11,3,2,2;3,12,3,2;2,3,12,3;3,2,3,12]

[Processus 0] Tentative de fusion avec message de P3 :
Message delivre. Mise a jour de l'horloge :
Mise ├á jour horloge[1][0] : 2 ÔåÆ 3
Mise ├á jour horloge[1][1] : 8 ÔåÆ 12
Mise ├á jour horloge[1][2] : 1 ÔåÆ 3
Mise ├á jour horloge[2][1] : 1 ÔåÆ 3
Mise ├á jour horloge[2][2] : 6 ÔåÆ 12
Mise ├á jour horloge[2][3] : 1 ÔåÆ 3
Mise ├á jour horloge[3][0] : 1 ÔåÆ 3
Mise ├á jour horloge[3][2] : 1 ÔåÆ 3
Mise ├á jour horloge[3][3] : 6 ÔåÆ 12
[Processus 0] Horloge matricielle apres fusion :
12  3  2  3
 3 12  3  2
 2  3 12  3
 3  2  3 12
[Client 0] Horloge matricielle apres fusion :
12 3 2 3
3 12 3 2
2 3 12 3
3 2 3 12
[Client] Recu signal NEXT, passage a l'iteration suivante

[Client 0] Iteration 5
Processus 0: Execution locale...
Resultat: 190
Horloge matricielle mise a jour:
[13,3,2,3]
[3,12,3,2]
[2,3,12,3]
[3,2,3,12]
```

---

## Partie 2 : Résultats en Langage Java

### 1. Horloge Scalaire (Lamport)

```plaintext
Client 0 demarre
Client 0 commence literation 1
Client 0 instruction locale [horloge: 1]
Client 0 a envoye un message Ã  1 [horloge: 2]
Client 0 attend un message de 3
Client 0 a recu: "FROM 3 CLOCK 8" [nouvelle horloge: 9]
Client 0 commence literation 2
Client 0 instruction locale [horloge: 10]
Client 0 a envoye un message Ã  2 [horloge: 11]
Client 0 attend un message de 2
Client 0 a recu: "FROM 2 CLOCK 13" [nouvelle horloge: 14]
Client 0 commence literation 3
Client 0 instruction locale [horloge: 15]
Client 0 a envoye un message Ã  3 [horloge: 16]
Client 0 attend un message de 1
Client 0 a recu: "FROM 1 CLOCK 14" [nouvelle horloge: 17]
Client 0 commence literation 4
Client 0 instruction locale [horloge: 18]
Client 0 a envoye un message Ã  1 [horloge: 19]
Client 0 attend un message de 3
Client 0 a recu: "FROM 3 CLOCK 25" [nouvelle horloge: 26]
Client 0 commence literation 5
Client 0 instruction locale [horloge: 27]
```

### 2. Horloge Vectorielle

```plaintext
Client 0 demarre
Client 0 commence literation 1
Client 0 instruction locale [horloge: [1, 0, 0, 0]]
Client 0 a envoye un message Ã  1 [horloge: [2, 0, 0, 0]]
Client 0 attend un message de 3
Client 0 a recu: "FROM 3 CLOCK 2 3 3 3" [nouvelle horloge: [3, 3, 3, 3]]
Client 0 commence literation 2
Client 0 instruction locale [horloge: [4, 3, 3, 3]]
Client 0 a envoye un message Ã  2 [horloge: [5, 3, 3, 3]]
Client 0 attend un message de 2
Client 0 a recu: "FROM 2 CLOCK 5 3 6 3" [nouvelle horloge: [6, 3, 6, 3]]
Client 0 commence literation 3
Client 0 instruction locale [horloge: [7, 3, 6, 3]]
Client 0 a envoye un message Ã  3 [horloge: [8, 3, 6, 3]]
Client 0 attend un message de 1
Client 0 a recu: "FROM 1 CLOCK 2 8 3 6" [nouvelle horloge: [9, 8, 6, 6]]
Client 0 commence literation 4
Client 0 instruction locale [horloge: [10, 8, 6, 6]]
Client 0 a envoye un message Ã  1 [horloge: [11, 8, 6, 6]]
Client 0 attend un message de 3
Client 0 a recu: "FROM 3 CLOCK 11 12 12 12" [nouvelle horloge: [12, 12, 12, 12]]
Client 0 commence literation 5
Client 0 instruction locale [horloge: [13, 12, 12, 12]]
```

### 3. Horloge Matricielle

```plaintext
Client 0 demarre
Client 0 commence iteration 1
Client 0 Instruction locale [horloge matricielle]:
  1 0 0 0
  0 0 0 0
  0 0 0 0
  0 0 0 0
Client 0 Envoi a 1 [horloge matricielle]:
  2 1 0 0
  0 0 0 0
  0 0 0 0 
  0 0 0 0
Client 0 attend un message de 3
Client 0 a recu: "FROM 3 EM 2 1 0 0 1 3 1 0 0 1 3 1 1 0 1 3" [nouvelle horloge matricielle]:
  3 1 0 1
  1 3 1 0
  0 1 3 1
  1 0 1 3
Client 0 commence iteration 2
Client 0 Instruction locale [horloge matricielle]:
  4 1 0 1
  1 3 1 0 
  0 1 3 1
  1 0 1 3 
Client 0 Envoi a 2 [horloge matricielle]:
  5 1 1 1
  1 3 1 0
  0 1 3 1
  1 0 1 3
Client 0 attend un message de 2
Client 0 a recu: "FROM 2 EM 5 1 1 1 1 3 1 0 2 1 6 1 1 0 1 3" [nouvelle horloge matricielle]:
  6 1 2 1
  1 3 1 0
  2 1 6 1
  1 0 1 3
Client 0 commence iteration 3
Client 0 Instruction locale [horloge matricielle]:
  7 1 2 1
  1 3 1 0
  2 1 6 1
  1 0 1 3 
Client 0 Envoi a 3 [horloge matricielle]:
  8 1 2 2
  1 3 1 0
  2 1 Client 0 a recu: "FROM 1 EM 5 1 1 1 2 9 2 2 2 2 8 1 1 2 1 6" [nouvelle horloge matricielle]:
6 1
    1 9 0 1 2 3 
Client 0 attend un message de 1
2 2
  2 9 2 2
  2 2 8 1
  1 2 1 6
Client 0 commence iteration 4
Client 0 Instruction locale [horloge matricielle]:
  10 2 2 2
  2 9 2 2
  2 2 8 1 
  1 2 1 6
Client 0 Envoi a 1 [horloge matricielle]:
  11 3 2 2
  2 9 2 2
  2 2 8 1
  1 2 1 6
Client 0 attend un message de 3
Client 0 a recu: "FROM 3 EM 11 3 2 2 3 12 3 2 2 3 12 3 3 2 3 12" [nouvelle horloge matricielle]:
  12 3 2 3 
  3 12 3 2
  2 3 12 3
  3 2 3 12
Client 0 commence iteration 5
Client 0 Instruction locale [horloge matricielle]:
  13 3 2 3
  3 12 3 2
  2 3 12 3
  3 2 3 12
```

---

## Remarques

- Chaque exécution affiche les événements en temps réel, mettant à jour les horloges après chaque action (locale, envoi, réception).
- Les logs démontrent la validité des relations de causalité dans le système.
- Les différences entre les trois types d’horloges sont clairement visibles dans leur capacité à détecter l’ordre et l’indépendance des événements.
---

## Scénario d’Exécution Étape par Étape

### Étape 1 : Connexion des clients au serveur
- **Serveur** : Attend que les 4 clients se connectent.
- **Clients** : Chacun se connecte au serveur sur le port spécifié.
- Chaque client initialise son horloge distribuée (scalaire, vectorielle ou matricielle).

### Étape 2 : Itération 1
- **P0** : Exécute une instruction locale, envoie à P1, puis attend jusqu’à ce qu’il reçoive de P3.
- **P1** : Exécute une instruction locale, reçoit de P0, puis envoie à P2.
- **P2** : Exécute une instruction locale, reçoit de P1, puis envoie à P3.
- **P3** : Exécute une instruction locale, reçoit de P2, puis envoie à P0.

### Étape 3 : Itération 2
- **P0** : Exécute une instruction locale, envoie à P2, puis attend jusqu’à ce qu’il reçoive de P2.
- **P1** : Exécute une instruction locale, envoie à P3, puis attend jusqu’à ce qu’il reçoive de P3.
- **P2** : Exécute une instruction locale, reçoit de P0, puis envoie à P0.
- **P3** : Exécute une instruction locale, reçoit de P1, puis envoie à P1.

### Étape 4 : Itération 3
- **P0** : Exécute une instruction locale, envoie à P3, puis attend jusqu’à ce qu’il reçoive de P1.
- **P1** : Exécute une instruction locale, envoie à P0.
- **P2** : Exécute une instruction locale, envoie à P1.
- **P3** : Exécute une instruction locale, reçoit de P0, puis envoie à P1.

### Étape 5 : Itération 4
- **P0** : Exécute une instruction locale, envoie à P1, puis attend jusqu’à ce qu’il reçoive de P3.
- **P1** : Exécute une instruction locale, reçoit de P0, puis envoie à P2.
- **P2** : Exécute une instruction locale, reçoit de P1, puis envoie à P3.
- **P3** : Exécute une instruction locale, reçoit de P2, puis envoie à P0.

### Étape 6 : Itération 5
- Chaque client exécute une instruction locale.