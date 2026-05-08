---
source-git-commit: f92cdf8d710acac28d29594f10713e055035cfe9
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---
# Référence d&#39;emplacement TOC.md

Lorsque la compétence génère une nouvelle page de diagramme d’architecture, elle doit ajouter une entrée à `/help/blueprints/TOC.md` afin que la page soit détectable dans la navigation sur le site. Ce document définit exactement où et comment cette entrée est envoyée.

## Section parente

Toutes les pages du diagramme d’architecture sont actives sous la section `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` de niveau supérieur dans TOC.md. Dans cette section, plusieurs sous-sections regroupent les pages par sujet.

## Mappage de sous-section

Sélectionnez la sous-section correspondant au dossier de rubrique de la nouvelle page :

| Dossier du topic | En-tête de sous-section Table des matières |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` (sous-sous-section imbriquée dans `Architecture overviews`) |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

Si l’utilisateur propose un dossier de rubrique qui ne figure pas dans ce tableau, traitez-le comme une nouvelle sous-section de niveau supérieur et mettez-le en pause - demandez à l’utilisateur de confirmer s’il doit le créer. N’inventez pas une nouvelle sous-section en silence.

## Format de saisie

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

Règles :

- **Mise en retrait :** exactement quatre espaces, puis `+ `. L’analyseur de la table des matières en dépend ; les onglets ou un espacement différent interrompront la navigation.
- **Texte du lien :** le titre de la page, correspondant exactement au sujet frontal `title`. Utilisez `[!DNL ...]` uniquement si des frères existants dans la même sous-section l’utilisent ; respectez la convention locale.
- **Cible du lien :** chemin d’accès absolu commençant par `/help/blueprints/`. Incluez toujours l’extension `.md`.
- **Position :** ajoutez comme dernière entrée dans la sous-section correspondante, sauf si l’utilisateur spécifie une position différente. Conserver l’ordre existant de toutes les entrées frères.

## Sous-sections imbriquées

`+ Architecture overviews{#architecture-overview}` contient un bloc de `+ Deployment{#deployment}` imbriqué pour les pages SDK. Si la nouvelle page réside sous `experience-platform/deployment/`, placez l’entrée à l’intérieur de `Deployment` avec **six** espaces de retrait :

```
      + [{Page title}](/help/blueprints/experience-platform/deployment/{filename}.md)
```

Autres paragraphes (`Audience & Profile Activation`, `B2B activation & marketing`, etc.) peut également contenir des regroupements imbriqués : inspectez la section avant de placer l’entrée. Si un groupe imbriqué est présent et que la nouvelle page lui appartient, mettez en retrait deux espaces supplémentaires ; sinon, placez l’entrée au niveau supérieur de la sous-section.

## Exemples de travail

### Exemple 1 : page AEP de niveau supérieur

- Dossier du topic : `experience-platform/`
- Nom de fichier : `mix-modeler-integration.md`
- Titre de la page : `Adobe Mix Modeler integration with Experience Platform`

Entrée :

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/experience-platform/mix-modeler-integration.md)
```

Placé sous `+ Architecture overviews{#architecture-overview}`.

### Exemple 2 : architecture du parcours AJO

- Dossier du topic : `customer-journeys/`
- Nom de fichier : `cross-channel-journey-architecture.md`
- Titre de la page : `Cross-channel journey architecture`

Entrée :

```
    + [Cross-channel journey architecture](/help/blueprints/customer-journeys/cross-channel-journey-architecture.md)
```

Placé sous `+ Customer journeys{#customer-journeys}`.

### Exemple 3 - Page SDK de déploiement

- Dossier du topic : `experience-platform/deployment/`
- Nom de fichier : `mobile-sdk-architecture.md`
- Titre de la page : `Mobile SDK deployment architecture`

Entrée (notez le retrait à six espaces) :

```
      + [Mobile SDK deployment architecture](/help/blueprints/experience-platform/deployment/mobile-sdk-architecture.md)
```

Placé sous `+ Deployment{#deployment}` à l’intérieur du `+ Architecture overviews{#architecture-overview}`.

## Vérification

Après modification du fichier TOC.md, relisez la sous-section concernée et confirmez :

1. La nouvelle entrée utilise exactement quatre espaces de retrait (ou six s’ils sont imbriqués sous `Deployment`).
2. La cible du lien correspond au chemin d’accès au fichier sur le disque, y compris l’extension `.md`.
3. L’entrée est regroupée dans la sous-section appropriée, et non entre des sous-sections.
4. Aucune entrée existante n’a été réorganisée ou modifiée.
