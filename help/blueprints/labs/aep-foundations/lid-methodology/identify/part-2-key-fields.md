---
hold: true
title: Partie 2 - Champs clés
description: Identifiez les champs d’identité principaux, de personne et de relation, ainsi que les champs d’événement d’expérience obligatoires dans les tables ERD libellées.
doc-type: article
solution: Experience Platform
exl-id: 24b6fdbd-0d59-4fe7-828e-c4bc7036db90
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---


# Partie 2 - Champs clés

## Conférence

Dans cette vidéo, vous apprendrez à identifier l’identité principale, les identités de personne et les identités de relation sur chaque table, ainsi que les champs _id, horodatage et type d’événement requis pour les événements d’expérience.

>[!VIDEO](https://video.tv.adobe.com/v/3459085/?quality=12&learn=on)



## Détails de l’atelier

### Champs d’identité

- **Identité de la personne** - Utilisé pour identifier une personne de manière unique. Ils ne sont utilisés que dans les tables d&#39;entité de Principal. Il doit y en avoir au moins un, mais il peut y en avoir plusieurs.
- **Identité de la relation (c&#39;est-à-dire une non-personne)** - Utilisé pour décrire les relations des tables d&#39;entité de Principal du profil client en temps réel vers une classe d&#39;entité de support associée (c&#39;est-à-dire des recherches).
- **Identité de Principal** - Il peut s’agir d’une identité de personne ou d’une identité de relation (non-personne) utilisée comme clé de stockage et requise pour tout schéma utilisé par le profil client en temps réel. Pour les tables d’entité de Principal, l’identité identifie également de manière unique une personne. Lorsqu&#39;il est spécifié pour les schémas de profil XDM et les schémas de recherche, ce champ détermine si un nouvel enregistrement est créé ou si un enregistrement existant est mis à jour. Il doit y en avoir un.

### Champs obligatoires (Événement d’expérience XDM uniquement)

- **\_id** - utilisé par le profil client en temps réel conjointement avec l’identité de Principal pour créer une clé de stockage unique pour l’événement. Requis pour éviter la duplication accidentelle des données d’événement dans le service de profil
- **Horodatage** - tous les événements se produisent à une heure spécifique et, par conséquent, chaque événement nécessite un horodatage

Non requis, mais fortement encouragés :

- **Type d’événement** - décrit le comportement général des données d’événement (c’est-à-dire achat, réservation, etc.)

### Règles générales

1. #2 de règles de table Bridge - dans les cas où une table de pontage existe entre un parent « **P** » ou « **E** » (c&#39;est-à-dire la table parent) et une table « **L** », traitez la table de pontage comme faisant partie de la table parent
1. À ce stade, vérifiez toujours que les identités sont propres à une **seule** personne afin d’éviter toute reprise lors de l’ingestion des données
1. Pour les schémas d’événement d’expérience, l’identité du Principal est ce qui identifie de manière unique ce comportement à une seule personne.
1. Pour les tables de recherche, la clé primaire (PK) du modèle relationnel sera toujours l&#39;identité du Principal non-personne

Pour chaque table de l’ERD Connection 5G Warehouse et de l’ERD de diffusion en continu que vous avez étiquetée comme **« P », « E » ou « L »,** vous effectuez désormais les étapes ci-dessous pour identifier les identités principales, les identités de personne, les identités de relation et les champs obligatoires pour les classes de schéma données.

>[!NOTE]
>
>Reportez-vous au diagramme ci-dessous pendant les exercices pratiques lorsque vous étiquetez des identités sur des schémas
>
>![Diagramme montrant des exemples de libellés d’identité de Principal, d’identité de personne et de relation appliqués aux tables ERD](assets/part-2-key-fields-identity-labeling-diagram.png)



## Étape 1 - Étiqueter les champs clés dans les tables XDM Individual Profile

Effectuez les étapes ci-dessous pour identifier les champs clés dans le tableau Compte client :

- Identifiez le champ qui sera utilisé comme identité du Principal et libellez-le avec un `PI`
- Identifier toutes les autres identités de personne et les étiqueter avec un `I`
- Identifiez les identités de relation et libellez-les avec un `R`



## Étape 2 - Étiqueter les champs clés dans les tableaux Événement d’expérience XDM

Effectuez le même ensemble de tâches que lors de l’étape 1, mais maintenant pour les tableaux Événement d’expérience XDM :

- Identifiez le champ de chaque table qui sera l&#39;identité du Principal et libellez-le avec un `PI`
- Identifiez toutes les autres identités de personne dans chaque tableau et libellez-les avec un `I`
- Identifier toutes les identités de relation et les étiqueter avec un `R`

En plus des libellés ci-dessus, étiquetez également les éléments suivants :

- Identifiez ou créez l’identifiant d’événement unique pour chaque table d’événements d’expérience XDM et libellez-le avec un `_id`
- Identifiez la date et l’heure de l’événement pour chaque table et libellez-les avec un `T`
- Identifiez ou créez le type d&#39;événement pour chaque table et libellez-le avec un `ET`



## Etape 3 - Libellé des champs clés dans les tables de recherche

Identifiez dans chaque table de recherche le champ qui sera l’identité du Principal et libellez-le avec un `PI`



## Révision

La vidéo ci-dessous passe en revue les champs clés identifiés dans les tableaux Connexion 5G, y compris la raison pour laquelle un champ concaténé était nécessaire en tant qu’identifiant d’événement unique pour les enregistrements d’ordre modifiables.

>[!VIDEO](https://video.tv.adobe.com/v/3459088/?quality=12&learn=on)
