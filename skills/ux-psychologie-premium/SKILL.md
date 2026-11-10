---
name: "ux-psychologie-premium"
description: "Concevoir ou auditer une UI/UX pour qu'elle paraisse premium et agréable : états, cohérence, récupération d'erreur, principes psychologiques (goal gradient, peak-end, labor illusion…)."
---

# UX : psychologie et perception « premium »

Sources : Tim Gabe (« The Psychology of Premium Apps »), Wyatt Feaster (« The psychology trick that makes any app feel 10x better »). À utiliser pour créer, revoir ou auditer un écran, un flow ou un produit entier (surtout quand l'UI a été générée par IA et paraît « correcte mais générique »).

## Idée centrale : le « commodity ceiling »
Aujourd'hui, un écran « décent » est accessible à tout le monde (agents IA, kits UI, Mobbin). Joli ≠ premium : le visuel fait choisir, mais ce sont les **preuves de qualité du produit** qui le font juger premium. Ces preuves se trouvent à trois endroits, au-dessus du plafond :

### 1. Les états que l'IA oublie (« design theater »)
Une IA justifie bien ses choix mais en laisse une partie hors de l'interface : feedback système, annulation, récupération d'erreur. Pour chaque action du flow principal, vérifier :
- l'utilisateur sait **ce qui vient de se passer** (feedback visible : chargement, succès, échec) ;
- il peut **revenir en arrière** (undo, annuler, retour) ;
- il sait **quoi faire ensuite** (prochaine action claire).
Un résultat vide ou « rien ne s'est passé » est le pire : toujours donner quelque chose (ex. session trop courte → expliquer pourquoi et proposer l'étape suivante).

### 2. La cohérence entre écrans (connective tissue)
Les écrans sont souvent revus un par un en « happy path ». L'utilisateur, lui, voit l'écran 80 à côté de l'écran 1. Les incohérences coûtent plus cher que ce que les utilisateurs disent ou que ce que les métriques montrent (étude York 2009 : déplacer une nav bar a doublé le temps passé, et les gens disaient que ça ne les gênait pas).
- Un même cas = un même pattern (ex. « quota épuisé » : un seul composant avec badge « 2/2 utilisées », phrase explicite et date de renouvellement, au lieu de deux écrans génériques).
- Avec des agents qui génèrent des écrans en une minute, le risque d'avoir 80 écrans qui « ne s'accordent pas » augmente : prévoir une passe de cohérence (composants, copy, structure d'états).
- Test : utiliser le produit 1 h comme un vrai utilisateur et noter chaque endroit où il ne ressemble plus au même produit.

### 3. Le pire moment du produit (erreurs et échecs)
Paiement qui échoue, perte de connexion, liste vide, doute de l'utilisateur. Une panne bien gérée peut rendre aussi satisfait, voire plus, qu'une absence de panne (service recovery paradox). Exemples : jeu T-Rex hors-ligne de Chrome ; paiement refusé → alerte « vérifier votre solde » + bouton contacter le support (a contribué à +60 % de nouveaux comptes et +79 % de fonds chargés dans le cas cité).
- Casser le produit exprès : couper le wifi en plein flow, faire échouer un paiement, vider chaque liste.
- Concevoir ces états aussi soigneusement que les écrans de succès.

## Principes psychologiques à appliquer
- **Goal gradient** : le cerveau veut fermer les boucles. Montrer la progression restante (« 5/7 tâches », « 3 min restantes », barres de progression, streaks, onboarding avec progress bar) plutôt qu'un simple « terminez la tâche ».
- **Peak-end** : on retient les sommets et les creux (et la fin). Soigner les écrans de succès et de renforcement positif (Airbnb, Duolingo), éliminer les moments de friction extrême, soigner la sortie du flow.
- **Labor illusion** : on valorise ce qui demande du temps/effort visible. Pour des tâches sensibles (vérification d'identité, contrôle de sécurité, calcul), un court temps de traitement avec feedback peut rassurer, même si le résultat est instantané. Garde-fou : ne jamais simuler de l'attente sur une action simple qui ralentit l'utilisateur ; l'usage se limite aux tâches où la perception de sérieux compte.
- **Von Restorff** : on retient ce qui est différent. Mettre en avant 1–2 éléments clés (icône, illustration, couleur) au lieu d'uniformiser ; si tout est mis en avant, rien ne l'est.
- **Choice overload** : trop d'options = tension et paralysie. Catégoriser, filtrer, rechercher, retirer des éléments, limiter ce qui s'affiche en même temps (onglets de réglages, nav courte).

## Méthode d'audit rapide
1. Dérouler le flow principal et lister, pour chaque étape : feedback ? annulation ? étape suivante ?
2. Lister les états : vide, chargement, erreur, hors-ligne, quota atteint, succès, permission refusée.
3. Chercher les doublons de patterns (deux écrans pour le même cas) et unifier.
4. Repérer les 3 moments les plus anxiogènes et y ajouter des informations et une action de sortie.
5. Appliquer goal gradient / peak-end / Von Restorff / choice overload aux écrans clés.
6. Rendre un rapport priorisé (impact élevé / effort faible d'abord).

## À éviter
- Livrer uniquement les écrans « happy path ».
- Copier un pattern d'une app célèbre sans vérifier qu'il convient au contexte et au public.
- Utiliser ces leviers psychologiques pour manipuler ; ils servent à réduire l'effort et l'anxiété de l'utilisateur.