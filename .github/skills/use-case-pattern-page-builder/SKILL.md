---
name: use-case-pattern-page-builder
description: 'Guidez la création de contenu de modèle de cas d’utilisation pour le référentiel de plans directeurs Adobe Experience Platform. Utilisez cette compétence lors de l’ajout d’un nouveau modèle de cas d’utilisation, de la création de contenu de guide d’implémentation ou lorsque l’utilisateur mentionne l’ajout de modèles au site de plans directeurs. Gère l’ensemble du workflow : collecte des informations de modèle, génération du fichier Markdown avec la structure de modèle appropriée et mise à jour de toutes les pages de référence croisée (TOC.md, overview.md).'
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 92%
---

# Modèle de cas d’utilisation de Page Builder

Cette compétence guide la création d’un modèle de cas d’utilisation pour le référentiel de plans directeurs Adobe Experience Platform. Il gère l’ensemble du workflow : la collecte des informations de modèle auprès de l’utilisateur ou de l’utilisatrice, la génération du fichier de contenu Markdown avec la structure de modèle appropriée et la mise à jour de toutes les pages de référence croisée afin que le nouveau modèle soit détectable.

Avant de commencer, lisez les fichiers de référence suivants pour connaître la structure complète du modèle et la liste de contrôle des pages à mettre à jour :

- `./references/pattern-template.md` : modèle markdown complet avec des valeurs d’espace réservé
- `./references/pages-to-update.md` : liste de contrôle des pages qui doivent être mises à jour lors de l’ajout d’un modèle

## Phase 1 : Collecte d&#39;informations

Interrogez l’utilisateur ou l’utilisatrice pour collecter toutes les informations requises avant de générer des fichiers. Demandez les éléments suivants et ne passez pas à la génération de contenu tant que chaque élément n’est pas fourni ou explicitement différé.

### Informations requises

1. **Nom du modèle** — Titre lisible par l&#39;utilisateur (par exemple, « Message déclenché par un événement »).

2. **Catégorie** — Exactement l&#39;un des éléments suivants :
   - `audience-building-activation`
   - `personalization`
   - `campaign-management-orchestration`
   - `analysis`
   - `conversational-experience`

3. **Description des fonctionnalités de Principal** — Une seule phrase décrivant ce que fait ce modèle (utilisée dans le tableau de présentation et la description du front-issue).

4. **Solutions Adobe principales** — Les produits Adobe sont au cœur de ce modèle. Choisissez l’une des options suivantes : Journey Optimizer, Real-Time Customer Data Platform, Experience Platform, Customer Journey Analytics, Brand Concierge, Journey Optimizer B2B edition, Real-Time CDP B2B edition ou d’autres, selon les besoins.

5. **Objectifs commerciaux pris en charge** — Un ou plusieurs objectifs commerciaux de l’ensemble existant visé par le `/help/blueprints/business-objectives/`. Chaque doit inclure le nom de l’objectif, le sous-dossier de la catégorie et le nom de fichier. Vérifiez que les fichiers référencés existent avant de générer le contenu.

6. **Exemples de cas d’utilisation tactiques** — Scénarios à 6-10 puces décrivant comment ce modèle peut être appliqué à différents contextes d’entreprise. Chaque scénario doit comporter un nom en gras suivi d’une description.

7. **KPIs** — Un tableau avec trois colonnes : KPI (nom), Description (ce qu&#39;il mesure), Mesure (formule ou approche).

8. **Liens de référence** : liens de référence vers des documents Experience League principaux couvrant les applications et les fonctionnalités du modèle de cas d’utilisation.

### Facultatif mais recommandé

- Paragraphes de présentation des cas d’utilisation (3 à 5 paragraphes ; si ces paragraphes ne sont pas fournis, rédigez-les à partir des autres informations)
- Liste des applications avec des descriptions du rôle de chaque application Adobe

Si l’utilisateur ne fournit pas les éléments facultatifs , générez des valeurs par défaut raisonnables en fonction de la catégorie de modèle, des solutions et du plan d’exécution.

## Phase 2 : génération de contenu

Générez le fichier Markdown de modèle à l’emplacement suivant :

```
/help/blueprints/use-case-patterns/{category}/{kebab-case-pattern-name}.md
```

Le nom de fichier doit utiliser la casse kebab dérivée du nom du modèle. Par exemple, la mention « Message déclenché par un événement » devient `event-triggered-messaging.md`.

Utilisez le modèle de `./references/pattern-template.md` et renseignez toutes les valeurs d’espace réservé avec les informations collectées. Le fichier généré doit inclure chaque section du modèle :

1. **FrontMATTER YAML** — titre, description, solution (séparée par des virgules), exl-id (générez un espace réservé UUID comme `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` — l&#39;équipe de publication attribuera le vrai).

2. **Section d&#39;ouverture** — `# {Pattern name}` titre suivi d&#39;un paragraphe d&#39;introduction et du guide « Utilisez ce guide pour comprendre... » phrase.

3. **Modèle de cas d’utilisation** — Paragraphe de description et plan d’exécution.

4. **Présentation des cas d’utilisation** : 3 à 5 paragraphes décrivant la portée du modèle, le moment où il s’applique, ce qu’il fait ou ne fait pas et qui sont les parties prenantes standard.

5. **Objectifs commerciaux clés** — Chaque objectif est un en-tête lié avec une brève description et une ligne de résumé des indicateurs de performance clés.

6. **Exemples de cas d’utilisation tactique** — Liste à puces de 6 à 10 scénarios.

7. **Indicateurs clés de performance** — Tableau avec indicateurs clés de performance, description, colonnes de mesure.

8. **Applications** — Liste des applications Adobe avec formatage et descriptions `[!DNL ...]`.

## Phase 3 : Mises À Jour Des Références Croisées

Après avoir généré le fichier de modèle, mettez à jour les fichiers suivants. Lisez `./references/pages-to-update.md` pour obtenir la liste de contrôle détaillée.

### TOC.md

**Fichier:** `/help/blueprints/TOC.md`

Ajoutez une nouvelle entrée sous la section de catégorie appropriée. Les catégories correspondent aux sections de la table des matières suivantes :

| Slug de catégorie | En-tête de section Table des matières |
| --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation{#audience-building-activation}` |
| `personalization` | `+ Personalization{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience{#conversational-experience-patterns}` |

Le format de saisie est :

```
    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)
```

Ajoutez la nouvelle entrée après la dernière entrée existante dans la section correspondante. Conservez la mise en retrait exacte (quatre espaces avant la `+`).

### Page Aperçu

**Fichier:** `/help/blueprints/use-case-patterns/overview.md`

Ajoutez une nouvelle ligne au tableau des catégories approprié. Le format est :

```
| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |
```

Ajoutez la nouvelle ligne après la dernière ligne existante dans le tableau de catégorie correspondant.

## Phase 4 : validation

Une fois tous les fichiers créés et mis à jour, vérifiez les points suivants :

1. **Liens d&#39;objectifs commerciaux** — Chaque lien d&#39;objectif commercial dans le fichier de modèle pointe vers un fichier existant sous `/help/blueprints/business-objectives/`. Utilisez la recherche d’espace de travail ou la lecture de fichier pour confirmer l’existence de chaque fichier cible.

2. **Emplacement de l&#39;entrée de la table des matières** — La nouvelle entrée de la table des matières se trouve dans la section de catégorie appropriée et utilise la mise en retrait et le format de chemin corrects.

3. **Ligne du tableau d&#39;aperçu** — La nouvelle ligne d&#39;aperçu se trouve dans le tableau de catégorie approprié et suit le même format de colonne que les lignes existantes.

4. **Dénomination du fichier** — Le nom du fichier de modèle utilise la casse kebab et correspond au chemin d&#39;accès référencé dans TOC.md et overview.md.

5. **Exhaustivité de FrontMATTER** — Le fichier de motifs comprend le titre, la description, la solution et l&#39;exl-id dans son frontMATTER YAML.

6. **Liens Experience League** — Vérifiez que toutes les URL Experience League sont plausibles (en commençant par `https://experienceleague.adobe.com/`).

Signalez à l’utilisateur les échecs de validation et corrigez-les avant de considérer la tâche comme terminée.

## Remarques

- Utilisez toujours la syntaxe `[!DNL ...]` pour les noms de produits Adobe dans les tableaux et le corps de texte, en respectant la convention des fichiers de modèle existants.
- L’`exl-id` dans frontend doit être un UUID d’espace réservé. Le pipeline de publication attribue la valeur réelle.
- Si l’utilisateur souhaite créer plusieurs modèles à la fois, répétez les phases 2 à 4 pour chaque modèle, mais collectez toutes les informations au cours de la phase 1.
- Si vous avez besoin d&#39;une nouvelle catégorie qui n&#39;existe pas dans la liste ci-dessus, avertissez l&#39;utilisateur que TOC.md et overview.md auront besoin de nouvelles sections créées, et traitez cela comme une étape distincte.
