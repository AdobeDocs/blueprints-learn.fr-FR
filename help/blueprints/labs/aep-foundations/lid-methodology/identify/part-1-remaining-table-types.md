---
title: Partie 1 - Autres types de tableau
description: Identifiez et étiquetez les tableaux de passerelles et les tableaux nécessitant une dénormalisation sur les ERD de profil individuel, d’événement d’expérience et de recherche.
doc-type: article
solution: Experience Platform
exl-id: 742b58fa-3feb-4275-ab45-eb8d3aade22c
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---


# Partie 1 - Autres types de tableau

## Conférence

Dans cette vidéo, vous apprendrez à libeller les tables non libellées restantes avec un type de dénormalisation D ou B, y compris la manière dont l&#39;#1 Règle de table Bridge transforme le côté multiple-à-un d&#39;une table de pont en recherche.

>[!VIDEO](https://video.tv.adobe.com/v/3459082/?quality=12&learn=on)



## Détails de l’atelier

Identifiez et étiquetez les tables de l’entrepôt de données 5G Connection et les ERD de diffusion en continu qui correspondent à l’une des catégories ci-dessous

- Table Bridge (étiquetée comme « **B** »)
- Nouvelles tables de recherche qui existent en raison des tables de pontage
- Tableaux qui nécessiteront une dénormalisation (étiquetés « **D** »)

>[!CAUTION]
>
>L&#39;ordre est très important ici ! Veillez à suivre les étapes dans l’ordre, car chaque étape dépend de la précédente



## Étape 1 : identifier et étiqueter les tables XDM Individual Profile

1. Identifiez toutes les tables directement liées aux tables XDM Individual Profile (à un bond) qui n’ont pas encore de libellé. Marquez-les avec une étoile « **\*** ».
1. En examinant uniquement les schémas que vous venez d’étiqueter avec une étoile, effectuez les tâches suivantes :
   1. **Ajoutez un libellé « B » pour la table de ponts** - une table est considérée comme une table de ponts lorsque plusieurs tables lui sont associées, le côté « plusieurs » de la relation des deux tables pointant vers la table de ponts
   2. **Ajoutez un libellé « D » pour les tables à dénormaliser** : toute entité qui a une cardinalité 1\:M ou M:1 avec le profil individuel XDM libellé table et qui n’est pas déjà marquée

>[!NOTE]
>
>Mémoriser les #1 de règles de table Bridge.
>
>Lorsque vous rencontrez une table de pontage directement liée à un « P » ou à un « E », la relation M:1 agit comme une recherche. Dans le cas contraire, suivez les règles de dénormalisation standard.



## Étape 2 : identifier et étiqueter les tables d’événements d’expérience XDM

1. Identifiez toutes les tables directement liées à l’événement d’expérience (à un saut de là) et étiquetées qui n’ont pas encore de libellé. Marquez-les d&#39;une étoile.
1. En examinant uniquement les tables que vous venez d’étiqueter avec une étoile, effectuez les tâches suivantes :
   1. **Ajoutez un libellé « B » pour les tables de pont** - une table est considérée comme une table de pont lorsque deux tables ou plus y sont liées, le côté « plusieurs » de la relation pointant vers la table de pont
   2. **Ajoutez un libellé « D » pour les tableaux à dénormaliser** - tout tableau ayant une cardinalité 1\:M ou M:1 avec l’événement d’expérience XDM libellé tableau et qui n’est pas déjà marqué

>[!NOTE]
>
>Mémoriser les #1 de règles de table Bridge.
>
>Lorsque vous rencontrez une table de pontage directement liée à un « P » ou à un « E », la relation M:1 agit comme une recherche. Dans le cas contraire, suivez les règles de dénormalisation standard.



## Étape 3 : identifier et étiqueter les tables de recherche

1. Identifiez toutes les tables liées (peu importe le nombre de sauts que vous effectuez) à l&#39;une des tables étiquetées de recherche qui n&#39;ont pas encore de libellé. Marquez-les avec une étoile « **\*** ».
1. En examinant uniquement les tables que vous venez d’étiqueter avec une étoile, effectuez les tâches suivantes :
   1. Ajoutez un libellé « **B** » pour les tables de pont : une table est considérée comme une table de pont lorsque plusieurs tables lui sont associées, le côté « plusieurs » de la relation pointant vers la table de pont
   2. Ajoutez un libellé « **D** » pour les tables à dénormaliser - toute table ayant une cardinalité 1\:M ou M:1 avec une table de choix ou une table de pont associée à une recherche

>[!NOTE]
>
>Mémoriser les #1 de règles de table Bridge.
>
>Lorsque vous rencontrez une table de pontage directement liée à un « P » ou à un « E », la relation M:1 agit comme une recherche. Sinon, suivez les règles de dénormalisation standard **(hint, hint)**



## Révision

La vidéo ci-dessous examine les libellés D et B corrects pour l’entrepôt de données 5G de Connection et les ERD de streaming, y compris les raisons pour lesquelles le type de produit est un tableau dénormalisé plutôt qu’une recherche.

>[!VIDEO](https://video.tv.adobe.com/v/3459064/?quality=12&learn=on)
