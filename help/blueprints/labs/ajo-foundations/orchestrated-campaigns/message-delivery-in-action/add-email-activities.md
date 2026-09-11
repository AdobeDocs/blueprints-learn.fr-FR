---
hold: true
title: Ajouter des activités d’e-mail
description: Découvrez comment ajouter et configurer deux activités E-mail sur des branches Branchement distinctes à l’aide de différentes configurations de canal e-mail dans une campagne orchestrée.
doc-type: article
solution: Experience Platform
exl-id: e911a251-9f9f-484c-a2de-101b0fc2c417
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# Ajouter des activités d’e-mail

## Objectif

Dans les étapes suivantes, vous allez développer la campagne pour ajouter deux activités E-mail aux deux branches d’activité Branchement . Vous allez configurer les deux activités E-mail pour utiliser les canaux E-mail, créés précédemment. Enfin, vous ajouterez également la configuration de base des e-mails (objet et corps) à chacune de ces activités d’e-mail.

>[!CAUTION]
>
>Avant de continuer, vous devez vous assurer que les deux configurations de canal e-mail sont activées dans leur statut.
>
>![Les deux configurations de canal e-mail affichant le statut actif](assets/add-email-activities-email-channel-configs-active.png "configurations de canal e-mail")



## Ajouter l’activité d’e-mail de branche principale

1. Cliquez sur le **+** du flux supérieur et sélectionnez **E-mail** dans les **Activités de canal**

![Ajouter une activité E-mail](assets/add-email-activities-select-email-activity.png)

Le volet de détails **E-mail** s’ouvre

![Volet Détails de l’e-mail](assets/add-email-activities-email-details-pane.png)

2. Renommez le libellé en **E-mail à l’aide de l’attribut de profil** pour l’activité **E-mail**, puis cliquez sur **Modifier l’e-mail**. Notez que la création du corps de l’e-mail n’est proposée qu’à des fins de test

![Renommer le libellé de l’activité E-mail et cliquez sur Modifier l’e-mail](assets/add-email-activities-rename-and-edit-email.png)

3. Sélectionnez l’onglet **Actions** et, dans la liste déroulante, sélectionnez **Profile-Email** configuration du canal

![Sélectionnez la configuration du canal Profil-E-mail dans l’onglet Actions](assets/add-email-activities-select-profile-email-channel.png)

4. Cliquez ensuite sur **Modifier le contenu** pour ajouter du contenu de test

![Cliquez sur Modifier le contenu pour ajouter du contenu de test](assets/add-email-activities-edit-content.png)

5. Fournissez une **Objet** (« Offre de mise à niveau pour les membres du plan de base ») et cliquez sur le bouton **Modifier le corps de l’e-mail**

![Ajouter un objet et modifier le corps de l’e-mail](assets/add-email-activities-subject-line-edit-body.png)

6. Il existe de nombreuses options pour ce test. Pour ce faire, choisissez **Coder le vôtre** l’option HTML .

![Choisissez l’option Coder votre propre contenu HTML ](assets/add-email-activities-code-your-own-html.png)

7. Dans le Designer d’e-mail **, insérez une ligne de test « Offre de mise à niveau disponible ! »** juste avant les balises `</body></html>` comme illustré et cliquez sur **Enregistrer**

![Insérez une ligne de test dans Email Designer et cliquez sur Enregistrer](assets/add-email-activities-email-designer-save.png)

8. Attendez que le message de confirmation s’affiche dans le coin inférieur droit

![Un message de confirmation apparaît](assets/add-email-activities-confirmation-message.png)

9. Cliquez sur la **flèche de gauche** en regard de la **Designer d’e-mail** pour quitter

![Cliquez sur la flèche gauche pour quitter Email Designer](assets/add-email-activities-exit-email-designer.png)

10. Une boîte de dialogue de confirmation s’affiche, cliquez sur le bouton **Enregistrer et fermer**

![Boîte de dialogue de confirmation avec le bouton Enregistrer et fermer](assets/add-email-activities-save-and-close-dialog.png)

11. Examinez les propriétés et les actions de l’e-mail, y compris le texte ajouté au corps de l’e-mail. Cliquez sur la **flèche de gauche** pour revenir à la zone de travail de campagne

![Revenez à la zone de travail de Campaign](assets/add-email-activities-back-to-campaign-canvas.png)

## Ajouter l’activité d’e-mail de la branche inférieure

De retour dans la zone de travail de campagne, cliquez sur le **+** du flux inférieur et sélectionnez **E-mail** dans les **Activités de canal**. Suivez les mêmes étapes que ci-dessus (étapes 2 à 11), à l’exception des suivantes :

- Renommez le libellé en **E-mail à l’aide de Target Dimension** pour l’activité **E-mail**
- Dans les paramètres d’e-mail, choisissez la configuration **Relational-Email** Canal e-mail .

![Deuxième activité E-mail configurée avec le canal E-mail relationnel](assets/add-email-activities-bottom-branch-relational-email.png "Ajoutez la deuxième activité E-mail")

## Récapituler

Vous avez maintenant vu comment configurer les activités E-mail avec les canaux e-mail. Chaque activité a ensuite été configurée avec un objet et un corps d’e-mail très basiques. L’ensemble de la campagne sera ensuite testé.
