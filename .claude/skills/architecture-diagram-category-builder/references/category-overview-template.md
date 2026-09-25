---
source-git-commit: e0ecfa4d74b8fcc0bbaf35d44c33c725a1b1a539
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# Présentation des catégories.modèle md

Chaque dossier de catégorie sous `help/blueprints/architecture-diagrams/` a besoin d’un `overview.md` qui ressemble aux cinq autres. Utilisez cette structure exacte.

## Matière Première

```yaml
---
title: {Category Label}
description: {One-sentence summary of what this category covers.}
solution: {Primary Adobe solution(s), comma-separated}
doc-type: overview-page
---
```

N’incluez pas `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt` ou `thumbnail` sur une nouvelle page. Le pipeline de publication les renseigne automatiquement.

## Corps

```markdown
# {Category Label}

{1-3 paragraph intro describing what this category of diagrams covers and why it matters.}

| Diagram | Description |
| --- | --- |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
```

Règles :

- Répertoriez chaque page de la catégorie, dans l’ordre dans lequel elles apparaissent dans le fichier TOC.md.
- Les cibles des liens sont des noms de fichier relatifs (sans préfixe de `/help/blueprints/...`), puisque la vue d’ensemble se trouve aux côtés de ses pages sœurs.
- Les descriptions sont composées d’une seule phrase, aucun point de fin n’est nécessaire si elle se lit comme une étiquette.
- Si une catégorie comporte un sous-regroupement naturel (par exemple, « Diagrammes obsolètes » sous parcours clients), ajoutez un en-tête `## {Sub-group name}` suivi de son propre tableau à deux colonnes dans le même format - ne mélangez pas les miniatures de diagramme ni les colonnes supplémentaires dans le tableau.
- N’incorporez pas `<img>` miniatures de diagramme dans ce tableau. Limitez-la à deux colonnes : `Diagram` (lien) et `Description` (texte). Les miniatures appartiennent aux pages de contenu individuelles, et non à la vue d’ensemble des catégories.
- N’utilisez pas de `<ul><li>` imbriqués HTML dans les cellules des tableaux. Texte brut uniquement.

## Exemple (Informations sur le client)

```markdown
---
title: Customer Insights
description: Unify and analyze data and customer behaviors from across the customer journey
solution: Customer Journey Analytics
doc-type: overview-page
---
# Customer Insights

Customer Journey Analytics shows how brands can unify customer data and behavior from various interaction channels and sources to create a journey-based view of all customer interactions.

| Diagram | Description |
| --- | --- |
| [Adobe Customer Journey Analytics](cja.md) | Core Customer Journey Analytics architecture, including B2B and audience-sharing derivations |
| [Adobe Customer Journey Analytics & Adobe Journey Optimizer integration](cja-ajo-integration.md) | Campaign and journey insights integration between Customer Journey Analytics and Journey Optimizer |
```
