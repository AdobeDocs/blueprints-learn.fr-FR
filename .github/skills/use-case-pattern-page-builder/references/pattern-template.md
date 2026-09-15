---
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 48%
---
# Modèle de modèle de cas d’utilisation

Ce fichier contient le modèle Markdown complet pour une page de modèle de cas d’utilisation. Remplacez toutes les valeurs `{{placeholder}}` par le contenu réel lors de la génération d’un nouveau modèle.

---

## Modèle

````markdown
---
title: {{Pattern Title}}
description: {{One-sentence description of what this pattern teaches}}
solution: {{Comma-separated Adobe solutions}}
exl-id: {{generate-uuid-placeholder}}
---
# {{Pattern title}}

This guide provides an overview of {{pattern name}} using {{solutions with [!DNL ...] formatting}}. It is designed for solution architects, marketing technologists, and implementation engineers who need to {{primary capability description}}.

## Use case pattern

**{{Pattern Name}}**

{{One-two sentence description of what the pattern does and enables.}}

**Execution plan:** {{Step 1}} > {{Step 2}} > {{Step 3}} > {{Step 4}} > {{Step 5}}

## Use case overview

{{Paragraph 1: Define the pattern. What does it do? How does it differ from related patterns? Provide a clear, specific definition.}}

{{Paragraph 2: Describe the typical trigger or starting condition. When does this pattern apply? What event, schedule, or condition initiates it?}}

{{Paragraph 3: Describe what the pattern delivers. What is the end result for the customer or business? What channels or touchpoints does it affect?}}

{{Paragraph 4: Clarify scope boundaries. What does this pattern NOT cover? What adjacent patterns handle those needs? Reference other patterns by name if relevant.}}

{{Paragraph 5 (optional): Identify typical stakeholders and teams involved in implementation. Who owns what?}}

## Key business objectives

The following business objectives are supported by this use case pattern.

**[{{Objective Name}}](../../business-objectives/{{category}}/{{objective-file}}.md)**

{{Brief description of how this pattern supports the objective -- 1-2 sentences.}}

| KPIs |
| --- |
| {{KPI1}}, {{KPI2}}, {{KPI3}} |

{{Repeat the above block for each supported business objective.}}

## Example tactical use cases

The following scenarios illustrate how {{pattern name}} can be applied across different business contexts.

- **{{Scenario name}}** -- {{Description of the scenario and how it uses this pattern}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
{{Include 6-10 scenarios total}}

## Key performance indicators

| KPI | Description | Measurement |
| --- | --- | --- |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}

## Related documentation

The following resources provide additional detail on the capabilities used in this pattern. Group the reference links to primary Experience League documents under descriptive subheadings.

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})
````

---

## Remarques sur l’utilisation de ce modèle

- **FrontMATTER YAML :** le `exl-id` doit être un UUID d’espace réservé (par exemple, `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`). Le pipeline de publication attribue la valeur réelle.
- **Ordre des sections :** la section `Use case pattern` s’affiche immédiatement après l’introduction, avant le `Use case overview`. Il offre aux lecteurs une définition claire en une ligne et un plan d’exécution détaillé dès le départ.
- **Noms de produits Adobe :** utilisez toujours `[!DNL ...]` syntaxe pour les noms de produits Adobe dans le corps du texte et les tableaux (par exemple, `[!DNL Journey Optimizer]`). Il s’agit d’une convention d’Experience League qui empêche la traduction des noms de produits.
- **Liens d’objectifs métier :** utilisez des chemins d’accès relatifs entre le fichier de modèle et le répertoire d’objectifs métier : `../../business-objectives/{{category}}/{{filename}}.md`.
- **Noms de fichier avec majuscules et minuscules :** le nom du fichier de modèle doit être en majuscules et minuscules et doit être dérivé du titre du modèle. Exemple : la « messagerie déclenchée par un événement » devient `event-triggered-messaging.md`.
- **Plan d’exécution :** utilisez ` > ` (espace, supérieur à, espace) comme séparateur entre les étapes. Conservez l’étiquette exactement `**Execution plan:**`.
- **Documentation connexe :** regroupez les liens de référence sous des sous-titres `###` descriptifs (par exemple, par application ou domaine de fonctionnalité). Il s’agit des références d’Experience League pour les applications et fonctionnalités utilisées dans le modèle.
- **Architecture (facultatif) :** si un modèle bénéficie d’un diagramme d’architecture de référence, une section de `## Architecture` facultative peut être placée entre `Applications` et `Related documentation`.
- **Portée :** ce modèle exclut intentionnellement les sections d’implémentation détaillées (fonctionnalités fondamentales/de prise en charge/d’application, conditions préalables, options d’implémentation et étapes d’implémentation par phases). Ces détails se trouvent dans la documentation Experience League liée à `Related documentation`.