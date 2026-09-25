---
name: architecture-diagram-category-builder
description: 'Guidez la création d’une toute nouvelle catégorie de niveau supérieur (sous-section) sous Diagrammes d’architecture et plans directeurs dans le référentiel de plans directeurs Adobe Experience Platform. Utilisez cette compétence lorsqu’un diagramme d’architecture proposé ne correspond à aucune des catégories existantes (présentation de l’architecture, activation des audiences et des profils, activation et marketing B2B, informations sur les clients, parcours clients) et qu’une nouvelle compétence est nécessaire. Gère l’ensemble du workflow : la confirmation d’une nouvelle catégorie est en fait justifiée, l’application des conventions de dénomination des dossiers/ancres, la création de la structure de dossiers et de la page de destination overview.md, l’ajout de la sous-section TOC.md et la mise à jour de la grille de cartes de la page de destination architecture-diagrammes. Pour ajouter une page à une catégorie *existante*, utilisez plutôt architecture-diagram-page-builder.'
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%
---

# Créateur de catégories du diagramme d&#39;architecture

Cette compétence guide la création d’une catégorie de niveau supérieur sous `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` dans `/help/blueprints/TOC.md`. Une catégorie est un dossier tel que `customer-insights/` ou `b2b-activation-marketing/` : un groupe de pages de diagramme d’architecture associées ayant sa propre page de destination `overview.md` et sa propre sous-section Table des matières.

**Il s’agit d’une opération rare.** Il y a cinq catégories aujourd&#39;hui. L’ajout d’un sixième ne doit se produire que lorsqu’un véritable domaine d’architecture de contenu nouveau ne correspond à aucun domaine existant, et non comme un raccourci pour éviter d’organiser une page sous une catégorie existante.

## Lecture requise avant de commencer

- `./references/naming-conventions.md` : règle de dénomination des dossiers/ancres/libellés et raisons de son importance. Lisez-le entièrement ; il s’agit de la source unique de vérité pour la manière dont les catégories doivent être nommées.
- `./references/category-overview-template.md` : structure exacte requise pour le `overview.md` de la nouvelle catégorie.
- Si vous ne l’avez pas déjà fait, effectuez également un `../architecture-diagram-page-builder/SKILL.md` rapide : une fois la catégorie existante, les pages individuelles qu’elle contient sont ajoutées en utilisant cette compétence, et non celle-ci.

## Phase 1 : confirmer qu’une nouvelle catégorie est réellement nécessaire.

Avant toute autre action, répertoriez les cinq catégories existantes et leur portée pour l’utilisateur :

| Catégorie | Dossier | Portée |
| --- | --- | --- |
| Aperçu de l’architecture | `architecture-overviews/` | Architecture Experience Cloud/Experience Platform de haut niveau, mécanismes de sécurisation, SDK de déploiement |
| Activation d’audience et de profil | `audience-profile-activation/` | Création et activation d’audiences/profils via Real-Time CDP, Audience Manager |
| Activation et marketing B2B | `b2b-activation-marketing/` | Activation basée sur les comptes, parcours de groupe d’achat, Marketo/Workfront |
| Informations sur le client | `customer-insights/` | Customer Journey Analytics et ses intégrations |
| Parcours client | `customer-journeys/` | Journey Optimizer, Gestion des décisions, Campaign v7/v8 |

Demandez à l’utilisateur de confirmer que le contenu proposé ne correspond à aucun de ces paramètres. S’il s’agit d’un élément qui convient bien (par exemple, un nouveau diagramme B2B, un nouveau diagramme de personnalisation), redirigez-le vers `architecture-diagram-page-builder` pour cette catégorie existante au lieu d’en créer une nouvelle. Passez à la phase 2 uniquement si l’utilisateur confirme qu’une catégorie réellement nouvelle est justifiée.

## Phase 2 : collecte d’informations sur la catégorie

Utilisez un formulaire de question pour collecter, en un seul tour :

1. **Libellé de la catégorie** — libellé de la table des matières complet et lisible par l’utilisateur (par exemple, « Architecture de Commerce », et non une abréviation). Présenter 2-3 expressions suggérées plus « Autre ».
2. **Description en une seule phrase** — ce que couvre cette catégorie, pour la carte de frontMATTER et de landing page `overview.md`.
3. **solution(s) Principal Adobe en** — pour le champ `solution` frontMATTER.
4. **Pages initiales** — l’utilisateur a-t-il déjà 1+ pages prêtes à être placées dans cette catégorie ou s’agit-il simplement d’une génération de modèles automatique pour les pages à suivre ultérieurement ?

Dérivez le nom et l’ancre du dossier à partir du libellé de la catégorie à l’aide de la règle slug en `./references/naming-conventions.md` (minuscules, `&`, trait d’union, aucune abréviation). Affichez à l’utilisateur le dossier/l’ancre dérivé et confirmez-le avant de continuer : il s’agit du détail qui coûte cher à corriger ultérieurement.

## Phase 3 : création de la structure de dossiers

```
help/blueprints/architecture-diagrams/{new-folder}/
help/blueprints/architecture-diagrams/{new-folder}/assets/
help/blueprints/architecture-diagrams/{new-folder}/overview.md
```

Générez des `overview.md` à l’aide de `./references/category-overview-template.md`. Si l’utilisateur ou l’utilisatrice dispose de pages initiales prêtes, répertoriez-les dans le tableau maintenant (à l’aide de `architecture-diagram-page-builder` pour générer ces fichiers de page eux-mêmes ; cette compétence ne crée que le modèle automatique de catégorie et sa page d’aperçu, et non des pages de diagramme individuelles). S’il n’existe pas encore de pages, le tableau peut être vide ou omis jusqu’à ce que la première page soit ajoutée. Notez ceci à l’utilisateur ou à l’utilisatrice plutôt que d’inventer des lignes d’espace réservé.

Le dossier `assets/` peut être vide au moment de la création ; il existe donc pour que la première page de diagramme ajoutée à la catégorie dispose d&#39;un emplacement pour y placer ses images.

## Phase 4 : ajouter la sous-section TOC.md

Insérez la nouvelle catégorie en tant qu’entrée de niveau supérieur sous `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`, positionnée après la dernière catégorie existante, sauf indication contraire de l’utilisateur :

```
  + {Category Label}{#{folder-slug}}
    + [Overview](/help/blueprints/architecture-diagrams/{new-folder}/overview.md)
    + [{Page title}](/help/blueprints/architecture-diagrams/{new-folder}/{filename}.md)
```

Règles :

- Retrait à 2 espaces pour l’en-tête de catégorie, correspondant aux cinq autres.
- Le `{#{folder-slug}}` d’ancrage doit être identique au nom du dossier (voir naming-conventions.md).
- `+ [Overview]` est toujours la première entrée, avec un retrait de 4 espaces, avant toute page de contenu.
- Conserver l&#39;ordre et le contenu existants de toutes les autres entrées du fichier TOC.md — insérer uniquement, ne jamais réorganiser ou réécrire les sections non liées.

## Phase 5 : mise à jour de la page de destination Diagrammes d’architecture et plans directeurs

Ajoutez une nouvelle carte à `help/blueprints/architecture-diagrams/overview.md`, dans la même grille `<table style="table-layout:fixed; width:100%;">` que les cinq autres cartes. La nouvelle carte :

- Liens vers `{new-folder}/overview.md`.
- Utilise une miniature de diagramme représentative de `{new-folder}/assets/` (ou une note d’espace réservé neutre s’il n’existe pas encore de diagramme ; signalez-la à l’utilisateur ou à l’utilisatrice au lieu d’inventer un chemin d’accès à l’image).
- Utilise exactement le même bloc de style intraligne que les cartes existantes (`width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;` sur l’image, `min-height:100px;` sur la balise de texte).

**Recalculer la disposition de la grille.** Les cinq cartes existantes remplissent une grille de 3 colonnes (deux lignes, une cellule vide à la fin). L’ajout d’une sixième carte remplit exactement cette cellule vide ; aucun changement de disposition n’est nécessaire. S’il s’agit de la 7e, 8e catégorie, etc., ajoutez une nouvelle `<tr>` avec la ou les nouvelles cartes et remplissez toutes les cellules vides restantes de cette ligne avec des éléments de `<td style="width:33%; ...;"></td>` vides afin que la ligne ne s’affiche pas en page.

## Phase 6 : validation

Confirmez et signalez à l’utilisateur :

1. **Cohérence d’affectation des noms** — Le nom du dossier, l’ancre de table des matières et le titre de rappel du libellé de la catégorie sont identiques (selon les conventions d’affectation des noms.md).
2. **structure overview.md** — correspond à `category-overview-template.md` (introduction + tableau de `Diagram | Description` à deux colonnes, aucune image incorporée ni liste imbriquée dans le tableau).
3. **Emplacement TOC.md** — la nouvelle sous-section se trouve sous Schémas et plans directeurs d&#39;architecture, `+ [Overview]` est la première, la mise en retrait est correcte, aucune autre entrée n&#39;a été modifiée.
4. **Carte de la page de destination** : ajoutée à la position correcte de la grille, utilise le style standard de la carte et renvoie au nouveau `overview.md`.
5. **Redirections** — si cette catégorie regroupe ou renomme du contenu qui résidait auparavant ailleurs (rare pour une toute nouvelle catégorie, mais cochez cette case), ajoutez des entrées à `redirects.csv` selon le format de `source,dest` utilisé pour les renommes précédents des diagrammes d&#39;architecture.

Résolvez les problèmes de validation avant de considérer la tâche comme terminée.

## Remarques

- Si l’utilisateur renomme ultérieurement une catégorie (libellé, dossier ou ancre), il s’agit d’une opération de renommage, et non d’une opération de nouvelle catégorie ; suivez la règle naming-conventions.md pour le nouveau nom, mettez à jour chaque lien interne (table des matières.md, les deux pages d’aperçu, les liens relatifs frères, les documents de compétences) et ajoutez des entrées de redirection. Traitez-le de la même manière que les renommés de catégorie ont été gérés précédemment dans ce référentiel : `git mv` le dossier, puis un remplacement à l’échelle du référentiel des anciens formulaires de chemin d’accès, jamais un remplacement de chaîne global invisible qui pourrait entrer en conflit avec des URL externes non liées (par exemple, des liens de document de produit `experienceleague.adobe.com/docs/experience-platform/...`).
- Gardez ces compétences et `architecture-diagram-page-builder` synchronisés : si le tableau de mappage des sous-sections dans le `references/toc-placement.md` de `architecture-diagram-page-builder` ne répertorie pas encore la nouvelle catégorie, ajoutez-la également à cet endroit.
