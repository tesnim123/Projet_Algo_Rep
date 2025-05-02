
#  Guide d'exécution – Horloges Logiques (C et Java)

##  En langage C

###  Compilation

- **Compiler le serveur** :
  ```bash
  gcc server.c -o server -lws2_32
  ```

- **Compiler le client** :
  ```bash
  gcc client.c -o client -lws2_32
  ```

###  Exécution
1. Lancer le serveur: ./server

2. Lancer le script PowerShell :
   ```bash
   ./execute.ps1
   ``` 
   execute.ps1:Un script qui automatise le lancement de 4 clients, chacun représentant un processus dans un système distribué, avec un type d’horloge logique identique.

    **Remarque** : Dans le fichier `execute.ps1`, ajuste la valeur selon le type d’horloge à tester :
   - `0` : Horloge scalaire
   - `1` : Horloge vectorielle
   - `2` : Horloge matricielle

---

##  En langage Java

###  Compilation

- **Compiler tous les fichiers** :
  ```bash
  javac *.java
  ```

###  Exécution

1. **Lancer le serveur** :
   - Pour les horloges scalaires :
     ```bash
     java Server
     ```
   - Pour les horloges vectorielles :
     ```bash
     java ServerV
     ```
   - Pour les horloges matricielles :
     ```bash
     java ServerM
     ```

2. **Lancer les clients dans 4 terminaux différents** :
   - Pour les horloges scalaires :
     ```bash
     java Client <numeroClient>
     ```
   - Pour les horloges vectorielles :
     ```bash
     java ClientV <numeroClient>
     ```
   - Pour les horloges matricielles :
     ```bash
     java ClientM <numeroClient>
     ```
