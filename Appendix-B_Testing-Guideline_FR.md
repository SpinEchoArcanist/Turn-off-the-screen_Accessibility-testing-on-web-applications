# Annexe B — Guide de test de l'accessibilité

## Introduction

Les WCAG, bien que complètes, peuvent être complexes à interpréter pour des équipes non spécialistes. Ce guide simplifie l'interprétation des critères WCAG et aide les équipes à valider concrètement l'accessibilité des interfaces web pour les **utilisateurs aveugles utilisant un lecteur d'écran, les utilisateurs malvoyants, les utilisateurs daltoniens, les utilisateurs ayant des limitations motrices ou cognitives, et les utilisateurs sur mobile ou avec zoom**. Il se concentre sur les critères essentiels des WCAG 2.2 qui affectent directement l'expérience des personnes utilisant un lecteur d'écran et d'autres technologies d'assistance, ainsi que sur les critères de perception visuelle, de zoom/responsive, de contraste, d'interaction tactile, de lisibilité et de cohérence de l'interface que les tests au lecteur d'écran ne peuvent pas valider à eux seuls.

Plutôt qu'une reformulation exhaustive du standard WCAG, ce document adopte une **approche pragmatique** : il fournit une checklist structurée pour tester concrètement la navigabilité au clavier, la structure sémantique, les formulaires, les composants dynamiques, les parcours métier critiques, les contraintes de temps, le comportement en zoom et en reflow, l'espacement du texte, le contraste des couleurs, le comportement responsive et l'orientation, les interactions tactiles et au pointeur, la taille des cibles et la cohérence de l'interface. Chaque élément renvoie au critère WCAG correspondant et à son niveau, afin que les équipes puissent revenir à la source officielle si nécessaire.

**Niveau de conformité visé :** WCAG 2.2 niveau AA.

**Note :** Ce guide ne remplace pas le standard WCAG officiel — il en est une mise en œuvre ciblée et pratique. Ces tests ne remplacent pas non plus un audit d'accessibilité complet (voir la section 4.6 du support de cours). La liste complète des critères de succès WCAG 2.2 et de leurs niveaux figure dans l'annexe A.

---

## Checklist par thème

Cette checklist est conçue pour guider la validation de l'accessibilité étape par étape, en décomposant les exigences des WCAG 2.2 par grande fonctionnalité de l'application (navigation, formulaires, composants interactifs, présentation visuelle, comportement responsive, etc.).

Chaque section vise un objectif clair (par ex. *« Assurer une navigation fluide et logique »*) et liste les vérifications à effectuer, chacune renvoyant directement au critère WCAG correspondant. Les vérifications marquées **bonne pratique** ou **APG** (ARIA Authoring Practices Guide) sont des conventions recommandées, et non des exigences WCAG.

Pour chaque domaine fonctionnel, vous trouverez :

- Une liste d'actions vérifiables, formulées simplement et directement (par ex. *« Le focus clavier est visible en permanence »*).
- Les références WCAG et leurs niveaux, pour revenir rapidement aux exigences officielles.
- Des critères d'acceptation en fin de section, qui résument les attentes minimales pour valider la conformité (par ex. *« 100 % des zones sont accessibles au clavier »*).

**Objectif :** Rendre l'audit rapide et reproductible, en donnant aux équipes un cadre structuré pour tester chaque aspect de l'application sans exiger une expertise WCAG approfondie.

### 1. Navigation générale (y compris la visibilité du focus)

**Objectif :** Assurer une navigation fluide et logique dans toute l'application, avec un indicateur de focus toujours clairement visible — y compris sur les composants personnalisés.

- La navigation au clavier (Tab, Maj+Tab, flèches) fonctionne correctement **(WCAG 2.1.1, 2.1.2 - A)**
- L'ordre de tabulation suit une séquence logique qui préserve le sens et l'utilisation (en général de haut en bas, de gauche à droite) **(WCAG 2.4.3 - A)**
- Les zones de navigation principales sont identifiables (en-tête, navigation, contenu principal, pied de page) **(WCAG 1.3.1 - A)**
- Les blocs de contenu répétés sur plusieurs pages peuvent être contournés : un lien « Aller au contenu principal », ou des repères et des titres **(WCAG 2.4.1 - A)**
- Plusieurs moyens permettent de trouver une page dans un ensemble de pages (par ex. recherche, plan du site ou menu de navigation), sauf pour les pages qui sont une étape ou le résultat d'un processus **(WCAG 2.4.5 - AA)**
- Il n'existe aucun piège au clavier (il est possible de sortir de chaque zone) **(WCAG 2.1.2 - A)**
- Les raccourcis clavier composés d'une seule touche caractère (lettre, chiffre ou ponctuation) peuvent être désactivés ou reconfigurés, ou ne sont actifs que lorsque le composant a le focus **(WCAG 2.1.4 - A)**
- La navigation ne dépend pas uniquement de la souris **(WCAG 2.1.1 - A)**
- Un indicateur de focus visible est présent sur chaque élément focalisable, y compris les composants développés sur mesure **(WCAG 2.4.7 - AA)**
- L'indicateur de focus n'est jamais supprimé par le CSS (par ex. `outline: none` sans remplacement visible) **(WCAG 2.4.7 - AA)**
- L'élément qui a le focus n'est jamais entièrement masqué par un autre contenu, comme un en-tête fixe, un bandeau de cookies ou un widget de chat **(WCAG 2.4.11 - AA)**
- L'indicateur de focus a un contraste suffisant par rapport à l'arrière-plan adjacent pour être clairement perceptible **(WCAG 1.4.11 - AA)** — voir le thème 13 (Contrastes visuels) pour l'exigence chiffrée

**Critères d'acceptation :**

- ✅ 100 % des zones sont accessibles au clavier
- ✅ L'ordre de tabulation ne présente aucune incohérence
- ✅ Le mécanisme de contournement (lien d'évitement, ou repères et titres) fonctionne sur chaque page
- ✅ 100 % des éléments focalisables affichent un indicateur de focus visible
- ✅ L'indicateur de focus a un contraste suffisant
- ✅ Aucun composant ne supprime le focus ni ne masque entièrement l'élément qui a le focus

---

### 2. Éléments interactifs (boutons, liens, contrôles)

**Objectif :** S'assurer que chaque élément interactif est accessible et compréhensible.

- Tous les boutons sont activables au clavier (les boutons natifs réagissent à Entrée et à Espace) **(WCAG 2.1.1 - A)**
- Les boutons ont des libellés explicites et descriptifs **(WCAG 4.1.2 - A, 2.4.6 - AA)**
- Lorsqu'un composant a un libellé texte visible, son nom accessible inclut ce texte visible **(WCAG 2.5.3 - A)**
- La fonction de chaque lien peut être déterminée à partir de son texte ou de son contexte **(WCAG 2.4.4 - A)**, idéalement à partir du seul texte du lien **(WCAG 2.4.9 - AAA)**
- Le texte des liens est explicite (éviter « cliquez ici », « en savoir plus » sans contexte) **(WCAG 2.4.4 - A)**
- Les éléments cliquables ont un rôle ARIA approprié uniquement lorsqu'il n'est pas déjà implicite (par ex. `<a>`, `<button>`) **(WCAG 4.1.2 - A)**
- Les menus déroulants sont utilisables au clavier **(WCAG 2.1.1 - A)** ; les touches attendues (flèches, Entrée, Échap) suivent les modèles de menu de l'APG
- Les éléments composés uniquement d'une icône ont des alternatives textuelles (`aria-label` ou texte masqué visuellement) **(WCAG 1.1.1, 4.1.2 - A)**
- Les boutons bascules indiquent clairement leur état (activé/désactivé) **(WCAG 4.1.2 - A)**
- Les éléments désactivés sont identifiables et annoncés comme tels **(WCAG 4.1.2 - A)**

**Critères d'acceptation :**

- ✅ Tous les boutons et liens critiques sont testés et fonctionnels
- ✅ Aucun élément interactif n'est invisible pour le lecteur d'écran
- ✅ Les états (activé, désactivé, sélectionné) sont correctement annoncés

---

### 3. Formulaires et champs de saisie

**Objectif :** Permettre une saisie d'informations claire et sans erreur.

- Tous les champs de formulaire ont une étiquette ou des instructions visibles **(WCAG 3.3.2 - A)**, associées au champ par le code (`<label for='field_id'>`, ou `aria-labelledby`) **(WCAG 1.3.1, 4.1.2 - A)**. Un `aria-label` donne au champ un nom accessible **(WCAG 4.1.2 - A)**, mais il n'est pas visible : à lui seul, il ne satisfait pas le critère 3.3.2
- Les instructions de saisie sont visibles, et annoncées avant ou pendant la saisie **(WCAG 3.3.2 - A)**
- Les champs obligatoires sont clairement identifiés, visuellement et dans le code (`required` ou `aria-required`) **(WCAG 3.3.2, 1.3.1 - A)**
- Les formats attendus sont communiqués (par ex. JJ.MM.AAAA, +41 XX XXX XX XX) **(WCAG 3.3.2 - A)**
- Les listes déroulantes (`<select>`) sont accessibles et leurs options lisibles **(WCAG 4.1.2 - A)**
- Les cases à cocher et les boutons radio ont des étiquettes associées **(WCAG 3.3.2, 1.3.1 - A)**
- Les groupes de champs sont regroupés logiquement (`<fieldset>` avec `<legend>`) **(WCAG 1.3.1 - A)**
- Les champs qui recueillent des informations sur l'utilisateur (nom, e-mail, adresse, téléphone…) exposent leur finalité avec l'attribut `autocomplete` **(WCAG 1.3.5 - AA)**
- Une information déjà saisie dans le même processus est pré-remplie ou proposée en sélection, au lieu d'être redemandée — sauf si la ressaisie est essentielle, exigée pour la sécurité, ou si l'information n'est plus valide **(WCAG 3.3.7 - A)**
- Les zones de recherche sont identifiables (élément `<search>` ou repère `role="search"`) **(WCAG 1.3.1 - A)**
- Les erreurs détectées par la validation côté client sont identifiées et décrites sous forme de texte **(WCAG 3.3.1 - A)**

**Critères d'acceptation :**

- ✅ Tous les champs sont identifiables et remplissables au clavier
- ✅ Les instructions et contraintes sont visibles et annoncées avant la saisie
- ✅ Aucun champ obligatoire n'est dépourvu d'indication

---

### 4. Messages et retours utilisateur

**Objectif :** Informer clairement l'utilisateur des actions réalisées et des éventuelles erreurs.

- Les erreurs de saisie détectées automatiquement identifient le champ en erreur et décrivent l'erreur sous forme de texte, et pas seulement par une couleur ou une icône **(WCAG 3.3.1 - A)**
- Les messages d'erreur qui apparaissent sans déplacer le focus sont annoncés via des régions live (`role="alert"`) **(WCAG 4.1.3 - AA)**. Lorsque le focus est déplacé sur le message d'erreur ou sur un récapitulatif des erreurs, il s'agit d'un changement de contexte, et non d'un message d'état
- Les messages de succès qui apparaissent sans déplacer le focus sont annoncés automatiquement **(WCAG 4.1.3 - AA)**
- La validation en temps réel est perceptible sans être intrusive **(WCAG 3.3.1 - A)**
- Les alertes et notifications qui ne prennent pas le focus sont clairement annoncées **(WCAG 4.1.3 - AA)**
- Aucun changement de contexte (nouvelle fenêtre, changement de page, saut du focus) ne se produit lorsqu'un élément reçoit le focus, et aucun ne se produit lorsque la valeur d'un champ change, sauf si l'utilisateur en a été averti au préalable **(WCAG 3.2.1, 3.2.2 - A)**
- Les messages d'erreur suggèrent des corrections lorsqu'elles sont connues, sauf si cela compromet la sécurité ou la finalité du contenu **(WCAG 3.3.3 - AA)**
- Les messages de chargement/d'attente sont annoncés **(WCAG 4.1.3 - AA)**

**Critères d'acceptation :**

- ✅ Tous les messages d'erreur sont testés et accessibles
- ✅ Les notifications importantes ne passent pas inaperçues
- ✅ Les messages temporaires ne disparaissent pas trop vite, sauf si la même information reste disponible ailleurs **(WCAG 2.2.1 - A)**

---

### 5. Structure et hiérarchie du contenu (y compris titres de page et cohérence)

**Objectif :** Organiser l'information de manière logique et navigable, et assurer la cohérence structurelle et de navigation sur l'ensemble du site.

- La structure des titres est hiérarchique et reflète la structure du contenu (H1 → H2 → H3) **(WCAG 1.3.1 - A)**
- Chaque page a un titre H1 unique et descriptif (⚠️ bonne pratique, pas un critère WCAG : le critère 2.4.2 porte sur l'élément `<title>` de la page — voir le point dédié ci-dessous)
- Les titres et les étiquettes décrivent le sujet ou la finalité de leur contenu **(WCAG 2.4.6 - AA)**
- Les listes sont balisées sémantiquement (`<ul>`, `<ol>`, `<li>`) **(WCAG 1.3.1 - A)**
- Les tableaux de données ont des en-têtes appropriés (`<th>`, `scope`) **(WCAG 1.3.1 - A)**
- Les tableaux complexes utilisent `id` et `headers` pour l'association **(WCAG 1.3.1 - A)**
- Les régions de repère sont utilisées correctement (`<main>`, `<header>`, `<footer>`, `<nav>`, `<aside>`, etc.) **(WCAG 1.3.1 - A)**
- Le contenu suit un ordre de lecture logique **(WCAG 1.3.2 - A)**
- Les citations sont balisées avec `<blockquote>` **(WCAG 1.3.1 - A)**
- Les définitions utilisent `<dl>`, `<dt>`, `<dd>` **(WCAG 1.3.1 - A)**
- Chaque page a un élément `<title>` descriptif **(WCAG 2.4.2 - A)**
- Les menus de navigation répétés sur plusieurs pages apparaissent dans le même ordre relatif, sauf si l'utilisateur le modifie **(WCAG 3.2.3 - AA)**
- Les composants qui ont la même fonctionnalité sont identifiés de manière cohérente (même libellé, même icône et même nom accessible) partout où ils apparaissent **(WCAG 3.2.4 - AA)**
- Les mécanismes d'aide répétés sur plusieurs pages (coordonnées, formulaire de contact ou chat, aide en libre-service comme une FAQ) apparaissent dans le même ordre par rapport au reste du contenu de la page **(WCAG 3.2.6 - A)**

**Critères d'acceptation :**

- ✅ La navigation par titres permet de comprendre la structure de la page
- ✅ Aucun niveau de titre n'est sauté (⚠️ il s'agit d'une bonne pratique, pas d'un critère WCAG en soi)
- ✅ Les tableaux de données sont compréhensibles
- ✅ 100 % des pages ont un `<title>` descriptif
- ✅ La navigation et l'aide sont cohérentes sur l'ensemble du site
- ✅ Aucun libellé ne se contredit pour une même action

---

### 6. Contenus multimédias

**Objectif :** Rendre accessibles les contenus visuels et audio.

- Toutes les images informatives ont des alternatives textuelles pertinentes (`alt`) **(WCAG 1.1.1 - A)**
- Les images décoratives ont un attribut `alt=""` vide ou `role="presentation"` **(WCAG 1.1.1 - A)**
- Les images complexes (graphiques, schémas) ont des descriptions détaillées **(WCAG 1.1.1 - A)**
- Le texte est du vrai texte, et non une image de texte, sauf pour les logos et lorsqu'une présentation particulière est essentielle **(WCAG 1.4.5 - AA)**
- Les vidéos pré-enregistrées ont des sous-titres synchronisés **(WCAG 1.2.2 - A)**
- Les vidéos en direct ont des sous-titres synchronisés **(WCAG 1.2.4 - AA)**
- Les vidéos pré-enregistrées ont une audio-description ou une transcription textuelle **(WCAG 1.2.3 - A)**
- Les vidéos pré-enregistrées ont une audio-description des informations visuelles importantes **(WCAG 1.2.5 - AA)**
- Les contenus audio seuls pré-enregistrés ont une transcription ; les contenus vidéo seuls pré-enregistrés ont une alternative textuelle ou une piste audio **(WCAG 1.2.1 - A)**
- Un son qui démarre automatiquement et dure plus de 3 secondes peut être mis en pause ou arrêté, ou son volume peut être réglé indépendamment du volume du système **(WCAG 1.4.2 - A)**
- Un contenu en mouvement, clignotant ou défilant qui démarre automatiquement, dure plus de 5 secondes et est présenté en parallèle d'autres contenus peut être mis en pause, arrêté ou masqué **(WCAG 2.2.2 - A)**
- Aucun contenu ne flashe plus de trois fois par seconde, sauf si les flashs restent sous les seuils de flash général et de flash rouge **(WCAG 2.3.1 - A)**
- Les graphiques interactifs ont des alternatives accessibles **(WCAG 1.1.1 - A)**
- Les infographies ont des descriptions textuelles complètes **(WCAG 1.1.1 - A)**
- Les CAPTCHA décrivent leur finalité sous forme de texte et proposent une forme alternative faisant appel à un autre sens (par ex. une version visuelle et une version audio) **(WCAG 1.1.1 - A)**

**Critères d'acceptation :**

- ✅ Aucune information ne dépend uniquement d'un contenu visuel
- ✅ Toutes les vidéos critiques ont des sous-titres
- ✅ Les alternatives textuelles sont pertinentes et suffisantes
- ✅ Aucun son ni aucune animation automatique ne tourne sans moyen de l'arrêter, et rien ne flashe plus de trois fois par seconde

---

### 7. Contenu dynamique et interactions avancées

**Objectif :** Gérer de manière accessible les mises à jour dynamiques et les interactions complexes.

- Les messages d'état (résultats, confirmations, progression) sont annoncés sans recevoir le focus (`aria-live`, `role="status"`) **(WCAG 4.1.3 - AA)**
- Les modales/popups sont identifiées (`role="dialog"` ou `role="alertdialog"`) **(WCAG 4.1.2 - A)**
- Le focus est automatiquement déplacé dans les modales à leur ouverture **(WCAG 2.4.3 - A)**
- Le focus revient sur l'élément déclencheur à la fermeture des modales **(WCAG 2.4.3 - A)**
- Les modales peuvent être fermées au clavier, ce qui rend le contrôle du clavier à la page **(WCAG 2.1.1, 2.1.2 - A)** ; la fermeture avec Échap est la convention de l'APG
- Les accordéons indiquent leur état (ouvert/fermé) via `aria-expanded` **(WCAG 4.1.2 - A)**
- Les onglets sont utilisables au clavier **(WCAG 2.1.1 - A)** ; les flèches gauche/droite sont la convention de l'APG
- Les onglets indiquent l'onglet actif via `aria-selected` **(WCAG 4.1.2 - A)**
- Les carrousels qui défilent automatiquement peuvent être mis en pause **(WCAG 2.2.2 - A)**
- Les carrousels sont contrôlables au clavier **(WCAG 2.1.1 - A)**
- Les infobulles et autres contenus affichés au survol ou au focus peuvent être affichés au clavier **(WCAG 2.1.1 - A)**, peuvent être masqués sans déplacer le pointeur ni le focus (par ex. Échap), restent visibles lorsque le pointeur passe dessus, et restent affichés jusqu'à leur fermeture ou tant qu'ils sont pertinents **(WCAG 1.4.13 - AA)**. Les infobulles natives du navigateur (attribut `title`) sont exemptées du critère 1.4.13
- Lorsqu'un contenu est chargé de manière asynchrone (AJAX), le message d'état qui en résulte (par ex. « 20 résultats chargés ») est annoncé **(WCAG 4.1.3 - AA)**

**Critères d'acceptation :**

- ✅ Toutes les modales sont identifiées et le focus est correctement géré
- ✅ Les mises à jour critiques sont annoncées automatiquement
- ✅ Aucun contenu dynamique n'est invisible pour le lecteur d'écran

---

### 8. Lisibilité et compréhension

**Objectif :** S'assurer que le contenu est clair et compréhensible, indépendamment de présupposés visuels ou linguistiques.

- Toute information visuelle a un équivalent textuel **(WCAG 1.1.1 - A)**
- La langue principale de la page est correctement définie dans le code **(WCAG 3.1.1 - A)**
- Le langage utilisé est clair et adapté au public cible (en lien avec le critère **WCAG 3.1.5 - AAA**, qui vise un niveau de lecture ne dépassant pas le premier cycle du secondaire)
- Les abréviations et acronymes peuvent être développés (par ex. forme complète à la première occurrence, glossaire, `<abbr title="">`) **(WCAG 3.1.4 - AAA)**
- Les instructions ne reposent pas uniquement sur des caractéristiques sensorielles (forme, couleur, taille, emplacement visuel, orientation ou son) **(WCAG 1.3.3 - A, 1.4.1 - A)**
- Les changements de langue dans le contenu sont indiqués dans le code (attribut `lang`), sauf pour les noms propres, les termes techniques et les mots entrés dans la langue environnante **(WCAG 3.1.2 - AA)**
- Les mots employés dans un sens inhabituel ou restreint (jargon, expressions idiomatiques, termes techniques) sont définis ou expliqués **(WCAG 3.1.3 - AAA)**
- Les contenus complexes sont accompagnés d'explications (en lien avec le critère **WCAG 3.1.5 - AAA**)

> **Note :** Les critères propres au contraste des couleurs (1.4.3, 1.4.11), au zoom et au reflow (1.4.10), à la taille de texte ajustable (1.4.4) et à l'espacement du texte (1.4.12) ne sont pas repris ici — voir les thèmes dédiés **Zoom et redimensionnement**, **Espacement du texte** et **Contrastes visuels** ci-dessous pour leurs étapes de vérification et critères d'acceptation complets.

**Critères d'acceptation :**

- ✅ Aucune instruction ne dépend uniquement de la couleur ou de la position
- ✅ Les abréviations critiques sont expliquées
- ✅ Le contenu est compréhensible sans s'appuyer sur la perception visuelle
- ✅ La langue de la page et les éventuels changements de langue dans le contenu sont correctement déclarés dans le code

---

### 9. Fonctionnalités critiques

**Objectif :** Valider que les parcours utilisateur essentiels sont entièrement accessibles.

- Le processus de connexion/authentification est accessible
- Aucune étape de la connexion n'exige de test de fonction cognitive (mémoriser ou recopier un mot de passe ou un code, résoudre une énigme), sauf si une méthode alternative ou un mécanisme d'assistance est disponible — par exemple, les gestionnaires de mots de passe et le copier-coller ne sont pas bloqués. Reconnaître des objets et identifier un contenu fourni par l'utilisateur sont admis à ce niveau **(WCAG 3.3.8 - AA)**
- L'inscription / la création de compte est réalisable
- Les transactions importantes peuvent être menées à bien (achat, paiement, soumission)
- Les soumissions qui créent des engagements juridiques ou financiers, modifient ou suppriment des données de l'utilisateur, ou envoient des réponses à un test sont réversibles, vérifiées (avec la possibilité de corriger les erreurs de saisie), ou peuvent être relues et confirmées avant leur finalisation **(WCAG 3.3.4 - AA)**
- La recherche est utilisable et les résultats sont accessibles
- Les filtres et le tri sont accessibles au clavier
- La pagination est navigable au clavier
- Les actions de téléchargement de fichiers sont réalisables
- Les actions de dépôt (upload) de fichiers sont accessibles
- Les tableaux de bord et les statistiques sont compréhensibles
- La déconnexion est accessible

En dehors des deux points référencés ci-dessus, cette section ne constitue pas en soi un critère WCAG. Elle vérifie la conformité opérationnelle des critères A et AA sur les parcours métier — principalement les critères d'accessibilité au clavier 2.1.1 et 2.1.2, et l'exigence de conformité des processus complets (WCAG 2.2, section 5.2.3 : lorsqu'une page fait partie d'un processus, toutes les pages du processus doivent être conformes).

**Critères d'acceptation :**

- ✅ Tous les parcours critiques identifiés sont testés de bout en bout
- ✅ Aucun parcours ne présente de blocage majeur
- ✅ Les fonctionnalités métier principales sont validées

---

### 10. Gestion du temps et contraintes temporelles

**Objectif :** Éviter que des limites de temps ne bloquent la réalisation des tâches.

- Chaque limite de temps imposée par le contenu peut être désactivée, ajustée (jusqu'à au moins dix fois la durée par défaut) ou prolongée après un avertissement — sauf pour les événements en temps réel, les limites essentielles et les limites de plus de 20 heures **(WCAG 2.2.1 - A)**
- Avant l'expiration d'une session, l'utilisateur est averti et peut la prolonger par une action simple, avec au moins 20 secondes pour réagir **(WCAG 2.2.1 - A)**
- Les contenus en mouvement ou animés peuvent être mis en pause, arrêtés ou masqués **(WCAG 2.2.2 - A)**
- Les contenus mis à jour automatiquement en parallèle d'autres contenus (fil d'actualités, résultats en direct) peuvent être mis en pause, arrêtés, masqués, ou leur fréquence de mise à jour peut être réglée **(WCAG 2.2.2 - A)**
- Les actualisations automatiques de la page et les mises à jour de contenu peuvent être reportées ou désactivées par l'utilisateur **(WCAG 2.2.4 - AAA)**
- Les interruptions (par ex. pop-ups) peuvent être reportées ou supprimées, sauf en cas d'urgence **(WCAG 2.2.4 - AAA)**
- La gestion du temps n'est pas un élément essentiel de l'activité : aucune limite de temps n'est imposée, sauf pour les médias synchronisés non interactifs et les événements en temps réel **(WCAG 2.2.3 - AAA)**

**Critères d'acceptation :**

- ✅ Aucune limite de temps ne bloque la réalisation d'une tâche
- ✅ Les avertissements d'expiration sont accessibles
- ✅ Les animations problématiques peuvent être contrôlées

---

### 11. Zoom et redimensionnement

**Objectif :** Assurer l'utilisabilité avec des niveaux de zoom élevés et de petites largeurs de fenêtre.

- Le texte peut être agrandi à 200 % (zoom du navigateur) sans perte de contenu ni de fonctionnalité **(WCAG 1.4.4 - AA)**
- À 400 % de zoom dans une fenêtre de 1280 px CSS de large (équivalent à une fenêtre de 320 px CSS), le contenu se réorganise sans perte d'information ni de fonctionnalité **(WCAG 1.4.10 - AA)**
- Aucun défilement horizontal n'est nécessaire pour lire un contenu qui défile verticalement **(WCAG 1.4.10 - AA)**
- Aucun texte n'est tronqué ni ne se chevauche **(WCAG 1.4.4, 1.4.10 - AA)**
- Les contenus qui nécessitent une présentation en deux dimensions (tableaux de données, cartes, schémas) sont exemptés du critère 1.4.10 et peuvent conserver un défilement horizontal, mais le contenu qui les entoure (titres, champs de recherche, pagination) doit tout de même se réorganiser **(WCAG 1.4.10 - AA)**. Placer un tableau large dans son propre conteneur défilant est une solution courante

**Critères d'acceptation :**

- ✅ 100 % du contenu et des fonctionnalités restent accessibles à 200 %
- ✅ À 400 %, aucune lecture ne nécessite de défilement horizontal (sauf à l'intérieur des tableaux de données et des autres contenus en deux dimensions)
- ✅ Aucun composant critique ne devient inutilisable
- ✅ Aucun contenu n'est masqué ou coupé

---

### 12. Espacement du texte

**Objectif :** Assurer la robustesse face aux adaptations de lisibilité.

Application manuelle des valeurs suivantes (par exemple via les DevTools ou un bookmarklet d'espacement du texte) :

- Hauteur de ligne : 1,5 × la taille de police (`line-height: 1.5`)
- Espacement après les paragraphes : 2 × la taille de police (par ex. `p { margin-bottom: 2em }`)
- Espacement des lettres : 0,12 × la taille de police (`letter-spacing: 0.12em`)
- Espacement des mots : 0,16 × la taille de police (`word-spacing: 0.16em`)

Vérifications **(WCAG 1.4.12 - AA)** :

- Aucun chevauchement ne se produit
- Aucun contenu n'est perdu
- Les composants restent utilisables

**Critères d'acceptation :**

- ✅ L'application reste entièrement fonctionnelle
- ✅ Aucun texte ne se chevauche
- ✅ Aucun défilement horizontal supplémentaire n'est généré (bonne pratique)

---

### 13. Contrastes visuels

**Objectif :** Assurer la perceptibilité du contenu et des composants.

- Contraste du texte normal ≥ 4,5:1 **(WCAG 1.4.3 - AA)**
- Contraste du texte de grande taille (au moins 18 pt, ou 14 pt en gras — soit environ 24 px, ou 18,5 px en gras) ≥ 3:1 **(WCAG 1.4.3 - AA)**
- Le texte des composants désactivés, le texte purement décoratif et les logos n'ont pas d'exigence de contraste **(WCAG 1.4.3 - AA)**
- Les composants d'interface et les graphiques porteurs de sens (bordures qui identifient un champ, icônes informatives, boutons, éléments de graphiques) ont un contraste ≥ 3:1 par rapport aux couleurs adjacentes **(WCAG 1.4.11 - AA)**
- Les indicateurs de focus respectent le même ratio de contraste non textuel que les autres composants d'interface **(WCAG 1.4.11 - AA)** — voir le thème 1 pour l'exigence d'un focus visible en permanence
- Les états (erreur, actif, sélectionné) ne sont pas transmis uniquement par la couleur **(WCAG 1.4.1 - A)**, et l'indicateur visuel d'un état a un contraste ≥ 3:1 **(WCAG 1.4.11 - AA)**

**Critères d'acceptation :**

- ✅ 100 % du texte respecte le ratio de contraste requis
- ✅ 100 % des composants interactifs respectent le ratio de contraste requis
- ✅ Aucun état n'est transmis uniquement par la couleur
- ✅ Le focus est perceptible sans ambiguïté

---

### 14. Responsive design et orientation

**Objectif :** Assurer l'adaptabilité mobile.

- Fonctionne correctement en orientation portrait **(WCAG 1.3.4 - AA)**
- Fonctionne correctement en orientation paysage **(WCAG 1.3.4 - AA)**
- Aucun contenu ni aucune interaction n'est limité à une seule orientation, sauf si une orientation particulière est essentielle (par ex. une application de piano, un chèque bancaire) **(WCAG 1.3.4 - AA)**

**Critères d'acceptation :**

- ✅ Toutes les fonctionnalités critiques sont accessibles dans les deux orientations
- ✅ Aucun contenu essentiel n'est masqué

---

### 15. Interactions tactiles et au pointeur

**Objectif :** Assurer l'accessibilité pour les utilisateurs d'écrans tactiles et ceux ayant des limitations motrices.

- Les gestes multipoints ou basés sur un tracé (pincer, balayer, dessiner un tracé) ont une alternative à pointeur unique sans tracé, sauf si le geste est essentiel **(WCAG 2.5.1 - A)**
- Les actions ne sont pas déclenchées à l'événement « down » (appui du doigt, bouton de souris enfoncé), sauf si c'est essentiel **(WCAG 2.5.2 - A)**
- Une action lancée par erreur peut être interrompue avant sa fin (en éloignant le pointeur avant de relâcher) ou annulée ensuite **(WCAG 2.5.2 - A)**
- Les fonctions déclenchées par un mouvement de l'appareil ou de l'utilisateur (secouer, incliner) peuvent aussi être activées par des composants d'interface, et la réaction au mouvement peut être désactivée **(WCAG 2.5.4 - A)**
- Chaque action de glisser-déposer a une alternative à pointeur unique sans glisser (par ex. des boutons ou un menu) **(WCAG 2.5.7 - AA)**

**Critères d'acceptation :**

- ✅ 100 % des gestes complexes, des mouvements de glisser et des fonctions déclenchées par le mouvement ont une alternative
- ✅ Aucune action irréversible n'est déclenchée accidentellement
- ✅ Les actions critiques peuvent être confirmées (bonne pratique)

---

### 16. Taille des cibles

**Objectif :** Réduire les erreurs d'activation.

- Les cibles de pointeur mesurent au moins 24 × 24 px CSS, ou les cibles plus petites sont espacées de sorte qu'un cercle de 24 px CSS de diamètre centré sur chacune ne touche ni une autre cible ni le cercle d'une autre petite cible **(WCAG 2.5.8 - AA)**
- Exceptions au critère 2.5.8 : un contrôle équivalent de la même page respecte la taille, la cible est intégrée dans une phrase, sa taille est fixée par le navigateur et n'est pas modifiée, ou une présentation particulière est essentielle ou exigée par la loi **(WCAG 2.5.8 - AA)**
- Les cibles mesurent au moins 44 × 44 px CSS **(WCAG 2.5.5 - AAA)** — au-delà de l'exigence AA, recommandé au moins pour les actions critiques
- Les éléments proches ne provoquent pas d'erreurs d'interaction **(WCAG 2.5.8 - AA)**

**Critères d'acceptation :**

- ✅ 100 % des cibles respectent la taille minimale (24 × 24 px CSS, AA)
- ✅ Aucun clic accidentel observé pendant les tests

---

### 17. Nom, rôle, valeur — principe général pour les composants personnalisés

**Objectif :** Assurer la robustesse des composants personnalisés au-delà de ce qui est déjà détaillé ailleurs dans ce guide.

Pour les composants JS personnalisés / non natifs :

- Le composant expose un nom accessible correct
- Le rôle est correct
- La valeur/l'état est exposé(e)
- Les changements d'état sont détectables

**Vérifications (WCAG 4.1.2 - A) :**

- Les composants personnalisés exposent un nom accessible
- Les rôles sont appropriés
- Les états sont correctement exposés
- Les changements d'état sont détectables

**Critères d'acceptation :**

- ✅ 100 % des composants interactifs exposent Nom/Rôle/Valeur
- ✅ Aucun composant critique n'est dépourvu de nom accessible
- ✅ Les états dynamiques sont correctement mis à jour

> **Note :** De nombreux cas particuliers de ce principe sont déjà vérifiés individuellement ailleurs dans ce guide — par ex. l'état des boutons bascules et l'annonce de l'état désactivé (thème 2), les rôles des `<select>` (thème 3) et l'exposition de l'état des dialogues, accordéons et onglets (thème 7). Ce thème fournit l'approche de vérification générale pour tout composant personnalisé non couvert par ces vérifications spécifiques.

---

## Checklist par niveau de conformité WCAG

Cette section transforme les thèmes ci-dessus en trois checklists courtes et pratiques, une par niveau de conformité, à appliquer pendant les tests d'intégration et les tests système. Chaque ligne regroupe des critères de succès qui peuvent être testés ensemble, avec les mêmes outils et dans le même passage ; il ne s'agit pas de la liste complète des WCAG triée par niveau.

- **Critères fondamentaux (niveau A)** : les 31 critères de succès de niveau A des WCAG 2.2, regroupés en 20 vérifications. Un échec à ce niveau bloque généralement complètement certains utilisateurs.
- **Critères légaux (niveau AA)** : les 24 critères de succès de niveau AA, regroupés en 18 vérifications. Le niveau AA est le niveau exigé par les cadres juridiques.
- **Critères d'excellence (niveau AAA et bonnes pratiques)** : une sélection de critères AAA et de bonnes pratiques utiles dans les applications métier.

Pour chaque vérification, le tableau indique un libellé court, ce qu'il faut vérifier, les critères de succès WCAG et le niveau couverts, et la manière de le vérifier.

**Objectif :** préparer l'application à la revue d'expert (voir la section 4.6 du support de cours) en détectant et en corrigeant tôt les problèmes les plus fréquents. Ces checklists ne remplacent pas cette revue : réussir toutes les lignes ne prouve pas la conformité, car la revue d'expert évalue chaque critère de succès en détail, sur un échantillon représentatif de pages et sur des processus complets.

### Critères fondamentaux (niveau A — éliminer les blocages)

Ce tableau couvre les 31 critères de succès de niveau A des WCAG 2.2. Ces critères garantissent un accès de base à l'information et aux fonctionnalités, sans lequel certains utilisateurs en situation de handicap ne pourraient tout simplement pas utiliser le service.

| Critère | Description | WCAG | Comment vérifier |
| --- | --- | --- | --- |
| **Accès au clavier** | Chaque fonctionnalité et chaque parcours critique (connexion, formulaires, transactions, recherche, déconnexion) peut être réalisé au clavier seul, et le focus peut toujours quitter chaque composant | 2.1.1, 2.1.2 (A) | 1. Ne plus utiliser la souris ni le pavé tactile.<br>2. Réaliser chaque parcours critique (connexion, formulaire principal, transaction, recherche, déconnexion) uniquement avec Tab, Maj+Tab, Entrée, Espace, les flèches et Échap.<br>3. Dans chaque widget (menu, dialogue, sélecteur de date, lecteur intégré), essayer d'en sortir avec Tab, Maj+Tab ou Échap.<br>✅ **Réussi :** chaque parcours peut être réalisé, et le focus ne reste jamais bloqué. |
| **Ordre et gestion du focus** | Le focus se déplace dans un ordre qui préserve le sens ; il entre dans un dialogue à son ouverture et revient à un endroit logique (en général l'élément déclencheur) à sa fermeture | 2.4.3 (A) | 1. Depuis le haut de la page, appuyer plusieurs fois sur Tab et observer où va le focus.<br>2. Ouvrir chaque dialogue : le focus doit arriver à l'intérieur.<br>3. Le fermer : le focus doit revenir sur le bouton qui l'a ouvert, ou à un autre endroit logique.<br>4. Soumettre un formulaire avec une erreur et noter où arrive le focus.<br>✅ **Réussi :** le focus suit l'ordre logique de la page et ne saute jamais à un endroit inattendu (par exemple, retour en haut de la page). |
| **Raccourcis clavier utilisant des caractères** | Les raccourcis à une seule touche caractère (lettre, chiffre, ponctuation) peuvent être désactivés ou reconfigurés, ou ne sont actifs que lorsque leur composant a le focus | 2.1.4 (A) | 1. Désactiver le lecteur d'écran (en mode navigation, il utilise lui-même les lettres seules).<br>2. Cliquer sur une zone vide de la page, en dehors de tout champ de texte.<br>3. Appuyer sur des touches lettre, chiffre et ponctuation seules (par exemple s, k, 1, ?).<br>4. Si quelque chose se passe, chercher un réglage pour désactiver ou modifier le raccourci, ou vérifier qu'il ne fonctionne que lorsque son composant a le focus.<br>✅ **Réussi :** aucun raccourci à une seule touche ne se déclenche, sauf s'il peut être désactivé ou reconfiguré, ou s'il ne fonctionne que sur le composant qui a le focus. |
| **Titres de page et contournement des blocs** | Chaque page a un `<title>` descriptif ; les blocs répétés sur plusieurs pages peuvent être contournés par un lien d'évitement, des repères ou des titres | 2.4.2, 2.4.1 (A) | 1. Ouvrir plusieurs pages et lire le titre dans l'onglet du navigateur (ou écouter le lecteur d'écran au chargement de la page).<br>2. Recharger une page et appuyer une fois sur Tab : un lien « Aller au contenu principal » devrait apparaître ; appuyer sur Entrée.<br>3. S'il n'y a pas de lien d'évitement, ouvrir la liste des repères et la liste des titres du lecteur d'écran (voir les annexes C–E).<br>✅ **Réussi :** chaque titre décrit le sujet ou la finalité de la page (par exemple « Paiement – Étape 2 sur 3 – MonApp ») ; le lien d'évitement mène au contenu principal, ou les repères et les titres permettent de passer les blocs répétés. |
| **Structure sémantique** | Les titres, repères, listes, en-têtes de tableaux de données, groupes de champs (`<fieldset>`/`<legend>`), associations d'étiquettes et champs obligatoires sont transmis par le code, et pas seulement visuellement | 1.3.1 (A) | 1. Ouvrir la liste des titres du lecteur d'écran, puis sa liste des repères (voir les annexes C–E).<br>2. Dans chaque tableau de données, se déplacer cellule par cellule avec les commandes de tableau du lecteur d'écran.<br>3. Dans chaque formulaire, entrer dans les champs avec Tab et écouter.<br>4. Dans les DevTools (panneau Elements, volet Accessibility), vérifier que ce qui ressemble à un titre, une liste ou un tableau utilise l'élément HTML correspondant.<br>✅ **Réussi :** chaque titre et chaque région visuels apparaissent dans les listes ; les en-têtes de colonne et de ligne sont lus avec chaque cellule ; chaque champ est lu avec son étiquette, son groupe (légende) et « obligatoire » le cas échéant. |
| **Ordre de lecture cohérent** | L'ordre de lecture dans le code correspond au sens du contenu (par ex. le contexte avant les détails) | 1.3.2 (A) | 1. Avec le lecteur d'écran, lancer la lecture continue en haut de la page.<br>2. Suivre à l'écran et comparer l'ordre de lecture avec l'ordre visuel.<br>✅ **Réussi :** le contenu est lu dans un ordre qui a du sens : les étiquettes avant leurs champs, un statut avant ses détails, aucun texte d'une colonne lu au milieu d'une autre. |
| **Alternatives textuelles** | Les images informatives, les contrôles composés d'une seule icône, les graphiques et les CAPTCHA ont une alternative textuelle qui remplit la même fonction ; les images décoratives sont masquées aux technologies d'assistance | 1.1.1 (A) | 1. Avec le lecteur d'écran, passer d'image en image (liste ou navigation par graphiques) et écouter chacune.<br>2. Dans les DevTools, vérifier que chaque `<img>` a un attribut `alt` (`alt=""` pour les images décoratives), et que chaque bouton composé d'une seule icône a un nom dans le volet Accessibility.<br>3. Pour chaque graphique ou schéma, chercher la même information sous forme de texte ou de tableau.<br>✅ **Réussi :** chaque image ou icône informative est annoncée avec un texte qui donne la même information ou la même fonction ; les images décoratives ne sont pas annoncées. |
| **Audio et vidéo pré-enregistrés** | Les contenus audio seuls ont une transcription ; les vidéos seules ont une alternative textuelle ou audio ; les vidéos avec son ont des sous-titres synchronisés, ainsi qu'une audio-description ou une alternative textuelle complète | 1.2.1, 1.2.2, 1.2.3 (A) | 1. Lire chaque vidéo avec les sous-titres activés : ils doivent correspondre aux paroles et aux sons importants, au même moment.<br>2. Pour chaque vidéo, chercher une version audio-décrite ou une alternative textuelle complète qui décrit aussi les informations visuelles importantes.<br>3. Pour un contenu audio seul (par exemple un podcast), chercher une transcription ; pour une vidéo sans son, chercher une description textuelle ou une piste audio.<br>✅ **Réussi :** chaque média pré-enregistré dispose des alternatives indiquées ci-dessus. |
| **Contenus en mouvement, qui flashent ou qui démarrent automatiquement** | Un contenu en mouvement, clignotant ou défilant pendant plus de 5 secondes, ou mis à jour automatiquement, peut être mis en pause, arrêté ou masqué ; un son qui démarre automatiquement et dure plus de 3 secondes peut être arrêté ou son volume réglé ; rien ne flashe plus de trois fois par seconde (sauf sous les seuils de flash) | 2.2.2, 1.4.2, 2.3.1 (A) | 1. Charger chaque page et attendre au moins 5 secondes ; lister tout ce qui bouge, clignote, défile ou se met à jour tout seul (carrousel, bandeau défilant, animation, fil en direct).<br>2. Pour chacun, trouver un bouton pause, arrêt ou masquer et l'utiliser au clavier.<br>3. Si un son démarre tout seul et dure plus de 3 secondes, trouver sur la page un contrôle pour l'arrêter ou baisser son volume.<br>4. Si quelque chose flashe plus de trois fois en une seconde, le vérifier avec un outil d'analyse du risque d'épilepsie photosensible (par exemple PEAT), ou le signaler pour la revue d'expert.<br>✅ **Réussi :** chaque élément de l'étape 1 peut être mis en pause, arrêté ou masqué ; le son automatique peut être arrêté ; rien ne flashe au-dessus des seuils. |
| **Limites de temps** | Chaque limite de temps peut être désactivée, ajustée (au moins dix fois la durée par défaut) ou prolongée après un avertissement (au moins 20 secondes, action simple), sauf pour les limites en temps réel, essentielles ou de plus de 20 heures | 2.2.1 (A) | 1. Demander à l'équipe quelles limites de temps existent (expiration de session, étapes chronométrées, réservations conservées pendant un temps limité).<br>2. Déclencher chacune : rester inactif jusqu'à peu avant l'expiration (demander un environnement de test avec une expiration courte si nécessaire).<br>3. Vérifier qu'un avertissement apparaît, que le lecteur d'écran l'annonce, et qu'une action simple (par exemple un seul bouton) prolonge le temps.<br>✅ **Réussi :** chaque limite de temps peut être désactivée, ajustée ou prolongée avec au moins 20 secondes pour réagir, ou est une limite en temps réel, essentielle ou de plus de 20 heures. |
| **Pas uniquement par la couleur ou les sens** | Les informations, états et instructions ne reposent pas uniquement sur la couleur, ni uniquement sur la forme, la taille, la position ou le son | 1.4.1, 1.3.3 (A) | 1. Dans les DevTools de Chrome, ouvrir Rendering > Emulate vision deficiencies > Achromatopsia (niveaux de gris).<br>2. Regarder les liens dans le texte, les erreurs de formulaire, les champs obligatoires, les graphiques et les indicateurs d'état.<br>3. Lire les instructions et chercher des références comme « le bouton vert », « le champ à droite » ou « quand vous entendez le bip ».<br>✅ **Réussi :** en niveaux de gris, toutes les informations et tous les états restent compréhensibles ; chaque instruction nomme aussi l'élément (par exemple « le bouton Envoyer »). |
| **Fonction des liens et libellé dans le nom** | La fonction de chaque lien est claire d'après son texte ou son contexte ; le nom accessible des liens, boutons et contrôles contient leur texte visible | 2.4.4, 2.5.3 (A) | 1. Ouvrir la liste des liens du lecteur d'écran et lire chacun, avec sa phrase, son paragraphe ou sa cellule de tableau si nécessaire.<br>2. Pour chaque lien et bouton avec un texte visible, comparer ce texte avec le nom accessible dans les DevTools (panneau Elements, volet Accessibility, « Name »).<br>✅ **Réussi :** aucun lien n'est ambigu (« cliquez ici » sans contexte) ; chaque nom accessible contient le texte visible, idéalement au début. |
| **Nom, rôle, valeur** | Tous les contrôles, natifs et personnalisés, exposent un nom, un rôle, ainsi que leurs états et valeurs (développé, sélectionné, coché, désactivé), et les changements sont transmis aux technologies d'assistance | 4.1.2 (A) | 1. Avec le lecteur d'écran, aller sur chaque contrôle avec Tab et écouter : il doit annoncer le nom, le type (bouton, case à cocher, onglet, menu…) et l'état (coché, développé, sélectionné, désactivé).<br>2. Changer l'état (ouvrir l'accordéon, cocher la case, sélectionner l'onglet) et écouter à nouveau.<br>3. Pour les composants personnalisés, vérifier le rôle et les états ARIA dans les DevTools (volet Accessibility).<br>✅ **Réussi :** chaque contrôle annonce son nom, son rôle et son état actuel, et le nouvel état est annoncé après chaque changement. |
| **Étiquettes et instructions des formulaires** | Chaque champ a une étiquette ou des instructions visibles, y compris l'indication des champs obligatoires et des formats attendus | 3.3.2 (A) | 1. Regarder chaque formulaire sans le lecteur d'écran : chaque champ doit avoir une étiquette visible ; les champs obligatoires et les formats attendus (date, téléphone) doivent être indiqués avant la saisie, et pas seulement dans un texte indicatif (placeholder) qui disparaît pendant la frappe.<br>2. Parcourir le formulaire avec Tab et le lecteur d'écran.<br>✅ **Réussi :** chaque étiquette, indication d'obligation et format est visible et est aussi annoncé. |
| **Identification des erreurs** | Les erreurs de saisie détectées automatiquement identifient le champ en erreur et décrivent l'erreur sous forme de texte | 3.3.1 (A) | 1. Soumettre chaque formulaire vide.<br>2. Le soumettre à nouveau avec des valeurs invalides (e-mail sans @, date au mauvais format).<br>3. Vérifier chaque erreur à l'écran et avec le lecteur d'écran.<br>✅ **Réussi :** chaque champ en erreur est identifié (message à côté du champ, ou nom du champ dans le message), et l'erreur est décrite sous forme de texte, pas seulement par une bordure rouge ou une icône. |
| **Focus et saisie prévisibles** | Recevoir le focus ne provoque jamais de changement de contexte ; changer la valeur d'un champ non plus, sauf si l'utilisateur en a été averti au préalable | 3.2.1, 3.2.2 (A) | 1. Parcourir tous les contrôles avec Tab sans rien activer.<br>2. Changer les valeurs des listes déroulantes, boutons radio et cases à cocher au clavier (flèches, Espace), sans appuyer sur aucun bouton.<br>✅ **Réussi :** aucune nouvelle fenêtre ne s'ouvre, la page ne change pas, aucun formulaire n'est soumis et le focus ne saute pas. Pour les changements de valeur uniquement, c'est admis si un texte visible l'a annoncé au préalable. |
| **Aide cohérente** | Les mécanismes d'aide répétés sur plusieurs pages (coordonnées, formulaire de contact ou chat, FAQ) apparaissent dans le même ordre par rapport au reste du contenu de la page | 3.2.6 (A) | 1. Lister les mécanismes d'aide du site (coordonnées, formulaire de contact, chat, lien vers la FAQ).<br>2. Ouvrir au moins trois pages où ils apparaissent et noter leur position par rapport au reste du contenu (par exemple « dans le pied de page, après les mentions légales »).<br>✅ **Réussi :** sur chaque page, ils apparaissent dans le même ordre par rapport au reste du contenu. |
| **Saisie redondante** | Une information déjà saisie dans le même processus est pré-remplie ou sélectionnable, sauf si la ressaisie est essentielle, exigée pour la sécurité, ou si l'information n'est plus valide | 3.3.7 (A) | 1. Parcourir chaque processus en plusieurs étapes (inscription, commande, demande).<br>2. Noter chaque information demandée plus d'une fois (par exemple l'adresse à l'étape 2, puis à nouveau à l'étape 4).<br>✅ **Réussi :** l'information redemandée est pré-remplie ou proposée en sélection (par exemple « Identique à l'adresse de livraison »), sauf si la ressaisie est essentielle, nécessaire pour la sécurité (par exemple un mot de passe) ou si la valeur précédente n'est plus valide. |
| **Gestes, annulation du pointeur et mouvement** | Les gestes multipoints ou basés sur un tracé ont une alternative à pointeur unique ; les actions ne se déclenchent pas à l'appui, ou peuvent être interrompues ou annulées ; les fonctions déclenchées par le mouvement ont une alternative par un contrôle et peuvent être désactivées | 2.5.1, 2.5.2, 2.5.4 (A) | 1. Sur un appareil tactile, lister chaque geste (pincer, balayer, appui à plusieurs doigts, dessin d'un tracé) et utiliser son alternative (bouton, lien, appui simple).<br>2. Appuyer sur un bouton avec la souris ou le doigt, maintenir l'appui, s'éloigner du bouton, puis relâcher.<br>3. Pour les fonctions déclenchées en secouant ou en inclinant l'appareil, chercher un bouton à l'écran et un réglage pour désactiver le mouvement.<br>✅ **Réussi :** chaque geste a une alternative par un appui ou un clic simple ; relâcher en dehors du bouton ne déclenche rien (ou l'action peut être annulée) ; chaque fonction liée au mouvement a un bouton et peut être désactivée. |
| **Langue de la page** | La langue par défaut de chaque page est déclarée dans le code (`lang` sur `<html>`) | 3.1.1 (A) | 1. Dans les DevTools, sélectionner l'élément `<html>` et lire son attribut `lang` (par exemple `lang="fr"`).<br>2. Écouter le début de la page avec le lecteur d'écran.<br>✅ **Réussi :** l'attribut `lang` est présent et correspond à la langue de la page ; le lecteur d'écran utilise la bonne prononciation. |

---

### Critères légaux (niveau AA — conformité exigée)

Ce tableau couvre les 24 critères de succès de niveau AA des WCAG 2.2. Le niveau AA est le niveau exigé par les cadres juridiques présentés au chapitre 2 du support de cours : EN 301 549 pour les directives de l'UE (la V4.1.1 est alignée sur les WCAG 2.2), le RGAA 4.1.2 en France et l'eCH-0059 V3.0 en Suisse (tous deux encore basés sur les WCAG 2.1). La conformité au niveau AA exige aussi tous les critères de niveau A du tableau précédent.

| Critère | Description | WCAG | Comment vérifier |
| --- | --- | --- | --- |
| **Focus visible et non masqué** | Un indicateur de focus visible est affiché sur chaque élément focalisable et n'est jamais supprimé par le CSS ; l'élément qui a le focus n'est jamais entièrement masqué par un en-tête fixe, un bandeau ou un widget de chat | 2.4.7, 2.4.11 (AA) | 1. Laisser affichés tous les éléments fixes (en-tête, bandeau de cookies, bouton de chat) : ne pas les fermer.<br>2. Parcourir toute la page avec Tab, jusqu'au pied de page, en observant l'indicateur de focus.<br>✅ **Réussi :** on voit toujours quel élément a le focus, et l'élément qui a le focus n'est jamais complètement caché derrière un en-tête fixe, un bandeau ou un widget (partiellement caché est admis au niveau AA). |
| **Contraste** | Texte ≥ 4,5:1 (texte de grande taille ≥ 3:1) ; composants d'interface, indicateurs d'état, indicateurs de focus et graphiques porteurs de sens ≥ 3:1 par rapport aux couleurs adjacentes. Les composants désactivés, la décoration et les logos sont exemptés | 1.4.3, 1.4.11 (AA) | 1. Lancer un outil automatique (axe DevTools ou WAVE) pour trouver les défauts de contraste du texte.<br>2. Avec un outil de vérification du contraste (par exemple le WebAIM Contrast Checker, ou le ratio de contraste du sélecteur de couleur des DevTools), mesurer ce que l'outil automatique ne peut pas évaluer : texte sur image ou sur dégradé, bordures de champs, icônes, indicateurs de focus et éléments de graphiques, chacun par rapport à la couleur voisine.<br>3. Répéter pour les états survol, focus, erreur et sélectionné.<br>✅ **Réussi :** texte normal ≥ 4,5:1 ; texte de grande taille (≥ 24 px, ou ≥ 18,5 px en gras) ≥ 3:1 ; composants, états, indicateurs de focus et graphiques porteurs de sens ≥ 3:1. |
| **Redimensionnement du texte** | Le texte peut être agrandi à 200 % sans perte de contenu ni de fonctionnalité | 1.4.4 (AA) | 1. Régler le zoom du navigateur à 200 % (Ctrl ou Cmd et +).<br>2. Parcourir chaque page et chaque composant (menus, dialogues, formulaires, tableaux).<br>✅ **Réussi :** tout le texte est agrandi, rien n'est coupé, masqué ni superposé, et chaque fonction marche toujours. |
| **Reflow** | À 320 px CSS de large (zoom à 400 % dans une fenêtre de 1280 px CSS), le contenu se réorganise sans défilement horizontal et sans perte d'information ni de fonctionnalité ; les tableaux de données, cartes et schémas sont exemptés | 1.4.10 (AA) | 1. Régler la fenêtre du navigateur sur 1280 px de large et le zoom à 400 % ; ou bien utiliser la barre d'outils de simulation d'appareil des DevTools avec une largeur de 320 px et un zoom à 100 %.<br>2. Parcourir chaque page en défilant uniquement vers le haut et le bas.<br>✅ **Réussi :** on peut lire tout le contenu et utiliser chaque fonction sans défiler sur le côté ; seuls les tableaux de données, cartes et schémas peuvent défiler horizontalement. |
| **Espacement du texte** | Augmenter la hauteur de ligne et l'espacement des paragraphes, des lettres et des mots aux valeurs du critère 1.4.12 ne provoque aucune perte de contenu ni de fonctionnalité | 1.4.12 (AA) | 1. Dans les DevTools, ajouter ces règles à la page : `* { line-height: 1.5 !important; letter-spacing: 0.12em !important; word-spacing: 0.16em !important; } p { margin-bottom: 2em !important; }` (ou utiliser un bookmarklet d'espacement du texte).<br>2. Parcourir chaque page.<br>✅ **Réussi :** aucun texte n'est coupé, masqué ni superposé, et chaque fonction marche toujours. |
| **Contenu au survol ou au focus** | Les infobulles, sous-menus et fenêtres contextuelles affichés au survol ou au focus peuvent être masqués sans déplacer le pointeur ni le focus, restent visibles lorsqu'on les survole, et restent affichés jusqu'à leur fermeture ou tant qu'ils sont pertinents | 1.4.13 (AA) | Pour chaque infobulle, sous-menu ou fenêtre contextuelle :<br>1. L'afficher avec la souris, puis au clavier (Tab).<br>2. Appuyer sur Échap (ou utiliser le mécanisme de fermeture prévu) : il doit se fermer sans déplacer le pointeur ni le focus.<br>3. L'afficher à nouveau avec la souris, puis déplacer le pointeur dessus : il doit rester visible.<br>4. Attendre sans bouger : il doit rester affiché jusqu'à ce qu'on s'éloigne ou qu'on le ferme.<br>✅ **Réussi :** les étapes 2 à 4 réussissent pour chacun. L'étape 2 n'est pas exigée si le contenu ne masque aucun autre contenu ou s'il signale une erreur de saisie ; les infobulles natives `title` sont exemptées. |
| **Images de texte** | Le texte est du vrai texte, et non une image de texte, sauf les logos et les présentations essentielles | 1.4.5 (AA) | 1. Zoomer à 200 % : les images de texte deviennent floues, le vrai texte reste net.<br>2. Essayer de sélectionner à la souris le texte suspect.<br>3. Dans les DevTools, vérifier si l'élément est une `<img>`, une image SVG ou une image d'arrière-plan CSS.<br>✅ **Réussi :** tout le texte est du vrai texte, sauf les logos et les cas où la présentation visuelle exacte est essentielle. |
| **Orientation** | L'interface fonctionne en portrait et en paysage, sauf si une orientation est essentielle | 1.3.4 (AA) | 1. Sur un téléphone ou une tablette, désactiver le verrouillage de la rotation.<br>2. Ouvrir chaque page en portrait, puis tourner l'appareil en paysage (et revenir).<br>✅ **Réussi :** le contenu s'affiche et fonctionne dans les deux orientations ; aucun message ne demande de tourner l'appareil, sauf si une orientation est essentielle. |
| **Finalité de la saisie** | Les champs qui recueillent des informations sur l'utilisateur exposent leur finalité avec `autocomplete` | 1.3.5 (AA) | 1. Dans les DevTools, inspecter chaque champ qui demande des données personnelles de l'utilisateur (nom, e-mail, téléphone, adresse, date de naissance…).<br>2. Lire sa valeur `autocomplete` et vérifier qu'elle correspond à la donnée (par exemple `given-name`, `email`, `tel`, `postal-code`, `bday`).<br>3. Facultatif : avec des données de remplissage automatique enregistrées dans le navigateur, vérifier que le navigateur propose les bonnes valeurs.<br>✅ **Réussi :** chacun de ces champs a la valeur correcte de la liste WCAG « Input Purposes for User Interface Components ». |
| **Messages d'état** | Les erreurs, confirmations, nombres de résultats et messages de chargement ou de progression qui apparaissent sans déplacer le focus sont annoncés par le lecteur d'écran | 4.1.3 (AA) | 1. Activer le lecteur d'écran.<br>2. Déclencher chaque message qui apparaît sans déplacer le focus : erreur de formulaire en ligne, confirmation « Enregistré », « 12 résultats trouvés » après une recherche ou un filtre, message de chargement, mise à jour du compteur du panier.<br>3. Ne pas déplacer le focus ; écouter.<br>✅ **Réussi :** chaque message est lu automatiquement. Si l'un ne l'est pas, vérifier dans les DevTools que son conteneur a `role="status"`, `role="alert"` ou `aria-live`, et que le conteneur est déjà présent dans la page (vide) avant l'insertion du message — `role="alert"` est généralement annoncé même s'il est injecté avec son message. |
| **Suggestion et prévention des erreurs** | Les messages d'erreur suggèrent une correction lorsqu'elle est connue ; les soumissions ayant des conséquences juridiques ou financières, qui modifient ou suppriment des données de l'utilisateur, ou qui envoient des réponses à un test peuvent être annulées, vérifiées ou confirmées avant leur finalisation | 3.3.3, 3.3.4 (AA) | **Suggestion des erreurs :**<br>1. Saisir des valeurs erronées typiques (e-mail sans @, date au mauvais format, nombre hors limites) et soumettre.<br>2. Lire chaque message d'erreur.<br>✅ **Réussi :** lorsque le format ou la valeur attendus sont connus, le message les indique (par exemple « Saisissez la date au format JJ.MM.AAAA »).<br>**Prévention des erreurs :**<br>3. Lister les formulaires qui engagent l'utilisateur juridiquement ou financièrement (contrat, paiement, déclaration d'impôts), qui modifient ou suppriment ses données enregistrées (profil, suppression du compte), ou qui envoient des réponses à un test.<br>4. Remplir chacun et le soumettre.<br>✅ **Réussi :** au moins une de ces conditions est remplie : une page récapitulative permet de vérifier, corriger et confirmer les données avant la soumission finale ; ou les données sont vérifiées et les erreurs peuvent être corrigées avant la finalisation ; ou la soumission peut être annulée ensuite. |
| **Titres et étiquettes descriptifs** | Les titres et les étiquettes décrivent le sujet ou la finalité de leur contenu | 2.4.6 (AA) | 1. Ouvrir la liste des titres du lecteur d'écran et lire les titres seuls, sans la page.<br>2. Parcourir les formulaires avec Tab et écouter les étiquettes seules.<br>✅ **Réussi :** chaque titre indique le sujet de sa section, et chaque étiquette indique ce qu'il faut saisir (pas de « Champ 1 », « Infos » ou « Détails » sans sujet). |
| **Plusieurs moyens d'accès** | Plusieurs moyens (recherche, plan du site, menu) mènent à chaque page, sauf aux pages qui sont une étape d'un processus | 2.4.5 (AA) | 1. Choisir environ cinq pages du site qui ne sont pas une étape d'un processus.<br>2. Pour chacune, essayer de l'atteindre de deux manières différentes : menu principal, recherche, plan du site, liens depuis des pages liées, table des matières.<br>✅ **Réussi :** chaque page peut être atteinte d'au moins deux manières. |
| **Navigation et identification cohérentes** | La navigation répétée apparaît dans le même ordre relatif sur chaque page ; les mêmes fonctions portent les mêmes libellés, icônes et noms accessibles | 3.2.3, 3.2.4 (AA) | 1. Ouvrir au moins trois pages qui partagent la même navigation.<br>2. Comparer les menus : les éléments doivent apparaître dans le même ordre relatif (des éléments peuvent être ajoutés ou retirés, pas réordonnés).<br>3. Comparer les fonctions présentes sur plusieurs pages (recherche, impression, téléchargement, fermeture, aide) : même libellé, même icône, même nom accessible.<br>✅ **Réussi :** aucun menu n'est réordonné et aucune fonction ne change de nom ou d'icône d'une page à l'autre. |
| **Langue des passages** | Les passages dans une autre langue sont signalés avec `lang`, sauf les noms propres et les termes techniques | 3.1.2 (AA) | 1. Repérer les passages dans une langue différente de celle de la page (par exemple une citation en anglais sur une page en français, ou « Deutsch » et « Italiano » dans un sélecteur de langue).<br>2. Dans les DevTools, vérifier que chacun a un attribut `lang` (par exemple `lang="de"`).<br>3. Écouter avec le lecteur d'écran : la prononciation doit changer.<br>✅ **Réussi :** chaque passage dans une autre langue est signalé, sauf les noms propres, les termes techniques et les mots couramment utilisés dans la langue de la page. |
| **Sous-titres en direct et audio-description** | Les vidéos en direct ont des sous-titres ; les vidéos pré-enregistrées ont une audio-description des informations visuelles importantes | 1.2.4, 1.2.5 (AA) | 1. Pour les diffusions en direct (webinaires, événements), activer les sous-titres pendant une diffusion et vérifier qu'ils apparaissent en temps réel.<br>2. Pour chaque vidéo pré-enregistrée, chercher une piste d'audio-description ou une version audio-décrite ; la lire et vérifier qu'elle décrit les informations visuelles importantes (texte à l'écran, actions, changements de scène).<br>✅ **Réussi :** les vidéos en direct ont des sous-titres ; les vidéos pré-enregistrées ont une audio-description, sauf si la bande-son transmet déjà toutes les informations visuelles importantes. |
| **Glisser et taille des cibles** | Chaque action de glisser a une alternative à pointeur unique sans glisser ; les cibles mesurent au moins 24 × 24 px CSS ou sont suffisamment espacées (voir le thème 16 pour les exceptions) | 2.5.7, 2.5.8 (AA) | **Glisser :**<br>1. Lister chaque interaction de glisser (liste réordonnable, curseur, zone de dépôt de fichiers, carte, tableau kanban).<br>2. Réaliser la même action uniquement par des clics ou appuis simples (par exemple un bouton « Monter », un clic sur la piste du curseur, un bouton « Parcourir »).<br>**Taille des cibles :**<br>3. Dans les DevTools, survoler les petites cibles (icônes, boutons de fermeture, liens dans des listes, pagination) avec l'outil de sélection d'élément : il affiche leur largeur × hauteur.<br>✅ **Réussi :** chaque action de glisser a une alternative par clic ou appui ; chaque cible mesure au moins 24 × 24 px CSS, ou est espacée comme décrit au thème 16, ou fait partie de ses exceptions (par exemple un lien dans une phrase). |
| **Authentification accessible** | La connexion ne repose pas sur un test de fonction cognitive sans alternative ni mécanisme d'assistance ; les gestionnaires de mots de passe et le copier-coller fonctionnent | 3.3.8 (AA) | 1. Enregistrer le compte de test dans un gestionnaire de mots de passe et se connecter avec le remplissage automatique.<br>2. Se déconnecter, copier le mot de passe et le coller dans le champ du mot de passe.<br>3. S'il y a une étape avec un code (code reçu par SMS ou par e-mail, mot de passe à usage unique), vérifier qu'on peut coller le code, ou qu'une alternative existe (par exemple un lien de connexion dans l'e-mail).<br>4. S'il y a un CAPTCHA ou une énigme, vérifier qu'une alternative existe qui n'exige ni de recopier ni de résoudre quoi que ce soit (reconnaître des objets est admis au niveau AA).<br>✅ **Réussi :** la connexion fonctionne avec le gestionnaire de mots de passe et avec le collage, et aucune étape n'exige de mémoriser, de recopier ou de résoudre quelque chose sans alternative. |

---

### Critères d'excellence (niveau AAA et bonnes pratiques — optimisation)

Cette section présente une sélection de critères de niveau AAA et de bonnes pratiques qui ne sont pas des exigences WCAG, qui visent une accessibilité optimale et une expérience utilisateur exceptionnelle. Contrairement aux niveaux A et AA, ces critères ne sont pas imposés par la réglementation, et les WCAG ne recommandent pas d'exiger le niveau AAA comme politique générale pour des sites entiers. Appliqués critère par critère lorsque le contenu le permet, ils améliorent le confort de tous, y compris des utilisateurs ayant des besoins spécifiques ou complexes.

| Critère | Description | WCAG | Comment vérifier |
| --- | --- | --- | --- |
| **Fonction du lien (lien seul)** | La fonction de chaque lien est claire d'après le seul texte du lien | 2.4.9 (AAA) | 1. Ouvrir la liste des liens du lecteur d'écran (elle affiche les textes des liens sans leur contexte).<br>2. Lire chaque lien.<br>✅ **Réussi :** chaque lien est compréhensible seul (par exemple « Télécharger le rapport annuel 2026 (PDF) » plutôt que « Télécharger »). |
| **Localisation et progression** | L'utilisateur sait où il se trouve dans le site (fil d'Ariane, élément courant de la navigation avec `aria-current`) et dans un processus en plusieurs étapes (« Étape 2 sur 4 ») | 2.4.8 (AAA) pour la localisation dans un ensemble de pages ; indicateurs d'étapes : bonne pratique | 1. Sur plusieurs pages, vérifier qu'on peut savoir où l'on se trouve : fil d'Ariane, élément courant mis en évidence dans le menu, titre de la page.<br>2. Avec le lecteur d'écran, vérifier que l'élément courant du menu est annoncé comme « actuel ».<br>3. Dans chaque processus en plusieurs étapes, vérifier que l'étape en cours et le nombre total d'étapes sont affichés et annoncés (par exemple « Étape 2 sur 4 : Adresse »).<br>✅ **Réussi :** la localisation et la progression sont visibles et annoncées. |
| **Aide contextuelle** | Une aide est disponible là où les utilisateurs en ont besoin (texte d'aide, lien d'aide, infobulle à côté des champs complexes) | 3.3.5 (AAA) | 1. Identifier les champs et fonctions complexes (par exemple IBAN, codes fiscaux, formats de fichiers acceptés).<br>2. Vérifier qu'un texte d'aide, un lien d'aide ou un bouton d'aide se trouve à côté.<br>3. Ouvrir l'aide au clavier et avec le lecteur d'écran.<br>✅ **Réussi :** une aide est disponible à côté de chaque champ ou fonction complexe, et elle peut être atteinte et lue au clavier et avec le lecteur d'écran. |
| **Mots rares et abréviations** | Le jargon, les termes techniques et les abréviations sont définis ou développés | 3.1.3, 3.1.4 (AAA) | 1. Demander à une personne extérieure au projet, ou nouvelle dans le domaine métier, de lire les pages principales et de noter chaque mot ou abréviation qu'elle ne comprend pas.<br>2. Pour chacun, chercher une définition ou une forme développée : à la première occurrence, dans un glossaire, ou avec `<abbr title="">`.<br>✅ **Réussi :** chaque terme noté à l'étape 1 est défini ou développé. |
| **Niveau de lecture** | Un texte qui exige un niveau de lecture supérieur au premier cycle du secondaire a une version plus simple ou un contenu complémentaire | 3.1.5 (AAA) | 1. Coller les textes principaux (instructions, messages d'erreur, aide) dans un outil de lisibilité adapté à la langue du contenu.<br>2. Pour les textes au-dessus du niveau du premier cycle du secondaire, chercher une version plus simple, un résumé ou des illustrations.<br>✅ **Réussi :** chaque texte au-dessus de ce niveau a une version plus simple ou un contenu complémentaire. |
| **Taille des cibles (renforcé)** | Les cibles interactives mesurent au moins 44 × 44 px CSS | 2.5.5 (AAA) | 1. Dans les DevTools, survoler chaque élément interactif avec l'outil de sélection d'élément et lire sa largeur × hauteur.<br>✅ **Réussi :** chaque cible mesure au moins 44 × 44 px CSS, sauf les liens dans le texte, les cibles qui ont un contrôle équivalent de cette taille sur la même page, les contrôles par défaut du navigateur et les présentations essentielles. |
| **Interruptions et mises à jour automatiques** | Les pop-ups, actualisations automatiques et mises à jour de contenu peuvent être reportées ou supprimées, sauf en cas d'urgence | 2.2.4 (AAA) | 1. Rester quelques minutes sur des pages qui affichent des notifications ou des pop-ups, ou qui s'actualisent toutes seules (tableaux de bord, boîtes de réception).<br>2. Chercher un moyen de les reporter ou de les désactiver (par exemple « Suspendre les mises à jour », réglages des notifications).<br>✅ **Réussi :** chaque interruption qui n'est pas une urgence peut être reportée ou désactivée. |
| **Changements sur demande et nouvelles fenêtres** | Les changements de contexte ne se produisent qu'à la demande de l'utilisateur ; les liens qui ouvrent une nouvelle fenêtre ou un nouvel onglet l'indiquent dans leur texte | 3.2.5 (AAA) | 1. Activer chaque lien et contrôle qui ouvre une nouvelle fenêtre ou un nouvel onglet.<br>2. Rester sur les pages sans agir et observer s'il y a des actualisations ou des redirections automatiques.<br>✅ **Réussi :** chaque lien qui ouvre une nouvelle fenêtre ou un nouvel onglet l'indique dans son texte (par exemple « (s'ouvre dans un nouvel onglet) », technique W3C H83) ; aucune actualisation ni redirection ne se produit sans action de l'utilisateur. |
| **Pas de limite de temps** | Aucune limite de temps n'est imposée, sauf pour les médias synchronisés non interactifs et les événements en temps réel | 2.2.3 (AAA) | 1. Demander à l'équipe la liste des limites de temps (la même liste que pour le critère 2.2.1).<br>✅ **Réussi :** aucune limite de temps n'existe, sauf dans les médias synchronisés non interactifs et les événements en temps réel (par exemple une enchère en direct). |
| **Hiérarchie des titres** | Un seul H1 par page et aucun niveau de titre sauté | — (bonne pratique, pas une exigence WCAG) | 1. Ouvrir la liste des titres du lecteur d'écran, ou utiliser une extension de navigateur qui affiche le plan des titres.<br>2. Vérifier les niveaux de titres.<br>✅ **Réussi :** exactement un H1 par page, et aucun niveau sauté (par exemple pas de H2 suivi directement d'un H4). |

---

## Niveaux de conformité

Rappel des niveaux de conformité WCAG.

### 1. Niveau A (minimal)

Le niveau A est le niveau de conformité WCAG minimal. Tous les critères de niveau A doivent être validés à 100 % pour atteindre ce niveau. Si un seul critère de niveau A n'est pas respecté, le site n'est pas conforme au niveau A.

- **Exemple :** Si 30 critères de niveau A sur 31 sont validés, le site n'est pas conforme au niveau A.
- **Conséquence (recommandation de l'auteur) :** Non apte à la mise en production (risque de bloquer certains utilisateurs).

### 2. Niveau AA (cible)

Pour atteindre le niveau AA, tous les critères de niveau A ET tous les critères de niveau AA doivent être validés à 100 %. C'est le niveau exigé par les cadres juridiques (EN 301 549 pour les directives de l'UE, RGAA en France, eCH-0059 en Suisse).

- **Exemple :** Si tous les critères de niveau A sont validés mais qu'un seul critère AA manque, le site n'est pas conforme au niveau AA.
- **Conséquence (recommandation de l'auteur) :** Apte à la mise en production uniquement si 100 % A + 100 % AA.

### 3. Niveau AAA (excellence)

Pour atteindre le niveau AAA, tous les critères A, AA et AAA doivent être validés à 100 %. Ce niveau est rare et difficile à atteindre sur l'ensemble du contenu : les WCAG ne recommandent pas de l'exiger comme politique générale pour des sites entiers.

- **Exemple :** Même si un seul critère AAA manque, le site n'est pas conforme au niveau AAA.
- **Conséquence (recommandation de l'auteur) :** Excellence en accessibilité (facultative, mais recommandée critère par critère lorsque le contenu le permet).

---

## Outils et prérequis

### Lecteurs d'écran recommandés

- **NVDA** (Windows – gratuit)
- **JAWS** (Windows – payant)
- **VoiceOver** (macOS/iOS – intégré)
- **TalkBack** (Android – intégré)
- **Orca** (Linux – gratuit)

### Navigateurs compatibles

- Chrome / Edge
- Firefox
- Safari (pour VoiceOver)

### Autres outils recommandés

- DevTools du navigateur (pour modifier le CSS)
- Un outil de vérification du contraste (WCAG Contrast Checker, axe, WAVE, SilkTide)
- Zoom du navigateur (200 % et 400 %)
- Un simulateur mobile / responsive
- Tests au clavier seul

### Compétences requises

- Connaissances de base des lecteurs d'écran
- Maîtrise de la navigation au clavier seul
- Compréhension des standards WCAG et ARIA, y compris les critères 1.4.x, 2.4.x, 2.5.x, 3.2.x et 4.1.2
- Capacité à tester une interface sans lecteur d'écran

---

## Ressources et références

### Standards et recommandations

- [WCAG 2.2 Quick Reference (How to Meet WCAG)](https://www.w3.org/WAI/WCAG22/quickref/)
- [RGAA - Référentiel Général d'Amélioration de l'Accessibilité](https://accessibilite.numerique.gouv.fr/)
- [ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/)
- [AcceDe Web - Notices d'accessibilité](https://www.accede-web.com/)

### Outils de validation

- **WAVE** (Web Accessibility Evaluation Tool)
- **axe DevTools** (extension pour Chrome/Firefox)
- **ARIA DevTools** (extension Chrome)
- **Lighthouse** (audit intégré à Chrome)
- **Pa11y** (outil en ligne de commande)
- **Assistant RGAA** (extension pour tester la conformité RGAA)
- **Narrateur Windows** (lecteur d'écran par défaut de Windows)

### Documentation des lecteurs d'écran

- [NVDA User Guide](https://www.nvaccess.org/files/nvda/documentation/userGuide.html)
- [JAWS Documentation](https://www.freedomscientific.com/training/jaws/)
- [VoiceOver Guide](https://support.apple.com/guide/voiceover/welcome/mac)
- [Complete guide to Narrator | Microsoft Support](https://support.microsoft.com/en-us/accessibility/windows/narrator/complete-guide-to-narrator)

### Ressources en français

- [AcceDe Web - Ressources et outils](https://www.accede-web.com/notices/)
- [ARIA en français - MDN](https://developer.mozilla.org/fr/docs/Web/Accessibility/ARIA)
- [Blog Access42](https://access42.net/blog)
- [Règles pour l'accessibilité des contenus Web (WCAG) 2.2 — traduction française autorisée du W3C](https://www.w3.org/Translations/WCAG22-fr-20260922/)
