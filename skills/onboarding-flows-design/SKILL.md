---
name: "onboarding-flows-design"
description: "Concevoir ou auditer un onboarding (mobile ou web) : aha moment, outcome plutôt que features, personnalisation, paywall, permissions, éducation en contexte, longueur perçue."
---

# Onboarding : principes issus d'une étude de 1 460 flows

Source : Mobbin, « I Studied 1,460 Onboarding Flows » (986 apps/sites). Ce sont des corrélations d'observation, pas des preuves causales : tester avec ses propres utilisateurs. Le focus est B2C ; pour du B2B complexe, adapter.

## Constats de base
- Le conseil « faites court » n'est pas la règle : l'app moyenne a ~25 écrans d'onboarding ; finance, santé/fitness et éducation sont les plus longs ; les plus courts sont souvent des produits IA.
- Schéma gagnant : **inscription → configuration → aha moment** (le moment où l'on ressent la valeur : première réservation, premier film regardé, premier écran sauvegardé). L'objectif est d'amener **vite à la valeur**, pas de minimiser le nombre d'écrans.
- **Se demander d'abord si l'onboarding est nécessaire** : pour un chat IA, le premier prompt est la valeur ; pour un produit qui parle de lui-même, laisser entrer vite et s'effacer.

## Techniques
### Montrer le résultat, pas la liste de features
- Écran d'accueil montrant le produit en action ou une animation qui se comprend sans lire.
- Laisser **essayer l'expérience cœur avant l'inscription**.
- Transformer l'écran d'inscription en pitch (preuve sociale, logos).

### Faire humain
- Note du fondateur (signature, petit dessin), message personnel du CEO après création de compte ou au moment du aha, reconnaissance d'un anniversaire.

### Personnaliser, et que ça en vaille la peine
- Poser peu de questions et faire visiblement bénéficier des réponses : home pré-remplie avec le contenu choisi, plan personnel avec date d'objectif, projection (« dans 2 mois vous pourrez… »).
- Accepter **plusieurs objectifs** (changement cité : +10 % de conversion en essai gratuit) ; laisser choisir un style/réglage qui rend l'app « à soi » ; formuler le quiz de façon conversationnelle (+5 % d'abonnements cité).
- Montrer ce que les réponses ont débloqué dès la fin du quiz.

### Paywall
- ~22 % des apps en présentent un pendant l'onboarding. Combiner avec la personnalisation : offre unique après quiz, page de preuve sociale avant, plans recommandés selon les réponses (+~20 % d'upgrades cité), paywall soigné ou ludique.
- **Être transparent sur le fait qu'un paiement arrive** : un long quiz « personnalisé » qui se termine par un paywall caché est perçu comme manipulateur.

### Faire paraître le flow court
- Du mouvement partout : animations de chargement et de vérification, mascotte, nom à donner, progression, valeur régulièrement rappelée.
- Faire vivre l'action avant le compte (ex. première leçon puis création de compte).

### Éduquer en contexte
- Pas de tout-en-un en tête : microcopy rassurante, tooltips expliquant l'impact de chaque étape, validation en temps réel (champ mot de passe qui coche les critères).
- État vide avec petit nudge au bon endroit plutôt que tours guidés et popups.
- Checklist persistante (cité : +10 % de rétention à 1 semaine).

### Demander au bon moment
- **Pré-écran personnalisé avant la popup de permission système** (notifications), voire un aperçu de la notification, améliore le taux d'acceptation.
- Découper un formulaire d'inscription en plusieurs écrans a fait +15 % de conversion dans un cas cité : de la friction à un endroit peut en retirer ailleurs.
- La culture compte : certains marchés tolèrent mieux les interfaces denses ; ne pas copier sans tester.

## Checklist d'audit
1. Quel est le aha moment ? Combien de temps et d'écrans pour l'atteindre ?
2. Le premier écran montre-t-il le résultat ou liste-t-il des features ?
3. Peut-on essayer avant de s'inscrire ?
4. Chaque question posée est-elle utilisée visiblement ensuite ?
5. Le paywall est-il annoncé, cohérent avec la personnalisation, et sans surprise ?
6. Permissions : pré-écran de contexte avant la popup système ?
7. Le flow donne-t-il une impression de progression et de vie (animations, feedback, humour) ?
8. L'éducation est-elle faite en contexte plutôt qu'en tête de flow ?
9. Peut-on ne pas avoir d'onboarding du tout ?