---
name: architecture-diagram-page-builder
description: 'Guidez la création de pages de diagramme d’architecture pour le référentiel de blueprints Adobe Experience Platform. Utilisez cette compétence lors de l’ajout d’un nouveau diagramme d’architecture de niveau supérieur, d’une page d’architecture d’intégration ou d’une présentation de l’architecture d’application. Les pages Architecture couvrent les architectures AEP et d’application de niveau supérieur, ainsi que les points d’intégration principaux, mais pas les cas d’utilisation détaillés (ceux-ci appartiennent au créateur de modèles de cas d’utilisation). Gère l’ensemble du workflow : collecte des informations sur la page, génération du fichier Markdown, placement dans le dossier de rubrique approprié et mise à jour du fichier TOC.md.'
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%
---

# Générateur de page du diagramme d’architecture

Cette compétence guide la création de pages de diagramme d’architecture pour le référentiel de plans directeurs Adobe Experience Platform. Les pages de diagramme d’architecture fournissent des références visuelles de niveau supérieur sur la manière dont les applications AEP et Adobe s’intègrent, les flux de données principaux entre elles et les points d’intégration dont les auteurs doivent tenir compte lors de la conception de solutions.

## Portée

Les pages du diagramme d’architecture sont des **pages de style de référence focalisées** (généralement 40 à 100 lignes de markdown) qui contiennent :

- Un ou plusieurs diagrammes d’architecture avec de brèves explications sur l’objectif de chaque diagramme.
- Liens vers les modèles de cas d’utilisation pris en charge par l’architecture (la page Architecture ne duplique pas ce contenu)
- Une courte liste des flux de données principaux et des points d’intégration illustrés
- Liens Experience League pour une lecture plus approfondie sur le domaine de l’application

Ils ne sont **pas** l’endroit pour le contenu de cas d’utilisation en profondeur. Les KPI, les objectifs commerciaux, les exemples de cas d’utilisation tactique, les fonctionnalités et les récits personnels appartiennent plutôt aux pages de modèle de cas d’utilisation, générées via la compétence `use-case-pattern-builder`. Voir `./references/scope-guardrails.md` pour les mécanismes de sécurisation complets.

## Lecture requise avant de commencer

Lisez les fichiers de référence suivants pour connaître les modèles et les règles :

- `./references/diagram-template.md` : modèle markdown complet avec des valeurs d’espace réservé
- `./references/toc-placement.md` — tableau de mappage de sous-section et format d&#39;entrée pour TOC.md
- `./references/scope-guardrails.md` — règles pour ce qui appartient à une page d’architecture par rapport à une page de modèle de cas d’utilisation

## Phase 1 : Collecte d&#39;informations

**Utilisez le formulaire de question disponible, et non un entretien linéaire.** Collectez toutes les informations requises par lots logiques plutôt que de poser une question à la fois. Cela permet à l’utilisateur de disposer d’une expérience rapide et analysable.

### Contraintes de formulaire de question

- Maximum de **4 questions** par formulaire.
- Options **4 maximum** par question.
- Si une question comporte plus de 4 options plausibles, divisez-la en deux appels (par exemple, posez les 4 premières options, puis suivez avec un oui/non sur le cinquième).
- Utilisez des `multiSelect: true` pour les questions auxquelles plusieurs réponses s’appliquent (solutions, modèles, flux de données).

### Première session — Informations sur la page principale (un formulaire de question, jusqu’à 4 questions)

Demandez tous les éléments suivants dans un seul formulaire :

1. **Titre de la page** — présentez 2 à 3 variantes suggérées dérivées de ce que l’utilisateur vous a déjà dit, plus une trappe d’échappement « Autre ».
2. **Dossier de sujets** — Présentez les 5 dossiers valides comme options ; recommandez le plus probable en fonction de l&#39;entrée de l&#39;utilisateur.
3. **Solutions Adobe** - sélection multiple ; suggérez les candidats les plus probables en fonction du sujet de la page.
4. **Nombre de diagrammes** — Nombre de diagrammes inclus dans la page (1/2/3/4+).

### Deuxième session — Détails du diagramme (un formulaire de question, jusqu&#39;à 4 questions)

Demandez le nom de fichier image de chaque diagramme et l’objectif de la page dans un seul formulaire :

- Pour chaque diagramme (jusqu’à 2 dans un seul tour de formulaire), demandez le **nom de fichier de l’image** sous la forme d’une question avec 2 à 3 noms de fichier suggérés (dérivés du titre de la page) plus une option « Autre ».
- Demandez la **fonction de la page** (description de 1 à 2 phrases) sous forme de question avec 2 à 3 phrases suggérées plus « Autre ».
- Demandez si une légende **est nécessaire (Oui/Non).**`>[!MORELIKETHIS]` Si oui, collectez l’URL et le texte du lien dans un message de relance.

> **Titres de section et texte de remplacement :** lorsque le nom de fichier de l’image est descriptif (par exemple, `fac-architecture.svg`, `fac-dataflow.svg`), déduisez le titre de la section H2 et le texte de remplacement ; il n’est pas nécessaire de demander à l’utilisateur. Utilisez la tige du nom de fichier, avec la casse du titre et l’humanisation, comme titre de section (par exemple, `Architecture diagram`, `Data flow diagram`). Ne demandez que si le nom de fichier est ambigu.

### Troisième session — Modèles de cas d’utilisation (formulaire de question après numérisation)

Avant de présenter ce formulaire, recherchez `/help/blueprints/use-case-patterns/` et identifiez 3 à 5 modèles correspondants probables en fonction du titre de la page, de l’objectif et des solutions. Vérifiez que chaque fichier existe avant de le suggérer.

Présentez les 4 meilleurs candidats comme une question `multiSelect`. S&#39;il existe un cinquième candidat solide, répondez par oui ou par non à une autre question. Invitez également l’utilisateur à nommer le modèle que vous avez manqué.

N’incluez que les modèles dont l’existence des fichiers est confirmée. Ne pas halluciner les noms des motifs.

### Round 4 — Flux de données et liens Experience League (une question)

**Flux de données :** proposez 3 à 5 puces de flux de données préécrites comme question `multiSelect` (dérivée de la rubrique de page). L’utilisateur ou l’utilisatrice sélectionne l’application. Conservez chaque option dans une phrase concise. Si l’utilisateur a besoin de flux personnalisés qui ne figurent pas dans votre liste, il peut les fournir dans une relance.

**Liens Experience League :** après le formulaire, présentez un tableau Markdown de 4 à 6 liens suggérés avec le titre de l’article, l’URL et une justification en une ligne. Marquez chaque URL comme **non vérifiée**. Demandez à l’utilisateur (a) d’accepter, (b) de remplacer par une URL vérifiée, ou (c) d’ajouter la sienne. Utilisez un formulaire de question complémentaire comportant jusqu’à 4 options si la liste est longue ; sinon, acceptez la confirmation en texte brut.

N’inventez jamais d’URL que vous n’avez pas récupérées. Si vous n’êtes pas sûr, suggérez le titre de l’article et laissez l’utilisateur fournir l’URL.

### Lorsque tous les tours sont terminés

Confirmez la totalité des informations définies avec l’utilisateur avant de générer des fichiers. Si un élément requis est toujours manquant ou marqué comme « Autre » sans valeur, demandez-le avant de continuer. Ne fabriquez pas de diagrammes, de modèles ou de liens.

## Phase 2 : vérification de la portée

Avant de générer, lisez à nouveau les descriptions des diagrammes de l’utilisateur, les puces du flux de données et tout brouillon de prose. Appliquez les mécanismes de sécurisation à partir de `./references/scope-guardrails.md`.

Si l’un des éléments suivants apparaît dans le contenu prévu, avertissez l’utilisateur et proposez de rediriger cette section vers une page de modèle de cas d’utilisation (ou de la supprimer de la page d’architecture) :

- KPI ou formules de mesure
- Objectifs commerciaux ou narratifs de l’impact commercial
- Exemples de cas d’utilisation tactiques (scénarios de personnalisation spécifiques, exemples de campagnes, etc.)
- Fonctionnalités (style `A > B > C > D`)
- Storytelling piloté par les personas

Si le contenu prévu reste dans la portée architecture-page (architecture de niveau supérieur, flux de données système, points d’intégration, topologie de déploiement, edge par rapport au hub), confirmez auprès de l’utilisateur et passez à la Phase 3.

## Phase 3 : génération de contenu

Générez la page à l’adresse :

```
/help/blueprints/{topic-folder}/{kebab-filename}.md
```

Utilisez `./references/diagram-template.md` comme modèle source. Renseignez toutes les valeurs d’espace réservé avec les informations collectées. Le fichier généré doit inclure :

1. **frontMATTER YAML** — `title`, `description`, `solution` uniquement.
   - **Ne pas inclure`exl-id`** : le pipeline de publication l’affecte automatiquement.
   - **N’incluez PAS** `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt` ou `thumbnail` - elles sont également automatiquement renseignées.

2. en-tête **H1** — titre de la page.

3. **Paragraphe d’ouverture** — 1 à 2 phrases dérivées de l’entrée page-objectif.

4. **Bloc de `>[!MORELIKETHIS]` facultatif** — uniquement si l’utilisateur a fourni un lien vers le contenu associé.

5. **Une section H2 par diagramme** — dans l’ordre dans lequel l’utilisateur les a fournies. Chaque section contient :
   - Titre de la section comme en-tête H2
   - 1 à 2 phrases expliquant l’objectif du diagramme
   - L’image est incorporée selon la convention standard :

     ```html
     <img src="assets/{filename}" alt="{Alt Text}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />
     ```

6. **`## Use case patterns supported`** — liste à puces. Chaque puce :

   ```
   - [{Pattern name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) -- {1-line note on why this architecture enables the pattern}
   ```

7. **`## Primary data flows and integration points`** : liste à puces de 3 à 7 éléments de flux/intégration.

8. **`## Further reading`** — liste à puces des liens Experience League :

   ```
   - [{Article title}]({Experience League URL})
   ```

Utilisez la syntaxe `[!DNL ...]` pour les noms de produits Adobe dans le corps du texte et les puces, en respectant la convention des pages existantes.

## Phase 4 : mises à jour des références croisées

Mettez à jour **`/help/blueprints/TOC.md`** pour ajouter la nouvelle page à la navigation. Il s’agit de la seule page de référence croisée à mettre à jour.

Lisez la `./references/toc-placement.md` pour le tableau et les règles de mappage de sous-section complets. Résumé :

| Dossier du topic | Sous-section Table des matières |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` (sous-sous-section des vues d’ensemble de l’architecture) |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

Format d’entrée (retrait de 4 espaces + `+`) :

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

Ajoutez la nouvelle entrée en tant que dernier élément de la sous-section correspondante, sauf si l&#39;utilisateur spécifie un autre poste. Conserver la mise en retrait exacte de 4 espaces ; l’analyse de la table des matières en dépend.

**Rechercher les sous-groupes imbriqués avant de placer.** Certaines sous-sections (notamment `Audience & Profile Activation`) contiennent des regroupements imbriqués (par exemple, `Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}`). Lisez la sous-section concernée du fichier TOC.md avant de la modifier. Les nouvelles pages d’architecture de niveau supérieur appartiennent au niveau de retrait de 4 espaces de la sous-section , **pas** à l’intérieur d’un sous-groupe imbriqué (qui utilise un retrait de 6 espaces). Placez la nouvelle entrée après la dernière entrée de sous-groupe imbriquée et avant l’en-tête de sous-groupe de niveau supérieur suivant.

## Phase 5 : validation

Une fois tous les fichiers créés et mis à jour, vérifiez les points suivants et signalez-les à l’utilisateur :

1. **Existence d’une ressource d’image** — Pour chaque diagramme, vérifiez que `/help/blueprints/{topic-folder}/assets/{filename}` existe. **Avertir** en cas d&#39;absence, ne pas bloquer (l&#39;utilisateur peut créer en parallèle avec la conception du diagramme). Affichez une liste claire des fichiers manquants afin que l’utilisateur sache quoi ajouter.

2. **Liens de modèle de cas d’utilisation** — Chaque lien de modèle dans le fichier pointe vers un fichier Markdown existant sous `/help/blueprints/use-case-patterns/`. Utilisez la recherche d’espace de travail ou la lecture de fichier pour confirmer l’existence de chaque cible.

3. **Liens Experience League** — Vérifiez que chaque URL de la section `## Further reading` commence par `https://experienceleague.adobe.com/fr`.

4. **Emplacement de l&#39;entrée de table des matières** — La nouvelle entrée se trouve à l&#39;intérieur de la sous-section appropriée, utilise une mise en retrait de 4 espaces et le chemin correspond exactement à l&#39;emplacement du fichier généré.

5. **Dénomination du fichier** — Le nom du fichier de la page est en majuscules et correspond au chemin d&#39;accès référencé dans le fichier TOC.md.

6. **Exhaustivité de FrontMATTER** — La page comprend `title`, `description` et `solution`. Il ne doit **pas** inclure `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt` ou `thumbnail`.

Résolvez les problèmes de validation avant de considérer la tâche comme terminée.

## Remarques

- Utilisez toujours la syntaxe `[!DNL ...]` pour les noms de produits Adobe dans le corps du texte et les puces, en respectant la convention des pages existantes.
- Les diagrammes d’architecture sont généralement SVG (préférés pour leur netteté et leur mise à l’échelle), mais PNG est acceptable pour les illustrations à source matricielle.
- Les `class="modal-image"` et la chaîne de style intégrée `<img>` (`border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;`) sont nécessaires ; ils activent l’interaction modale-zoom d’Experience League.
- Si l’utilisateur crée une page pour un tout nouveau dossier de rubrique qui n’existe pas encore, avertissez-le que TOC.md requiert une nouvelle sous-section de niveau supérieur sous `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`. Gérer cela comme une étape distincte avec l’approbation explicite de l’utilisateur.
- Si le diagramme d’architecture documente de manière exhaustive un *cas d’utilisation unique de bout en bout* (avec des indicateurs de performance clés, des objectifs commerciaux et des fonctionnalités), redirigez l’utilisateur vers `use-case-pattern-builder`, qui n’est pas une page d’architecture.
