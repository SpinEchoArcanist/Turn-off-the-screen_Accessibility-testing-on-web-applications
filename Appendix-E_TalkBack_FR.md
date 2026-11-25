---
Type:
  - Notes
tags:
  - Test/Accessibility
  - Android
  - TalkBack
Comment: Aide-mémoire des commandes TalkBack pour les tests d'accessibilité mobile
---

# Annexe E — TalkBack (Android) : aide-mémoire pour les tests d'accessibilité

> **Périmètre.** Les gestes ci-dessous s'appliquent à **TalkBack 9.1 et versions ultérieures**, sur les appareils compatibles avec les gestes à plusieurs doigts (pour le vérifier : avec TalkBack activé, toucher l'écran avec trois doigts — si le menu TalkBack s'ouvre, les gestes à plusieurs doigts sont pris en charge). Les alternatives à un doigt sont indiquées lorsqu'elles existent. Le comportement exact peut varier selon le fabricant de l'appareil, la version d'Android et la version de TalkBack.

---

## 1. Activer et désactiver TalkBack

| Méthode | Comment | Remarque |
|---|---|---|
| Paramètres | Paramètres > Accessibilité > TalkBack > Utiliser TalkBack | Toujours disponible |
| Raccourci des touches de volume | Maintenir les deux touches de volume enfoncées pendant quelques secondes | Doit être activé (Paramètres > Accessibilité > TalkBack > Raccourci TalkBack) |
| Assistant Google | « Hey Google » puis « Activer TalkBack » / « Désactiver TalkBack » | Si l'Assistant est configuré |
| Clavier externe | Action + Alt + T | Uniquement sur la dernière version, Android 16 |

**Conseil :** activer le raccourci des touches de volume **avant** le premier test, pour pouvoir désactiver TalkBack rapidement.

---

## 2. Gestes de navigation de base

| Action | Geste | Objectif du test |
|---|---|---|
| Entendre l'élément sous le doigt | Faire glisser un doigt sur l'écran (explorer au toucher) | Vérifier ce qui est annoncé à une position donnée |
| Sélectionner un élément | Toucher | Placer le focus sur l'élément et entendre son libellé |
| Élément suivant | Balayer vers la droite | Ordre de navigation vers l'avant |
| Élément précédent | Balayer vers la gauche | Ordre de navigation vers l'arrière |
| Activer l'élément | Toucher deux fois | Déclencher le contrôle |
| Appui long | Toucher deux fois et maintenir | Vérifier les actions d'appui long |
| Faire défiler | Balayer avec deux doigts vers le haut / le bas / la gauche / la droite | Faire défiler le contenu |
| Mettre en pause / reprendre la parole | Toucher avec deux doigts | Contrôler la parole |

---

## 3. Contrôles de lecture (équivalent du rotor de VoiceOver)

| Action | Geste |
|---|---|
| Passer au contrôle de lecture suivant | Balayer vers le bas avec trois doigts (ou balayer vers le haut puis vers le bas avec un doigt) |
| Passer au contrôle de lecture précédent | Balayer vers le haut avec trois doigts (ou balayer vers le bas puis vers le haut avec un doigt) |
| Élément suivant du contrôle sélectionné | Balayer vers le bas |
| Élément précédent du contrôle sélectionné | Balayer vers le haut |

**Contrôles de lecture par défaut :** Caractères · Mots · Lignes · Paragraphes · Lignes et colonnes (tableaux) · **Titres** · **Commandes** (boutons, cases à cocher, champs de texte) · **Liens** · Vitesse d'élocution · Langue parlée · Rechercher sur l'écran.

| Contrôle de lecture | Objectif du test |
|---|---|
| Titres | Valider la structure des titres de la page |
| Commandes | Vérifier que chaque champ et chaque bouton est atteignable et étiqueté |
| Liens | Vérifier le nom des liens hors contexte |
| Lignes et colonnes | Vérifier la navigation dans les tableaux de données |

**Modifier la liste :** paramètres TalkBack > Modifier les menus > Personnaliser les commandes de lecture.

**Remarque :** les points de repère ne font pas partie des contrôles de lecture par défaut — sur Android, les titres portent l'essentiel de la navigation structurelle.

---

## 4. Menu TalkBack

| Action | Geste |
|---|---|
| Ouvrir le menu TalkBack | Toucher avec trois doigts (ou balayer vers le bas puis vers la droite d'un seul mouvement) |

Les options par défaut comprennent : **Lire à partir de l'élément sélectionné** · Copier la dernière expression énoncée · Langue parlée · **Rechercher sur l'écran** · **Afficher ou masquer l'écran** · Commandes vocales · Paramètres TalkBack · Paramètres de la synthèse vocale · Paramètres braille.

Selon l'élément qui a le focus, le menu peut aussi afficher des **Actions**, des **Liens**, des options d'édition ou des options de libellé — l'utiliser pour vérifier que les actions personnalisées sont exposées.

---

## 5. Gestes système Android avec TalkBack

| Action | Geste à un doigt | Geste à plusieurs doigts (navigation par gestes activée) |
|---|---|---|
| Retour | Balayer vers le bas puis vers la gauche | Balayer avec deux doigts depuis le bord gauche ou droit |
| Accueil | Balayer vers le haut puis vers la gauche | Balayer avec deux doigts vers le haut depuis le bas de l'écran |
| Applications récentes | Balayer vers la gauche puis vers le haut | Balayer avec deux doigts vers le haut depuis le bas de l'écran et maintenir |
| Notifications | Balayer vers la droite puis vers le bas | Balayer avec deux doigts vers le bas depuis le haut de l'écran |

---

## 6. Édition de texte

| Action | Geste |
|---|---|
| Démarrer / terminer le mode sélection | Toucher deux fois avec deux doigts et maintenir |
| Copier le texte sélectionné | Toucher deux fois avec trois doigts |
| Couper (en mode sélection) | Toucher deux fois avec trois doigts et maintenir |
| Coller | Toucher trois fois avec trois doigts |

---

## 7. Aide et entraînement

| Action | Geste |
|---|---|
| Essayer les gestes | Toucher avec quatre doigts |
| Aide de TalkBack | Toucher deux fois avec quatre doigts |
| Geste de désactivation ponctuelle (le geste suivant est interprété comme si TalkBack était désactivé) | Toucher deux fois avec quatre doigts et maintenir |

---

## 8. Masquer l'écran (important pour des tests réalistes)

| Fonctionnalité | Comment | Pourquoi c'est important |
|---|---|---|
| Afficher ou masquer l'écran | Menu TalkBack > Afficher ou masquer l'écran | **Masque l'affichage tandis que TalkBack reste actif** — le testeur ne dispose que de ce qui est annoncé, comme un utilisateur aveugle |
| Raccourci pour masquer l'écran | Appuyer trois fois sur les deux touches de volume | Google ne documente ce raccourci que pour **TalkBack 8.2 et versions antérieures** ; avec les versions couvertes par cet aide-mémoire, utiliser le menu TalkBack |

---

## 9. Navigation dans Chrome avec TalkBack (focus sur les tests web)

| Action | Geste | Objectif du test |
|---|---|---|
| Élément suivant / précédent de la page | Balayer vers la droite / la gauche | Parcourir le texte, les liens, les boutons, les champs |
| Lire à partir de l'élément actuel | Menu TalkBack > Lire à partir de l'élément sélectionné | Auditer le flux du contenu |
| Naviguer par titres | Contrôle de lecture **Titres** + balayer vers le bas / le haut | Valider la structure sémantique |
| Naviguer par contrôles de formulaire | Contrôle de lecture **Commandes** + balayer vers le bas / le haut | S'assurer que les champs sont atteignables et étiquetés |
| Naviguer par liens | Contrôle de lecture **Liens** + balayer vers le bas / le haut | Vérifier la structure et l'étiquetage des liens |
| Trouver un texte à l'écran | Menu TalkBack > Rechercher sur l'écran | Localiser rapidement un élément précis |
| Activer un lien ou un bouton | Toucher deux fois | Déclencher la navigation ou l'action |
| Revenir en arrière | Geste Retour (section 5) | Quitter un dialogue ou revenir à la page précédente |

---

## 10. Points de contrôle QA de l'accessibilité

| Domaine | Cible de validation |
|---|---|
| Ordre du focus | Logique et complet en balayant vers la droite |
| Libellés | Chaque élément est annoncé de manière explicite |
| Actions | Toutes les interactions sont atteignables avec TalkBack |
| Modales | Le contenu derrière un dialogue ouvert n'est pas atteignable |
| Mises à jour | Les changements dynamiques et les messages sont annoncés |
| Interface masquée | Aucun accès aux éléments masqués ou inactifs |
| Écran masqué | La tâche principale peut être réalisée avec Masquer l'écran activé |

---

## 11. Défaillances courantes

| Problème | Symptôme observable |
|---|---|
| Libellés manquants | Seul le rôle (« Bouton ») est annoncé, sans nom |
| Ordre cassé | Navigation qui saute des éléments ou tourne en boucle |
| Interface non focalisable | Éléments inatteignables en balayant |
| Mises à jour silencieuses | Aucun retour sonore après une action |
| Problèmes de sortie des modales | Arrière-plan encore atteignable |
| Fonctions limitées aux gestes | Fonction impossible sans balayage, pincement ou glisser |

---

## Sources

- Google — [Activer TalkBack](https://support.google.com/accessibility/android/answer/6007100?hl=fr)
- Google — [Utiliser les gestes TalkBack](https://support.google.com/accessibility/android/answer/6151827?hl=fr)
- Google — [Utiliser le menu TalkBack et les contrôles de lecture](https://support.google.com/accessibility/android/answer/6007066?hl=fr)
- Google — [En savoir plus sur les paramètres et la confidentialité de TalkBack](https://support.google.com/accessibility/android/answer/6006589?hl=fr)
- Google — [Premiers pas avec Android et TalkBack](https://support.google.com/accessibility/android/answer/6283677?hl=fr)
