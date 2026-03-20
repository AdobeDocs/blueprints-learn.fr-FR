---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---
# Pages à mettre à jour lors de l’ajout d’un modèle de cas d’utilisation

Lorsqu’un nouveau modèle de cas d’utilisation est créé, les pages suivantes doivent être mises à jour pour s’assurer que le modèle est détectable et correctement lié.

## Mises à jour requises

### 1. TOC.md
- **Fichier:** `/help/blueprints/TOC.md`
- **Action :** ajoutez une nouvelle entrée sous la section de catégorie appropriée
- **Format:** `    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)`
- **Emplacement par catégorie :**
   - Création et activation d’audience : après la ligne ~47 (après les entrées existantes dans cette section)
   - Personalization : après la ligne ~52
   - Campaign Management et orchestration : après la ligne ~58
   - Analyse : après la ligne ~61
   - Expérience de conversation : après la ligne ~63

#### Mappage catégorie-table des matières

| Slug de catégorie | En-tête de section Table des matières | Ancrer |
| --- | --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation` | `{#audience-building-activation}` |
| `personalization` | `+ Personalization` | `{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration` | `{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis` | `{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience` | `{#conversational-experience-patterns}` |

#### Règles de mise en retrait

- Les en-têtes de catégorie utilisent deux espaces + `+` (par exemple, `  + Personalization{#personalization-patterns}`).
- Les entrées de motif utilisent quatre espaces + `+` (par exemple, `    + [Pattern Title](path)`).

### &#x200B;2. Présentation des modèles de cas d’utilisation
- **Fichier:** `/help/blueprints/use-case-patterns/overview.md`
- **Action :** ajoutez une nouvelle ligne au tableau des catégories approprié
- **Format:** `| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |`
- **Catégories dans la vue d’ensemble :**
   - Création et activation d’une audience (ligne ~18)
   - Personalization (ligne ~29)
   - Gestion et orchestration des campagnes (ligne ~40)
   - Analyse (ligne ~52)
   - Expérience de conversation (ligne ~61)

#### Exemple de format de ligne

```
| [Event-Triggered Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
```

## Liste de contrôle de validation

- [ ] fichier Markdown de motif créé dans le répertoire de catégorie approprié
- [ ] FrontMATTER comprend le titre, la description, la solution et l&#39;exl-id
- [ ] entrée TOC.md ajoutée dans la bonne catégorie
- [ ] ligne de tableau Overview.md ajoutée sous la catégorie appropriée.
- [ ] Tous les liens d’objectifs commerciaux pointent vers des fichiers existants
- [ Le fichier ] utilise la convention de dénomination kebab-case
- [ ] Tous les liens Experience League sont des URL valides
- [ ] noms de produits Adobe utilisent la syntaxe `[!DNL ...]`
- [ ] chaîne de fonction utilise ` > ` format de séparateur
- [ ] fichier pattern comprend toutes les sections requises (voir pattern-template.md)
