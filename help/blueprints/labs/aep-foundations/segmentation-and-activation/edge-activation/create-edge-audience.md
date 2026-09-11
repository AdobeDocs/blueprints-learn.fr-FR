---
hold: true
title: Création d’une audience Edge
description: Créez et publiez une audience évaluée par Edge avec un équivalent de lot pour comparer la manière dont chaque audience répond aux événements entrants en temps réel.
doc-type: article
solution: Experience Platform
exl-id: 79265a8f-81dd-41a3-89c5-c6646e435328
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Création d’une audience Edge

Cette audience sera utilisée pour qualifier une personne lorsqu’une payload (par exemple, page vue) vient du client (par exemple, Web SDK) vers Edge.

>[!NOTE]
>
>Nous évaluons généralement une audience sur l’Edge afin de pouvoir la retourner et l’utiliser dans Personalization. Si nous n’effectuons pas Personalization sur Edge, nous pouvons simplement demander à l’audience d’évaluer comme étant en flux continu sur le Hub.

## Créer une audience

1. Dans le rail de gauche, cliquez sur Audiences .
1. Cliquez ensuite sur Créer une audience dans le coin supérieur droit de l’écran
1. Cliquez ensuite sur Créer une règle



![Page Audiences avec le bouton Créer une audience et l’option Créer une règle en surbrillance](assets/create-edge-audience-create-audience-step-1.png)



![La zone de travail Créer une règle s’est ouverte pour créer une audience](assets/create-edge-audience-create-audience-step-2.png)



## Convertir l’audience en règles

1. Accédez à **Audiences** et cliquez sur le dossier **Experience Platform**
1. Faites glisser et déposez l’audience nommée **dep: Any Event Streaming (dans l’heure)** sur la zone de travail

![Faire glisser l’audience Dep : toute audience de diffusion en continu d’événements (au cours de l’heure) sur la zone de travail du créateur de règles](assets/create-edge-audience-drag-audience-to-canvas.png)



1. Convertissez l’audience en un ensemble de règles dans la zone de travail en cliquant sur l’**icône** affichée ci-dessous, puis cliquez sur **Convertir**

![Icône Convertir dans la zone de travail utilisée pour convertir l’audience en un ensemble de règles](assets/create-edge-audience-convert-to-rules-icon.png)

## Mettre à jour les règles d’événement

Apportez les modifications suivantes aux règles d’événement (vous devrez peut-être développer l’événement pour l’afficher)

1. En dernier
1. 15
1. Minutes

![Règle d’événement configurée pour se déclencher au cours des 15 dernières minutes](assets/create-edge-audience-update-event-rules.png)

## Publier le segment

1. Remplacez le nom du segment par **Any Event Edge (dans les 15 minutes)**
1. Mise à jour de la méthode d’évaluation vers Edge
1. Publication du segment

![Détails du segment présentant la méthode d’évaluation Edge avant publication](assets/create-edge-audience-publish-segment.png)

## Créer un segment évalué par lot

Répétez les mêmes étapes que celles que vous venez de suivre pour le segment Edge que vous avez créé, mais utilisez plutôt les informations suivantes :

>[!NOTE]
>
>Nous allons créer une audience par lots afin que vous puissiez constater que même si un événement est transmis dans Edge, les audiences enregistrées en tant qu’évaluation par lots ne sont pas évaluées en mode de diffusion en continu.

Règles d’événement :

- En dernier
- 1
- Jour



Détails du segment :

- Nom -> **Tout lot d’événement (dans un délai d’un jour)**
- Méthode d&#39;évaluation -> lot
