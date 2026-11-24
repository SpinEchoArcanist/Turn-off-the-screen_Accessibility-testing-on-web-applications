# Annexe B — Guide de test de l'accessibilité

## Introduction

Les WCAG, bien que complètes, peuvent être complexes à interpréter pour des équipes non spécialistes. Ce guide simplifie l'interprétation des critères WCAG et aide les équipes à valider concrètement l'accessibilité des interfaces web pour les **utilisateurs aveugles utilisant un lecteur d'écran, les utilisateurs malvoyants, les utilisateurs daltoniens, les utilisateurs ayant des limitations motrices ou cognitives, et les utilisateurs sur mobile ou avec zoom**. Il se concentre sur les critères essentiels des WCAG 2.2 qui affectent directement l'expérience des personnes utilisant un lecteur d'écran et d'autres technologies d'assistance, ainsi que sur les critères de perception visuelle, de zoom/responsive, de contraste, d'interaction tactile, de lisibilité et de cohérence de l'interface que les tests au lecteur d'écran ne peuvent pas valider à eux seuls.

Plutôt qu'une reformulation exhaustive du standard WCAG, ce document adopte une **approche pragmatique** : il fournit une checklist structurée pour tester concrètement la navigabilité au clavier, la structure sémantique, les formulaires, les composants dynamiques, les parcours métier critiques, les contraintes de temps, le comportement en zoom et en reflow, l'espacement du texte, le contraste des couleurs, le comportement responsive et l'orientation, les interactions tactiles et au pointeur, la taille des cibles et la cohérence de l'interface. Chaque élément renvoie au critère WCAG correspondant et à son niveau, afin que les équipes puissent revenir à la source officielle si nécessaire.

**Niveau de conformité visé :** WCAG 2.2 niveau AA.

**Note :** Ce guide ne remplace pas le standard WCAG officiel — il en est une mise en œuvre ciblée et pratique. Ces tests ne remplacent pas non plus un audit d'accessibilité complet (voir la section 4.6 du support de cours). La liste complète des critères de succès WCAG 2.2 et de leurs niveaux figure dans l'annexe A.

---

## Checklist par thème

Cette checklist est conçue pour guider la validation de l'accessibilité étape par étape, en décomposant les exigences des WCAG 2.2 par grande fonctionnalité de l'application (navigation, formulaires, composants interactifs, présentation visuelle, comportement responsive, etc.).

Chaque section vise un objectif clair (par ex. *« Assurer une navigation fluide et logique »*) et liste les vérifications à effectuer, chacune renvoyant directement au critère WCAG correspondant.

Pour chaque domaine fonctionnel, vous trouverez :

- Une liste d'actions vérifiables, formulées simplement et directement (par ex. *« Le focus clavier est visible en permanence »*).
- Les références WCAG et leurs niveaux, pour revenir rapidement aux exigences officielles.
- Des critères d'acceptation en fin de section, qui résument les attentes minimales pour valider la conformité (par ex. *« 100 % des zones sont accessibles au clavier »*).

**Objectif :** Rendre l'audit rapide et reproductible, en donnant aux équipes un cadre structuré pour tester chaque aspect de l'application sans exiger une expertise WCAG approfondie.

### 1. Navigation générale (y compris la visibilité du focus)

**Objectif :** Assurer une navigation fluide et logique dans toute l'application, avec un indicateur de focus toujours clairement visible — y compris sur les composants personnalisés.

- La navigation au clavier (Tab, Maj+Tab, flèches) fonctionne correctement **(WCAG 2.1.1, 2.1.2 - A)**
- L'ordre de tabulation suit une séquence logique (de haut en bas, de gauche à droite) **(WCAG 2.4.3 - A)**
- Les zones de navigation principales sont identifiables (en-tête, navigation, contenu principal, pied de page) **(WCAG 1.3.1 - A)**
- Des liens d'évitement (« Aller au contenu principal ») sont présents et fonctionnels **(WCAG 2.4.1 - A)**
- Plusieurs moyens permettent de trouver une page dans un ensemble de pages (par ex. recherche, plan du site ou menu de navigation) **(WCAG 2.4.5 - AA)**
- Il n'existe aucun piège au clavier (il est possible de sortir de chaque zone) **(WCAG 2.1.2 - A)**
- Les raccourcis clavier composés d'une seule touche caractère (lettre, chiffre ou ponctuation) peuvent être désactivés ou reconfigurés, ou ne sont actifs que lorsque le composant a le focus **(WCAG 2.1.4 - A)**
- La navigation ne dépend pas uniquement de la souris **(WCAG 2.1.1 - A)**
- Un indicateur de focus visible est présent sur chaque élément focalisable, y compris les composants développés sur mesure **(WCAG 2.4.7 - AA)**
- L'élément qui a le focus n'est jamais entièrement masqué par un autre contenu, comme un en-tête fixe, un bandeau de cookies ou un widget de chat **(WCAG 2.4.11 - AA)**
- L'indicateur de focus a un contraste suffisant pour être clairement perceptible **(WCAG 1.4.11 - AA)** — voir le thème 13 (Contrastes visuels) pour l'exigence chiffrée

**Critères d'acceptation :**

- ✅ 100 % des zones sont accessibles au clavier
- ✅ L'ordre de tabulation ne présente aucune incohérence
- ✅ Les liens d'évitement fonctionnent sur chaque page
- ✅ 100 % des éléments focalisables affichent un indicateur de focus visible
- ✅ L'indicateur de focus a un contraste suffisant
- ✅ Aucun composant ne supprime le focus ni ne masque entièrement l'élément qui a le focus

---

### 2. Éléments interactifs (boutons, liens, contrôles)

**Objectif :** S'assurer que chaque élément interactif est accessible et compréhensible.

- Tous les boutons sont activables au clavier (Entrée ou Espace) **(WCAG 2.1.1 - A)**
- Les boutons ont des libellés explicites et descriptifs **(WCAG 4.1.2 - A, 2.4.6 - AA)**
- Lorsqu'un composant a un libellé texte visible, son nom accessible inclut ce texte visible **(WCAG 2.5.3 - A)**
- Les liens sont clairement identifiables et leur destination est compréhensible **(WCAG 2.4.4 - A, 2.4.9 - AAA)**
- Le texte des liens est explicite (éviter « cliquez ici », « en savoir plus » sans contexte) **(WCAG 2.4.4 - A)**
- Les éléments cliquables ont un rôle ARIA approprié uniquement lorsqu'il n'est pas déjà implicite (par ex. `<a>`, `<button>`) **(WCAG 4.1.2 - A)**
- Les menus déroulants sont navigables au clavier (flèches, Entrée, Échap) **(WCAG 2.1.1 - A)**
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

- Tous les champs de formulaire ont une étiquette (`<label for='field_id'>`, ou `aria-labelledby` / `aria-label` lorsqu'un `<label>` visible ne peut pas être utilisé) **(WCAG 3.3.2 - A)**, associée au champ par le code **(WCAG 1.3.1, 4.1.2 - A)**
- Les instructions de saisie sont annoncées avant ou pendant la saisie **(WCAG 3.3.2 - A)**
- Les champs obligatoires sont clairement identifiés (visuellement et via `required` ou `aria-required`) **(WCAG 3.3.2 - A)**
- Les formats attendus sont communiqués (par ex. JJ/MM/AAAA, +41 XX XXX XX XX) **(WCAG 3.3.2 - A)**
- Les listes déroulantes (`<select>`) sont accessibles et leurs options lisibles **(WCAG 4.1.2 - A)**
- Les cases à cocher et les boutons radio ont des étiquettes associées **(WCAG 3.3.2, 1.3.1 - A)**
- Les groupes de champs sont regroupés logiquement (`<fieldset>` avec `<legend>`) **(WCAG 1.3.1 - A)**
- Les champs qui recueillent des informations sur l'utilisateur (nom, e-mail, adresse, téléphone…) exposent leur finalité avec l'attribut `autocomplete` **(WCAG 1.3.5 - AA)**
- Une information déjà saisie dans le même processus est pré-remplie ou proposée en sélection, au lieu d'être redemandée **(WCAG 3.3.7 - A)**
- Les zones de recherche sont identifiables (élément `<search>` ou repère `role="search"`) **(WCAG 1.3.1 - A)**
- La validation côté client est accessible **(WCAG 3.3.1 - A)**

**Critères d'acceptation :**

- ✅ Tous les champs sont identifiables et remplissables au clavier
- ✅ Les instructions et contraintes sont annoncées avant la saisie
- ✅ Aucun champ obligatoire n'est dépourvu d'indication

---

### 4. Messages et retours utilisateur

**Objectif :** Informer clairement l'utilisateur des actions réalisées et des éventuelles erreurs.

- Les messages d'erreur sont lisibles et associés aux champs concernés **(WCAG 3.3.1 - A, 3.3.3 - AA)**
- Les erreurs sont annoncées via des régions live (`role="alert"`) **(WCAG 4.1.3 - AA)**
- Les messages de succès sont annoncés automatiquement **(WCAG 4.1.3 - AA)**
- La validation en temps réel est perceptible sans être intrusive **(WCAG 3.3.1 - A)**
- Les alertes et notifications sont clairement annoncées **(WCAG 4.1.3 - AA)**
- Aucun changement de contexte (nouvelle fenêtre, changement de page, saut du focus) ne se produit de manière inattendue lorsqu'un élément reçoit le focus ou lorsque la valeur d'un champ change, sauf si l'utilisateur en a été averti au préalable **(WCAG 3.2.1, 3.2.2 - A)**
- Les messages d'erreur suggèrent des corrections **(WCAG 3.3.3 - AA)**
- Les messages de chargement/d'attente sont annoncés **(WCAG 4.1.3 - AA)**

**Critères d'acceptation :**

- ✅ Tous les messages d'erreur sont testés et accessibles
- ✅ Les notifications importantes ne passent pas inaperçues
- ✅ Les messages ne disparaissent pas trop vite **(WCAG 2.2.1 - A)**

---

### 5. Structure et hiérarchie du contenu (y compris titres de page et cohérence)

**Objectif :** Organiser l'information de manière logique et navigable, et assurer la cohérence structurelle et de navigation sur l'ensemble du site.

- La structure des titres est hiérarchique et cohérente (H1 → H2 → H3) **(WCAG 1.3.1 - A, 2.4.6 - AA)**
- Chaque page a un titre H1 unique et descriptif. **[Inférence]** Le document source rattachait cette exigence au critère WCAG 2.4.2 ; or le critère 2.4.2 porte formellement sur l'élément `<title>` de la page (voir le point dédié ci-dessous), et non sur le H1. Un H1 unique et descriptif sert le même objectif de navigation en tant que bonne pratique, mais n'est pas en soi l'exigence littérale du critère 2.4.2.
- Les titres reflètent fidèlement la structure du contenu **(WCAG 2.4.6 - AA)**
- Les listes sont balisées sémantiquement (`<ul>`, `<ol>`, `<li>`) et étiquetées **(WCAG 1.3.1 - A)**
- Les tableaux de données ont des en-têtes appropriés (`<th>`, `scope`) **(WCAG 1.3.1 - A)**
- Les tableaux complexes utilisent `id` et `headers` pour l'association **(WCAG 1.3.1 - A)**
- Les régions de repère sont utilisées correctement (`<main>`, `<header>`, `<footer>`, `<nav>`, `<aside>`, etc.) **(WCAG 1.3.1 - A)**
- Le contenu suit un ordre de lecture logique **(WCAG 1.3.2 - A)**
- Les citations sont balisées avec `<blockquote>` **(WCAG 1.3.1 - A)**
- Les définitions utilisent `<dl>`, `<dt>`, `<dd>` **(WCAG 1.3.1 - A)**
- Chaque page a un élément `<title>` descriptif **(WCAG 2.4.2 - A)**
- Les menus de navigation sont placés de manière cohérente d'une page à l'autre **(WCAG 3.2.3 - AA)**
- Une même fonctionnalité porte le même libellé partout où elle apparaît **(WCAG 3.2.4 - AA)**
- Les mécanismes d'aide répétés sur plusieurs pages (coordonnées, formulaire de contact, chat, FAQ) apparaissent dans le même ordre relatif **(WCAG 3.2.6 - A)**

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
- Les vidéos pré-enregistrées ont des sous-titres synchronisés **(WCAG 1.2.2 - A)**
- Les vidéos en direct ont des sous-titres synchronisés **(WCAG 1.2.4 - AA)**
- Les vidéos pré-enregistrées ont une audio-description ou une transcription textuelle **(WCAG 1.2.3 - A)**
- Les vidéos pré-enregistrées ont une audio-description des informations visuelles importantes **(WCAG 1.2.5 - AA)**
- Les contenus audio ont des transcriptions **(WCAG 1.2.1 - A)**
- Les animations peuvent être mises en pause ou désactivées **(WCAG 2.2.2 - A)**
- Les graphiques interactifs ont des alternatives accessibles **(WCAG 1.1.1 - A)**
- Les infographies ont des descriptions textuelles complètes **(WCAG 1.1.1 - A)**
- Les CAPTCHA ont des alternatives audio ou logiques **(WCAG 1.1.1 - A)**

**Critères d'acceptation :**

- ✅ Aucune information ne dépend uniquement d'un contenu visuel
- ✅ Toutes les vidéos critiques ont des sous-titres
- ✅ Les alternatives textuelles sont pertinentes et suffisantes

---

### 7. Contenu dynamique et interactions avancées

**Objectif :** Gérer de manière accessible les mises à jour dynamiques et les interactions complexes.

- Les mises à jour dynamiques du contenu sont annoncées (`aria-live`, `role="status"`) **(WCAG 4.1.3 - AA)**
- Les modales/popups sont identifiées (`role="dialog"` ou `role="alertdialog"`) **(WCAG 4.1.2 - A)**
- Le focus est automatiquement déplacé dans les modales à leur ouverture **(WCAG 2.4.3 - A)**
- Le focus revient sur l'élément déclencheur à la fermeture des modales **(WCAG 2.4.3 - A)**
- Les modales peuvent être fermées au clavier (Échap) **(WCAG 2.1.1, 2.1.2 - A)**
- Les accordéons indiquent leur état (ouvert/fermé) via `aria-expanded` **(WCAG 4.1.2 - A)**
- Les onglets sont navigables au clavier (flèches gauche/droite) **(WCAG 2.1.1 - A)**
- Les onglets indiquent l'onglet actif via `aria-selected` **(WCAG 4.1.2 - A)**
- Les carrousels peuvent être mis en pause **(WCAG 2.2.2 - A)**
- Les carrousels sont contrôlables au clavier **(WCAG 2.1.1 - A)**
- Les infobulles sont accessibles au clavier et au focus, peuvent être masquées et restent visibles lorsqu'elles sont survolées **(WCAG 1.4.13 - AA)**
- Les contenus chargés en AJAX sont annoncés **(WCAG 4.1.3 - AA)**

**Critères d'acceptation :**

- ✅ Toutes les modales sont identifiées et le focus est correctement géré
- ✅ Les mises à jour critiques sont annoncées automatiquement
- ✅ Aucun contenu dynamique n'est invisible pour le lecteur d'écran

---

### 8. Lisibilité et compréhension

**Objectif :** S'assurer que le contenu est clair et compréhensible, indépendamment de présupposés visuels ou linguistiques.

- Toute information visuelle a un équivalent textuel **(WCAG 1.1.1 - A)**
- La langue principale de la page est correctement définie dans le code **(WCAG 3.1.1 - A)**
- Le langage utilisé est clair et adapté au public cible **(WCAG 3.1.5 - AAA)**
- Les abréviations et acronymes sont expliqués (`<abbr title="">`) **(WCAG 3.1.4 - AAA)**
- Les instructions ne reposent pas uniquement sur des caractéristiques visuelles (couleur, forme, position) **(WCAG 1.3.3 - A, 1.4.1 - A)**
- Les changements de langue dans le contenu sont indiqués dans le code (attribut `lang`) **(WCAG 3.1.2 - AA)**
- Les termes techniques sont définis ou expliqués **(WCAG 3.1.3 - AAA)**
- Les contenus complexes sont accompagnés d'explications **(WCAG 3.1.5 - AAA)**

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
- La connexion n'exige pas de test de fonction cognitive (mémoriser ou recopier un mot de passe, résoudre une énigme) sans alternative — par exemple, les gestionnaires de mots de passe et le copier-coller ne sont pas bloqués **(WCAG 3.3.8 - AA)**
- L'inscription / la création de compte est réalisable
- Les transactions importantes peuvent être menées à bien (achat, paiement, soumission)
- Les soumissions ayant des conséquences juridiques ou financières peuvent être relues, corrigées ou confirmées avant leur finalisation **(WCAG 3.3.4 - AA)**
- La recherche est utilisable et les résultats sont accessibles
- Les filtres et le tri sont accessibles au clavier
- La pagination est navigable au clavier
- Les actions de téléchargement de fichiers sont réalisables
- Les actions de dépôt (upload) de fichiers sont accessibles
- Les tableaux de bord et les statistiques sont compréhensibles
- La déconnexion est accessible

En dehors des deux points référencés ci-dessus, cette section ne constitue pas en soi un critère WCAG. Elle vérifie la conformité opérationnelle des critères A et AA sur les parcours métier — principalement les critères d'accessibilité au clavier 2.1.1 et 2.1.2, et l'exigence de conformité des processus complets (WCAG 2.2, section 5.2.3).

**Critères d'acceptation :**

- ✅ Tous les parcours critiques identifiés sont testés de bout en bout
- ✅ Aucun parcours ne présente de blocage majeur
- ✅ Les fonctionnalités métier principales sont validées

---

### 10. Gestion du temps et contraintes temporelles

**Objectif :** Éviter que des limites de temps ne bloquent la réalisation des tâches.

- Les limites de temps peuvent être désactivées ou ajustées par l'utilisateur **(WCAG 2.2.1 - A)**
- Les sessions peuvent être prolongées ou sauvegardées avant leur expiration **(WCAG 2.2.1 - A)**
- Les contenus en mouvement ou animés peuvent être mis en pause ou désactivés **(WCAG 2.2.2 - A)**
- Les mises à jour automatiques (par ex. actualisation de la page) peuvent être contrôlées par l'utilisateur **(WCAG 2.2.4 - AAA)**
- Les interruptions (par ex. pop-ups) peuvent être reportées ou désactivées **(WCAG 2.2.4 - AAA)**
- Le temps accordé pour les actions de l'utilisateur (par ex. soumission d'un formulaire) est suffisamment long ou ajustable **(WCAG 2.2.1 - A)**

**Critères d'acceptation :**

- ✅ Aucune limite de temps ne bloque la réalisation d'une tâche
- ✅ Les avertissements d'expiration sont accessibles
- ✅ Les animations problématiques peuvent être contrôlées

---

### 11. Zoom et redimensionnement

**Objectif :** Assurer l'utilisabilité avec des niveaux de zoom élevés et de petites largeurs de fenêtre.

- Le contenu est utilisable à 200 % de zoom **(WCAG 1.4.4 - AA)**
- Le contenu est utilisable à 400 % de zoom ou avec une largeur de fenêtre de 320 px **(WCAG 1.4.10 - AA)**
- Aucun défilement horizontal n'est nécessaire pour lire le contenu principal **(WCAG 1.4.10 - AA)**
- Aucun texte n'est tronqué ni ne se chevauche
- Les tableaux larges ont une alternative accessible

**Critères d'acceptation :**

- ✅ 100 % du contenu et des fonctionnalités restent accessibles à 200 %
- ✅ À 400 %, aucune lecture ne nécessite de défilement horizontal
- ✅ Aucun composant critique ne devient inutilisable
- ✅ Aucun contenu n'est masqué ou coupé

---

### 12. Espacement du texte

**Objectif :** Assurer la robustesse face aux adaptations de lisibilité.

Application manuelle des valeurs suivantes :

- `line-height: 1.5`
- `letter-spacing: 0.12em`
- `word-spacing: 0.16em`
- `paragraph spacing: 2em`

Vérifications **(WCAG 1.4.12 - AA)** :

- Aucun chevauchement ne se produit
- Aucun contenu n'est perdu
- Les composants restent utilisables

**Critères d'acceptation :**

- ✅ L'application reste entièrement fonctionnelle
- ✅ Aucun texte ne se chevauche
- ✅ Aucun défilement horizontal supplémentaire n'est généré

---

### 13. Contrastes visuels

**Objectif :** Assurer la perceptibilité du contenu et des composants.

- Contraste du texte normal ≥ 4,5:1 **(WCAG 1.4.3 - AA)**
- Contraste du texte de grande taille ≥ 3:1 **(WCAG 1.4.3 - AA)**
- Contraste des composants d'interface (bordures de champs, icônes informatives, boutons) ≥ 3:1 **(WCAG 1.4.11 - AA)**
- Les indicateurs de focus respectent le même ratio de contraste non textuel que les autres composants d'interface **(WCAG 1.4.11 - AA)** — voir le thème 1 pour l'exigence d'un focus visible en permanence
- Les états (erreur, actif, sélectionné) ne sont pas transmis uniquement par la couleur **(WCAG 1.4.1 - A)**

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
- Aucune interaction n'est bloquée en fonction de l'orientation **(WCAG 1.3.4 - AA)**

**Critères d'acceptation :**

- ✅ Toutes les fonctionnalités critiques sont accessibles dans les deux orientations
- ✅ Aucun contenu essentiel n'est masqué

---

### 15. Interactions tactiles et au pointeur

**Objectif :** Assurer l'accessibilité pour les utilisateurs d'écrans tactiles et ceux ayant des limitations motrices.

- Les gestes complexes (multipoints ou basés sur un tracé) ont une alternative simple à pointeur unique **(WCAG 2.5.1 - A)**
- Les actions ne sont pas déclenchées uniquement au « toucher » (touch down) **(WCAG 2.5.2 - A)**
- Les actions critiques peuvent être annulées **(WCAG 2.5.2 - A)**
- Chaque action de glisser-déposer a une alternative à pointeur unique sans glisser (par ex. des boutons ou un menu) **(WCAG 2.5.7 - AA)**

**Critères d'acceptation :**

- ✅ 100 % des gestes complexes et des mouvements de glisser ont une alternative
- ✅ Aucune action irréversible n'est déclenchée accidentellement
- ✅ Les actions critiques peuvent être confirmées

---

### 16. Taille des cibles

**Objectif :** Réduire les erreurs d'activation.

- Les cibles mesurent au moins 24 × 24 px CSS, ou sont espacées de sorte qu'un cercle de 24 px centré sur chaque cible ne chevauche pas une autre cible **(WCAG 2.5.8 - AA)**
- Les cibles critiques mesurent au moins 44 × 44 px CSS **(WCAG 2.5.5 - AAA)**
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

Cette section organise et résume les exigences des WCAG 2.2 en trois catégories distinctes :

- **Critères fondamentaux**, indispensables pour éliminer les blocages majeurs : niveau A, plus quelques critères de niveau AA jugés critiques ;
- **Critères légaux**, correspondant au niveau AA, le niveau exigé par les cadres juridiques ;
- **Critères d'excellence**, alignés sur le niveau AAA, plus des bonnes pratiques qui ne sont pas des exigences WCAG, pour améliorer le confort des utilisateurs.

Chaque catégorie définit un palier de conformité, des exigences minimales qui évitent les blocages d'accès jusqu'aux bonnes pratiques pour une accessibilité optimale.

Pour chaque critère, un tableau détaillé présente son libellé précis, une description claire de l'exigence et de son impact sur l'expérience utilisateur, le critère de succès WCAG et son niveau, une méthode de vérification pas à pas et la référence du test Xray correspondant lorsqu'il existe déjà. **Les lignes ont été triées par niveau WCAG : chaque ligne conserve son cas de test Xray et son étape d'origine, si bien qu'un même cas de test Xray peut apparaître dans plusieurs tableaux. Les lignes sans cas de test Xray sont laissées vides et seront complétées lorsque de nouveaux cas de test auront été créés.**

L'objectif est de donner aux équipes une base de référence unifiée pour comprendre les attentes associées à chaque niveau de conformité, prioriser les corrections selon les contraintes du projet et mesurer objectivement les progrès en accessibilité.

### Critères fondamentaux (niveau A — éliminer les blocages)

Cette section regroupe les exigences minimales WCAG de niveau A, ainsi que certains critères de niveau AA jugés critiques pour éviter les **blocages** d'accès (marqués **AA** dans la colonne WCAG). Ces critères garantissent un accès de base à l'information et aux fonctionnalités, sans lequel certains utilisateurs en situation de handicap ne pourraient tout simplement pas utiliser le service.

| Critère | Description | WCAG | Comment vérifier | Test Xray | Étape(s) |
| --- | --- | --- | --- | --- | --- |
| **Fonctionnalités critiques accessibles** | 100 % des parcours essentiels (connexion, transactions, recherche, activation/désactivation de services) sont réalisables au clavier avec un lecteur d'écran | 2.1.1, 2.1.2 (A) | Tester tous les parcours métier majeurs de bout en bout sans souris | AFCXRAY-12125 | Étape 1 |
| **Navigation complète au clavier** | Toutes les zones et fonctionnalités sont accessibles sans souris (Tab, Maj+Tab, Entrée, Espace, flèches) | 2.1.1 (A) | Parcourir toute l'application uniquement au clavier | AFCXRAY-12125 | Étape 2 |
| **Gestion du focus** | Le focus clavier suit un ordre logique, sans sauts ni pièges, et est toujours visible | 2.4.3, 2.1.2 (A) ; 2.4.7 (AA) | Vérifier visuellement le focus et confirmer qu'il est possible de sortir de chaque zone | AFCXRAY-12125 | Étape 3 |
| **Messages d'erreur accessibles** | Tous les messages d'erreur sont lisibles par le lecteur d'écran, annoncés automatiquement et associés aux champs concernés | 3.3.1 (A) ; 4.1.3 (AA) | Déclencher volontairement des erreurs et vérifier leur annonce | AFCXRAY-12125 | Étape 4 |
| **Formulaires identifiables** | Tous les champs ont des étiquettes explicites (`<label for='field_id'>`, ou `aria-labelledby` / `aria-label`) et les champs obligatoires sont identifiés | 3.3.2, 1.3.1, 4.1.2 (A) | Tester tous les formulaires avec le lecteur d'écran | AFCXRAY-12125 | Étape 5 |
| **Modales/popups identifiées** | Les fenêtres modales sont annoncées comme telles (`role="dialog"`), avec un focus géré à l'ouverture et à la fermeture | 4.1.2, 2.4.3 (A) | Ouvrir toutes les modales et vérifier l'annonce et la gestion du focus | AFCXRAY-12125 | Étape 6 |
| **Alternatives textuelles** | Toutes les images informatives ont des attributs `alt` pertinents ; les images décoratives sont masquées | 1.1.1 (A) | Parcourir l'application et écouter toutes les descriptions d'images | AFCXRAY-12125 | Étape 7 |
| **Structure de titres cohérente** | La hiérarchie H1–H6 reflète la structure du contenu sur chaque page. Ne sauter aucun niveau et avoir un seul H1 par page sont des bonnes pratiques | 1.3.1 (A) ; 2.4.6 (AA) | Utiliser la navigation par titres du lecteur d'écran sur chaque page | AFCXRAY-12125 | Étape 8 |
| **Contexte des actions** | Les actions (boutons, liens) fournissent assez de contexte pour comprendre leur effet sans information visuelle | 2.4.4, 4.1.2 (A) | Tester tous les boutons/liens et vérifier que leur fonction est claire | AFCXRAY-12125 | Étape 9 |
| **Ordre de présentation logique** | L'information est présentée dans un ordre qui a du sens (contexte avant les détails, statut avant les coordonnées) | 1.3.2 (A) | Écouter l'annonce complète de chaque section et vérifier la cohérence | AFCXRAY-12126 | Étape 1 |
| **Régions de repère** | Utilisation correcte de `<main>`, `<header>`, `<footer>`, `<nav>`, ou de `role="main"`, `role="navigation"`, `role="search"`, etc. lorsque les éléments natifs ne sont pas utilisés | 1.3.1 (A) | Vérifier la structure des repères avec les outils de développement et la navigation par repères du lecteur d'écran | AFCXRAY-12126 | Étape 3 |
| **États des composants** | Les états (ouvert/fermé, coché/décoché, activé/désactivé) sont correctement annoncés | 4.1.2 (A) | Tester tous les composants interactifs et leurs différents états | AFCXRAY-12126 | Étape 5 |
| **Instructions de saisie** | Les formats et contraintes attendus sont annoncés avant ou pendant la saisie | 3.3.2 (A) | Tester tous les champs avec contraintes (date, téléphone, e-mail, etc.) | AFCXRAY-12126 | Étape 6 |
| **Retour du focus après une action** | Après une action (fermeture d'une modale, soumission d'un formulaire), le focus revient à un emplacement logique | 2.4.3 (A) | Effectuer des actions et vérifier où arrive le focus | AFCXRAY-12126 | Étape 7 |
| **Tableaux de données** | Les tableaux ont des en-têtes appropriés et sont compréhensibles pour le lecteur d'écran | 1.3.1 (A) | Parcourir tous les tableaux en mode tableau du lecteur d'écran | AFCXRAY-12126 | Étape 8 |
| **Liens d'évitement** | Un lien « Aller au contenu principal » (ou des repères et des titres) permet de contourner les blocs répétés | 2.4.1 (A) | Appuyer sur Tab dès l'arrivée sur la page | AFCXRAY-12127 | Étape 1 |
| **Raccourcis clavier utilisant des caractères** | Les raccourcis à une seule touche caractère peuvent être désactivés ou reconfigurés, ou ne sont actifs qu'au focus | 2.1.4 (A) | Tester les raccourcis et vérifier qu'ils peuvent être désactivés ou reconfigurés | AFCXRAY-12127 | Étape 2 |
| **Sous-titres des vidéos** | Des sous-titres synchronisés sont présents pour tous les contenus vidéo pré-enregistrés | 1.2.2 (A) | Regarder toutes les vidéos avec les sous-titres activés | AFCXRAY-12127 | Étape 3 |
| **Transcriptions audio** | Les contenus audio pré-enregistrés ont des transcriptions textuelles disponibles | 1.2.1 (A) | Vérifier la disponibilité des transcriptions | AFCXRAY-12127 | Étape 4 |
| **Contrôle des animations** | Possibilité de mettre en pause, d'arrêter ou de masquer les animations automatiques | 2.2.2 (A) | Tester les carrousels et les animations automatiques | AFCXRAY-12127 | Étape 5 |
| **Descriptions détaillées** | Les graphiques complexes ont des descriptions longues (`aria-describedby` ou liens vers des descriptions) | 1.1.1 (A) | Parcourir tous les graphiques et schémas | AFCXRAY-12127 | Étape 6 |
| **Titres de page descriptifs** | Chaque page a un élément `<title>` descriptif | 2.4.2 (A) | Inspecter l'élément `<title>` du DOM sur chaque page | | |
| **Utilisation de la couleur** | L'information et les états ne sont pas transmis uniquement par la couleur | 1.4.1 (A) | Effectuer une inspection visuelle des états et des instructions | | |
| **Gestes de pointeur** | Les gestes complexes ont une alternative simple à pointeur unique | 2.5.1 (A) | Effectuer un test tactile de tous les gestes | | |
| **Annulation du pointeur** | Les actions critiques peuvent être annulées et ne sont pas déclenchées uniquement au « toucher » (touch down) | 2.5.2 (A) | Tester avec la souris et au toucher | | |
| **Nom/Rôle/Valeur** | Les composants personnalisés exposent un nom accessible, un rôle et une valeur/un état corrects via le DOM | 4.1.2 (A) | Inspecter les attributs DOM/ARIA des composants personnalisés avec les DevTools du navigateur | | |
| **Libellé dans le nom** | Lorsqu'un composant a un libellé texte visible, son nom accessible inclut programmatiquement ce texte visible | 2.5.3 (A) | Comparer le libellé visible de chaque composant avec son nom accessible calculé dans les DevTools | | |
| **Aide cohérente** | Les mécanismes d'aide répétés sur plusieurs pages apparaissent dans le même ordre relatif | 3.2.6 (A) | Parcourir plusieurs pages et comparer la position des mécanismes d'aide | | |
| **Saisie redondante** | Une information déjà saisie dans le même processus n'est pas redemandée, ou est pré-remplie ou sélectionnable | 3.3.7 (A) | Parcourir les processus en plusieurs étapes et noter toute donnée demandée deux fois | | |
| **Reflow à 400 % de zoom** | Le contenu reste utilisable à 400 % de zoom ou avec une largeur de fenêtre de 320 px, sans défilement horizontal nécessaire pour lire le contenu principal | 1.4.10 (AA) | Régler le zoom à 400 % (ou la fenêtre à 320 px) et confirmer qu'aucun défilement horizontal n'est nécessaire et qu'aucun contenu n'est perdu | | |
| **Contraste textuel et non textuel** | Les ratios de contraste du texte et des composants d'interface respectent les seuils WCAG — 4,5:1 pour le texte normal, 3:1 pour le texte de grande taille et les composants d'interface | 1.4.3, 1.4.11 (AA) | Mesurer les ratios de contraste avec un outil de vérification du contraste | | |
| **Focus visible** | Un indicateur de focus est toujours visible et suffisamment contrasté sur chaque élément focalisable | 2.4.7, 1.4.11 (AA) | Parcourir toute l'interface au clavier et confirmer que l'indicateur est toujours visible | | |
| **Redimensionnement du texte à 200 %** | Le contenu reste utilisable et aucun contenu n'est perdu à 200 % de zoom | 1.4.4 (AA) | Régler le zoom du navigateur à 200 % et vérifier que rien n'est perdu ni cassé | | |
| **Espacement du texte** | L'application de valeurs augmentées d'interligne, d'espacement des lettres, des mots et des paragraphes ne provoque ni chevauchement ni perte de contenu | 1.4.12 (AA) | Appliquer les valeurs d'espacement indiquées via le CSS des DevTools et rechercher les chevauchements | | |

---

### Critères légaux (niveau AA — conformité exigée)

Cette section résume les exigences de niveau AA, qui constituent le niveau de référence légal pour l'accessibilité numérique (EN 301 549 pour les directives de l'UE, RGAA en France, eCH-0059 en Suisse). Leur application est requise pour assurer la conformité réglementaire et une expérience utilisateur fluide et autonome pour les personnes en situation de handicap. La conformité au niveau AA exige aussi tous les critères de niveau A du tableau précédent.

Ces critères vont au-delà des exigences de base du niveau A en couvrant des aspects essentiels tels que la navigation cohérente, la finalité des champs, les messages d'état, la visibilité du focus et la taille des cibles.

| Critère | Description | WCAG | Comment vérifier | Test Xray | Étape(s) |
| --- | --- | --- | --- | --- | --- |
| **Annonces dynamiques** | Les mises à jour de contenu sont annoncées via `aria-live` ou `role="alert"` sans interrompre la lecture ni déplacer le focus | 4.1.3 (AA) | Déclencher des mises à jour et vérifier qu'elles sont annoncées | AFCXRAY-12126 | Étape 4 |
| **Prévention des erreurs (juridiques, financières, données)** | Pour les soumissions ayant des conséquences juridiques ou financières, l'utilisateur peut annuler, vérifier ou confirmer la soumission avant sa finalisation | 3.3.4 (AA) | Déclencher une soumission juridique/financière/de données et vérifier qu'une étape de relecture, de correction ou de confirmation est proposée avant la finalisation | | |
| **Orientation** | L'interface fonctionne correctement en orientation portrait et paysage | 1.3.4 (AA) | Tester sur un appareil mobile ou un simulateur dans les deux orientations | | |
| **Navigation cohérente** | Les menus de navigation sont placés de manière cohérente d'une page à l'autre | 3.2.3 (AA) | Parcourir plusieurs pages et comparer l'emplacement des menus | | |
| **Plusieurs moyens de trouver le contenu** | Plusieurs moyens permettent de trouver une page dans un ensemble de pages, par ex. une recherche plus un plan du site ou un menu de navigation | 2.4.5 (AA) | Vérifier la présence d'au moins deux moyens d'orientation indépendants (recherche, plan du site, menu, fil d'Ariane) | | |
| **Identification cohérente** | Une même fonctionnalité porte le même libellé partout où elle apparaît | 3.2.4 (AA) | Vérifier les libellés de l'interface sur les composants équivalents | | |
| **Finalité de la saisie** | Les champs qui recueillent des informations sur l'utilisateur exposent leur finalité avec `autocomplete` | 1.3.5 (AA) | Inspecter les valeurs `autocomplete` des champs de données personnelles dans les DevTools | | |
| **Focus non masqué** | L'élément qui a le focus n'est jamais entièrement masqué par des en-têtes fixes, des bandeaux ou des superpositions | 2.4.11 (AA) | Parcourir la page à la touche Tab avec les éléments fixes et les bandeaux affichés | | |
| **Mouvements de glisser** | Chaque action de glisser-déposer peut aussi être réalisée avec un pointeur unique sans glisser | 2.5.7 (AA) | Identifier chaque interaction de glisser et rechercher une alternative par clic/toucher | | |
| **Taille des cibles (minimum)** | Les cibles de pointeur mesurent au moins 24 × 24 px CSS ou sont suffisamment espacées | 2.5.8 (AA) | Mesurer les petites cibles (icônes, liens dans des listes) dans les DevTools | | |
| **Authentification accessible** | La connexion ne repose pas sur un test de fonction cognitive sans alternative ; les gestionnaires de mots de passe et le copier-coller fonctionnent | 3.3.8 (AA) | Se connecter avec un gestionnaire de mots de passe et par copier-coller | | |

---

### Critères d'excellence (niveau AAA et bonnes pratiques — optimisation)

Cette section présente les exigences de niveau AAA et des bonnes pratiques qui ne sont pas des exigences WCAG, qui visent une accessibilité optimale et une expérience utilisateur exceptionnelle. Contrairement aux niveaux A et AA, ces critères ne sont pas imposés par la réglementation, mais leur mise en œuvre est fortement recommandée pour dépasser les standards légaux et répondre aux besoins les plus exigeants.

Bien que leur mise en œuvre puisse représenter un défi technique ou organisationnel, ces critères permettent d'atteindre un niveau d'inclusion remarquable, garantissant un confort d'utilisation maximal pour tous, y compris pour les utilisateurs ayant des besoins spécifiques ou complexes. Ils marquent un engagement proactif en faveur d'une accessibilité exemplaire.

| Critère | Description | WCAG | Comment vérifier | Test Xray | Étape(s) |
| --- | --- | --- | --- | --- | --- |
| **Indicateurs de progression** | Les processus en plusieurs étapes indiquent clairement l'étape en cours | 2.4.8 (AAA) | Parcourir les workflows et vérifier l'annonce de la progression | AFCXRAY-12127 | Étape 7 |
| **Aide contextuelle** | Une aide et des infobulles accessibles sont disponibles pour les fonctionnalités complexes | 3.3.5 (AAA) | Tester l'accessibilité des infobulles et des bulles d'aide | AFCXRAY-12127 | Étape 8 |
| **Taille des cibles (amélioré)** | Les cibles interactives mesurent au moins 44 × 44 px CSS | 2.5.5 (AAA) | Inspecter les éléments interactifs critiques | | |
| **Lisibilité générale** | L'interface est globalement claire et facile à lire | 3.1.5 (AAA, apparenté) | Effectuer une revue visuelle générale | | |
| **Liens externes identifiés** | Les liens qui ouvrent un nouvel onglet ou un site externe sont annoncés comme tels | — (bonne pratique, pas une exigence WCAG) | Tester tous les liens et vérifier que le contexte est clair | AFCXRAY-12126 | Étape 2 |

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
