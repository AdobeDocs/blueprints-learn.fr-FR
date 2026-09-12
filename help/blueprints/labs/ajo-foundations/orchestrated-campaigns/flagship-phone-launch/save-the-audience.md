---
title: Enregistrer l’audience
description: Découvrez comment modifier la dimension, dédupliquer et enregistrer une audience sur le portail d’audiences à partir d’un workflow Campagne orchestré.
doc-type: article
solution: Experience Platform
exl-id: 6422ea8d-146b-4fc7-86e6-491f77590ca1
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Enregistrer l’audience

## Objectif

Dans les étapes suivantes, vous allez enregistrer l’audience que vous avez créée sur le portail d’audiences afin que d’autres solutions de Adobe Experience Platform et ses applications puissent l’exploiter pour leurs propres cas d’utilisation.



## Modifier la dimension

1. Dans la zone de travail du workflow, cliquez sur le **+** **icône** sur la branche **Enregistrer l’audience**, puis, dans la liste des activités, sélectionnez l’activité **Modifier la dimension**

   ![Ajoutez l’activité Changement de dimension sur la branche Enregistrement d’audience](assets/save-the-audience-add-change-dimension.png)



2. Mettez à jour les propriétés de la dimension de modification comme indiqué ci-dessous :
   - **Libellé :** `Convert Line to Account`
   - **Nouvelle dimension cible :** `dep-rel: Customer Account`

   ![Modifier le libellé de dimension et nouveaux champs de dimension cible](assets/save-the-audience-change-dimension-label.png)

   ![Compte client sélectionné comme nouvelle dimension cible](assets/save-the-audience-select-customer-account.png)

   >[!NOTE]
   >
   >**Pourquoi faites-vous cela, demandez-vous ?**  N’oubliez pas que pour rejoindre le profil client en temps réel (où vous enregistrez les audiences), vous devez utiliser le mapping de ciblage de profil que vous avez configuré et qui ne rejoint que le schéma Deep-Real : Compte client .



3. Une fois cette opération terminée, voici à quoi ressemble votre zone de travail.  Enregistrez votre travail !

![Zone de travail du workflow après l’ajout de l’activité de changement de dimension](assets/save-the-audience-canvas-after-change-dimension.png)



## Dédupliquer le résultat

1. Cliquez sur **+** **icône** après l’activité Modifier la dimension et sélectionnez l’activité **Déduplication** dans la liste des activités

   ![Ajoutez l’activité Déduplication après le changement de dimension](assets/save-the-audience-add-deduplication-activity.png)



2. Mettez à jour le libellé de l’activité Déduplication sur `Dedup customer id`

   ![Libellé de l’activité Déduplication défini sur ID client de déduplication](assets/save-the-audience-deduplication-label.png)



3. Cliquez maintenant sur le bouton **+ Ajouter un attribut** et sélectionnez le champ dans le schéma intitulé **ID du client**

   ![Bouton Ajouter un attribut pour l’activité Déduplication](assets/save-the-audience-add-attribute-button.png)

   ![Champ ID du client sélectionné dans le schéma](assets/save-the-audience-select-customer-id-field.png)



4. Dans les paramètres Déduplication , assurez-vous que les éléments suivants sont définis :
   - **Doublons à conserver :** `1`
   - **Méthode de déduplication :** `Random selection`

   ![Paramètres de déduplication avec doublons à conserver et méthode &#x200B;](assets/save-the-audience-deduplication-settings.png)

   >[!NOTE]
   >
   >Les autres options de déduplication vous permettent de spécifier votre propre logique personnalisée.  La plupart du temps, si vous devez dédupliquer, vous le ferez à l’aide de la clé primaire de la table.



5. Lorsque vous avez terminé, la zone de travail ressemble à ceci. Cliquez sur le bouton **Enregistrer** en haut à droite avant de passer à autre chose.

![Activité Déduplication entièrement configurée sur la zone de travail](assets/save-the-audience-deduplication-configured.png)



## Ajouter une activité Enregistrer l’audience

1. Cliquez sur l’icône **+** après l’activité Déduplication et sélectionnez l’activité **Enregistrer l’audience**

   ![Ajouter l’activité Sauvegarde d’audience après déduplication](assets/save-the-audience-add-save-audience-activity.png)

2. Dans le rail de droite, définissez les propriétés de l’activité sur ce qui suit :
   - **Libellé de l’audience** : `Apple Upgrade Eligible Customer Accounts`
   - **Champ de mappage de profil** : `dep-rel: Customer Account - customer id`

![Enregistrer les paramètres de champ de mappage de profil et de libellé d’audience](assets/save-the-audience-label-and-profile-mapping.png)

>[!NOTE]
>
>Le « champ de mappage de profil » est ce que vous avez configuré précédemment afin que le magasin relationnel puisse être joint au profil client en temps réel.  Le profil a été modélisé au niveau d’un compte client afin que vous souhaitiez enregistrer l’audience dans le même dossier.  D’où la nécessité de changer de dimension et de dédupliquer.



## Mappages de champs d’audience

Par défaut, la clé primaire de la dimension de ciblage (c’est-à-dire l’ID du client) est ajoutée à l’audience sous forme de champ. Vous pouvez le voir en regardant dans la partie droite et en développant le champ.  Deux choses à noter :

- Le champ **Audience Source** —> fait référence au champ provenant du schéma relationnel
- **Champ cible de l’audience** —> nom du champ qui sera créé dans le cadre de l’enregistrement de l’audience

![Champ ID de client par défaut ajouté à l’activité Sauvegarde d’audience](assets/save-the-audience-default-field-added.png)

>[!NOTE]
>
>Notez à quel point le champ Audience cible est `Dep_rel_customer_account_Customer_id`.  Vous devriez toujours changer cela pour quelque chose de plus lisible pour un spécialiste du marketing, sans excuses.



## Correction du champ d’audience par défaut

1. Renommez le champ Audience cible par défaut **Customer\_ID** comme illustré ci-dessous :

   ![Le champ Audience cible est renommé Customer_ID](assets/save-the-audience-field-renamed.png)

   >[!TIP]
   >
   >Vous disposez désormais d’un nom de champ lisible par un utilisateur 🎉



2. Cliquez sur le bouton **Démarrer** pour exécuter le workflow. Votre workflow ressemble désormais à ceci, et les chiffres affichés sont les suivants :
   - Créer une audience : `65`
   - Convertir la ligne en compte : `65`
   - Dédupliquer l’ID client : `46`

![Exécution de test du workflow affichant les nombres de création, de conversion et de déduplication](assets/save-the-audience-test-run-counts.png)

>[!NOTE]
>
>L’activité de sauvegarde d’audience ne crée l’audience que lorsque le workflow est publié, et non lorsqu’il est simplement démarré. Lorsque l’audience est créée, elle inclut tous les attributs que vous lui avez ajoutés et est jointe au profil client en temps réel lors de la prochaine exécution quotidienne planifiée de la tâche de service de segmentation.

>[!CAUTION]
>
>NE PUBLIEZ PAS VOTRE WORKFLOW.



## Défi

Que se passe-t-il si vous ne dédupliquez pas avant d’enregistrer l’audience ?  L’audience stockera-t-elle les 65 enregistrements ou uniquement les 46 ?

![Enregistrer au préalable le scénario de défi d’audience sans déduplication « Enregistrer au préalable l’audience avec l’activité de déduplication »](assets/save-the-audience-challenge-without-dedup.png "Enregistrer au préalable l’audience avec l’activité de déduplication")



## Réponse

L’audience stocke les 65 enregistrements, mais une activité Lecture d’audience les déduplique lors de l’importation en fonction de la condition de jointure 😁







## Récapituler

Vous devriez maintenant bien comprendre comment fonctionne la fonction Enregistrer l’audience et pourquoi la déduplication est importante.  N’oubliez pas que vous devez toujours définir le mapping de ciblage de profil, car les données du magasin relationnel doivent savoir comment se joindre au profil client en temps réel.  Le mapping de ciblage du profil est la condition de jointure 🙂
