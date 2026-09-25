---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%
---
# Conventions de dénomination : schémas et plans directeurs d’architecture

Ce document est la source de vérité sur la manière dont les catégories sous `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` sont nommées. La compétence `architecture-diagram-category-builder` (nouvelles catégories) et la compétence `architecture-diagram-page-builder` (nouvelles pages dans les catégories existantes) doivent toutes deux suivre ces règles.

## La règle

**Nom du dossier = rappel de la table des matières = kebab-case du libellé complet de la table des matières.** Les trois doivent correspondre exactement, sans abréviation ni troncature.

| Libellé de la table des matières | Ancrer | Dossier |
| --- | --- | --- |
| Aperçu de l’architecture | `#architecture-overviews` | `architecture-overviews/` |
| Activation d’audience et de profil | `#audience-profile-activation` | `audience-profile-activation/` |
| Activation et marketing B2B | `#b2b-activation-marketing` | `b2b-activation-marketing/` |
| Informations sur le client | `#customer-insights` | `customer-insights/` |
| Parcours client | `#customer-journeys` | `customer-journeys/` |

Il s&#39;agit de l&#39;état actuel corrigé des cinq catégories (en date du 16 septembre 2026). Plus tôt dans l&#39;histoire de ce référentiel, certains d&#39;entre eux ont été abrégés (`architecture-overview`, `audience-activation`, `b2b-activation`) — que l&#39;incohérence a été corrigée. Ne réintroduisez pas de noms de dossier/ancre abrégés pour les catégories nouvelles ou existantes.

## Pourquoi cela est important

- **Prévisibilité.** Un contributeur (humain ou agent) doit pouvoir deviner le chemin du dossier à partir du libellé de la table des matières, et vice versa, sans ouvrir TOC.md.
- **Automatisation sécurisée.** Les compétences et les scripts qui génèrent des chemins à partir des libellés (ou des libellés à partir des chemins) ne fonctionnent de manière fiable que lorsque le mappage est exact et mécanique (casse de kebab, aucune abréviation).
- **Hygiène des redirections.** Chaque changement de nom nécessite de nouvelles entrées dans `redirects.csv`. Le fait de conserver des noms stables et entièrement descriptifs dès le début évite une perte de noms répétée.

## Comment dériver un slug d’un libellé

1. Mettez le libellé en minuscules.
2. Déposez `&` entièrement et joignez les mots environnants par un trait d’union (par exemple `Audience & Profile Activation` -> `audience-profile-activation`).
3. Remplacez les espaces par des tirets.
4. Ponctuation en bandes autre que les tirets.
5. N’abrégez pas, ne tronquez pas ou ne supprimez pas de mots de l’étiquette (aucune `b2b-activation` pour « Activation et marketing B2B » — utilisez `b2b-activation-marketing`).

## Ressources par catégorie requises

Chaque dossier de catégorie directement sous `help/blueprints/architecture-diagrams/` doit contenir :

1. **`overview.md`** : une page de destination pour la catégorie. Voir `./category-overview-template.md` pour la structure requise. Chaque page d’aperçu de catégorie doit ressembler à un paragraphe d’introduction, puis à un seul tableau de `| Diagram | Description |` répertoriant chaque page de la catégorie (dans l’ordre de la table des matières). N’utilisez pas de cellules `<ul><li>` imbriquées, d’images de diagramme incorporé ou d’une troisième colonne. Correspondez exactement aux cinq catégories existantes.
2. **`assets/`** — dossier pour les images du diagramme, même si vide au moment de la création (créez-le une fois le premier diagramme ajouté).

## Exigences relatives à TOC.md

- L’entrée `+ [Overview](/help/blueprints/architecture-diagrams/{folder}/overview.md)` de la catégorie est toujours la **première** entrée sous l’en-tête de catégorie, avant toute page de contenu.
- L&#39;en-tête de catégorie et son ancre passent immédiatement sous `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`, au même niveau de retrait de 2 espaces que les cinq autres catégories.
- Les pages de contenu comportent 4 espaces mis en retrait (`+` précédés de quatre espaces au début). Les sous-regroupements imbriqués (par exemple, le regroupement RTCDP sous Activation d’audience et de profil) sont constitués de 6 espaces mis en retrait.

## Exigences relatives aux pages de destination

`help/blueprints/architecture-diagrams/overview.md` (la page de destination des schémas d’architecture et des plans directeurs de niveau supérieur) doit comporter exactement une carte par catégorie, dans l’ordre de la table des matières. Chaque carte :

- Liens vers le `overview.md` de la catégorie (et non vers une page de contenu).
- Utilise une image de diagramme représentative du dossier `assets/` de cette catégorie comme miniature, avec le style standard de la carte CSS (`background-color:#ffffff; border:1px solid #d3d3d3;` plus les règles de dimensionnement/remplissage partagées déjà présentes dans le fichier).
- Inclut le nom de la catégorie (en gras/fort) et une description d’une seule phrase correspondant à l’introduction de la présentation de la catégorie.

Lorsque le nombre de catégories est un multiple de 3, le tableau s’affiche en tant que lignes complètes et propres (3 colonnes, `table-layout:fixed`, `width:33%` par cellule). S’il ne s’agit pas d’un multiple de 3, ajoutez un `<td>` vide par emplacement manquant dans la dernière ligne (ne laissez pas le tableau sans style).
