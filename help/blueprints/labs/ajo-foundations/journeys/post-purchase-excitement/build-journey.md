---
title: Créer un parcours
description: Créez un parcours unitaire qui répond à un événement de commande expédiée, appelle une action personnalisée pour l’expédition d’ETA et envoie un e-mail personnalisé.
doc-type: article
solution: Experience Platform
exl-id: 4dd15071-51e5-445a-932d-690d9a73a913
source-git-commit: 93fba2a4818790431306801b43a791508451f344
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%
---

# Créer un parcours

## Objectif d’apprentissage

Créez un parcours unitaire qui commence par l’événement de commande expédiée configuré, obtient l’ETA d’un service externe et envoie un e-mail.

## Créer un parcours

Accédez à **Parcours** et cliquez sur **Créer un Parcours**

![Créer un Parcours - Créer à partir de zéro dans Adobe Journey Optimizer](assets/build-journey-create-journey-from-scratch.png)



## Propriétés du parcours

1. Mettez à jour les propriétés du Parcours dans le rail de droite avec les éléments suivants :
   - **Nom** : `Order Shipped Journey`
   - **Description** : `Notify customer that order has shipped. Include shipping details.`
   - **Balises** : *laisser vide*
   - **mesures de Parcours** : *laisser vide*

     >[!NOTE]
     >
     >**Liste Déroulante Vide ?**
     >
     >Ne vous inquiétez pas et passez à autre chose. Le tout premier parcours créé dans un sandbox doit « amorcer la pompe ».  Une fois que nous aurons publié le parcours, cette liste déroulante aura le choix entre différentes options.

   - **Autoriser une reprise** : `checked`

   - **Période d’attente de reprise :** `5 minutes`

   - **Libellés d’accès** : *laisser vide*

   - **Fuseau Horaire** : `Your Local timezone`

   - **Utiliser le fuseau horaire du profil dans les attentes et conditions** : `NOT checked`

   - **Date de début/fin** : *laisser vide*

   - **Temporisation ou erreur** : `30`

   - **Règles de limitation :** *laisser vide*

   - **Priorité** : `0`



2. Si tout vous semble correct, cliquez sur le bouton **Enregistrer**

![Bouton Enregistrer pour le panneau Propriétés du Parcours](assets/build-journey-save-journey-properties.png)




## Zone de travail des parcours

### Ajouter un événement unitaire

Cliquez sur une icône plus, accédez à **Événements personnalisés** et sélectionnez l’événement **orderShipped** comme illustré ci-dessous

![Faites glisser l&#39;événement orderShipped du menu Événements vers la zone de travail de parcours](assets/build-journey-drag-order-shipped-event-onto-canvas.png)



![Événement de commande expédiée placé sur la zone de travail du parcours](assets/build-journey-drag-order-shipped-event-onto-canvas--2.png)





### Ajouter une action personnalisée

1. Cliquez sur une icône plus, accédez à **Actions personnalisées** et sélectionnez l’action que vous avez créée nommée **GetShippingDetails** afin qu’elle apparaisse après l’événement orderShipped

   ![Faites glisser l&#39;action personnalisée GetShippingDetails sur la zone de travail après l&#39;événement orderShipped](assets/build-journey-drag-getshippingdetails-action-onto-canvas.png)

2. Dans le rail de droite, sous la liste déroulante Configuration de l’accès et de la confidentialité —> Action marketing , assurez-vous que la valeur est définie sur **Aucune**

   ![Liste déroulante Action marketing définie sur Aucune dans la configuration Accès et confidentialité](assets/build-journey-set-marketing-action-to-none.png)

3. Dans le menu Configuration du point d’entrée —> Paramètres de requête, cliquez sur l’icône **Crayon** à côté de orderid

   ![Icône en forme de crayon pour modifier le paramètre de requête orderid dans la configuration de point d’entrée](assets/build-journey-edit-orderid-query-parameter.png)

4. Dans la boîte de dialogue modale qui s’affiche, développez **Context** -> **orderShipped** -> **Order**, puis sélectionnez **ID de commande (orderID)** et cliquez sur **OK**

   ![Sélectionnez ID de commande (orderID) dans les champs contextuels de commande orderShipped](assets/build-journey-select-order-id-context-field.png)

5. De retour dans le rail de droite, assurez-vous que l’option Temporisation ou erreur est **décochée**, puis cliquez sur le bouton **Enregistrer**

Option de délai d&#39;expiration ou d&#39;erreur ![décochée avec le bouton Enregistrer en surbrillance](assets/build-journey-uncheck-timeout-or-error.png)



### Ajouter une action e-mail

1. Cliquez sur l’icône plus après votre événement personnalisé GetShippingDetails et sélectionnez **Action**.

   ![Faites glisser le nœud Action sur la zone de travail après l&#39;action GetShippingDetails](assets/build-journey-drag-email-action-onto-canvas.png)

2. Sélectionnez **E-mail** pour l’action marketing, puis **Ajouter**.

   ![Sélectionnez E-mail comme action marketing et cliquez sur Ajouter](assets/build-journey-select-email-marketing-action.png)

3. Dans le rail de droite, cliquez sur **Configurer l’action**

   ![Configurer le bouton d’action dans le rail de droite](assets/build-journey-click-configure-action.png)

4. définissez **Configuration du canal e-mail** sur `Profile-Email`, puis cliquez sur **Modifier le contenu**

![Configuration du canal e-mail définie sur Profil-E-mail avec le lien Modifier le contenu](assets/build-journey-set-profile-email-channel-configuration.png)



### Ajouter le contenu du corps de l’e-mail

Pour le contenu, vous allez garder les choses simples. Comme stupide simple.

1. Mettez à jour l’Objet sur `Order Shipped`, puis cliquez sur le bouton **Modifier le corps de l’e-mail**

   ![Objet mis à jour sur la commande expédiée avec le bouton Modifier le corps de l&#39;e-mail](assets/build-journey-update-subject-line-order-shipped.png)

2. Dans la barre supérieure, cliquez sur le bloc de contenu **Créer en partant de zéro**

   ![Créer en partant de zéro le bloc de contenu dans la barre supérieure](assets/build-journey-click-design-from-scratch.png)

3. Dans la barre de gauche, accédez à l’onglet Composants et, depuis le conteneur Structure , faites glisser &#39;n et déposez la colonne **1:1** sur la zone de travail

   ![Faites glisser l’élément de structure de colonne 1:1 sur la zone de travail de l’e-mail](assets/build-journey-drag-1-1-column-onto-canvas.png)

4. Ensuite, sous le conteneur Contenu, faites glisser &#39;n et déposez le composant **Texte** dans votre **Colonne 1:1**

   ![Faites glisser le composant Texte dans la colonne 1:1](assets/build-journey-drag-text-component-into-column.png)

5. Cliquez dans le composant Texte et **supprimez le texte actuel**, puis cliquez sur l’icône **Ajouter Personalization**

   ![Ajouter une icône Personalization après la suppression du texte par défaut](assets/build-journey-click-add-personalization-icon.png)

6. Dans le rail de gauche, cliquez sur le dossier **Attributs contextuels**, puis accédez à **Journey Orchestration** -> **Actions** et sélectionnez **GetShippingDetails**

   ![Sélectionnez GetShippingDetails sous Attributs contextuels - Journey Orchestration - Actions](assets/build-journey-select-getshippingdetails-contextual-attribute.png)

7. Dans le corps principal de l’e-mail, **copiez et collez** le code JSON ci-dessous dans l’éditeur **Personalization**

   ```json
   {{profile.person.name.firstName}}, your order has shipped
   ETA:
   Tracking Number:
   ```

8. Ajoutez les champs de personnalisation comme suit (**cliquez sur le signe plus « + » en regard du champ du rail de gauche**) :
   - **ETA:** `eta`
   - **Numéro De Suivi :** `tracking_number`

   ![Ajout de champs de personnalisation ETA et Numéro de suivi à l’e-mail](assets/build-journey-add-eta-tracking-number-fields.png)

   >[!NOTE]
   >
   >Cliquez sur le symbole **+** pour ajouter des attributs de personnalisation du rail à la zone de travail.  Il les placera à l’endroit où se trouve votre curseur pour vous assurer que vous êtes bien « aligné »

   >[!NOTE]
   >
   >Votre e-mail utilisera une combinaison d’attributs de contexte (ETA et numéro de suivi) et d’attributs de profil (prénom). Si vous souhaitez ajouter d’autres attributs de profil, vous pouvez cliquer sur l’onglet Attributs de profil et sélectionner tout ce qui s’affiche.
   >
   >![Onglet Attributs de profil pour ajouter des attributs de profil supplémentaires](assets/build-journey-profile-attributes-tab.png)

9. Dans la partie inférieure de l&#39;écran, cliquez sur le bouton **Valider** et vérifiez que vous n&#39;avez aucune erreur

   ![Bouton Valider sans erreur affiché en bas de l&#39;écran](assets/build-journey-click-validate-button.png)

10. Si tout semble correct, cliquez sur le bouton **Enregistrer** en haut à droite
11. Cliquez ensuite de nouveau sur le bouton **Enregistrer** en haut à droite et cliquez sur la flèche **\&lt;- gauche** en haut à gauche

![Bouton Enregistrer et flèche vers l&#39;arrière en haut à droite et en haut à gauche](assets/build-journey-save-and-back-arrow.png)

1. Enfin, cliquez sur l’icône **\&lt; Précédent** en haut à gauche pour revenir à la zone de travail de Parcours

![Icône Précédent en haut à gauche pour revenir au Parcours de la zone de travail](assets/build-journey-back-icon-to-journey-canvas.png)

>[!TIP]
>
>Puis cliquez de nouveau sur le bouton **Précédent**... Plaisanterie ! Il s&#39;agit du dernier bouton Précédent... de cette section 😜



### Remplacer les paramètres d’e-mail

De retour sur la zone de travail de Parcours principale, sur le nœud E-mail, assurez-vous que vous pouvez voir les champs en lecture seule (vous devrez peut-être cliquer sur l&#39;icône **Afficher les champs en lecture seule**)

![Champs en lecture seule affichés sur le nœud E-mail dans la zone de travail de Parcours](assets/build-journey-show-read-only-fields-email-node.png)

1. Faites défiler jusqu’à **Paramètres d’e-mail** et cliquez sur l’icône **Activer le remplacement du paramètre**

   ![Activer l’icône de remplacement de paramètre sous Paramètres d’e-mail](assets/build-journey-enable-parameter-override.png)

2. Cliquez dans la zone de texte vide, puis, dans le rail de gauche, accédez à **Context** -> **orderShipped** -> **\_dep** et cliquez sur le champ **PersonalEmail**.  Cliquez ensuite sur le bouton **OK**
(Notez que le nom du client commençant par un trait de soulignement peut être différent pour votre environnement ; dans cet exemple, il s’agit de _dep.)

   ![Sélectionnez le champ personalEmail sous orderShipped context _dep](assets/build-journey-select-personalemail-context-field.png)

   >[!WARNING]
   >
   >Il est dangereux d’éviter cette méthode, sauf si vous devez l’utiliser dans un contexte de production.  Cette option remplace l’emplacement par défaut que Parcours recherche sur le profil pour exécuter les messages.



3. Cliquez sur le bouton **Enregistrer** en haut à droite, puis sur la **flèche vers l&#39;arrière** \&lt;- en haut à gauche pour **fermer** le Parcours

![Bouton Enregistrer et flèche vers l&#39;arrière pour fermer le Parcours](assets/build-journey-save-and-close-journey.png)

## Récapituler

Un parcours publié capable de répondre au déclencheur d’événement de commande envoyée, d’obtenir l’ETA d’un service externe et d’envoyer un e-mail.
