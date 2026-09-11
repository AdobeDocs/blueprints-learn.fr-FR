---
title: Prétravail
description: Examinez les champs de schéma pour l’utilisation de la facturation et le nom du plan, en soulignant comment les descriptions manquantes et les champs en double peuvent perturber les créateurs d’audience.
doc-type: article
solution: Experience Platform
exl-id: c26de19e-82da-4070-a918-2d2c8ef2c116
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Prétravail

Pour ce cas d’utilisation, il n’y a pas beaucoup de travail à faire. En gros, nous recherchons deux choses : 1) l’utilisation, 2) le plan.  Trouvez où ils sont.

## Utilisation des données de facturation

1. Création d’une audience
1. Recherchez « usage » dans Attributs. Cliquez sur le « i » pour consulter la description (il n’y en a pas).

   ![Rechercher une utilisation dans les attributs - Aucune description affichée](assets/pre-work-search-usage-in-attributes.png)



3. Recherchez « usage » dans Événements.  Cliquez sur le « i » pour consulter la description (il n’y en a pas).

![Rechercher une utilisation dans les événements - aucune description affichée](assets/pre-work-search-usage-in-events.png)

>[!NOTE]
>
>Aucune de ces descriptions n’étant fournie, le spécialiste marketing peut émettre des hypothèses et faire des suppositions erronées.
>
>Les descriptions sont importantes.  Sans description, comment le marketeur saura-t-il :
>
>- Quel(le) utiliser ?
>- Latence des données ?
>- Recommandé/préféré dans des cas d’utilisation spécifiques ?
>
>En fournissant ces informations dans des descriptions, nous pouvons mieux les guider.

>[!NOTE]
>
>Recherchez « Facturation ».  Notez qu’il ne s’affiche pas en tant qu’attribut de profil.  Elle s’affiche sous la forme d’une carte Type d’événement avec le champ « Utilisation des données de facturation ».
>
>Il existe également des conventions de nommage pour votre professionnel du marketing.  Selon ce sur quoi ils effectuent une recherche ou s’ils considèrent/s’attendent à ce qu’il s’agisse d’un événement ou d’un profil, cela affecte ce qu’ils trouvent et utilisent finalement.

## Plan

Recherchez « Plan » dans Attributs.  Notez que nous avons un certain nombre de choix à faire.  Réduisez-le à « Nom du plan ».  Nous avons deux noms de plan?!



![Attribut Nom du premier plan trouvé lors de la recherche dans le plan](assets/pre-work-duplicate-plan-name-field.png)



![Deuxième attribut de nom de plan trouvé lors de la recherche dans le plan](assets/pre-work-duplicate-plan-name-field--2.png)

Le Nom du plan (Nom du plan) semble être celui dont nous avons besoin en fonction de la description et l’autre ne contient pas de description.
