---
title: Configurer le canal SMS
description: Découvrez comment configurer un canal SMS basé sur Twilio et ses dimensions d’exécution pour une utilisation dans des campagnes orchestrées.
doc-type: article
solution: Experience Platform
exl-id: 63c994f2-4b6b-42e9-aa82-cb6697390a08
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%
---

# Configurer le canal SMS

## Objectif

Dans l’ensemble d’étapes suivant, vous configurez le canal SMS. Cette étape est requise afin que vous puissiez envoyer ultérieurement des messages à des détenteurs de ligne individuels lors de la création de votre campagne.



## Accès aux canaux

1. Dans Adobe Journey Optimizer, accédez au menu **Administration** -> **Canaux**.
1. Sélectionnez **Paramètres SMS** → **Informations d’identification de l’API**.
1. Cliquez sur **Créer des informations d’identification d’API**.

![Accédez aux paramètres SMS et aux informations d’identification d’API dans le menu Canaux d’administration « Accéder aux paramètres SMS »](assets/configure-sms-channel-navigate-to-sms-settings.png "Accédez aux paramètres SMS")



## Définir les informations d’identification de l’API SMS

Commencez par créer le connecteur API qu’AJO utilise pour envoyer les requêtes SMS sortantes.

1. Sous Fournisseur SMS, choisissez **Twilio**.
1. Saisissez les informations d’identification d’API suivantes à l’aide de votre propre compte d’évaluation [Twilio](https://www.twilio.com/try-twilio) :
   - **Name:** `DEP SMS`
   - **SID du compte :** présent dans le tableau de bord de la console Twilio
   - **Jeton d’authentification :** présent dans le tableau de bord de la console Twilio (cliquez sur **Afficher** pour l’afficher).
1. Cliquez sur **Envoyer** pour enregistrer les informations d’identification de l’API

>[!NOTE]
>
>Vous aurez besoin d&#39;un compte d&#39;essai Twilio gratuit avec un numéro de téléphone vérifié avant de commencer cette étape. Inscrivez-vous à l’adresse [](https://www.twilio.com/try-twilio), puis recherchez le SID de votre compte et le jeton d’authentification dans le tableau de bord de la console Twilio. Voir le [guide de prise en main](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account) de Twilio pour une présentation complète.

![Champs d’informations d’identification de l’API SMS pour le fournisseur Twilio](assets/configure-sms-channel-enter-api-credentials.png)



## Créer une configuration de canal SMS

Vous allez à présent mapper ces informations d’identification d’API à une configuration de canal que les parcours et les campagnes peuvent utiliser.

1. Accédez à **Canaux** → **Paramètres généraux** → **Configurations de canal**.

   ![Accédez aux configurations de canal sous Paramètres généraux](assets/configure-sms-channel-navigate-channel-configurations.png)



2. Cliquez sur **Créer une configuration de canal**.

   ![bouton Créer une configuration de canal](assets/configure-sms-channel-click-create-configuration.png)



3. Renseignez les Paramètres de configuration du canal SMS avec les valeurs suivantes :
   - **Name:** `Relational-SMS-Multi-Entity`
   - **Canal:** `Mobile Message`
   - **Action marketing :** `SMS Targeting`

>[!NOTE]
>
>Si vous obtenez une erreur indiquant que l’utilisateur ne dispose pas de l’autorisation nécessaire, ignorez-la et continuez.

## Paramètres SMS

Lorsque vous sélectionnez Canal comme Message mobile, une nouvelle section appelée Paramètres SMS s’affiche. Renseignez-le avec les détails suivants :

- **Type de message mobile :** `Marketing`
- **Configuration des messages mobiles :** `DEP SMS`
- **Numéro expéditeur :** `01234567890`
- **Subdomain:** `leave blank`
- **Numéro d’opt-out :** `leave blank`

![Paramètres SMS avec le numéro de l’expéditeur et le type de message mobile](assets/configure-sms-channel-sms-settings-fields.png)



## Détails d’exécution

1. Sous Détails d’exécution, cliquez sur l’onglet **Campagne orchestrée**

   ![Onglet Campagne orchestrée sous Détails d’exécution](assets/configure-sms-channel-execution-details-tab.png)



2. Vérifiez que la case **Activé** est cochée

   ![Case activée cochée pour les campagnes orchestrées](assets/configure-sms-channel-enabled-checkbox.png)



3. Ensuite, sous la sous-section **Dimension d’exécution** assurez-vous que les éléments suivants sont configurés comme suit :
   - **Diffuser sur le message per:** `Target + Secondary Dimension`
   - **Profile Target Dimension :** `dep-rel: Customer Account - customer_id`
   - **Dimension Secondaire:** `Customer Line`

   ![Paramètres de la dimension d’exécution avec dimension cible et dimension secondaire](assets/configure-sms-channel-execution-dimension-setup.png)

   ![Dimension Secondaire défini sur Ligne client dans les paramètres de dimension d’exécution « Dimension Secondaire« ](assets/configure-sms-channel-secondary-dimension-detail.png "Dimension Secondaire ")

   >[!NOTE]
   >
   >Ce paramètre indique aux campagnes orchestrées que lorsqu’elles envoient des messages, elles doivent diffuser un message par enregistrement correspondant au Dimension cible du profil.



4. Sous l’en-tête Adresse d’exécution , assurez-vous de sélectionner le bouton radio pour **Dimension Secondaire** puis cliquez sur le bouton de modification sur le **Champ d’exécution du SMS**

   ![Adresse d’exécution définie sur Dimension Secondaire avec champ d’édition](assets/configure-sms-channel-execution-address-selection.png)



5. Sur la fenêtre pop-up, cliquez dans le schéma **dep-rel : Customer Line** et sélectionnez **Téléphone mobile**.

   ![Fenêtre contextuelle de schéma pour le dep-rel : schéma Ligne du client](assets/configure-sms-channel-customer-line-schema-popup.png)

   ![Champ de téléphone mobile sélectionné à partir du dep-rel : schéma de ligne client « Champ de téléphone mobile »](assets/configure-sms-channel-mobile-phone-field-selected.png "champ de téléphone mobile")



6. Confirmez la dernière correspondance de la section Détails d’exécution ci-dessous

![La configuration des détails d’exécution finale correspond aux paramètres requis](assets/configure-sms-channel-final-execution-details.png)



## Envoyer et réviser

1. Cliquez sur le bouton **Envoyer** pour terminer la configuration et afficher un message de réussite

   ![Message de réussite après l’envoi de la configuration du canal](assets/configure-sms-channel-submit-success-message.png)



2. Sur la page d’inventaire des configurations de canal, assurez-vous que le statut indique **Actif** avant de continuer

   ![Statut de configuration du canal affiché comme Actif](assets/configure-sms-channel-active-status.png)

   >[!CAUTION]
   >
   >Patientez jusqu’à ce que l’état devienne **Actif** sinon les prochaines étapes de l’atelier échoueront



3. Lorsque l’état devient Actif , vous avez terminé.

>[!TIP]
>
>🚀 Booyah ! Votre canal SMS est maintenant en ligne et prêt à être utilisé.



## Récapituler

Vous savez maintenant comment configurer un canal SMS.  Notez que cette configuration est un SMS basé sur une API. Selon votre fournisseur, il peut donc utiliser d’autres méthodes d’authentification.

Vous pouvez en savoir plus [ici](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration) si cela vous intéresse.
