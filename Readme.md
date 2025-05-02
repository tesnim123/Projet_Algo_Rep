## Rapport de Projet : Simulation des Horloges Logiques en Systèmes Distribués

### I. Introduction

Dans les systèmes distribués, la gestion de l'ordre des événements est essentielle, car l'absence d'une horloge globale rend complexe la synchronisation entre processus. Pour résoudre ce problème, on utilise des horloges logiques : **horloge scalaire**, **horloge vectorielle** et **horloge matricielle**.

Ce projet vise à simuler le fonctionnement de ces trois types d'horloges en utilisant les langages **C et Java**, avec une communication entre processus via **sockets TCP**. Il permet de visualiser la progression des horloges lors d'événements locaux, d'envois et de réceptions de messages.

---

### II. Objectifs du projet

- Implémenter des processus communicants dans un environnement distribué simulé.
- Utiliser les sockets TCP pour permettre la communication entre processus.
- Mettre en œuvre et comparer les trois types d’horloges logiques.
- Vérifier les relations de causalité entre événements.
- Étudier le comportement des horloges en cas de réception de messages hors ordre.

---

### III. Architecture de l'application

#### 1. Composants

- **Serveur** : Attend la connexion des clients et orchestre le déroulement des itérations.
- **Clients (P0 à Pn)** : Simulent les processus distribués. Chacun maintient sa propre horloge et communique avec les autres selon un scénario prédéfini.

#### 2. Communication

Les processus communiquent entre eux via des **sockets TCP**. Chaque message envoyé contient :
- Un identifiant de l’événement.
- L’horloge actuelle du processus émetteur.

#### 3. Scénario

Chaque client :
- Réalise des événements locaux.
- Envoie ou reçoit des messages.
- Met à jour son horloge selon le type utilisé.

---
### Prérequis
## En langage C:
Compilateur : MinGW (Minimalist GNU for Windows)
Bibliothèque réseau : WinSock2 (native à Windows, incluse via #include <winsock2.h>)
Éditeur : Visual Studio Code 
Terminal : PowerShell ou l’invite de commandes 

## En langage Java:
Kit de développement Java (JDK) 8 
Éditeur : Visual Studio Code 
Interface en ligne de commande 

### IV. Horloges logiques implémentées

#### A. Horloge Scalaire (Lamport)

- Chaque processus maintient un entier `Li`.
- Lors d’un événement local : `Li = Li + 1`
- Lors de l’envoi d’un message : `Li = Li + 1`, message contient `Li`
- À la réception : `Li = max(Li, Lm) + 1`

#### B. Horloge Vectorielle

- Chaque processus maintient un vecteur `Vi[0..n-1]`
- Événement local : `Vi[i] = Vi[i] + 1`
- Envoi : `Vi[i] = Vi[i] + 1`, message contient `Vi`
- Réception de Vj : `Vi[k] = max(Vi[k], Vj[k])` pour tout `k`, puis `Vi[i] = Vi[i] + 1`

#### C. Horloge Matricielle (Logique modifiée)

##### 1. Événement local à Pi
```plaintext
HMi[i][i] = HMi[i][i] + 1
```

##### 2. Envoi de Pi vers Pj
```plaintext
HMi[i][i] = HMi[i][i] + 1
HMi[i][j] = HMi[i][j] + 1
Em = copie de HMi
```

##### 3. Réception de (m, Em) par Pi
- Condition de délivrance : `Em[k][i] <= HMi[k][i]` pour tout `k ≠ i, j`
- Si condition vérifiée :
```plaintext
HMi[j][i] = HMi[j][i] + 1
HMi[i][i] = HMi[i][i] + 1
Pour tout k ≠ i, j et l ≠ i : HMi[k][l] = max(HMi[k][l], Em[k][l])
```

---

### V. Défis rencontrés

- **Synchronisation des messages** : éviter les conflits lors de réceptions multiples.
- **Complexité des horloges matricielles** : vérifier les conditions de délivrance.
- **Affichage clair de l’évolution des horloges** : développement de logs détaillés.

---

### VI. Résultats obtenus

- Fonctionnement correct des horloges dans un scénario multi-processus.
- Validation des relations de causalité entre événements.
- Détection des réceptions précoces grâce aux horloges matricielles.

---

### VII. Conclusion

Ce projet a permis de comprendre en profondeur les mécanismes d'horlodatage logique dans les systèmes distribués. Les trois modèles implémentés ont montré leur utilité respective :

- **Scalaire** : simple, mais peu précis pour la causalité.
- **Vectoriel** : très utilisé, efficace pour la causalité.
- **Matriciel** : précis, adapté à la détection de terminaisons.

Ce travail pourrait être enrichi par une visualisation graphique des relations de causalité, ou par l’ajout de pannes pour simuler des conditions de réseau réel.

---

### VIII. Annexes

- Résultats (Disponibles dans le fichier Résultats.md)
- Captures d’écran des matrices d’horloges
- Exemple de scénario d’échange entre quatres processus


