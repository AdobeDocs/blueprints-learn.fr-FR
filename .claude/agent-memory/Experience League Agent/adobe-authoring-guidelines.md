---
name: Adobe Experience League Authoring Guidelines
description: Référence complète pour les règles de création Markdown d’Adobe Experience League, explorée du guide de création officiel en mars 2026.
type: reference
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---


# Instructions de création d’Adobe Experience League

SOURCE : https://experienceleague.adobe.com/en/docs/authoring-guide/using/home
Exploré : 2026-03-15

---

## &#x200B;1. MÉTADONNÉES/DONNÉES DE FAÇADE

### Champs obligatoires
| Champ | Exigence | Règles |
|---|---|---|
| `title` | Obligatoire | 60 caractères maximum (anglais). Casse du titre. Aucun nom de produit, sauf si nécessaire pour des raisons de clarté. Le système ajoute » | ProductName » automatiquement. Placez-le entre guillemets s’il contient des deux-points ou des crochets. |
| `description` | Obligatoire | 150 à 160 caractères max. Ne peut pas être vide/nul. Les concepts commencent par « En savoir plus sur... » Les tâches commencent par « Découvrir comment... » ou le verbe impératif. |

### Champs facultatifs mais fréquemment utilisés
| Champ | Valeurs valides | Remarques |
|---|---|---|
| `feature` | Doit correspondre aux valeurs YAML de la fonctionnalité ; casse du titre avec espaces (par exemple, « Fragment de contenu »). | 1-2 par article ; s&#39;affiche dans les rubriques |
| `feature-set` | Doit valider par rapport au YAML de la fonctionnalité | Application parente de la fonctionnalité |
| `role` | Utilisateur, Développeur, Leader, Administrateur, Architecte, Architecte de données, Ingénieur de données | Respect de la casse ; affiche « Créé pour » |
| `level` | Débutant, intermédiaire, expérimenté | La valeur par défaut est Débutant si non spécifié. |
| `solution` | Doit correspondre au YAML de la solution (par exemple, « Campaign, Campaign Standard v7 »). | Valeurs multiples autorisées ; utilisé pour le filtrage de recherche |
| `topic` | Doit correspondre à la rubrique YAML ; casse du titre avec espaces | Pour le filtrage inter-produits (par exemple, « Intégrations ») |
| `type` | Documentation, tutoriel, dépannage | Repo-level ; par défaut, documentation |
| `short-description` | Une phrase, 20 mots max. | Pour les landing pages ExL lorsque la description est trop longue |
| `badgePremium` | `label="Premium" type="Positive" url="..."` | Badge au niveau de la page |
| `mini-toc-levels` | 1-6 (par défaut 2) | Contrôle la profondeur d’affichage de l’en-tête de navigation droite. |
| `hidefromtoc` | true/false | Exclut du volet de navigation de gauche, mais conserve l’URL accessible. |

### Emplacement des métadonnées
- Niveau d’article : haut du fichier markdown en tant que front-issue YAML
- Niveau de la table des matières : dans le fichier TOC.md
- Niveau de référentiel : dans le fichier metadata.md

### Règles de formatage clés
- Placer les valeurs contenant des virgules ou des crochets entre guillemets
- Valeurs multiples séparées par des virgules
- Correspondance sensible à la casse avec les définitions YAML
- Les valeurs de balise vides ou vides entraînent l’échec de la validation.

### Champs obsolètes
seo-title, seo-description, audience, difficulté, uuid (de l’ère de la migration)

---

## &#x200B;2. SYNTAXE DE MARKDOWN (AVEC ADOBE)

### Formatage de texte
- Gras : `**text**`
- Italique : `*text*`
- Gras + Italique : `***text***`
- Échapper les caractères spéciaux : utilisez une barre oblique inverse `\` avant de `# { } [ ] * + - . !`
- Entités HTML : `&lt;` `&gt;` `&amp;` `&mdash;` `&ndash;`

### En-têtes
- Utilisez le style ATX (syntaxe `#` uniquement, jamais le style souligné/setext).
- Un H1 par document (généralement le titre de page correspondant aux `title` de métadonnées)
- Toutes les rubriques suivantes H2 (`##`) ou moins
- Lignes vides requises avant et après les en-têtes (sauf le tout premier en-tête)
- 69 caractères maximum (anglais) / 120 caractères maximum (localisé)
- Max ~5 mots préférés
- Casse de la phrase pour tous les en-têtes (mettre uniquement le premier mot et les noms propres en majuscules)
- Casse du titre UNIQUEMENT pour le champ de métadonnées `title`
- Pas de ponctuation de fin (points d’interrogation autorisés pour les en-têtes de FAQ)
- Identifiants d’ancre personnalisés : `## Title {#custom-id}` — utilisez des tirets, pas des points
- Aucun ID d’ancre d’en-tête dupliqué dans un document
- Évitez les noms d’ancre réservés : recherche, résultats, facettes, pagination, tri, requête, searchbox, contenu, en-tête, pied de page, principal, navigation, barre latérale, page, conteneur, wrapper
- Suivez chaque en-tête avec au moins un paragraphe de corps de texte (ne placez pas de listes/tableaux directement après un en-tête)
- En-têtes de concept : substantif/groupes nominaux
- En-têtes de tâche : verbes impératifs (PAS de refinancement — « Créer un segment » pas « Créer un segment »)
- Structure parallèle entre les niveaux d&#39;en-tête

### Listes
- Puces (non triées) : `*`, `-` ou `+` — utiliser de manière cohérente dans un document
- Commandé : `1.` pour chaque article (numéros automatiques)
- Lignes vides avant et après les listes
- Retrait d’éléments numérotés imbriqués 3 espaces ; puces imbriquées 2 espaces
- Ponctuation des puces : omettez les points-virgules/virgules/conjonctions à la fin ; ajoutez des points uniquement pour les phrases complètes.
- N’ajoutez pas de points si tous les éléments contiennent ≤ 3 mots ou des libellés/en-têtes d’interface utilisateur

### Liens
- Externe : `[text](https://url.com)`
- Relatif (même niveau) : `[text](file.md)`
- Racine relative : `[text](/help/path/file.md)` — doit commencer par `/`
- Liens profonds (même page) : `[text](#heading-anchor)`
- Liens profonds entre documents : `[text](file.md#heading-id)`
- Forcer un nouvel onglet : `[text](url){target="_blank"}`
- URL nues : entourez-les de crochets `<https://example.com>` pour les rendre cliquables
- Liens de référence : seuls les liens absolus fonctionnent pour les liens de style référence
- N’incluez pas le même fichier dans plusieurs emplacements de table des matières via des liens relatifs
- Utilisateurs Windows : convertir des barres obliques inverses en barres obliques directes dans les chemins d’accès

### Images
- De base : `![alt text](image.png "hover tooltip")`
- Redimensionner : `{width="300"}`
- Aligner : `{align="center"}` ou `{align="right"}`
- Zoom : `{zoomable="yes"}` ou `{modal="regular"}`
- Taille de fichier max. : 100 Mo (recommandée sous 5 Mo)
- Le texte secondaire est OBLIGATOIRE pour toutes les images (pour l’optimisation du moteur de recherche et l’accessibilité)
- Noms de fichiers image : en minuscules avec des tirets
- Stocker les images dans un dossier de ressources désigné

### Blocs de code
- En ligne : accents graves `` `code` ``
- Utiliser pour : noms de fichier, URL, termes définis par l’utilisateur, commandes
- Blocs de code clôturés : triple backticks avec identifiant de langue

  ```
  ```javascript
  code here
  ```

  ```
  
  
- Options : `{line-numbers="true"}`, `{start-line="7"}`, `{highlight="11-13, 16"}`
- Incluez toujours un identifiant de langue dans les blocs de code clôturés

### Tableaux
- La ligne de séparation nécessite au moins 3 tirets par colonne : `|---|---|---|`
- Alignement : `|---|` gauche, `|:---:|` centre, `|---:|` droite
- Échapper les tuyaux littéraux : `\|` ou utiliser `&vert;`
- Tables HTML autorisées ; utilisez `<table style="table-layout:auto">` ou `table-layout:fixed`
- Alignement du tableau HTML : `<td align="left|center|right">`
- Évitez la syntaxe Markdown dans les tables HTML (par exemple, `[!NOTE]` ne fonctionne pas dans les tables HTML)
- Supprimer les bordures : `<tr style="border: 0;">`
- Option de disposition de tableau Markdown : ajouter des `{style="table-layout:auto"}` après le tableau avec des lignes vides
- Évitez les tableaux très grands/très larges en raison de problèmes de visibilité de la barre de défilement horizontale

---

## &#x200B;3. EXTENSIONS DE SYNTAXE ADOBE SPÉCIALES

### Légendes / Admonitions

```
>[!NOTE]
>
>Text here.

>[!TIP]
>
>Text here.

>[!IMPORTANT]
>
>Text here.

>[!WARNING]
>
>Text here.

>[!CAUTION]
>
>Text here.

>[!ADMIN]
>[!AVAILABILITY]
>[!PREREQUISITES]
>[!INFO]
>[!ERROR]
>[!SUCCESS]
```
- CRITIQUE : aucun espace entre `>` et `[!` — utiliser `>[!NOTE]` NON `> [!NOTE]`
- Ajouter une ligne vide entre `>[!NOTE]` et la ligne de texte du corps

### Onglets

```
>[!BEGINTABS]

>[!TAB iOS]
Content here

>[!TAB Android]
Content here

>[!ENDTABS]
```

### Sections réductibles (accordéons)

```
+++Click to expand
Content inside
+++
```
Remarque : les sections réductibles imbriquées ne sont PAS prises en charge.

### Cases d&#39;ombrage

```
>[!BEGINSHADEBOX "Optional Title"]
Content here
>[!ENDSHADEBOX]
```

### Vidéos

```
>[!VIDEO](https://video.tv.adobe.com/v/ID/?quality=12&learn=on)
```
Ajoutez des `{transcript=true}` pour les transcriptions.

### Plus Comme Ceci :

```
>[!MORELIKETHIS]
>* [Article 1](url)
>* [Article 2](url)
```

### Aide contextuelle

```
>[!CONTEXTUALHELP]
>id="..."
>title="..."
>abstract="..."
>additional-url="..."
```

### Badges (intégrés)

```
[!BADGE Label]{type=Informative url="https://example.com" tooltip="text"}
```
Types : `Informative` (bleu), `Positive` (vert), `Negative` (rouge), `Neutral` (gris), `Caution` (jaune)

### Mise en surbrillance du texte (aperçu)

```html
<span class="preview">highlighted text</span>
```

### Inclut et fragments de code
- Inclure le fichier entier : `{{$include /help/_includes/legal-blurb.md}}`
- Extrait de code (sans en-têtes) : `{{snippet-id}}`
- Stocker les fichiers réutilisables dans `help > _includes/` dossier
- Fragments de code stockés dans `help > _includes/snippets.md`
- Inclut peut avoir des en-têtes ; les fragments de code NE PEUVENT PAS
- Ne fonctionne que dans le même référentiel (et non entre référentiels).
- Caractères d’échappement `{{` ou `}}` dans les fichiers ne faisant pas référence

### Balise DNL (Do Not Localize)
- `[!DNL ProductName]` : inclut les noms de produits/marques qui ne doivent pas être traduits
- Utiliser sur la première mention ou sur une mention importante dans une page

### Balise UICONTROL
- `[!UICONTROL Button Label]` : recouvre le texte des éléments de l&#39;interface utilisateur (boutons, menus, noms de champ)
- Assure l’extraction des chaînes de l’interface utilisateur des bases de données de produits plutôt que la traduction automatique
- Pas d&#39;apostrophes, de guillemets ou de ponctuation dans les balises UICONTROL
- Utiliser le format Gras pour les éléments de l’interface utilisateur référencés dans les étapes

### Fonctionnalités non prises en charge
- Listes de tâches (cases à cocher)
- Émoji
- Règles horizontales
- Sections réductibles imbriquées

---

## &#x200B;4. DÉNOMINATION DES FICHIERS ET STRUCTURE DES DOSSIERS

### Règles de dénomination des fichiers
- Noms de fichiers en minuscules avec des tirets uniquement
- Pas de majuscules, de traits de soulignement, de points ou d’espaces
- Noms descriptifs et compatibles avec l’optimisation du moteur de recherche (par exemple, `calculated-metric-overview.md` non `cmo.md`)
- Évitez les nombres dans les noms de fichier ; utilisez des mots descriptifs
- Évitez les noms réservés/conflictuels : `metadata.md`, `search.md`
- La modification du nom des fichiers dynamiques nécessite une gestion des redirections (modifications d’URL)

### Structure de dossiers
- Les noms de répertoire/dossier n’affectent PAS les URL (seuls les noms de référentiel et les noms de fichier affectent les URL).
- La table des matières.md contrôle la hiérarchie de navigation, et non l’emplacement du dossier Git
- Stocker des images/ressources dans un dossier de ressources désigné
- Inclusions réutilisables stockées dans `help/_includes/`
- Fragments de code stockés dans `help/_includes/snippets.md`

### Règles TOC.md
- Chaque article doit être répertorié dans TOC.md pour être rendu sur Experience League
- Format H1 : `# Guide Title {#anchor-id}` — l’ancre génère le chemin de l’URL de base
- Les en-têtes de section doivent avoir des ID d’ancrage : `+ Section Name {#section-id}`
- Les en-têtes de section (éléments parents) ne peuvent pas être des liens eux-mêmes
- Liens de l’article : `+ [Title](path/file.md)`
- La modification des ID d’ancre de section modifie toutes les URL d’article imbriquées (nécessite des redirections)
- Utilisez un style de puce cohérent dans l’ensemble (`+`, `*` ou `-`).
- Métadonnées de la table des matières : `user-guide-description`, éventuellement `breadcrumb-title`
- `mini-toc-levels` : contrôle l’affichage de l’en-tête de navigation à droite (1-6, valeur par défaut 2)

---

## &#x200B;5. QUALITÉ DU CONTENU ET NORMES ÉDITORIALES

### Voix et tonalité
- Voix active préférée à voix passive
- Le présent au détriment du futur
- Deuxième personne (« vous ») pour le contenu pédagogique
- Phrases de moins de 35 mots
- Verbes forts et précis — évitez les adverbes faibles (« très », « extrêmement »)

### Étapes/procédures
- Chaque étape est UNE commande unique et concise (une phrase)
- Les informations supplémentaires sont ajoutées à la ligne suivante (mises en retrait sous l’étape)
- Commencez chaque étape par un verbe impératif
- Limitez les procédures à environ 7 étapes (10 au maximum avant de diviser en sous-tâches)
- Placer les informations conceptuelles AVANT les étapes
- Placez des captures d’écran APRÈS l’étape appropriée.
- Répéter les noms de pages/onglets pour l’orientation du lecteur
- Mise en forme UICONTROL en gras des éléments de l’interface utilisateur par étapes

### Terminologie de l&#39;interface
- **Ouvrir/Fermer** : applications et programmes
- **Accéder à** : menus, onglets ou emplacements d’interface utilisateur
- **Sélectionner** : texte, cellules ou options des listes
- **Clic** : actions de la souris (évitez de spécifier le type de contrôle, sauf si nécessaire)
- **Menu déroulant** (et non pas « liste déroulante »)

### Noms de produits
- N’ajoutez pas le nom du produit aux titres/en-têtes, sauf si la clarté l’exige
- Omettre « le » avant les noms de produits
- Inclure « Adobe » sur la première mention au niveau du guide (exigence relative à la marque déposée)
- Déposez « Adobe » dans les mentions secondaires, sauf si la loi l’exige
- Utiliser des balises DNL pour les noms de produit afin d’éviter les erreurs de traduction

### Accent et mise en forme
- Gras : éléments de l’interface utilisateur et actions au clavier
- Italique : messages d’erreur, mots étrangers, accentuation
- Code (accents graves) : noms de fichier, URL, termes définis par l’utilisateur
- Pas de guillemets autour des éléments de l’interface utilisateur (utilisez plutôt la balise UICONTROL)

### Majuscules
- Cas de phrase pour les en-têtes, navigation, sous-titres
- Casse du titre UNIQUEMENT pour `title` champ de métadonnées
- Les noms propres sont toujours en majuscules

---

## &#x200B;6. BONNES PRATIQUES D’OPTIMISATION POUR LES MOTEURS DE RECHERCHE

- Un H1 par page — doit être concis, descriptif, dire aux utilisateurs sur quoi porte la page
- Hiérarchie d’en-tête séquentielle (h1 → h2 → h3, ne jamais ignorer les niveaux)
- Inclure les mots-clés dans H1, le corps de texte et les métadonnées (pas la balise meta `keywords` — Google l’ignore)
- Éviter le bourrage de mots-clés (intention > fréquence)
- Titre : 50 à 60 caractères max. ; le système ajoute « | » Adobe ProductName » automatiquement
- Description : 150 à 160 caractères ; doit être un call to action, et non une répétition du contenu
- Ajouter un texte de remplacement descriptif à toutes les images
- Inclure les transcriptions vidéo (les moteurs de recherche ne peuvent lire que le texte)
- Lier stratégiquement aux pages associées (éviter les pages orphelines)
- Inclure les éléments structurés : listes numérotées, sous-titres, blocs de code
- Utilisez des outils tels que AnswerThePublic, Google Trends pour rechercher des mots-clés
- Le contenu doit démontrer l’E-A-T (expérience, expertise, autorité, fiabilité)

---

## &#x200B;7. LOCALISATION

### Traduction automatique en premier
- Le contenu source en anglais génère automatiquement des versions localisées
- Langues prises en charge : allemand, français, japonais, italien, espagnol, portugais brésilien, chinois simplifié, chinois traditionnel, coréen, néerlandais, suédois

### Écriture pour la localisation
- Terminologie cohérente dans l’ensemble
- Phrases courtes et voix active
- Ordre des mots anglais standard (objet → verbe → objet)
- Utilisez des pronoms relatifs (« que », « qui »).
- Évitez : l&#39;humour, les idiomes, le jargon, les expressions régionales, les métaphores, les mots inutiles

### Balises de localisation
- `[!UICONTROL Label]` : garantit que les chaînes de l’interface utilisateur sont extraites de la base de données du produit et non traduites par ordinateur
- `[!DNL ProductName]` — empêche la traduction des noms de produits ou de marques
- Les images d’un dossier « do-not-localize » sont exclues de la localisation

---

## &#x200B;8. TYPES DE CONTENU

- **Guide** : collection en ligne de pages référencées dans une table des matières ; couvre les bonnes pratiques officielles
- **Tutoriel** : contenu didactique (vidéo ou texte) pour des cas d’utilisation spécifiques ; publié dans les référentiels d’apprentissage.
- **Guide de référence** : API/SDK de développement, généralement au format tableau, publié sur developer.adobe.com .
- **Cours** : collection de leçons sélectionnées par des experts et ciblant des rôles utilisateur spécifiques
- **Articles de la base de connaissances** : contenu de dépannage court et temporairement pertinent
- **Page de destination/page d’accueil** : gérée séparément (SCCM)

---

## &#x200B;9. ERREURS DE VALIDATION COURANTES À ÉVITER

- Métadonnées `title` ou `description` manquantes ou vides
- `description` ne commençant pas par « En savoir plus sur... » ou « Découvrez comment... »
- Espace entre `>` et `[!` dans la syntaxe de la légende (`> [!NOTE]` au lieu de `>[!NOTE]`)
- Espaces en gras : `**text **` (espaces de fin en gras)
- Syntaxe Markdown dans les tableaux HTML (par exemple, les légendes ne fonctionnent pas à cet endroit)
- Dupliquer les ID d’ancre d’en-tête dans un document
- ID d’ancrage contenant des points (utilisez plutôt des tirets)
- Utilisation de noms d’ancres réservés (recherche, résultats, en-tête, pied de page, etc.)
- `role`, `level`, `feature` `topic` valeurs qui ne correspondent pas aux définitions YAML
- En-têtes empilés sans corps de texte entre eux
- H1 utilisé plus d&#39;une fois par document
- Niveaux de cap ignorés (p. ex. H1 → H3)
- Nommage des fichiers avec des majuscules, des traits de soulignement ou des espaces
- Texte secondaire manquant sur les images
- Gérer les en-têtes de tâche (« Création... ») au lieu de « Créer... »)
