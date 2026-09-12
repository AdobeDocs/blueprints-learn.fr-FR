---
title: Branchement du résultat
description: Découvrez comment ajouter une activité Branchement à une campagne orchestrée pour brancher un résultat afin d’enregistrer une audience et d’envoyer des SMS.
doc-type: article
solution: Experience Platform
exl-id: 8f1d0839-e4ca-4b7c-bc97-4e271a457296
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# Branchement du résultat

## Objectif

Cette étape est simple dans la mesure où tout ce que vous souhaitez faire est d’ajouter une activité Branchement afin de pouvoir dupliquer le résultat pour en faire deux choses différentes lors des étapes suivantes :

1. Enregistrez l’audience pour que d’autres personnes l’utilisent à des fins publicitaires ou cross-canal
1. Envoyez des SMS aux lignes individuelles.



## Créer le branchement

1. Dans la zone de travail du workflow, cliquez sur le **+** **icône** après l’activité Créer une audience et sélectionnez l’activité **Branchement**

   ![Ajoutez une activité Branchement après l’activité Créer une audience](assets/fork-the-result-add-fork-activity.png)



2. Mettez à jour les noms de chaque transition du branchement en cliquant sur la transition, puis attribuez-leur les noms comme indiqué ci-dessous :
   - **Haut** —> `Save Audience`
   - **Bas** —> `SMS`

   ![Les transitions en branchement sont renommées Enregistrer l’audience et les SMS](assets/fork-the-result-rename-transitions.png)



   Lorsque vous avez terminé, votre zone de travail doit maintenant ressembler à ceci...

   ![Zone de travail du workflow après l’ajout de l’activité branchement](assets/fork-the-result-final-canvas.png)

   >[!NOTE]
   >
   >Une activité branchement consiste essentiellement à dupliquer le résultat de l’activité précédente dans deux branches indépendantes



3. Cliquez sur **Enregistrer** dans la partie supérieure de la zone de travail du workflow.

![Bouton Enregistrer dans la barre d’outils de la zone de travail du workflow](assets/fork-the-result-click-save.png)

>[!TIP]
>
>C&#39;était assez difficile, n&#39;est-ce pas 😁



## Récapituler

Eh bien, vous avez créé un Branchement du résultat (c’est-à-dire que vous dupliquez le résultat) qui vous permet de dicter clairement à une branche de traiter une Sauvegarde d’audience, tandis que l’autre peut être utilisée pour l’envoi de SMS.

>[!NOTE]
>
>Vous devez utiliser Branchements en particulier si vous prévoyez d’enregistrer l’audience, car une activité Sauvegarde d’audience ne permet pas aux activités de la suivre.
