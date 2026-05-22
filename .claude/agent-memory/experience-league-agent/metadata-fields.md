---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 1%

---
# Adobe Experience League - Référence Des Champs De Métadonnées Approuvés

*Provenant du Guide de création Adobe ExL (exploré en février 2026) + analyse du référentiel de blueprints-learn.en*

---

## Hiérarchie des métadonnées

Les métadonnées se présentent en cascade dans cet ordre (l’article remplace la table des matières, le référentiel de remplacements de la table des matières) :
1. Matière première de l’article (priorité la plus élevée)
2. Table des matières.md dans le guide de l’utilisateur
3. metadata.md à la racine du référentiel (priorité la plus faible)

---

## Champs au niveau de l’article

### OBLIGATOIRE

| Champ | Description | Format / Contraintes |
|-------|-------------|----------------------|
| `title` | Titre de la page d’optimisation du moteur de recherche. Apparaît dans les résultats de recherche. | Max ~60 caractères ; casse du titre ; utiliser `[!DNL Product]` pour les noms de produits ; NE PAS dupliquer H1 exactement, sauf si prévu |
| `description` | Description Meta pour les moteurs de recherche et les recommandations ExL. | 150 à 160 caractères ; commence idéalement par « Apprendre à... » ou « En savoir plus sur... » ; la validation échoue si elle est manquante/nulle. |
| `exl-id` | Identifiant unique attribué par le système. Utilisé pour le suivi du contenu. | Format UUID (par exemple `70573eb9-cd69-4fe6-b2ae-dae81665a308`); **supprimer lors de la copie d&#39;un fichier** — il sera attribué automatiquement ; ne jamais dupliquer entre les fichiers |

### FORTEMENT RECOMMANDÉ

| Champ | Description | Valeurs valides |
|-------|-------------|--------------|
| `solution` | Produit(s) Adobe couvert(s) par l’article. Utilisé pour la recherche/le filtrage ExL et les recommandations de contenu. | Séparés par des virgules ; sensible à la casse ; doit correspondre à l’énumération approuvée (voir Valeurs de solution valides ci-dessous) |

### FACULTATIF — COMMUN

| Champ | Description | Valeurs / Notes valides |
|-------|-------------|----------------------|
| `kt` | Ancien numéro JIRA de l’article de connaissances. Utilisé pour le suivi Analytics. | Nombre entier (par exemple `7207`) ; vide acceptable ; `null` acceptable |
| `thumbnail` | Référence d’image miniature pour Recommendations/Analytics. | Chaîne de nom de fichier ou `null` ou vide |
| `version` | Filtre de version du produit. Principalement utilisé pour les blueprints AEM et Campaign. | E.g. `Campaign v8`, `Campaign v8 Client Console` ; doit correspondre à version.yml |
| `doc-type` | Classification de contenu utilisée dans le référentiel/l’analyse. | `blueprint`, `overview-page`, `Video`, `Tutorial`, `Troubleshooting` (en minuscules de préférence) |
| `feature` | Balises de rubrique affichées sous la forme de « rubriques » sur les pages ExL. | 1-2 par article ; casse du titre ; doit correspondre à feature.yml ; séparé par des virgules |
| `feature-set` | Application parente pour la validation des fonctionnalités. | Les valeurs feature.yml doivent correspondre. |
| `role` | Rôle d’audience cible. Affiché comme « Créé pour » sur ExL. | `Admin`, `Architect`, `Data Architect`, `Data Engineer`, `Developer`, `Leader`, `User` |
| `level` | Niveau d’expérience de l’utilisateur. Affiché comme « Créé pour » sur ExL. | `Beginner`, `Intermediate`, `Experienced` (casse du titre) |
| `topic` | Rubriques interproduits pour la recherche/le filtrage. | Casse du titre ; doit correspondre à topic.yml ; séparé par des virgules |
| `type` | Classification du guide. | `Documentation` (par défaut), `Tutorial`, `Troubleshooting` |
| `last-substantial-update` | Affiche le contenu dans les widgets « Nouveautés ». | Format : `YYYY-MM-DD` |
| `hide` | Exclut la page de toutes les recherches et recommandations ; définit également l’index sur non. | `yes` ou `no` |
| `hidefromtoc` | Supprime de la navigation de la table des matières, mais la page reste accessible via un lien direct. | `yes` ou `no` |
| `index` | Contrôle si la page apparaît dans la recherche externe/le plan du site. | `yes`/`no` ou `y`/`n` ; par défaut : `no` (indexé) |
| `recommendations` | Contrôle le comportement du widget « Plus d’aide sur cette fonctionnalité ». | `noDisplay` (empêche l’affichage du widget), `noCatalog` (exclut du pool de recommandations) |
| `internal` | Marque la page comme Adobe interne uniquement. Empêche le marquage des liens internes. | `yes` |
| `short-description` | Description condensée des pages de destination ExL. Utilise le `description` s’il est omis. | Une phrase ; max ~20 mots |
| `activity` | Classification d’utilisation de la page. | `understand`, `implement`, `troubleshoot` (minuscules) |
| `sub-product` | Sous-composant du produit. Travaillez avec les équipes de solution pour obtenir des énumérations valides. | Minuscules ; par exemple `search`, `assets`, `sites` |
| `team` | Affectation d’équipes pour les analyses. | E.g. `TM` |
| `landing-page-name` | Liens vers la page de destination du chemin de navigation. | E.g. `experience-manager` |
| `landing-page-breadcrumb-title` | Texte du chemin de navigation pour le lien de la page de destination. | E.g. `AEM` |
| `auto-video-transcripts` | Active les transcriptions vidéo par défaut. | `true` |
| `badgeType` | Badge pour le statut du contenu. | Varie ; par exemple, `informative`, `positive` |
| `badgePremium` | Indicateur de badge Premium. | Par spécification de badge Adobe |
| `badgeLabel` | Texte du libellé du badge. | Chaîne courte |
| `source-git-url` | URL du référentiel Source. | URL GitHub complète |
| `cloud` | Remplacement de la catégorie de cloud au niveau de l’article. | Casse du titre ; doit correspondre à cloud.html. |

---

## Champs TOC.md

| Champ | Description | Remarques |
|-------|-------------|-------|
| `user-guide-title` | Nom du guide affiché dans les chemins de navigation et les pages de destination ExL. | Obligatoire pour les fichiers de table des matières |
| `breadcrumb-title` | Un nom de guide plus court pour les chemins de navigation lorsque le titre du guide de l’utilisateur est trop long. | Facultatif |
| `user-guide-description` | Résumé du guide pour la page de destination ExL. | Une phrase ; max ~20 mots recommandés |
| `product` | Suivi d’Analytics pour le guide. Valeur unique uniquement. | Doit correspondre à product.yml (voir Valeurs de produit valides). |
| `mini-toc-levels` | Nombre de niveaux de titre affichés dans la mini-table des matières de navigation de droite. | Entier 1-6 ; valeur par défaut 2 |
| `role` | Rôle d’audience par défaut pour le guide. | Mêmes valeurs que l’article `role` ; séparées par des virgules |
| `index` | Indique si le guide est indexé. | `yes`/`no` |

---

## Champs metadata.md au niveau du référentiel

| Champ | Remarques |
|-------|-------|
| `cloud` | Catégorie cloud par défaut pour tous les articles du référentiel |
| `solution` | Solution par défaut pour tous les articles |
| `product` | Produit par défaut pour le suivi Analytics |
| `type` | Type de guide par défaut |
| `doc-type` | Type de document par défaut |
| `mini-toc-levels` | Niveaux de mini-table des matières par défaut |
| `git-repo` | URL du référentiel GitHub ; active les boutons « Modifier cette page » et « Consigner le problème ». |
| `index` | Paramètre d’index par défaut |

---

## Valeurs De Solution Valides (Sensible À La Casse)

Valeurs courantes utilisées dans ce référentiel :
- `Experience Platform`
- `Real-Time Customer Data Platform`
- `Journey Optimizer`
- `Journey Optimizer B2B Edition`
- `Customer Journey Analytics`
- `Campaign`
- `Campaign v8`
- `Campaign Classic v7`
- `Campaign Standard`
- `Audience Manager`
- `Target`
- `Analytics`
- `Data Collection`
- `Commerce`
- `Marketo Engage`
- `Experience Cloud`
- `Journey Orchestration`

Valeurs multiples : séparées par des virgules, par exemple `Real-Time Customer Data Platform, Campaign`

---

## Valeurs de produit valides (pour `product` champ — suivi Analytics)

Voir l’invite système pour obtenir la liste complète. Valeurs clés :
- `adobe experience platform` / `experience platform` / `aem`
- `adobe analytics` / `analytics` / `aa`
- `adobe journey optimizer` / `journey optimizer` / `jo`
- `adobe customer journey analytics` / `customer journey analytics` / `cja`
- `adobe real time customer data platform` / `real time cdp` / `rtcdp`
- `adobe marketo` / `marketo` / `amk`
- `adobe campaign` / `campaign` / `ac`
- `adobe target` / `target` / `at`

---

## Valeurs de rôle valides

- `Admin`
- `Architect`
- `Data Architect`
- `Data Engineer`
- `Developer`
- `Leader`
- `User`

---

## Règles de validation des clés

1. Ne laissez jamais `exl-id` avec le même UUID dans un fichier copié : supprimez-le et laissez le système en attribuer un nouveau.
2. Les `thumbnail` et `kt` vides/nuls sont acceptables ; il s’agit de champs hérités.
3. `solution` valeurs doivent correspondre exactement à l’énumération approuvée, en respectant la casse.
4. `description` validation échoue en cas d’absence ou de valeur nulle ; fournissez toujours une valeur significative.
5. Placez `title` valeurs entre guillemets si elles contiennent des deux-points, des crochets ou des caractères spéciaux de début.
6. Plusieurs valeurs de `solution` sont séparées par des virgules dans une seule valeur de chaîne.
7. `product` valeur est unique uniquement (pour le suivi analytics) ; n’utilisez pas de valeurs séparées par des virgules.
8. Pour demander de nouvelles valeurs d’énumération, enregistrez un ticket JIRA UGP avec le composant « Balisage de contenu ».
