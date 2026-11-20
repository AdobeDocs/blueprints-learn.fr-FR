---
title: Filtrer les lignes
description: Découvrez comment filtrer les lignes client exclues avec une activité Partage et utiliser Modifier la dimension pour aligner la dimension cible d’un workflow avec la configuration du canal SMS.
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 8d5a87f094e2fba7abd7f5a9acf8e9e775d9b534
workflow-type: tm+mt
source-wordcount: '748'
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



## Ajouter une dimension de modification

1. Dans la zone de travail du workflow, cliquez sur l’icône **+** après la condition de partage que vous avez ajoutée et sélectionnez l’activité **Modifier la dimension**

   ![Ajoutez l’activité Changement de dimension après la condition de partage](assets/filter-the-lines-add-change-dimension-activity.png)

2. Mettez à jour les propriétés de la dimension de modification comme indiqué ci-dessous et cliquez sur **Confirmer** :
Libellé : `Convert Line to Account`
Nouvelle dimension cible : `dep-rel: Customer Account`

   ![Modifier la dimension cible](assets/filter-the-lines-add-edit-target-dimension.png)

   ![Modifier la dimension cible](assets/filter-the-lines-add-select-target-dimension.png)



## Ajouter l’activité SMS

1. Cliquez sur l’icône **+** après la dimension Modifier que vous avez ajoutée et sélectionnez l’**Activité de message mobile**

   ![Ajouter l&#39;activité Message mobile après la condition de partage](assets/filter-the-lines-add-sms-activity.png)

   ![Activité SMS ajoutée à la zone de travail du workflow](assets/filter-the-lines-sms-activity-on-canvas.png)



2. Dans le rail de droite, cliquez sur le bouton **Modifier le message mobile** pour démarrer la configuration du SMS

   ![Bouton Modifier le message mobile dans le rail de droite](assets/filter-the-lines-edit-sms-button-only.png)



3. Dans le volet de navigation supérieur, cliquez sur l’élément de menu Actions , puis dans le menu déroulant Configuration du message mobile , sélectionnez le canal que vous avez précédemment créé.

![Liste déroulante de configuration des SMS n’affichant aucune erreur de résultats](assets/filter-the-lines-sms-configuration-no-results.png)

>[!CAUTION]
>
>Oh non 🫨 !  Pourquoi n’obtenez-vous aucun résultat ?  N’avez-vous pas déjà configuré votre canal SMS ?  Le produit est-il cassé ?
>
>PANIQUE!!!!!!!!!



## Moment d’interruption

La configuration du canal pour les SMS a déjà été configurée par vous au préalable et elle ressemble actuellement à ceci...

![Configuration des détails d’exécution définie lors du Lab Configurer le canal SMS](assets/configure-sms-channel-final-execution-details.png)

**Voici comment vous lisez ceci :**

- Diffusez un message par dimension cible (par exemple, Compte client) sur le nombre d’enregistrements associés trouvés dans la dimension secondaire (par exemple, Ligne client)
- Exécutez chaque diffusion SMS à l’aide du numéro de téléphone mobile figurant dans la dimension secondaire (c’est-à-dire Ligne du client)

Cette capacité unique d’envoyer de nombreux messages à un profil est l’une des principales fonctionnalités des campagnes orchestrées, qui la différencie des Parcours. Cependant, votre transition menant à l’activité Message mobile est définie sur Compte client. Vous pouvez ainsi la joindre à nouveau au profil client en temps réel au moment de l’envoi, de sorte que les informations de diffusion et de suivi des messages soient attribuées à un profil.


Comment faire pour que ça marche ? Modifiez la cible pour l’exécution du message afin qu’elle corresponde à la configuration de votre canal 😀



## Modifier Target et terminer la configuration des messages SMS

1. Cliquez sur le bouton Précédent dans l’écran de modification des SMS

   Bouton Précédent ![pour quitter l&#39;écran de modification du SMS](assets/filter-the-lines-exit-sms-editor.png)



2. Une fois l’activité de message mobile sélectionnée, dans le rail de droite, modifiez d’abord le choix de Target de l’option par défaut d’un message par profil en **Un message par dimension secondaire**, puis cliquez de nouveau sur **Modifier le message mobile**

   ![Bouton Modifier la cible puis Modifier le message mobile dans le rail de droite](assets/filter-the-lines-edit-sms-button.png)



3. Dans le volet de navigation supérieur, cliquez sur l’élément de menu **Actions**, puis dans le menu déroulant Configuration du message mobile , sélectionnez le canal que vous avez précédemment créé.

   ![Configuration des SMS affichant le canal sélectionné](assets/filter-the-lines-sms-configuration-selected.png)



## Récapituler

Vous avez filtré toutes les lignes qui n’étaient pas autorisées à être ciblées avec un SMS en raison de l’opt-out, vous avez modifié la dimension de ligne en compte et à la fin, vous avez correctement configuré l’activité SMS pour celles qui étaient autorisées à être ciblées.
J’espère que vous avez également appris une chose très importante : **votre cible doit correspondre à la configuration de canal que vous souhaitez utiliser**
