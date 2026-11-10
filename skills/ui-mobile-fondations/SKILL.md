---
name: "ui-mobile-fondations"
description: "Concevoir ou revoir une UI d'app mobile : navigation, échelle, layout, cartes, une-écran-une-tâche, bottom sheets, gestes, états vides. Utiliser pour tout écran ou flow mobile."
---

# UI mobile : fondations

Source : Kole Jain, « Everything you need to know about Mobile App UI's ». Pensé iOS d'abord ; adapter les gestes et transitions aux conventions Material/Android quand la cible est Android (zoom d'arrière-plan et flou au long appui sont des conventions iOS ; penser aussi edge-to-edge, insets système et mode paysage/foldables).

## Navigation
- Barre du bas (souvent flottante), avec l'action principale mise en évidence. **3–4 liens idéal, 5 maximum**. Cibles tactiles **≥ 44 px**.
- Si trop de destinations : transformer la sidebar en **page d'accueil** (liste de sections, éléments récents, compteurs sur le côté) et libérer le bas pour une recherche ou une action principale (approche type Notion).
- En haut : cloche et menu « plus » comme base, mais **actions contextuelles** selon la page.

## Échelle
- Les écrans sont plus petits, mais texte et espacements ne rétrécissent pas : base iOS 17 px contre 13 px sur macOS. Sur mobile, les éléments tendent à être **plus grands**, pas plus petits.
- Conséquence : on ne peut pas porter tout un dashboard desktop ; **choisir une chose** par zone.

## Layout et contenu
- Un dashboard desktop s'étend dans deux directions ; sur mobile, **une direction par section** : empilé verticalement **ou** défilement horizontal, pas les deux.
- Quatre briques seulement : **cartes**, texte/liens, images, inputs (chacun peut être dans une carte).
- Les cartes regroupent le contenu à la place de l'espace blanc rare. **Éviter les cartes imbriquées** (padding sur padding) ; grouper avec de l'espace blanc quand c'est possible.

## Un écran, une tâche
- Hors accueil, chaque écran fait une seule chose (réglages = réglages, éditeur = éditeur). Pas de suggestions ou de récents parasites ; besoin d'ajouter quelque chose → **autre page**, pas un autre layout.
- Quand il faut rester dans le contexte (ex. choisir un template en éditant une note) : **bottom sheet** (titre, recherche, confirmer/annuler, hauteur variable, pilotable par gestes).
- Le bouton « + » ouvre un petit menu ou directement le clavier avec un input prêt à saisir.

## Gestes
- **Swipe droite = retour** : déplacer l'arrière-plan d'environ 35 % vers la gauche en parallèle pour une transition fluide.
- Bottom sheet : l'arrière-plan se réduit à l'ouverture et revient au swipe bas.
- Les swipes sont partout, mais **à enseigner** à l'utilisateur (ex. swipe haut pour chercher).
- **Appui long** = équivalent du clic droit : flou du reste, actions affichées, léger zoom sur l'élément, voire aperçu dynamique (iOS).

## Dynamisme
- L'espace est limité : les actions **apparaissent et disparaissent** selon le contexte (ouvrir une note masque la navbar et affiche mise en forme/partage ; choisir un template ne laisse que confirmer et fermer). Soigner l'animation d'entrée/sortie.

## États vides
- Concevoir l'état **premier lancement sans contenu** : écran vide plein écran qui attire l'attention vers l'action principale (+), avec un popover d'explication, plutôt que des cartes d'invitation partout.
- **Recherche sans résultat** : image ou illustration, message qui reconnaît l'absence de résultat pour ces mots-clés, suggestions (fautes de frappe), action pour sortir de l'état vide.

## Checklist de revue
1. Nav : ≤ 5 liens, cibles ≥ 44 px, action principale distincte.
2. Tailles de texte et d'espacement adaptées au pouce, pas réduites.
3. Une direction de scroll par section ; pas de cartes dans des cartes.
4. Chaque écran n'a qu'une tâche ; bottom sheet pour les actions contextuelles.
5. Gestes standards supportés et découvrables ; conventions de la plateforme respectées.
6. États vides (premier lancement, recherche sans résultat) conçus.
7. Penser aux insets système, au mode paysage et aux tailles d'écran multiples.