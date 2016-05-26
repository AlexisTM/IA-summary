IA - Séance 2 - Recherche de solution
===============

État
-----------------
- État initial
- Instant donné
- Modifié selon l'environnement/Actions

Action
----------------
- Effectué à l'environnement
- Fonction successeur 
- Actions possibles selon l'état

Arbre d'exécution
----------------
- Souvent infini
- Noeuds - État
- Arrêtes - Action
- Chemin - Exécution donnée

Espace d'états
---------------
- Ne duplique pas les états égaux
- Défini par l'état initial et la fonction successeur
- Chemin - Exécution donnée

Problème 
--------------
- Objectif : Nettoyer 
- Actions : Avance, recule, tourne à gauche, tourne à droite
- Arbre d'exécution (souvent infini)
- Coût par action
- Minimise le coût pour une solution optimale

![Formalise mathématique](https://github.com/AlexisTM/IA-summary/blob/master/FormalismeMath.PNG)

![Formalise mathématique exemple](https://github.com/AlexisTM/IA-summary/blob/master/FormalismeMathExemple.PNG)

![Fonction successeur](https://github.com/AlexisTM/IA-summary/blob/master/FonctionSuccesseur.PNG)

Algorithme
------------
- Performances 
  - Complétude : Toujours une solution ?
  - Optimale : Meilleure solution ?
  - Complexité temporelle : Temps pour trouver la solution
  - Complexité spatiale : Mémoire pour trouver la solution

Recherche non informée 
----------------------
- Aveugle
- Recherche basée sur la définition du problème
- Distinction des algorithmes selon l'ordre d'exploration
- **BFS - Breadth-First Search**
  - En largeur
  - Par niveau
  - Complet
  - Optimale si les coûts sont identiques
  - Complexité temporelle : O(b^(d+1))
    - b : facteur de branchement (nombre d'action par état)
    - d : profondeur de la solution la moins profonde
  - Complexité spaciale : O(b^(d+1))
- **Uniform-Cost Search**
  - Exploration par le coût le plus faible
  - Complet & optimal
    - Si les coûts sont > ε,  ε > 0 (sinon on peut ignorer une branche alors qu'il y a des coûts négatifs plus tard)
  - Complexité temporelle : O(b^(1+C*/ε))
    - C* le coût optimal
    - ε : coût minimal
- **DFS - Depth-First Search**
  - Descend le plus bas dans une feuille de l'arbre
  - Complexité temporelle O(b^m)
    - b : nombre d'actions
    - m : profondeur maximale de l'arbre
  - Complexité spatiale O(bm+1) 
- **DFS limited - Depht Limited Search**
  - Profondeur maximale, fonctionne comme DFS
  - Complexité temporelle O(b^l)
    - b : nombre d'actions
    - l : profondeur limite
  - Complexité spaciale O(bl)
  - *Échecs*
    - Failure : No solution
    - Cutoff : No solution in limited range
- **IDFS limited - Iterative Deepening Depht-First Limited Search**
  - Profondeur maximale, fonctionne comme DFS limited
  - Incrémente l pour chaque étape
- **Bidirectionnal Search**
  - Deux recherches parallèles
    - Depuis l'état initial
    - Depuis l'état final
  - Fonction successeur et prédécesseur
  - Solution au croisement des deux recherches

Recherche informée 
----------------------
- Connaissances spécifiques
- Best-First search
- Fonction d'évaluation f(n) : Détermine le coût de l'exploration
- Fonction heuristique h(n) : Coût estimé le moins cher
- **Greedy Best-First Search**
  - Choix du noeud le plus proche (f(n) = h(n))
  - Heuristique h(n) selon le problème
  - Similaire à DFS
  - Non complet, non optimal
  - Complexité spaciale & temporelle : O(b^m) : Meilleure selon l'heuristique
- **A***
  - g(n) : coût d'avoir atteint n
  - h(n) : coût d'atteindre l'objectif depuis n
  - f(n) : g(n) + h(n)
  - Complet et optimal si h(n) n'est pas surestimé
- **Adversarial Search**
  - Recherche de solution avec deux adversaires
  - Joueurs MIN et MAX, MAX joue en premier
  - *Définition du problème :*
    - État initial : Position sur le plateau
    - Fonction successeur : List des paires (move, state)
    - Test terminal : Vérifie si le jeu est terminé
    - Fonction d'utilité : Donne une valeur aux états terminaux
  - *Arbre de jeu*
    - État initial
    - Mouvements légaux
  - *Stratégie* : 
    - Max veut gagner sachant que MIN joue aussi
    - Définit: 
      - Le premier coup
      - La réponse optimale de MIN
      - La réponse de MAX 
      - ...
    - On joue le meilleur coût en espérant que l'adversaire joue parfaitement
  - *Caractéristiques des jeux*
    - Somme nulle : L'un gagne, l'autre perd
    - Information parfaite (accessibilité à toutes les informations des deux joueurs)
    - Pas de chance dans le jeu
    - Valeur d'un état terminal
  - **Algorithme Minimax**
    - Delta vers le HAUT = MAX, delta vers le BAS = MIN
    - MAX choisit le max du choix minimal de MIN
  - **Alpha-Beta Pruning**
    - Comme minimax
    - N'explorer pas si inutile
    - Simplifications, pruning : 
      - α cutoff : α borne inférieure pour MAX, la plus grande valeur trouvée

      - β cutoff : β borne supérieure pour MIN, la plus petite valeur trouvée
    - Mémorisation des bornes durant l'exploration de l'arbre
