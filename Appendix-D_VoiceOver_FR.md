---
Type:
  - Notes
Communauté:
  - Pratique Test
Comment: Aide-mémoire des commandes VoiceOver pour les tests d'accessibilité mobile
tags:
  - Test/Accessibilité
  - iOS
  - VoiceOver
---

# Annexe D — VoiceOver (iOS) : aide-mémoire pour les tests d'accessibilité

> **Périmètre.** Les gestes ci-dessous sont ceux documentés par Apple pour VoiceOver sur iPhone. Le comportement exact peut varier selon la version d'iOS. Avant le premier test, s'entraîner aux gestes dans **Réglages > Accessibilité > VoiceOver > Entraînement VoiceOver** (*VoiceOver Practice*) : une fois VoiceOver activé, l'iPhone doit être utilisé avec les gestes VoiceOver.

---

## 1. Activer et désactiver VoiceOver

| Méthode | Comment | Remarque |
|---|---|---|
| Réglages | Réglages > Accessibilité > VoiceOver | Toujours disponible |
| Siri | « Active VoiceOver » / « Désactive VoiceOver » | Si Siri est configuré |
| Raccourci d'accessibilité | Triple-clic sur le bouton latéral (iPhone avec Face ID) | Fonctionne seulement si le raccourci d'accessibilité est réglé sur VoiceOver |

**Conseil :** configurer le raccourci d'accessibilité **avant** le premier test, pour pouvoir désactiver VoiceOver rapidement.

---

## 2. Gestes de navigation de base

|Action|Geste|Objectif du test|
|---|---|---|
|Entendre l'élément sous le doigt|Toucher l'écran ou y faire glisser un doigt|Vérifier ce qui est annoncé à une position donnée|
|Sélectionner un élément|Toucher avec 1 doigt|Placer le focus sur l'élément et annoncer son libellé|
|Activer un élément|Toucher deux fois avec 1 doigt|Déclencher le contrôle|
|Élément suivant|Balayer vers la droite avec 1 doigt|Ordre de navigation vers l'avant|
|Élément précédent|Balayer vers la gauche avec 1 doigt|Ordre de navigation vers l'arrière|
|Premier / dernier élément de l'écran|Toucher avec 4 doigts près du haut / du bas de l'écran|Vérifier le début et la fin de l'ordre de lecture|
|Lire depuis le haut|Balayer vers le haut avec 2 doigts|Revue de tout l'écran|
|Lire depuis l'élément actuel|Balayer vers le bas avec 2 doigts|Revue à partir d'un point donné|
|Mettre en pause / reprendre la parole|Toucher avec 2 doigts|Contrôler la parole|
|Faire défiler d'une page|Balayer vers le haut / bas avec 3 doigts|Faire défiler le contenu|
|Sélecteur d'éléments (liste des éléments de l'écran)|Toucher trois fois avec 2 doigts|Trouver rapidement un élément|
|Échapper / retour|Frotter avec 2 doigts (déplacer deux doigts trois fois rapidement d'avant en arrière, en formant un « z »)|Fermer les alertes, quitter les dialogues / vues|

---

## 3. Le rotor

|Action|Geste|Objectif du test|
|---|---|---|
|Choisir un réglage du rotor|Rotation à 2 doigts (comme pour tourner une molette) ; VoiceOver annonce chaque réglage, lever les doigts pour le choisir|Changer de mode de navigation|
|Aller à l'élément suivant du réglage choisi|Balayer vers le bas avec 1 doigt|Valider la structure (titres, contrôles de formulaire, points de repère, etc.)|
|Aller à l'élément précédent du réglage choisi|Balayer vers le haut avec 1 doigt|Vérifier le regroupement sémantique|

**Modifier la liste :** Réglages > Accessibilité > VoiceOver > Rotor > Éléments du rotor (*Rotor Items*).

---

## 4. Comportement des interactions

|Action|Geste|Objectif du test|
|---|---|---|
|Activer l'action par défaut|Toucher deux fois|Équivalent d'un toucher/clic|
|Actions personnalisées|Lorsque VoiceOver annonce « Actions disponibles » : rotor **Actions**, balayer vers le haut / bas avec 1 doigt pour entendre chaque action, toucher deux fois pour l'exécuter|Vérifier les actions personnalisées|
|Appui long ou autre geste standard|Toucher deux fois et maintenir jusqu'à entendre trois tonalités ascendantes, puis effectuer le geste|Vérifier le comportement de l'appui long ; s'assurer que les actions secondaires sont aussi exposées dans le rotor Actions|
|Régler un curseur ou un autre contrôle ajustable|Le sélectionner, puis balayer vers le haut / bas avec 1 doigt|Vérifier les contrôles ajustables|
|Démarrer ou arrêter l'action en cours (média, enregistrement)|Toucher deux fois avec 2 doigts|Vérifier l'action principale des contrôles média|

---

## 5. Édition de texte

|Action|Geste|Objectif du test|
|---|---|---|
|Entrer en mode édition|Toucher deux fois le champ|Placer le focus dans le champ et ouvrir le clavier|
|Navigation par caractère / mot|Rotor **Caractères** ou **Mots** + balayer vers le haut / bas avec 1 doigt|Valider la granularité|
|Actions d'édition (sélectionner, copier, coller)|Rotor **Édition** (disponible pendant l'édition d'un champ) + balayer vers le haut / bas avec 1 doigt, puis toucher deux fois|Vérifier l'édition et la sélection de texte|

---

## 6. Contrôles système (support aux tests)

| Action | Geste | Objectif |
| --- | --- | --- |
| Activer/désactiver VoiceOver | Triple-clic sur le bouton latéral | **Activer ou désactiver VoiceOver** (si le raccourci d'accessibilité est réglé sur VoiceOver) |
| Mettre en pause / reprendre la parole | Toucher avec 2 doigts | Contrôler la verbosité |
| Couper / rétablir la parole de VoiceOver | Toucher deux fois avec 3 doigts | Couper la parole tout en gardant VoiceOver actif |
| Entraînement VoiceOver | Réglages > Accessibilité > VoiceOver > Entraînement VoiceOver | S'entraîner aux gestes sans les déclencher |

---

## 7. Rideau d'écran (important pour des tests réalistes)

| Fonctionnalité | Geste | Pourquoi c'est important |
| --- | --- | --- |
| Rideau d'écran | Toucher trois fois avec 3 doigts (quatre fois avec 3 doigts si le Zoom est aussi activé) | **Éteint l'affichage tout en gardant VoiceOver actif** — le testeur ne dispose que de ce qui est annoncé, comme un utilisateur aveugle |

---

## 8. Navigation dans Safari avec VoiceOver (focus sur les tests web)

| Action | Geste / commande | Objectif du test |
| --- | --- | --- |
| Aller à l'élément suivant de la page | Balayer vers la droite avec 1 doigt | Parcourir le texte, les liens, les boutons, les champs de formulaire |
| Aller à l'élément précédent | Balayer vers la gauche avec 1 doigt | Ordre de navigation inversé |
| Activer un lien | Toucher deux fois avec 1 doigt | Ouvrir la page / déclencher la navigation |
| Faire défiler la page | Balayer vers le haut/bas avec 3 doigts | Parcourir le contenu web |
| Lecture continue | Balayer avec 2 doigts vers le haut (depuis le haut) ou vers le bas (depuis l'élément actuel) | Auditer le flux complet du contenu de la page |
| Mettre la parole en pause | Toucher avec 2 doigts | Contrôler la verbosité pendant l'inspection |
| Retour | Frotter avec 2 doigts, ou sélectionner le bouton Précédent de Safari | Quitter un dialogue ou revenir à l'écran précédent |
| Avancer | Sélectionner le bouton Suivant de Safari (VoiceOver n'a pas de geste « avancer ») | Aller à la page suivante |

### Contrôles de navigation propres à Safari

| Action | Geste / commande | Objectif du test |
| --- | --- | --- |
| Ouvrir le rotor (éléments web) | Rotation à 2 doigts | Passer d'une option à l'autre : Titres, Points de repère, Liens, Liens visités, Contrôles de formulaire, Tableaux, etc. |
| Naviguer par titres | Rotor → Titres + balayer vers le bas/haut | Valider la structure sémantique de la page |
| Naviguer par points de repère | Rotor → Points de repère + balayer vers le bas/haut | Vérifier les régions de la page |
| Naviguer par liens | Rotor → Liens + balayer vers le bas/haut | Vérifier la structure et l'étiquetage des liens |
| Naviguer par contrôles de formulaire | Rotor → Contrôles de formulaire + balayer vers le bas/haut | S'assurer que les champs sont atteignables et étiquetés |
| Lister les éléments de la page | Sélecteur d'éléments : toucher trois fois avec 2 doigts | Localiser rapidement un élément précis |

---

## 9. Points de contrôle QA de l'accessibilité

|Domaine|Cible de validation|
|---|---|
|Ordre du focus|Logique et complet en balayant vers la droite|
|Libellés|Chaque élément est annoncé de manière explicite|
|Actions|Toutes les interactions sont atteignables avec VoiceOver|
|Modales|Le contenu derrière un dialogue ouvert n'est pas atteignable|
|Mises à jour|Les changements dynamiques et les messages sont annoncés|
|Interface masquée|Aucun accès aux éléments masqués ou inactifs|
|Écran masqué|La tâche principale peut être réalisée avec le rideau d'écran activé|

---

## 10. Défaillances courantes

| Problème | Symptôme observable |
| --- | --- |
| Libellés manquants | Seul le rôle (« Bouton ») est annoncé, sans nom |
| Ordre cassé | Navigation qui saute des éléments ou tourne en boucle |
| Interface non focalisable | Éléments inatteignables en balayant |
| Mises à jour silencieuses | Aucun retour sonore après une action |
| Problèmes de sortie des modales | Arrière-plan encore atteignable |

---

## Sources

- Apple — [iPhone User Guide, Use VoiceOver gestures on iPhone](https://support.apple.com/guide/iphone/use-voiceover-gestures-iph3e2e2281/ios)
- Apple — [Learn VoiceOver gestures on iPhone (iOS 13 edition, gesture tables)](https://support.apple.com/guide/iphone/iph3e2e2281/13.0/ios/13.0)
- Apple — [Turn on and practice VoiceOver on iPhone](https://support.apple.com/guide/iphone/turn-on-and-practice-voiceover-iph3e2e415f/ios)
- Apple Support — [About the VoiceOver rotor on iPhone or iPad](https://support.apple.com/en-us/111796)
- Apple Developer Forums — [Adjustable elements and custom accessibility actions (Actions rotor)](https://developer.apple.com/forums/thread/726964)
- AppleVis — [iDevice Primer 103: What is the rotor for and how do I use it?](https://applevis.com/guides/idevice-primer-103-what-rotor-how-do-i-use-it) (guide communautaire : rotor Édition, Actions)
