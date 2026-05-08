---
source-git-commit: f92cdf8d710acac28d29594f10713e055035cfe9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---
# Modèle de page du diagramme d’architecture

Il s’agit du modèle Markdown complet d’une page de diagramme d’architecture. Remplacez chaque `{placeholder}` par la valeur collectée lors de la phase 1 du workflow de compétence. Supprimez toute section facultative qui ne s’applique pas (par exemple, le bloc `>[!MORELIKETHIS]`) — ne laissez pas d’espaces réservés vides dans le fichier généré.

&#x200B;---

```markdown
---
title: {Page title}
description: {1-2 sentence page purpose, used for search snippets and previews}
solution: {Comma-separated Adobe solutions, e.g. Experience Platform, Journey Optimizer, Customer Journey Analytics}
---
# {Page title}

{Opening paragraph -- 1-2 sentences describing what the diagrams collectively illustrate. Frame the page as a top-level architecture reference, not a use case walkthrough.}

>[!MORELIKETHIS]
>
>[{Related-content link text}]({Related-content URL}).

## {Diagram 1 section title}

{1-2 sentence explanation of what the diagram shows and why it matters.}

<img src="assets/{filename-1}" alt="{Alt text for diagram 1}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## {Diagram 2 section title}

{1-2 sentence explanation.}

<img src="assets/{filename-2}" alt="{Alt text for diagram 2}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Primary data flows and integration points

- {Flow or integration 1 -- e.g., "Real-time event ingestion from [!DNL Web SDK] to [!DNL Edge Network]"}
- {Flow or integration 2 -- e.g., "Profile sync between [!DNL Experience Platform] Hub and Edge"}
- {Flow or integration 3}
- {Flow or integration 4}
- {Flow or integration 5}

## Use case patterns supported

The architecture above supports the following use case patterns:

- [{Pattern 1 name}](/help/blueprints/use-case-patterns/{category}/{pattern-1-file}.md) -- {1-line note on why this architecture enables the pattern}
- [{Pattern 2 name}](/help/blueprints/use-case-patterns/{category}/{pattern-2-file}.md) -- {1-line note}
- [{Pattern 3 name}](/help/blueprints/use-case-patterns/{category}/{pattern-3-file}.md) -- {1-line note}

## Further reading

- [{Article 1 title}]({Experience League URL 1})
- [{Article 2 title}]({Experience League URL 2})
- [{Article 3 title}]({Experience League URL 3})
```

&#x200B;---

## Règles de FrontMATTER

- **Champs obligatoires** : `title`, `description`, `solution`.
- **Champs interdits** (affectés automatiquement à la publication) : `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt`, `thumbnail`. Ne les incluez pas dans les fichiers nouvellement créés.

## Conventions de corps

- **Un H1** — Titre de la page. Correspondre exactement à la matière frontale `title`.
- **Un H2 par diagramme.** Pas de H3 à l&#39;intérieur des sections de diagramme ; conservez-les à une introduction de 1 à 2 phrases plus l&#39;image.
- **`<img>`incorporer** : le style et les `class="modal-image"` intégrés sont requis. Ils pilotent l’interaction modale-zoom d’Experience League.
- **Chemin de l’image** — Toujours `assets/{filename}` (par rapport au dossier de rubrique de la page). N’utilisez pas de chemins absolus.
- **Noms de produits Adobe** — encapsulez les `[!DNL ...]` dans le corps du texte et les puces. Exemple : `[!DNL Real-Time CDP]`, `[!DNL Journey Optimizer]`, `[!DNL Experience Platform]`.
- **Liens de modèle de cas d’utilisation** — utilisez toujours le formulaire `/help/blueprints/use-case-patterns/{category}/{file}.md` absolu afin que le lien soit résolu à partir de toute page susceptible de transclure ce contenu.
- **Liens Experience League** — URL absolues commençant par `https://experienceleague.adobe.com/fr`. Préférez l’URL de document canonique à une variante localisée.

## Ordre des sections

Conservez la cohérence de l’ordre sur toutes les pages d’architecture afin que les lecteurs puissent l’analyser de manière prévisible :

1. Matière Première
2. H1 + paragraphe d’ouverture
3. (Facultatif) Légende `>[!MORELIKETHIS]`
4. Un H2 par diagramme (dans l&#39;ordre spécifié par l&#39;utilisateur)
5. `## Use case patterns supported`
6. `## Primary data flows and integration points`
7. `## Further reading`

## Attentes de longueur

40 à 100 lignes de markdown sont typiques. Si la page dépasse 150 lignes, le contenu a probablement dérivé en territoire de modèle de cas d’utilisation — revérifiez les `scope-guardrails.md` et envisagez de diviser.
