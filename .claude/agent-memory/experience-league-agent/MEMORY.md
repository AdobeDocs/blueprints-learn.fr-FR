---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---
# Mémoire de l’agent Experience League

## Fichiers de référence clés de ce référentiel
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/metadata.md` — valeurs par défaut des métadonnées au niveau du référentiel
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/help/blueprints/TOC.md` — métadonnées au niveau du guide
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/.cursor/skills/blueprint-document-reference/reference.md` — modèles de création de plans directeurs

## Règles de métadonnées (pour plus d’informations, voir metadata-fields.md )
- Article matière première REQUISE : `title`, `description`, `exl-id`
- Article front MATTER FORTEMENT RECOMMANDÉ : `solution`
- `exl-id` doit être un UUID valide ; supprimer/laisser vide lors de la copie de fichiers (affecté automatiquement par le système)
- `description` doit commencer par « Découvrez comment... ». ou « En savoir plus sur... » selon les directives d’Adobe
- `title` ~60 caractères maximum pour l’optimisation du moteur de recherche ; utilisez `[!DNL ProductName]` pour les noms de produit dans le titre.
- `solution` valeurs sont sensibles à la casse et doivent correspondre à l’énumération approuvée (voir metadata-fields.md)
- `thumbnail: null` ou `thumbnail:` (vide) sont utilisés ; une valeur vide est acceptable
- `kt:` est un champ hérité (numéro JIRA de l’article de la connaissance) ; toujours affiché dans ce référentiel ; un champ vide est acceptable
- Les fichiers de table des matières utilisent : `user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`
- Le `metadata.md` au niveau du référentiel utilise : `cloud`, `solution`, `product`, `type`, `doc-type`, `mini-toc-levels`, `git-repo` et `index`.

## Modèles courants dans ce référentiel (blueprints-learn.en)
- La plupart des fichiers de plan directeur comportent les éléments suivants : `title`, `description`, `solution` et `exl-id`
- Certains fichiers plus anciens incluent également : `kt`, `thumbnail`
- Certains fichiers utilisent `version` (plans directeurs de Campaign v8)
- Les pages d’aperçu utilisent des `doc-type: overview-page`
- `solution` contient souvent plusieurs valeurs séparées par des virgules : par exemple `Real-Time Customer Data Platform, Campaign`
- Les fichiers SANS `solution` passent toujours la validation si `exl-id` est présent

## Extensions Adobe Markdown utilisées dans ce référentiel
- `>[!NOTE]`, `>[!TIP]`, `>[!IMPORTANT]`, `>[!WARNING]`, `>[!CAUTION]`
- `>[!BEGINTABS]` / `>[!TAB Name]` / `>[!ENDTABS]` pour le contenu avec onglets
- `[!DNL ProductName]` — Ne pas localiser les balises pour les noms de produits
- `[!UICONTROL Label]` — Références de contrôle de l&#39;interface utilisateur
- `{zoomable="yes"}` — attribut de zoom d&#39;image
- `{width="1000"}` — attribut de largeur d&#39;image
- `{target="_blank"}` — cible du lien externe

## Références détaillées
- Référence complète du champ de métadonnées : `metadata-fields.md`
- Guide de création exploré : https://experienceleague.adobe.com/en/docs/authoring-guide-exl/using/home (février 2026)
