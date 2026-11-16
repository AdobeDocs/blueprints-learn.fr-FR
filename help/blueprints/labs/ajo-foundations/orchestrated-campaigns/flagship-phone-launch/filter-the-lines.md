---
title: Filtrer les lignes
description: Découvrez comment filtrer les lignes client exclues avec une activité Partage et utiliser Modifier la dimension pour aligner la dimension cible d’un workflow avec la configuration du canal SMS.
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 689f227965176096ccd1785699de65046af4f3d3
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%
---

# Filtrer les lignes

## Objectif

Dans les étapes suivantes, vous allez filtrer toutes les lignes qui ne sont pas réellement autorisées à être ciblées avec un SMS en raison de leur opt-out au niveau de la ligne.  Vous ne pouvez pas vous fier ici au consentement du profil, car il s’agit d’une cible au niveau de la ligne.



## Configurer l’activité de partage

1. Cliquez sur l’icône **+** sur la transition inférieure de l’activité Branchement et sélectionnez l’activité **Fractionner** dans la fenêtre contextuelle.

   ![Ajoutez une activité Partage à la branche de branchement inférieure](assets/filter-the-lines-add-split-activity.png)



2. Dans le rail de droite, mettez à jour le Libellé pour indiquer ce qui suit : `Filter out opt'd out lines`

   ![Fractionner le libellé d&#39;activité défini pour filtrer les lignes exclues](assets/filter-the-lines-set-split-label.png)



3. Dans le rail de droite, développez la section Segment par défaut **Sous-ensemble** et cliquez sur le bouton **Créer un filtre**

   ![Bouton Créer un filtre dans la section Sous-ensemble](assets/filter-the-lines-create-filter-button.png)



4. Ajoutez une condition pour vous assurer de supprimer toutes les lignes client exclues de la messagerie SMS, puis cliquez sur **Confirmer**.

   ![Condition de suppression des lignes client exclues des SMS](assets/filter-the-lines-sms-optin-condition.png)

   >[!NOTE]
   >
   >Vous devez comprendre comment créer la condition, mais le résultat final correspond à la capture d’écran ci-dessus.  C&#39;est bon !



5. Cliquez sur le bouton Enregistrer en haut à droite pour enregistrer votre travail.  Votre zone de travail ressemble à ceci maintenant\...

![Zone de travail du workflow après l’enregistrement de l’activité de partage](assets/filter-the-lines-canvas-after-split-save.png)



## Ajouter l’activité SMS

1. Dans la zone de travail du workflow, cliquez sur l’icône **+** après la condition de partage que vous avez ajoutée et sélectionnez l’**Activité de message mobile**

   ![Ajouter l&#39;activité Message mobile après la condition de partage](assets/filter-the-lines-add-sms-activity.png)

   ![Activité SMS ajoutée à la zone de travail du workflow](assets/filter-the-lines-sms-activity-on-canvas.png)



2. Dans le rail de droite, cliquez sur le bouton Modifier le message mobile pour démarrer la configuration du SMS

   ![Bouton Modifier le message mobile dans le rail de droite](assets/filter-the-lines-edit-sms-button.png)



3. Dans le volet de navigation supérieur, cliquez sur l’élément de menu Actions , puis dans le menu déroulant Configuration du message mobile , sélectionnez le canal que vous avez précédemment créé.

![Configuration des SMS affichant le canal sélectionné](assets/filter-the-lines-sms-configuration-selected.png)




## Récapituler

Vous avez filtré toutes les lignes qui n’ont pas été autorisées à être ciblées avec un SMS en raison de votre désinscription et vous avez ajouté une activité SMS pour celles qui ont été autorisées à être ciblées.
