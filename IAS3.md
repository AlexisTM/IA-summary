IA - Séance 3 - Satisfaction de contraintes
===============

Contraint satisfaction problem
-------------
- Variables : X = {X1, X2, ..., Xn}
- Domaines : D = {D1, D2, ..., Dn} (Domaine des variables)
  - Domaine de variables
  - Discret, fini, infini ou booléen
- Contraintes : C = {C1, C2, ..., Cm}
- Plusieurs solutions
- Phase de propagation
- Phase de recherche
- Propagateurs
- Heuristiques

Contraintes
--------------
- Linéaires : +, -, /, *
- Non linéaires
- Unaires : une variable : F NOT 3
- Binaires : une paire de variables : F NOT G
- Globales ou d'ordre supérieur: 3+ variables : alldiff
- Soft contraint : Ajout de coûts selon la contrainte
- Graphe des contraintes
  - UN noeud par variable 
  - Liens représentant les contraintes
- Une contrainte peut aussi être une paire (Tj, Rj)
  - Tj est un sous ensemble de k variables
  - Rj est une relation de sous ensembles de Dj : Valeurs possibles des variables Tj

Expression
-------------
- État initial
- Fonction successeur : Affecte une valeur en respectant les contraintes
- Test de l'objectif : Vérification de la consistance des valeurs
- Coût : 1 pour chaque étape
- Exemple : 4-Queens
  - X = {Q1, Q2, Q3, Q4}
  - Di = {1,2,3,4}
  - Initial state : {}

Résolution 
--------------
- Backtracking : Lorsque qu'il n'y a plus de possibilité, revient en arrière dans l'arbre
- Propagation de contraintes
- Recherche locale
- Peut y avoir une fonction objectif 
- En général : utilisation d'algorithmes de type DFS
- Commutativité de l'affectation des variables
- **Heuristique** : 
  - *MRV* : Minimum Remaining Value
  - *Degree* : Variable la plus contrainte
  - *Least constraining value*
- **Accélération** : 
  - *Forward checking* : Corrige le domaine des autres variables lors de l'affectation, AVANT d'explorer l'arbre
  - *Constraint propagation*
- **Backtracking de type DFS** : image

Solution 
-----------
- **Affectation** : Donne une valeur à 1+ variable
  - Consistante : ne viole aucune règle
  - Complète : toutes les variables ont une valeur
- Une **Solution** est une affectation complète et consistante
- Peut ne pas avoir de solution : sur-contraint


IA - Séance 3bis - Réseaux de neurones
===============

Cerveau humain 
----------------
- 10^11 neurones
- 10^14 synapses
- 20+ neurones différents
- Neurone est excitable
- Signal bioélectrique
- Deux voies : Signaux *entrants* et *sortants*
- L'information est das l'architecture des connexions


Neurone artificiel
------------------
- Unité de McCulloch-Pitts, simplification du neurone : McCulloch-Pitts.PNG
  - Liens d'entrée
  - Fonction d'entrée
  - Fonction d'activation : Escalier (seuil) ou sigmoide
  - Sortie
  - Liens de sortie
  - Biais : a0 fixé à -1
  - Poids du biais : W0 : translation horizontale du graphe
  - Seuil : Neurone actif si SUM(INPUT) > W0

Fonctions booléennes
------------------
- AND : W0 = 1.5
- OR : W0 = 0.5
- NOT : W0 = -0.5
- MAJORITÉ : W0 = n/2
  - n : Nombre d'entrée
  - Wj fixés à 1

Réseaux artificiels 
------------------
- Fortement connectés
- Interconnexion possible entre réseaux
- Chaque processeur effectue une simple opération : GPU

Structure des réseaux
----------------------
- **Feed-forward** : Ne stoque rien, que les poids
  - Calcule une fonction hW(x)
    - x : Vecteur d'entrée
    - W : Vecteur de poids
  - *Apprends* en ajustant les poids **W**
  - Perceptron : Une Couche de sortie
    - Fonction *booléenne*
  - Multicouche pour réaliser des fonctions plus complexes
  - Toutes les fonctions continues avec une couche cachée
  - Fonctions discontinues avec deux couches cachées
- **Recurrent** : Cyclique, avec rétroaction
  - Stocke une information