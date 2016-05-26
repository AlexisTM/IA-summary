IA - Séance 4 - Logique et connaissance
===============

Agent basé sur la connaissance 
-----------------------
- A une KB, Knowledge Database
- Peut: 
    - Ask : Poser une question
    - Tell : Ajouter une nouvelle entrée
- Inférence : Détermine de nouvelles vérités, phrases à partir d'anciennes
- Les connaissances sont différentes pour les différents types d'application

Logique 
------------
- KB est représenté par un ensemble de phrases
- Syntaxe donne la formation des phrases
- Sémantique définit la signification de la phrase
- Une phrase peut être vraie ou fausse dans un monde donné
- Modèle : 
    - Un modèle est un monde possible
    - m est un modèle d'une phrase α, si la phrase est vraie dans ce monde
- Conséquence logique
    - exemple 
        - entre α et β  
        -  "α |= β", si α est conséquence logique de β
        - Dans tout modèle où α est vrai, β doit l'être aussi 
- Utilisation de l'arithmétique ordinaire
    - “x + y = 4” est vraie dans un monde où x = 2 et y = 2
    - “x + y = 4” est fausse dans un monde où x = 1 et y = −1
- **Inférence**
    - Conséquence logique pour dériver des conclusions
    - "KB |-i α" Retrouver α dans KB avec l'algorithme i
    - Sound : Si ne dérive que des phrases conséquences
    - Complete : Si sait dériver toutes les phrases conséquences
- Tautologie : Est toujours vraie

Syntaxe 
-------------
- Sentence → AtomicSentence | ComplexSentence
- AtomicSentence → True | False | Symbol
- Symbol → P | Q | R | ...
- ComplexSentence → ¬Sentence
    - | (Sentence ∧ Sentence)
    - | (Sentence ∨ Sentence)
    - | (Sentence ⇒ Sentence)
    - | (Sentence ⇔ Sentence)
- Connecteurs logique : 
    - Négation (=/= ou ¬), NOT
    - Conjonction (∧), AND 
    - Disjonction (∨), OR
    - Implication (⇒), A ⇒ B : A?B==A?true:false:true 
    - Biconditionnelle (⇔), XOR
- Priorité :  ¬,∧,∨,⇒,⇔
- ≡ : équivalence
- A |= B: A est la conséquence logique de B 


Équivalences logiques usuelles
-------------------

| Équivalence   |     Nom         |
| --- | :---: |
| (α ∧ β) ≡ (β ∧ α) | commutativité de ∧ |
| (α ∨ β) ≡ (β ∨ α) | commutativité de ∨ |
| ((α ∧ β) ∧ γ) ≡ (α ∧ (β ∧ γ)) | associativité de ∧ |
| ((α ∨ β) ∨ γ) ≡ (α ∨ (β ∨ γ)) | associativité de ∨ |
| ¬(¬α) ≡ α | élimination d’une double négation |
| (α ⇒ β) ≡ (¬β ⇒ ¬α) | contraposition |
| (α ⇒ β) ≡ (¬α ∨ β) | élimination de l’implication |
| (α ⇔ β) ≡ (α ⇒ β) ∧ (β ⇒ α) | élimination de la biconditionnelle |
| ¬(α ∧ β) ≡ (¬α ∨ ¬β) | De Morgan |
| ¬(α ∨ β) ≡ (¬α ∧ ¬β) | De Morgan |
| (α ∧ (β ∨ γ)) ≡ ((α ∧ β) ∨ (α ∧ β)) | distribution de ∧ sur ∨ |
| (α ∨ (β ∧ γ)) ≡ ((α ∨ β) ∧ (α ∨ β)) | distribution de ∨ sur ∧ |
