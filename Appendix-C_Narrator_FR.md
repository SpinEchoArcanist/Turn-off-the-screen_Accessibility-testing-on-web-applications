# Annexe C — Narrateur Windows : guide de test de l'accessibilité web

## Objectif

Ce guide s'adresse aux testeurs d'accessibilité qui n'ont jamais utilisé le Narrateur Windows. Il leur permet de réaliser des tests d'accessibilité web avec le Narrateur sans documentation complémentaire.

Il porte exclusivement sur l'utilisation du Narrateur pour naviguer dans les applications web et les inspecter. Il n'explique **pas** les concepts d'accessibilité, les exigences WCAG ni les méthodologies de test.

Le guide couvre :

- Le démarrage et la configuration du Narrateur
- La navigation dans les pages web et la lecture de leur contenu
- L'utilisation du mode Analyse
- Le déplacement entre les éléments web courants (titres, liens, boutons, contrôles de formulaire, points de repère)
- La vérification du focus clavier
- Le test d'un formulaire pas à pas
- La compréhension des annonces du Narrateur

[Complete guide to Narrator \| Microsoft Support](https://support.microsoft.com/en-us/accessibility/windows/narrator/complete-guide-to-narrator)

---

## 1. Démarrer et arrêter le Narrateur

### Activer/désactiver le Narrateur

```text
Ctrl + Windows + Entrée
```

Active ou désactive le Narrateur.

---

## 2. La touche Narrateur

Par défaut, ces deux touches servent de touche de modification du Narrateur :

```text
Verr. Maj
```

```text
Inser
```

Dans tout ce guide :

```text
Narrateur = Verr. Maj
```

Exemple :

```text
Narrateur + T
```

signifie

```text
Verr. Maj + T
```

---

## 3. Vérifier que le Narrateur fonctionne

Après le démarrage du Narrateur :

- L'élément qui a le focus est annoncé.
- La navigation au clavier est énoncée.
- Les rôles et états accessibles sont annoncés.

Exemples d'annonces :

```text
Accueil lien

Rechercher bouton

Nom modifier

Case à cocher activée
```

---

## 4. Commandes fondamentales

### Lire l'élément actuel

```text
Narrateur + Tab
```

Annonce l'élément qui a actuellement le focus clavier. Très utile pendant les tests.

---

### Lire le titre de la fenêtre actuelle

```text
Narrateur + T
```

Utile après une navigation entre pages ou à l'ouverture de boîtes de dialogue.

---

### Lire l'heure et la date actuelles

```text
Narrateur + F12
```

---

### Afficher la liste des commandes du Narrateur

```text
Narrateur + F1
```

---

## 5. Mode Analyse

Le mode Analyse est le principal mode de navigation pour parcourir les pages web.

Activer/désactiver le mode Analyse :

```text
Narrateur + Barre d'espace
```

Lorsque le mode Analyse est activé :

- Les flèches haut et bas parcourent le contenu de la page.
- La navigation par lettre unique est disponible.
- Entrée ou Barre d'espace active l'élément courant.
- La navigation se comporte comme celle d'un lecteur d'écran traditionnel.

Toujours vérifier que le mode Analyse est activé lors du test d'une page web.

---

## 6. Lire le contenu de la page

### Lancer la lecture du document

```text
Narrateur + Ctrl + R
```

ou

```text
Narrateur + Flèche bas
```

Lance la lecture continue du document. Microsoft nomme cette commande « Start reading document ».

---

### Lire à partir du curseur

```text
Narrateur + R
```

---

### Arrêter la lecture

```text
Ctrl
```

Arrête immédiatement la parole.

---

## 7. Navigation de base (mode Analyse)

Passer au texte ou à l'élément suivant :

```text
Flèche bas
```

Passer au texte ou à l'élément précédent :

```text
Flèche haut
```

---

## 8. Navigation rapide (mode Analyse)

Ces commandes ne fonctionnent que lorsque le mode Analyse est activé.

---

### Titres

Titre suivant :

```text
H
```

Titre précédent :

```text
Maj + H
```

Le Narrateur annonce le texte du titre et son niveau.

Exemple :

```text
Titre de niveau 2
Informations personnelles
```

Vérifications :

- La hiérarchie des titres H1–H6 reflète la structure de la page
- Aucun niveau de titre n'est sauté (bonne pratique)

---

### Navigation par niveau de titre

Titre de niveau 1 suivant :

```text
1
```

Titre de niveau 1 précédent :

```text
Maj + 1
```

De même :

```text
2 / Maj + 2
3 / Maj + 3
4 / Maj + 4
5 / Maj + 5
6 / Maj + 6
```

Ces commandes sont utiles pour passer rapidement en revue la hiérarchie des titres.

---

### Liens

Lien suivant :

```text
K
```

Lien précédent :

```text
Maj + K
```

Le Narrateur annonce si un lien a déjà été visité.

Exemple :

```text
Lien visité
```

ou

```text
Lien
```

Vérifications :

- Chaque lien a un nom accessible
- L'intitulé du lien est pertinent

---

### Boutons

Bouton suivant :

```text
B
```

Bouton précédent :

```text
Maj + B
```

Le Narrateur annonce le nom du bouton et son état le cas échéant.

Vérifications :

- Le nom est annoncé
- L'état est annoncé

---

### Contrôles de formulaire

Contrôle de formulaire suivant :

```text
F
```

Contrôle de formulaire précédent :

```text
Maj + F
```

Cette commande parcourt tous les contrôles de formulaire, pas seulement les champs de texte.

Le Narrateur annonce généralement :

- L'étiquette
- Le type de contrôle
- L'état obligatoire
- La valeur actuelle
- L'état invalide (le cas échéant)

Exemple :

```text
Prénom
Modifier
Obligatoire
```

Vérifications :

- L'étiquette est lue
- L'état obligatoire est annoncé
- L'état invalide est annoncé

---

### Zones de liste déroulante

Zone de liste déroulante suivante :

```text
C
```

Zone de liste déroulante précédente :

```text
Maj + C
```

---

### Boutons radio

Bouton radio suivant :

```text
R
```

Bouton radio précédent :

```text
Maj + R
```

---

### Cases à cocher

Case à cocher suivante :

```text
X
```

Case à cocher précédente :

```text
Maj + X
```

---

### Graphiques

Graphique suivant :

```text
G
```

Graphique précédent :

```text
Maj + G
```

Utile pour vérifier les alternatives textuelles.

---

### Listes

Liste suivante :

```text
L
```

Liste précédente :

```text
Maj + L
```

---

### Éléments de liste

Élément de liste suivant :

```text
I
```

Élément de liste précédent :

```text
Maj + I
```

---

### Tableaux

Tableau suivant :

```text
T
```

Tableau précédent :

```text
Maj + T
```

---

### Points de repère

Point de repère suivant :

```text
D
```

Point de repère précédent :

```text
Maj + D
```

La navigation par points de repère est fondamentale pour tester selon les WCAG. Elle permet de vérifier la présence des régions banner, navigation, main, complementary, contentinfo et search.

Exemples :

```text
Bannière

Navigation

Principal

Recherche

Informations sur le contenu
```

---

## 9. Listes des titres, des liens et des points de repère

Ouvrir une liste des éléments de la page :

```text
Narrateur + F5
```

Liste des points de repère.

```text
Narrateur + F6
```

Liste des titres.

```text
Narrateur + F7
```

Liste des liens.

Ces listes donnent une vue d'ensemble rapide de la structure de la page et permettent d'accéder directement à un élément. Elles font partie des outils de navigation les plus utiles pour les tests d'accessibilité.

---

## 10. Navigation par le focus clavier

Déplacer le focus vers l'avant :

```text
Tab
```

Déplacer le focus vers l'arrière :

```text
Maj + Tab
```

Pour identifier l'élément qui a le focus après chaque déplacement :

```text
Narrateur + Tab
```

Points à vérifier :

- Ordre du focus logique
- Absence de piège clavier
- Visibilité du focus

---

## 11. Activer des contrôles

Lorsque le focus est sur un bouton, un lien ou une case à cocher, l'activer avec :

```text
Entrée
```

ou

```text
Barre d'espace
```

selon le type de contrôle.

---

## 12. Tester un formulaire (pas à pas)

Méthode recommandée.

### Étape 1

Naviguer avec :

```text
Tab
```

Vérifier :

- L'ordre du focus
- La cohérence du parcours dans le formulaire

---

### Étape 2

Sur chaque champ, vérifier que le Narrateur annonce :

```text
Étiquette
Type du champ
Obligatoire (le cas échéant)
Valeur
```

Exemple attendu :

```text
Prénom
Modifier
Obligatoire
```

---

### Étape 3

Déclencher les erreurs (soumettre des valeurs vides ou invalides).

Vérifier :

- Les messages d'erreur sont annoncés
- Les états invalides sont annoncés

---

### Étape 4

Soumettre le formulaire.

Vérifier que le focus arrive sur :

- Le titre principal de la page obtenue
- Ou le premier élément pertinent (par exemple la première erreur ou le message de confirmation)

Jamais sur un élément aléatoire.

---

## 13. Annonces courantes du Narrateur

Pendant les tests, le Narrateur peut annoncer des informations telles que :

### Titre

```text
Titre de niveau 1
Titre de niveau 2
```

---

### Liens

```text
Lien

Lien visité
```

---

### Boutons

```text
Bouton
```

---

### Contrôles de formulaire

```text
Modifier

Obligatoire

Entrée non valide
```

---

### Contrôles extensibles

```text
Développé

Réduit
```

---

### Sélection

```text
Sélectionné

Non sélectionné
```

---

### Cases à cocher

```text
Activé

Non activé

Mixte
```

---

### Boutons radio

```text
Bouton radio sélectionné
```

---

### Points de repère

```text
Bannière

Navigation

Principal

Recherche

Informations sur le contenu
```

---

## 14. Vérifications WCAG minimales avec le Narrateur

| Domaine | Vérifications | WCAG 2.2 |
|---|---|---|
| Structure | Un H1 est présent ; la hiérarchie des titres est cohérente | 1.3.1 (A), 2.4.6 (AA) |
| Liens | Chaque lien a un nom pertinent ; pas de « Cliquez ici » isolé | 2.4.4 (A) |
| Boutons | Le nom et l'état sont correctement annoncés | 4.1.2 (A) |
| Formulaires | Chaque champ a une étiquette ; les champs obligatoires et les erreurs sont annoncés | 3.3.2, 3.3.1 (A), 4.1.3 (AA) |
| Navigation | Les points de repère sont présents, y compris le contenu principal | 1.3.1, 2.4.1 (A) |
| Clavier | Ordre du focus logique ; aucun piège clavier | 2.4.3, 2.1.2 (A) |

---

## 15. Récapitulatif des commandes essentielles

| Commande | Action |
|---------|--------|
| Ctrl + Windows + Entrée | Démarrer / arrêter le Narrateur |
| Narrateur + Barre d'espace | Activer/désactiver le mode Analyse |
| Narrateur + Tab | Lire l'élément actuel |
| Narrateur + T | Lire le titre de la fenêtre |
| Narrateur + F1 | Afficher la liste des commandes du Narrateur |
| Narrateur + Ctrl + R (ou Narrateur + Flèche bas) | Lancer la lecture du document |
| Narrateur + R | Lire à partir du curseur |
| Ctrl | Arrêter la parole |
| Flèche bas / Flèche haut (mode Analyse) | Texte ou élément suivant / précédent |
| Tab | Élément focalisable suivant |
| Maj + Tab | Élément focalisable précédent |
| H / Maj + H | Titre suivant / précédent |
| 1–6 | Titre suivant du niveau indiqué |
| Maj + 1–6 | Titre précédent du niveau indiqué |
| K / Maj + K | Lien suivant / précédent |
| B / Maj + B | Bouton suivant / précédent |
| F / Maj + F | Contrôle de formulaire suivant / précédent |
| C / Maj + C | Zone de liste déroulante suivante / précédente |
| R / Maj + R | Bouton radio suivant / précédent |
| X / Maj + X | Case à cocher suivante / précédente |
| G / Maj + G | Graphique suivant / précédent |
| L / Maj + L | Liste suivante / précédente |
| I / Maj + I | Élément de liste suivant / précédent |
| T / Maj + T | Tableau suivant / précédent |
| D / Maj + D | Point de repère suivant / précédent |
| Narrateur + F5 / F6 / F7 | Liste des points de repère / des titres / des liens |
| Entrée | Activer le contrôle qui a le focus |
| Barre d'espace | Activer ou basculer le contrôle qui a le focus |

---

## 16. Recommandation de test

Pour les audits professionnels d'accessibilité web, utiliser le Narrateur **en complément** des lecteurs d'écran de bureau les plus utilisés, JAWS et NVDA. Le Narrateur est rarement le lecteur d'écran principal (0,4 % des répondants à l'enquête WebAIM Screen Reader User Survey #11), mais 36,1 % des répondants l'utilisent couramment. Tester avec le Narrateur permet de valider la compatibilité avec le lecteur d'écran intégré à Windows, disponible sur tout ordinateur Windows sans installation.

---

## Sources

- Microsoft — [Complete guide to Narrator](https://support.microsoft.com/en-us/accessibility/windows/narrator/complete-guide-to-narrator)
- Microsoft — [Appendix B: Narrator keyboard commands and touch gestures](https://support.microsoft.com/help/22806)
- Microsoft — [Chapter 3: Using scan mode](https://support.microsoft.com/help/22809)
- WebAIM — [Screen Reader User Survey #11 Results](https://webaim.org/projects/screenreadersurvey11/) (données d'enquête — pas un standard)
