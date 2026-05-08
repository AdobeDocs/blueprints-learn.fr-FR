---
name: architecture-diagram-page-builder
description: 'Guidez la création de pages de diagramme d’architecture pour le référentiel de blueprints Adobe Experience Platform. Utilisez cette compétence lors de l’ajout d’un nouveau diagramme d’architecture de niveau supérieur, d’une page d’architecture d’intégration ou d’une présentation de l’architecture d’application. Les pages Architecture couvrent les architectures AEP et d’application de niveau supérieur, ainsi que les points d’intégration principaux, mais pas les cas d’utilisation détaillés (ceux-ci appartiennent au créateur de modèles de cas d’utilisation). Gère l’ensemble du workflow : collecte des informations sur la page, génération du fichier Markdown, placement dans le dossier de rubrique approprié et mise à jour du fichier TOC.md.'
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 2%

---


# Générateur de page du diagramme d’architecture

Cette compétence guide la création de pages de diagramme d’architecture pour le référentiel de plans directeurs Adobe Experience Platform. Les pages de diagramme d’architecture fournissent des références visuelles de niveau supérieur sur la manière dont les applications AEP et Adobe s’intègrent, les flux de données principaux entre elles et les points d’intégration dont les auteurs doivent tenir compte lors de la conception de solutions.

## Portée

Les pages du diagramme d’architecture sont des **pages de style de référence focalisées** (généralement 40 à 100 lignes de markdown) qui contiennent :

- Un ou plusieurs diagrammes d’architecture avec de brèves explications sur l’objectif de chaque diagramme.
- Liens vers les modèles de cas d’utilisation pris en charge par l’architecture (la page Architecture ne duplique pas ce contenu)
- Une courte liste des flux de données principaux et des points d’intégration illustrés
- Liens Experience League pour une lecture plus approfondie sur le domaine de l’application

Ils ne sont **pas** l’endroit pour le contenu de cas d’utilisation en profondeur. Les KPI, les objectifs commerciaux, les exemples de cas d’utilisation tactique, les chaînes de fonctions et les récits personnels appartiennent plutôt aux pages de modèle de cas d’utilisation, générés via la compétence `use-case-pattern-builder`. Voir `references/scope-guardrails.md` pour les mécanismes de sécurisation complets.

## Lecture requise avant de commencer

Lisez les fichiers de référence suivants pour connaître les modèles et les règles :

- `references/diagram-template.md` : modèle markdown complet avec des valeurs d’espace réservé
- `references/toc-placement.md` — tableau de mappage de sous-section et format d&#39;entrée pour TOC.md
- `references/scope-guardrails.md` — règles pour ce qui appartient à une page d’architecture par rapport à une page de modèle de cas d’utilisation

## Phase 1 : Collecte d&#39;informations

Interrogez l’utilisateur ou l’utilisatrice pour collecter toutes les informations requises avant de générer des fichiers. Ne passez pas à la génération de contenu tant que chaque élément requis n’est pas fourni ou explicitement différé.

### Informations requises

1. **Titre de la page** — Titre lisible par l’utilisateur (par exemple, `Adobe Journey Optimizer architecture diagrams`).

2. **Dossier de rubrique** — Emplacement de la page. Choisissez-en un exactement en fonction du domaine principal du diagramme :
   - `experience-platform/` : diagrammes AEP de niveau supérieur, multi-applications ou de niveau plateforme
   - `customer-journeys/` — AJO, Campaign, orchestration des parcours
   - `customer-journey-analytics/` — Architectures CJA
   - `audience-activation/` — RTCDP, activation des audiences et des profils
   - `b2b/` : architectures spécifiques au B2B

3. **Nom de fichier** — Majuscule, dérivé du titre de la page (par exemple, `Journey Optimizer architecture` -> `journey-optimizer-architecture.md`). Confirmez avec l’utilisateur.

4. **Objectif de la page** — 1 à 2 phrases décrivant ce que les diagrammes illustrent collectivement. Utilisé pour le champ de front-issue `description` et le paragraphe d’ouverture.

5. **Solutions Adobe** — Liste séparée par des virgules des produits Adobe centraux dans la page. Utilisé pour le champ de frontMATTER `solution`. Exemples : `Experience Platform, Journey Optimizer, Customer Journey Analytics`.

6. **Diagrammes** — Un ou plusieurs diagrammes. Pour chaque diagramme, collectez :
   - **Nom du fichier image** (par exemple, `aep_data_flow.svg`). SVG préféré ; PNG acceptable.
   - **Titre de la section** — devient l&#39;en-tête H2 du diagramme (par exemple `Data flow diagram`, `Detailed architecture diagram`).
   - **Explication de l’objectif** — 1 à 2 phrases décrivant ce que le diagramme montre.
   - **Texte de remplacement** — Description courte accessible.

7. **Modèles de cas d’utilisation pris en charge** — 2 à 5 modèles existants activés par cette architecture.

   **Recommander les candidats en premier.** Avant de demander à l’utilisateur de fournir des modèles, numérisez les `/help/blueprints/use-case-patterns/` et proposez 3 à 6 correspondances probables en fonction du titre de la page, de l’objectif de la page et des solutions Adobe collectées ci-dessus. Pour chaque suggestion, présentez :
   - Nom du modèle (avec le chemin d’accès lié)
   - Explication en une seule phrase expliquant pourquoi il s’adapte à cette architecture

   Présentez les suggestions sous forme de liste restreinte numérotée et demandez à l’utilisateur (a) d’accepter les suggestions, (b) de les rejeter et (c) d’ajouter les modèles que vous avez manqués. Générez uniquement des suggestions qui pointent vers des fichiers réels — glob/read pour confirmer avant de suggérer. Ne pas halluciner les noms des motifs.

   Pour chaque modèle accepté, capturez la catégorie et le nom de fichier. Vérifiez que chaque fichier existe à l’emplacement `/help/blueprints/use-case-patterns/{category}/{pattern-file}.md` avant de le générer.

8. **Flux de données de Principal/points d’intégration** — 3 à 7 puces décrivant les flux clés et les limites d’intégration affichés sur les diagrammes (par exemple, `Real-time event ingestion from Web SDK to Edge Network`, `Profile synchronization between Experience Platform Hub and Edge`).

9. **Liens Experience League** — 3 à 6 liens vers la documentation Experience League pertinente pour une lecture plus approfondie. Chaque doit commencer par `https://experienceleague.adobe.com/fr`.

   **Recommander les candidats en premier.** En fonction des solutions Adobe et de l’objectif de la page, proposez 4 à 8 articles Experience League plausibles (par exemple, les pages de destination ou d’aperçu canoniques pour chaque solution nommée, les guides d’intégration clés, les références de déploiement). Pour chaque suggestion, présentez :
   - Titre de l’article
   - URL
   - Justification en une ligne de la pertinence de la page

   Marquez les suggestions comme **non vérifiées** à moins que vous n’ayez réellement récupéré l’URL. L’utilisateur doit confirmer ou remplacer chacune d’elles avant qu’elle n’arrive dans le fichier généré. Demandez à l’utilisateur ou à l’utilisatrice de (a) accepter, (b) remplacer toute URL par une URL vérifiée qu’il ou elle a déjà et (c) ajouter la sienne. N’inventez jamais des URL que vous n’avez pas vues. Si vous n’êtes pas sûr, suggérez le titre de l’article et laissez l’utilisateur ou l’utilisatrice fournir l’URL.

### Facultatif

- **Légende du contenu associé** : lien unique rendu sous forme `>[!MORELIKETHIS]` bloc en haut de la page. Utile lorsqu’il existe un guide d’intégration ou de configuration frère sur Experience League que le lecteur doit connaître.

Si l’utilisateur ne fournit pas tous les éléments requis, demandez les éléments manquants avant de continuer. Ne fabriquez pas de diagrammes, de modèles ou de liens.

## Phase 2 : vérification de la portée

Avant de générer, lisez à nouveau les descriptions des diagrammes de l’utilisateur, les puces du flux de données et tout brouillon de prose. Appliquez les mécanismes de sécurisation à partir de `references/scope-guardrails.md`.

Si l’un des éléments suivants apparaît dans le contenu prévu, avertissez l’utilisateur et proposez de rediriger cette section vers une page de modèle de cas d’utilisation (ou de la supprimer de la page d’architecture) :

- KPI ou formules de mesure
- Objectifs commerciaux ou narratifs de l’impact commercial
- Exemples de cas d’utilisation tactiques (scénarios de personnalisation spécifiques, exemples de campagnes, etc.)
- Chaînes de fonctions (style `A > B > C > D`)
- Storytelling piloté par les personas

Si le contenu prévu reste dans la portée architecture-page (architecture de niveau supérieur, flux de données système, points d’intégration, topologie de déploiement, edge par rapport au hub), confirmez auprès de l’utilisateur et passez à la Phase 3.

## Phase 3 : génération de contenu

Générez la page à l’adresse :

```
/help/blueprints/{topic-folder}/{kebab-filename}.md
```

Utilisez `references/diagram-template.md` comme modèle source. Renseignez toutes les valeurs d’espace réservé avec les informations collectées. Le fichier généré doit inclure :

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

Lisez la `references/toc-placement.md` pour le tableau et les règles de mappage de sous-section complets. Résumé :

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

## Phase 5 : validation

Une fois tous les fichiers créés et mis à jour, vérifiez les points suivants et signalez-les à l’utilisateur :

1. **Existence d’une ressource d’image** — Pour chaque diagramme, vérifiez que `/help/blueprints/{topic-folder}/assets/{filename}` existe. **Avertir** en cas d&#39;absence, ne pas bloquer (l&#39;utilisateur peut créer en parallèle avec la conception du diagramme). Affichez une liste claire des fichiers manquants afin que l’utilisateur sache quoi ajouter.

2. **Liens de modèle de cas d’utilisation** — Chaque lien de modèle dans le fichier pointe vers un fichier Markdown existant sous `/help/blueprints/use-case-patterns/`. Utilisez `Read` ou glob pour confirmer que chaque cible existe.

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
- Si le diagramme d’architecture documente de manière exhaustive un *cas d’utilisation unique de bout en bout* (avec des indicateurs de performance clés, des objectifs commerciaux, une chaîne de fonctions), redirigez l’utilisateur vers `use-case-pattern-builder`, qui n’est pas une page d’architecture.
