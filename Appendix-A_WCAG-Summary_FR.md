# Annexe A — Synthèse des WCAG

## Introduction

### Qu'est-ce que le WCAG ?

Les **WCAG** (_Web Content Accessibility Guidelines_ – Règles pour l'accessibilité des contenus web) sont un ensemble de recommandations publiées par le **W3C**, à travers son initiative **WAI** (_Web Accessibility Initiative_).
Elles ont pour but de rendre les sites, applications et services numériques accessibles à toutes et à tous, y compris aux personnes en situation de handicap (visuel, auditif, moteur, cognitif, etc.).

La version actuelle est **WCAG 2.2** (Recommandation du W3C du 5 octobre 2023, mise à jour le 12 décembre 2024). Le W3C en publie une traduction française autorisée.

[https://www.w3.org/TR/WCAG22/](https://www.w3.org/TR/WCAG22/)

### Objectifs

Les WCAG poursuivent trois grands objectifs :

- **Assurer l'accessibilité universelle** : permettre l'usage du web quelles que soient les capacités physiques, sensorielles ou technologiques des utilisateurs.
- **Fournir une référence internationale** : offrir un cadre reconnu pour la conception de contenus accessibles. Les WCAG 2.2 sont aussi publiées comme norme internationale **ISO/IEC 40500:2025**.
- **Soutenir la réglementation** : servir de base à de nombreuses lois et normes en matière d'accessibilité numérique, comme le **RGAA** en France, la norme **EN 301 549** en Europe, la norme **eCH-0059** en Suisse, ou la **Section 508** aux États-Unis.

---

## Principes fondamentaux du WCAG

Les WCAG reposent sur quatre grands **principes _(principles)_**, souvent résumés par l'acronyme **P.O.U.R.**
Ces principes définissent les bases de toute accessibilité numérique : un contenu qui ne respecte pas l'un d'eux ne peut être considéré comme accessible.

Pour chaque principe il y a des **règles** _**(guidelines)**_ (13 au total dans les WCAG 2.2), qui fixent les objectifs à atteindre pour que les applications soient accessibles aux utilisateurs en situation de handicap. Les règles ne sont pas testables.

Chaque règle possède une liste de **critères de succès** _**(success criteria)**_, testables, qui permettent de valider la conformité. Les WCAG 2.2 comptent **86 critères de succès** (le critère 4.1.1 Analyse syntaxique est obsolète et a été retiré).
Afin de répondre aux besoins des différents groupes et situations, trois niveaux de conformité sont définis : A (le plus bas), AA et AAA (le plus élevé).

### Chapitre 1 – Perceptible (_Perceivable_)

Les informations et les éléments de l'interface doivent être présentés de manière à pouvoir être perçus par tous les utilisateurs.
Le principe _Perceptible_ rappelle que l'information doit être présentée de façon à ce que chaque utilisateur puisse l'appréhender, quels que soient ses moyens sensoriels.
Cela implique de rendre visibles, audibles ou compréhensibles les contenus à travers différents formats.

- _Exemple : fournir des textes alternatifs pour les images ou assurer un contraste suffisant entre le texte et l'arrière-plan._

Les règles de ce principe sont :

- **1.1 Équivalents textuels** : fournir des descriptions textuelles pour les images, icônes ou tout contenu non textuel.
- **1.2 Média temporel** : proposer des sous-titres, transcriptions ou audio-descriptions pour les vidéos et contenus multimédias.
- **1.3 Adaptable** : permettre de présenter le contenu sous différentes formes (par exemple, en mode lecture simplifiée ou avec une autre mise en page) sans perte d'information ni de structure.
- **1.4 Distinguable** : s'assurer que les éléments essentiels soient faciles à voir et à entendre, grâce à des contrastes suffisants, un texte redimensionnable et une séparation nette entre premier plan et arrière-plan.

### Chapitre 2 – Utilisable (_Operable_)

L'interface et la navigation doivent pouvoir être utilisées, quels que soient les moyens de navigation.
Le principe _Utilisable_ insiste sur le fait qu'un site ou une application doit pouvoir être manipulé facilement, quels que soient les moyens de saisie employés (clavier, souris, écran tactile, commandes vocales, etc.). Une interface accessible ne se limite pas à être visible : elle doit aussi être actionnable par tous.

- _Exemple : permettre l'accès complet au site uniquement au clavier, ou s'assurer que les zones interactives soient suffisamment grandes pour être manipulées facilement._

Les règles de ce principe sont :

- **2.1 Accessibilité au clavier** : permettre l'accès complet au contenu et aux fonctionnalités sans recourir à la souris.
- **2.2 Délai suffisant** : donner aux utilisateurs le temps de lire, comprendre et interagir avec les contenus, sans contraintes de temps excessives.
- **2.3 Crises et réactions physiques** : limiter les contenus susceptibles de provoquer des réactions négatives (par exemple, éviter les animations clignotantes qui peuvent déclencher des crises d'épilepsie).
- **2.4 Navigable** : fournir des moyens clairs pour s'orienter dans le site (titres de page, menus cohérents, titres explicites, focus visible, etc.).
- **2.5 Modalités d'entrée** : rendre les fonctionnalités utilisables avec d'autres moyens que le clavier (pointeur, toucher, gestes, mouvement de l'appareil), par exemple avec des cibles suffisamment grandes et des alternatives simples aux gestes complexes.

En résumé, un contenu utilisable est un contenu qui ne met pas d'obstacle à l'interaction, quel que soit le dispositif ou la méthode employée par l'utilisateur.

### Chapitre 3 – Compréhensible (_Understandable_)

Les informations et le fonctionnement de l'interface doivent être clairs et prévisibles.
Le principe _Compréhensible_ signifie que le contenu et le fonctionnement d'un site ou d'une application doivent être clairs, prévisibles et faciles à comprendre pour tous les utilisateurs.
Il ne suffit pas que l'information soit visible et manipulable : elle doit aussi être intelligible.

- _Exemple : utiliser un langage simple, donner des instructions explicites et éviter les comportements inattendus (comme un bouton qui change brusquement de fonction)._

Les règles de ce principe sont :

- **3.1 Lisible** : rendre identifiable la langue de la page et de ses passages, et rendre le texte compréhensible (mots rares, abréviations, niveau de lecture).
- **3.2 Prévisible** : maintenir une cohérence dans la navigation et le comportement des éléments interactifs, afin que l'utilisateur sache à quoi s'attendre.
- **3.3 Assistance à la saisie** : aider l'utilisateur à éviter et corriger les erreurs, avec des étiquettes, des instructions claires, des messages d'erreur explicites et des suggestions, y compris pour les utilisateurs ayant des difficultés cognitives ou des troubles d'apprentissage.

En résumé, un contenu compréhensible est un contenu qui permet à l'utilisateur de saisir l'information et d'interagir avec elle sans confusion ni frustration.

### Chapitre 4 – Robuste (_Robust_)

Le contenu doit être techniquement fiable et interprétable par une grande variété d'agents utilisateurs, y compris les technologies d'assistance actuelles et futures.
Le principe _Robuste_ signifie que le contenu doit pouvoir être interprété de manière fiable par différents outils et technologies, y compris les technologies d'assistance actuelles et futures.
Il s'agit de garantir que le site ou l'application reste accessible même si le contexte technique ou le dispositif change.

- _Exemple : respecter les standards du web pour que les lecteurs d'écran et autres outils puissent interpréter correctement la page._

Ce principe comporte une seule règle :

- **4.1 Compatible** : optimiser la compatibilité avec les agents utilisateurs actuels et futurs, y compris les technologies d'assistance. En pratique : chaque composant expose un nom, un rôle, des états et des valeurs que les technologies d'assistance peuvent déterminer (usage correct du HTML et d'ARIA), et les messages d'état sont annoncés sans déplacer le focus.

En résumé, un contenu robuste est un contenu qui reste fiable et utilisable, quels que soient le dispositif, le navigateur ou la technologie d'assistance employée.

---

## Chapitre 1 : Perceptible

Ce chapitre présente l'ensemble des critères du _principe 1 des WCAG 2.2 – Perceptible_, avec le numéro, le niveau de conformité (A, AA, AAA) et une brève description de chaque point.

### 1.1 Équivalents textuels

- **1.1.1 Contenu non textuel (A)** : tout contenu non textuel dispose d'une alternative textuelle qui remplit la même fonction (le contenu décoratif est ignoré par les technologies d'assistance).

### 1.2 Média temporel

- **1.2.1 Contenus seulement audio et seulement vidéo (pré-enregistrés) (A)** : fournir une alternative textuelle pour les contenus seulement audio pré-enregistrés, et une alternative textuelle ou audio pour les contenus seulement vidéo pré-enregistrés.
- **1.2.2 Sous-titres (pré-enregistrés) (A)** : des sous-titres sont fournis pour tout contenu audio pré-enregistré dans un média synchronisé.
- **1.2.3 Audio-description ou version de remplacement pour un média temporel (pré-enregistré) (A)** : les vidéos pré-enregistrées ont une audio-description ou une alternative textuelle complète (transcription).
- **1.2.4 Sous-titres (en direct) (AA)** : des sous-titres sont fournis pour tout contenu audio en direct dans un média synchronisé.
- **1.2.5 Audio-description (pré-enregistrée) (AA)** : une audio-description est fournie pour le contenu vidéo pré-enregistré d'un média synchronisé.
- **1.2.6 Langue des signes (pré-enregistrée) (AAA)** : une interprétation en langue des signes est fournie pour le contenu audio pré-enregistré d'un média synchronisé.
- **1.2.7 Audio-description étendue (pré-enregistrée) (AAA)** : lorsque les pauses dans l'audio sont trop courtes pour une audio-description, la vidéo est mise en pause pour permettre une description étendue.
- **1.2.8 Version de remplacement pour un média temporel (pré-enregistrée) (AAA)** : une alternative textuelle complète est fournie pour tous les médias synchronisés pré-enregistrés et les contenus seulement vidéo.
- **1.2.9 Seulement audio (en direct) (AAA)** : une alternative (par exemple des sous-titres en direct ou une transcription) est fournie pour les contenus seulement audio en direct.

### 1.3 Adaptable

- **1.3.1 Information et relations (A)** : la structure et les relations entre éléments (titres, listes, tableaux, champs de formulaire et leurs étiquettes) sont déterminables par le code et compréhensibles par les technologies d'assistance.
- **1.3.2 Ordre séquentiel logique (A)** : l'ordre de lecture est logique et déterminable par le code, indépendamment de la présentation visuelle.
- **1.3.3 Caractéristiques sensorielles (A)** : les instructions ne reposent pas uniquement sur des caractéristiques sensorielles (forme, couleur, taille, position visuelle, orientation ou son).
- **1.3.4 Orientation (AA)** : le contenu n'est pas limité à une seule orientation de l'écran (portrait/paysage), sauf si une orientation précise est essentielle.
- **1.3.5 Identifier la finalité de la saisie (AA)** : la finalité des champs qui recueillent des informations sur l'utilisateur (nom, e-mail, adresse, etc.) est déterminable par le code, par exemple avec l'attribut `autocomplete`.
- **1.3.6 Identifier la fonction (AAA)** : la fonction des composants d'interface, des icônes et des régions est déterminable par le code.

### 1.4 Distinguable

- **1.4.1 Utilisation de la couleur (A)** : la couleur n'est pas le seul moyen de transmettre une information, d'indiquer une action ou de distinguer un élément.
- **1.4.2 Contrôle du son (A)** : un son joué automatiquement pendant plus de 3 secondes peut être mis en pause ou arrêté, ou son volume réglé indépendamment.
- **1.4.3 Contraste (minimum) (AA)** : le texte et les images de texte ont un rapport de contraste d'au moins 4,5:1 avec l'arrière-plan (3:1 pour le texte en grands caractères).
- **1.4.4 Redimensionnement du texte (AA)** : le texte peut être agrandi jusqu'à 200 % sans perte de contenu ni de fonctionnalité.
- **1.4.5 Texte sous forme d'image (AA)** : du vrai texte est utilisé plutôt que des images de texte, sauf images personnalisables ou présentation essentielle (par exemple un logo).
- **1.4.6 Contraste (amélioré) (AAA)** : contraste du texte et des images de texte porté à 7:1 (4,5:1 pour le texte en grands caractères).
- **1.4.7 Arrière-plan sonore de faible volume ou absent (AAA)** : la parole pré-enregistrée n'a pas de son d'arrière-plan, ou celui-ci peut être coupé, ou il est au moins 20 dB plus faible que la parole.
- **1.4.8 Présentation visuelle (AAA)** : les blocs de texte peuvent être présentés avec des couleurs choisies par l'utilisateur, une largeur de ligne limitée, sans justification, avec un interlignage suffisant, et être agrandis sans défilement horizontal.
- **1.4.9 Texte sous forme d'image (sans exception) (AAA)** : les images de texte ne sont utilisées que pour la décoration ou lorsqu'une présentation précise est essentielle.
- **1.4.10 Redistribution (AA)** : le contenu peut être présenté sans perte d'information ni de fonctionnalité, et sans défilement dans deux dimensions, à une largeur équivalente à 320 pixels CSS.
- **1.4.11 Contraste du contenu non textuel (AA)** : les composants d'interface (bordures, états, indicateur de focus) et les objets graphiques nécessaires à la compréhension ont un rapport de contraste d'au moins 3:1.
- **1.4.12 Espacement du texte (AA)** : aucun contenu ni aucune fonctionnalité n'est perdu lorsque l'utilisateur augmente l'interlignage, l'espacement des paragraphes, des lettres et des mots.
- **1.4.13 Contenu au survol ou au focus (AA)** : le contenu qui apparaît au survol ou au focus peut être masqué, peut être survolé, et reste visible jusqu'à ce que l'utilisateur le masque.

---

## Chapitre 2 – Utilisable

Ce chapitre présente l'ensemble des critères du _principe 2 des WCAG 2.2 – Utilisable_, avec le numéro, le niveau de conformité (A, AA, AAA) et une brève description de chaque point.

### 2.1 Accessibilité au clavier

- **2.1.1 Clavier (A)** : toutes les fonctionnalités sont utilisables au clavier, sans exiger de rythme précis pour la frappe des touches.
- **2.1.2 Pas de piège au clavier (A)** : le focus clavier peut toujours être retiré d'un composant à l'aide du seul clavier.
- **2.1.3 Clavier (pas d'exception) (AAA)** : toutes les fonctionnalités sont utilisables au clavier, sans exception.
- **2.1.4 Raccourcis clavier utilisant des caractères (A)** : les raccourcis clavier composés d'une seule touche caractère peuvent être désactivés, reconfigurés, ou ne sont actifs que lorsque le composant a le focus.

### 2.2 Délai suffisant

- **2.2.1 Réglage du délai (A)** : pour chaque limite de temps, l'utilisateur peut la désactiver, l'ajuster ou la prolonger (avec des exceptions pour les événements en temps réel et les limites essentielles).
- **2.2.2 Mettre en pause, arrêter, masquer (A)** : tout contenu en mouvement, clignotant, défilant ou mis à jour automatiquement peut être mis en pause, arrêté ou masqué.
- **2.2.3 Pas de délai d'exécution (AAA)** : le temps n'est pas un élément essentiel de l'événement ou de l'activité (sauf médias synchronisés non interactifs et événements en temps réel).
- **2.2.4 Interruptions (AAA)** : les interruptions (alertes, mises à jour) peuvent être reportées ou supprimées par l'utilisateur, sauf en cas d'urgence.
- **2.2.5 Nouvelle authentification (AAA)** : à l'expiration d'une session, l'utilisateur peut poursuivre l'activité sans perte de données après s'être authentifié de nouveau.
- **2.2.6 Délais d'expiration (AAA)** : l'utilisateur est averti de la durée d'inactivité qui peut entraîner une perte de données, sauf si les données sont conservées plus de 20 heures.

### 2.3 Crises et réactions physiques

- **2.3.1 Pas plus de trois flashs ou sous le seuil critique (A)** : les pages ne contiennent rien qui flashe plus de trois fois par seconde, ou le flash est sous les seuils de flash général et de flash rouge.
- **2.3.2 Trois flashs (AAA)** : les pages ne contiennent rien qui flashe plus de trois fois par seconde.
- **2.3.3 Animation résultant d'interactions (AAA)** : les animations de mouvement déclenchées par une interaction peuvent être désactivées, sauf si l'animation est essentielle.

### 2.4 Navigable

- **2.4.1 Contourner des blocs (A)** : un mécanisme permet de contourner les blocs de contenu répétés sur plusieurs pages (lien d'évitement, repères, titres).
- **2.4.2 Titre de page (A)** : chaque page a un titre qui décrit son sujet ou sa finalité.
- **2.4.3 Parcours du focus (A)** : l'ordre du focus préserve la signification et l'opérabilité.
- **2.4.4 Fonction du lien (selon le contexte) (A)** : la fonction de chaque lien peut être déterminée par son intitulé, ou par son intitulé et son contexte déterminé par le code.
- **2.4.5 Accès multiples (AA)** : plusieurs moyens permettent de trouver une page dans un ensemble de pages (menu, recherche, plan du site…).
- **2.4.6 En-têtes et étiquettes (AA)** : les titres et les étiquettes décrivent le sujet ou la finalité.
- **2.4.7 Visibilité du focus (AA)** : l'indicateur de focus clavier est visible.
- **2.4.8 Localisation (AAA)** : une information sur la position de l'utilisateur dans l'ensemble de pages est disponible (fil d'Ariane, page courante indiquée).
- **2.4.9 Fonction du lien (lien uniquement) (AAA)** : la fonction de chaque lien peut être identifiée par son seul intitulé.
- **2.4.10 En-têtes de section (AAA)** : des titres de section sont utilisés pour organiser le contenu.
- **2.4.11 Focus non obscurci (minimum) (AA)** : un composant qui reçoit le focus clavier n'est pas entièrement masqué par un contenu créé par l'auteur (en-tête fixe, bandeau de cookies…).
- **2.4.12 Focus non obscurci (amélioré) (AAA)** : aucune partie du composant qui a le focus n'est masquée par un contenu créé par l'auteur.
- **2.4.13 Apparence du focus (AAA)** : l'indicateur de focus respecte des exigences minimales de taille et de contraste entre l'état avec et sans focus.

### 2.5 Modalités d'entrée

- **2.5.1 Gestes pour le contrôle du pointeur (A)** : les fonctionnalités qui utilisent des gestes multipoints ou basés sur un tracé peuvent aussi être utilisées avec un pointeur unique sans tracé.
- **2.5.2 Annulation de l'action du pointeur (A)** : une fonctionnalité utilisée avec un pointeur unique n'est pas déclenchée au seul appui (événement « down »), ou l'action peut être interrompue ou annulée.
- **2.5.3 Étiquette dans le nom (A)** : le nom accessible d'un composant qui a une étiquette textuelle visible contient ce texte visible.
- **2.5.4 Activation par le mouvement (A)** : une fonctionnalité déclenchée par le mouvement de l'appareil ou de l'utilisateur peut aussi être utilisée via l'interface, et la réponse au mouvement peut être désactivée.
- **2.5.5 Taille de la cible (amélioré) (AAA)** : les cibles de pointeur mesurent au moins 44 × 44 pixels CSS (avec exceptions).
- **2.5.6 Modalités d'entrée concurrentes (AAA)** : le contenu ne restreint pas l'usage des modalités d'entrée disponibles sur la plateforme.
- **2.5.7 Déplacements par glisser-déposer (AA)** : une fonctionnalité qui utilise le glisser peut aussi être réalisée avec un pointeur unique sans glisser.
- **2.5.8 Taille de la cible (minimum) (AA)** : les cibles de pointeur mesurent au moins 24 × 24 pixels CSS, ou disposent d'un espacement suffisant (avec exceptions).

---

## Chapitre 3 : Compréhensible

Ce chapitre présente l'ensemble des critères du _principe 3 des WCAG 2.2 – Compréhensible_, avec le numéro, le niveau de conformité (A, AA, AAA) et une brève description de chaque point.

### 3.1 Lisible

- **3.1.1 Langue de la page (A)** : la langue humaine par défaut de la page est déterminable par le code.
- **3.1.2 Langue d'un passage (AA)** : la langue de chaque passage dans une autre langue que celle de la page est déterminable par le code.
- **3.1.3 Mots rares (AAA)** : un mécanisme permet d'identifier la définition des mots utilisés de façon inhabituelle ou restreinte, y compris les expressions idiomatiques et le jargon.
- **3.1.4 Abréviations (AAA)** : un mécanisme permet d'identifier la forme développée ou la signification des abréviations.
- **3.1.5 Niveau de lecture (AAA)** : lorsqu'un texte exige une capacité de lecture supérieure au premier cycle de l'enseignement secondaire, un contenu supplémentaire ou une version plus simple est disponible.
- **3.1.6 Prononciation (AAA)** : un mécanisme permet d'identifier la prononciation des mots dont le sens est ambigu sans elle.

### 3.2 Prévisible

- **3.2.1 Au focus (A)** : la prise de focus ne déclenche pas de changement de contexte.
- **3.2.2 À la saisie (A)** : modifier le paramètre d'un composant ne provoque pas automatiquement de changement de contexte, sauf si l'utilisateur en a été averti au préalable.
- **3.2.3 Navigation cohérente (AA)** : les mécanismes de navigation répétés sur plusieurs pages apparaissent dans le même ordre relatif.
- **3.2.4 Identification cohérente (AA)** : les composants ayant la même fonction sont identifiés de manière cohérente d'une page à l'autre.
- **3.2.5 Changement à la demande (AAA)** : les changements de contexte ne sont déclenchés qu'à la demande de l'utilisateur, ou un mécanisme permet de les désactiver.
- **3.2.6 Aide cohérente (A)** : les mécanismes d'aide (coordonnées, formulaire de contact, chat, FAQ) répétés sur plusieurs pages apparaissent dans le même ordre relatif.

### 3.3 Assistance à la saisie

- **3.3.1 Identification des erreurs (A)** : lorsqu'une erreur de saisie est détectée automatiquement, l'élément en erreur est identifié et l'erreur est décrite à l'utilisateur sous forme de texte.
- **3.3.2 Étiquettes ou instructions (A)** : des étiquettes ou des instructions sont fournies lorsque le contenu demande une saisie de l'utilisateur.
- **3.3.3 Suggestion après une erreur (AA)** : lorsqu'une erreur de saisie est détectée et que des suggestions de correction sont connues, elles sont proposées à l'utilisateur (sauf si cela compromet la sécurité ou la finalité).
- **3.3.4 Prévention des erreurs (juridiques, financières, de données) (AA)** : pour les soumissions qui ont des conséquences juridiques ou financières, ou qui modifient ou suppriment des données, la soumission est réversible, vérifiée ou confirmée par l'utilisateur.
- **3.3.5 Aide (AAA)** : une aide contextuelle est disponible.
- **3.3.6 Prévention des erreurs (toutes) (AAA)** : la même protection que 3.3.4 s'applique à toutes les soumissions d'informations.
- **3.3.7 Saisie redondante (A)** : une information déjà saisie par l'utilisateur dans le même processus est pré-remplie ou proposée en sélection, plutôt que d'avoir à la saisir de nouveau.
- **3.3.8 Authentification accessible (minimum) (AA)** : aucune étape d'un processus d'authentification ne repose sur un test de fonction cognitive (mémoriser un mot de passe, résoudre une énigme), sauf si une alternative ou un mécanisme d'assistance est disponible (gestionnaire de mots de passe, copier-coller, reconnaissance d'objets…).
- **3.3.9 Authentification accessible (amélioré) (AAA)** : comme 3.3.8, sans les exceptions de reconnaissance d'objets et de contenu personnel.

---

## Chapitre 4 : Robuste

Ce chapitre présente l'ensemble des critères du _principe 4 des WCAG 2.2 – Robuste_, avec le numéro, le niveau de conformité (A, AA, AAA) et une brève description de chaque point.

### 4.1 Compatible

- **4.1.1 Analyse syntaxique** : obsolète et retiré dans les WCAG 2.2 (il est considéré comme toujours satisfait pour les contenus HTML et XML).
- **4.1.2 Nom, rôle et valeur (A)** : pour tous les composants d'interface, le nom et le rôle sont déterminables par le code ; les états, propriétés et valeurs peuvent être définis par le code, et leurs changements sont notifiés aux technologies d'assistance.
- **4.1.3 Messages d'état (AA)** : les messages d'état (confirmation, erreur, progression, résultats de recherche) sont déterminables par le code, afin que les technologies d'assistance puissent les annoncer sans déplacer le focus.

---

## Conformité aux WCAG

#### Cadre officiel de conformité et exigences formelles

La conformité définit **comment un contenu web peut être déclaré conforme aux WCAG** et selon quelles conditions.
Elle ne porte pas sur l'expérience utilisateur uniquement, mais sur le **respect mesurable des critères de succès**.

### Niveaux de conformité

La conformité est structurée en trois niveaux hiérarchiques :

- **Niveau A** : exigences minimales indispensables à l'accessibilité.
- **Niveau AA** : niveau intermédiaire, généralement exigé par les réglementations (ex. marchés publics).
- **Niveau AAA** : niveau maximal. Les WCAG ne recommandent pas d'exiger le niveau AAA comme politique générale pour des sites entiers, car certains contenus ne peuvent pas satisfaire tous les critères AAA.

👉 Pour être conforme au niveau AA, **tous les critères A + AA doivent être respectés** (ou une version de remplacement conforme doit être fournie).

### Les 5 exigences de conformité

Pour qu'une page soit conforme, les WCAG 2.2 (section 5.2) fixent **5 exigences**, toutes obligatoires :

#### 1. Niveau de conformité

Un des niveaux (A, AA ou AAA) est **atteint en totalité** : la page satisfait tous les critères de succès de ce niveau et des niveaux inférieurs, ou une version de remplacement conforme est fournie.

#### 2. Pages complètes

La conformité s'applique à **la page entière**, et non à une partie isolée.

- Si une section n'est pas conforme, la page entière ne l'est pas.
- Les composants tiers intégrés (widgets, modules externes) font partie de la page. S'ils ne peuvent pas être corrigés, l'auteur ne peut faire qu'une _déclaration de conformité partielle_ pour contenu tiers.

#### 3. Processus complets

Lorsqu'un service implique plusieurs étapes (ex. commande en ligne, inscription, paiement),
**toutes les étapes doivent être conformes** au niveau déclaré.

Un seul écran non conforme invalide le processus complet.

#### 4. Uniquement des façons d'utiliser les technologies compatibles avec l'accessibilité

Seules les façons d'utiliser les technologies qui sont :

- prises en charge par les technologies d'assistance des utilisateurs (lecteurs d'écran, navigation clavier, etc.),
- et correctement implémentées

peuvent être utilisées pour satisfaire les critères de succès. Toute information ou fonctionnalité fournie d'une autre façon doit aussi être disponible d'une façon compatible avec l'accessibilité.

#### 5. Non-interférence

Les contenus non conformes sont tolérés **uniquement s'ils ne bloquent pas l'accès au reste de la page**. Quatre critères s'appliquent à tout le contenu sans exception : 1.4.2 Contrôle du son, 2.1.2 Pas de piège au clavier, 2.3.1 Pas plus de trois flashs ou sous le seuil critique et 2.2.2 Mettre en pause, arrêter, masquer.

Exemple :

- Une animation décorative ne doit pas empêcher la navigation clavier.
- Un script non accessible ne doit pas piéger un utilisateur de lecteur d'écran.

#### Points clés à retenir

- La conformité WCAG est **formelle et vérifiable**.
- Elle s'applique à une page complète ou à un processus complet.
- Le niveau AA est aujourd'hui le standard réglementaire le plus courant.
- L'intégration de composants tiers n'exonère pas de responsabilité : ils font partie de la page.
- Une déclaration de conformité est facultative au sens des WCAG ; lorsqu'elle est faite, elle doit contenir les informations requises et être transparente et documentée.

---

## Déclaration de conformité et cadre réglementaire

### Déclaration officielle d'accessibilité (Accessibility Statement)

#### Rôle et objectif

La déclaration d'accessibilité est un document public qui :

- informe les utilisateurs du niveau réel d'accessibilité du service,
- précise le référentiel utilisé (WCAG, EN 301 549, RGAA, eCH-0059, etc.),
- indique l'état de conformité atteint,
- détaille les éventuelles non-conformités et les alternatives accessibles,
- fournit un contact et un mécanisme de retour pour signaler un problème.

Dans l'Union européenne, elle est obligatoire pour les sites web et applications mobiles des **organismes du secteur public** (directive (UE) 2016/2102), sur la base d'un modèle fixé par la décision d'exécution (UE) 2018/1523.

#### Contenu minimal recommandé

Une déclaration devrait inclure :

##### 1. Référentiel utilisé

- Version de la norme appliquée (ex. **WCAG 2.2**, ou **EN 301 549**)
- Ou référentiel national (ex. **RGAA** en France, **eCH-0059** en Suisse)

##### 2. État de conformité

- Totalement conforme
- Partiellement conforme
- Non conforme

##### 3. Évaluation

- Date de l'évaluation
- Méthode utilisée (auto-évaluation ou évaluation par un tiers)
- Outils de test

##### 4. Contenus non accessibles

- Liste précise des critères non respectés
- Justification éventuelle (charge disproportionnée, contenu tiers, contenu hors du champ d'application, etc.)

##### 5. Mécanisme de contact

- E-mail ou formulaire permettant de signaler un problème ou de demander un contenu inaccessible

##### 6. Voie de recours

- Information sur l'autorité compétente en l'absence de réponse satisfaisante

#### Points clés à retenir

- La déclaration est publique : elle engage l'organisation sur l'accessibilité qu'elle décrit.
- Elle doit être tenue à jour.
- Elle ne remplace pas la conformité réelle : elle la documente.

### Implications juridiques et cadres réglementaires

#### Référentiels nationaux

Les WCAG sont un standard international du **World Wide Web Consortium**,
mais les obligations légales dépendent des législations nationales (et européennes).

En France :

- Le référentiel officiel est le **Référentiel général d'amélioration de l'accessibilité (RGAA)**.
- Il est obligatoire pour :
    - les services publics,
    - les délégataires de service public,
    - certaines grandes entreprises.

La version actuelle, **RGAA 4.1.2**, est basée sur les WCAG 2.1 niveaux A et AA. Le **RGAA 5** est en préparation, avec une publication prévue fin 2026.

#### Cadre européen

L'**European Accessibility Act** (EAA, directive (UE) 2019/882) :

- Harmonise les exigences d'accessibilité de certains produits et services au sein de l'Union européenne, y compris dans le secteur privé.
- S'applique notamment :
    - aux services de commerce électronique,
    - aux services bancaires aux consommateurs,
    - aux services de communications électroniques, aux livres numériques et à certains services de transport de voyageurs.
- S'applique depuis le **28 juin 2025**.

La **directive sur l'accessibilité du web** (directive (UE) 2016/2102) couvre les sites web et applications mobiles des organismes du secteur public.

Les deux directives s'appuient sur la norme européenne harmonisée **EN 301 549**, dont les exigences pour le web reprennent les critères de succès des **niveaux A et AA des WCAG**.

#### Cadre suisse

**LHand et eCH-0059 (Suisse)** :

- La loi fédérale sur l'élimination des inégalités frappant les personnes handicapées (**LHand**, RS 151.3, en vigueur depuis le 1er janvier 2004) prévoit à l'art. 14, al. 2, que dans la mesure où les autorités offrent leurs prestations sur Internet, l'accès à ces prestations ne doit pas être rendu difficile aux personnes handicapées de la vue. Son ordonnance (**OHand**, RS 151.31) étend cette exigence aux informations et prestations destinées aux personnes handicapées de la parole, de l'ouïe, de la vue ou motrices.
- Depuis 2004, les unités administratives de la **Confédération** sont tenues de rendre leurs contenus Internet et Intranet accessibles.
- Les exigences techniques sont fixées par la **norme d'accessibilité eCH-0059 V3.0**, basée sur les **WCAG 2.1** et couvrant les sites web et les applications mobiles. C'est une directive informatique contraignante pour l'administration fédérale, et les déclarations d'accessibilité fédérales indiquent qu'elle exige le **niveau AA des WCAG 2.1**.
- Pour les cantons et les communes, les obligations dépendent du droit cantonal ; beaucoup s'alignent sur eCH-0059.

#### Risques en cas de non-conformité

Selon le pays et le cadre applicable :

- Sanctions administratives
- Sanctions financières (par exemple celles fixées par les États membres de l'UE pour l'EAA)
- Contentieux juridiques
- Atteinte à l'image de marque
- Exclusion des marchés publics

#### Impact projet (Produit / QA / Gouvernance)

La conformité WCAG ne relève pas uniquement du développement :

- **Produit** : intégration des critères dès la phase de conception.
- **UX/UI** : respect des contrastes, du focus, de la navigation.
- **Développement** : implémentation technique accessible.
- **QA** : tests systématiques manuels + automatisés.
- **Juridique / conformité** : publication et mise à jour de la déclaration.

#### Points clés à retenir

- Les WCAG sont un standard technique ; les lois et normes nationales les rendent obligatoires.
- La déclaration d'accessibilité est une exigence réglementaire formelle pour le secteur public dans l'UE.
- Le niveau AA est aujourd'hui la référence juridique dominante en Europe et en Suisse.
- L'accessibilité est une responsabilité organisationnelle transverse.

---

## Conformité théorique vs accessibilité réelle

### Conformité WCAG : approche normative

La conformité WCAG est :

- Basée sur des **critères de succès mesurables**
- Vérifiable par audit
- Structurée par niveaux (A, AA, AAA)
- Documentable par une déclaration de conformité et une déclaration d'accessibilité

Elle répond à la question :

> « Le site respecte-t-il formellement les critères définis par les WCAG ? »

Une application peut être conforme au niveau AA selon les **WCAG 2.2** tout en présentant des difficultés d'usage non couvertes explicitement par les critères.

### Accessibilité réelle : approche expérientielle

L'accessibilité réelle concerne :

- L'expérience effective d'un utilisateur en situation de handicap
- L'ergonomie globale
- La fluidité des parcours
- La charge cognitive
- La robustesse en situation réelle (lecteur d'écran, zoom, navigation clavier, etc.)

Elle répond à la question :

> « Un utilisateur peut-il réellement accomplir sa tâche sans obstacle significatif ? »

### Limites de la conformité formelle

Même avec une conformité AA :

- Une navigation peut être techniquement correcte mais inefficace.
- Un formulaire peut être conforme mais cognitivement complexe.
- Une structure ARIA peut être valide mais mal interprétée par certains lecteurs d'écran.
- Des micro-interactions peuvent ralentir fortement l'usage du clavier.

Les WCAG définissent un **socle minimal**, pas une garantie d'excellence UX.

### Exemples concrets d'écart

| Conforme aux critères | Mais en pratique |
|---|---|
| Tous les champs ont une étiquette | Le formulaire comporte 25 champs non groupés |
| Le contraste respecte 4,5:1 | L'interface est visuellement surchargée |
| La navigation clavier fonctionne | L'ordre de tabulation est long et inefficace |
| Les erreurs sont annoncées | Les messages sont trop techniques |

### Bonnes pratiques pour réduire l'écart

#### 1. Tests utilisateurs réels

Inclure :

- des utilisateurs de lecteurs d'écran,
- une navigation 100 % clavier,
- des utilisateurs avec troubles cognitifs.

#### 2. Audit hybride

- Tests automatisés (axe, Lighthouse)
- Audit manuel expert
- Tests en conditions réelles

#### 3. Intégration continue

- Accessibilité dès la conception (Design System accessible)
- Revue QA systématique
- Non-régression dans les releases

### Points clés à retenir

- La conformité WCAG est nécessaire mais non suffisante.
- L'accessibilité réelle dépasse la simple validation des critères.
- Une stratégie mature combine conformité normative et validation expérientielle.
- L'accessibilité doit être intégrée comme une exigence produit, pas seulement comme une contrainte légale.

---

## Historique des versions du WCAG

Les **WCAG** ont évolué au fil des années pour mieux répondre aux besoins des utilisateurs et aux évolutions technologiques du web :

- **WCAG 2.0 (11 décembre 2008)** : pose les bases de l'accessibilité numérique, en définissant les quatre principes fondamentaux (Perceptible, Utilisable, Compréhensible, Robuste) et les critères de succès associés.
- **WCAG 2.1 (5 juin 2018)** : complète la version 2.0 avec **1 nouvelle règle (2.5 Modalités d'entrée) et 17 nouveaux critères de succès**, notamment pour les **dispositifs mobiles**, la basse vision et les handicaps cognitifs.
- **WCAG 2.2 (5 octobre 2023, mise à jour le 12 décembre 2024)** : dernière version en date, qui ajoute **9 nouveaux critères de succès** et retire le critère **4.1.1 Analyse syntaxique**. Les nouveaux critères aident surtout les personnes avec des **handicaps cognitifs**, les personnes avec des **troubles moteurs**, celles qui ne peuvent pas utiliser de souris, et les personnes **malvoyantes**. Les WCAG 2.2 sont rétrocompatibles : un contenu conforme aux 2.2 est aussi conforme aux 2.1 et 2.0.
- **WCAG 3** : un premier brouillon, pas encore une norme. Le W3C recommande de viser les WCAG 2.2 en attendant.

---

## Sources

- W3C — [Web Content Accessibility Guidelines (WCAG) 2.2](https://www.w3.org/TR/WCAG22/) (normatif : principes, règles, critères de succès, exigences de conformité de la section 5.2)
- W3C — [Règles pour l'accessibilité des contenus Web (WCAG) 2.2, traduction française autorisée](https://www.w3.org/Translations/WCAG22-fr-20260922/) (titres français des principes, des règles et des critères 1.1.1 à 2.2.1)
- Koena / Intopia — [Carte des WCAG 2.2 en français](https://intopia.digital/wp-content/uploads/2024/05/French-WCAG-2.2-Map-by-Intopia.pdf) (titres français des critères 2.2.2 à 4.1.3)
- W3C — [Understanding Conformance (WCAG 2.2)](https://www.w3.org/WAI/WCAG22/Understanding/conformance) (informatif)
- W3C WAI — [WCAG 2 Overview](https://www.w3.org/WAI/standards-guidelines/wcag/) et [What's New in WCAG 2.2](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-22/) (informatif)
- Commission européenne — [Web Accessibility (directive (UE) 2016/2102)](https://digital-strategy.ec.europa.eu/en/policies/web-accessibility) (officiel)
- EUR-Lex — [Directive (UE) 2019/882 — European Accessibility Act](https://eur-lex.europa.eu/eli/dir/2019/882/oj) (officiel)
- DINUM — [Accessibilité numérique — RGAA](https://accessibilite.numerique.gouv.fr/) (officiel)
- Fedlex — [LHand, RS 151.3](https://www.fedlex.admin.ch/eli/cc/2003/667/fr) (officiel)
- BFEH — [Livingdocs : liste de contrôle pour contenus accessibles (LHand, OHand, eCH-0059)](https://www.ebgb.admin.ch/dam/fr/sd-web/G5Au8IXxycUv/Livingdocs%20%20liste%20de%20contr%C3%B4le%20pour%20contenus%20accessibles%20v2.1.pdf) (officiel)
- eCH — [eCH-0059 Accessibility Standard V3.0](https://www.ech.ch/de/ech/ech-0059/3.0) (officiel) ; Département fédéral des affaires étrangères — [Accessibility statement](https://www.eda.admin.ch/en/accessibility-statement) (officiel)
