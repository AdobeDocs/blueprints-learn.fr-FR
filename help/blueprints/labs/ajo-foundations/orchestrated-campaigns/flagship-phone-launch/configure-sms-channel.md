---
title: Configurer le canal SMS
description: Découvrez comment configurer un canal SMS basé sur Twilio et ses dimensions d’exécution pour une utilisation dans des campagnes orchestrées.
doc-type: article
solution: Experience Platform
exl-id: 63c994f2-4b6b-42e9-aa82-cb6697390a08
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 027d4d3373dd18fa4711e5c403465c03d374de70
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%
---

# Configurer le canal SMS

## Objectif

Dans l’ensemble d’étapes suivant, vous configurez le canal SMS. Cette étape est requise afin que vous puissiez envoyer ultérieurement des messages à des détenteurs de ligne individuels lors de la création de votre campagne.



## Accès aux canaux

1. Dans Adobe Journey Optimizer, accédez au menu **Administration** -> **Canaux**.
1. Sélectionnez **Paramètres SMS** → **Informations d’identification d’API**.
1. Cliquez sur **Créer des informations d’identification API**.

![Accédez aux paramètres SMS et aux informations d’identification de l’API dans le menu Canaux d’administration « Accéder aux paramètres SMS »](assets/configure-sms-channel-navigate-to-sms-settings.png "Accéder aux paramètres SMS")



## Définir les informations d’identification de l’API SMS

Commencez par créer le connecteur API qu’AJO utilise pour envoyer les requêtes SMS sortantes.

1. Sous Fournisseur SMS, choisissez **Twilio**.
1. Saisissez les informations d’identification d’API suivantes à l’aide de votre propre compte d’évaluation [Twilio](https://www.twilio.com/try-twilio) :
   - **Nom :** `DEP SMS`
   - **SID du compte :** trouvé sur le tableau de bord de la console Twilio
   - **Jeton d’authentification :** trouvé sur le tableau de bord de la console Twilio (cliquez sur **Afficher** pour l’afficher)
1. Cliquez sur **Envoyer** pour enregistrer les informations d’identification de l’API

>[!NOTE]
>
>Vous aurez besoin d&#39;un compte d&#39;essai Twilio gratuit avec un numéro de téléphone vérifié avant de commencer cette étape. Inscrivez-vous à l’adresse [twilio.com/try-twilio](https://www.twilio.com/try-twilio), puis recherchez le SID de votre compte et le jeton d’authentification dans le tableau de bord de la console Twilio. Consultez le [guide de prise en main](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account) de Twilio pour une présentation complète.

![Champs d’informations d’identification de l’API SMS pour le fournisseur Twilio](assets/configure-sms-channel-enter-api-credentials.png)



## Créer une configuration de canal SMS

Vous allez à présent mapper ces informations d’identification d’API à une configuration de canal que les parcours et les campagnes peuvent utiliser.

1. Accédez à **Canaux** → **Paramètres généraux** → **Configurations de canal**.

   ![Accédez aux configurations de canal sous Paramètres généraux](assets/configure-sms-channel-navigate-channel-configurations.png)



2. Cliquez sur **Créer une configuration de canal**.

   ![Bouton Créer une configuration de canal](assets/configure-sms-channel-click-create-configuration.png)



3. Renseignez les Paramètres de configuration du canal SMS avec les valeurs suivantes :
   - **Nom :** `Relational-SMS-Multi-Entity`
   - **Canal :** `Mobile Message`
   - **Action Marketing :** `SMS Targeting`

>[!NOTE]
>
>Si vous obtenez une erreur indiquant que l’utilisateur ne dispose pas de l’autorisation nécessaire, ignorez-la et continuez.

## Paramètres SMS

Lorsque vous sélectionnez Canal comme Message mobile, une nouvelle section appelée Paramètres SMS s’affiche. Renseignez-le avec les détails suivants :

- **Type de message mobile :** `Marketing`
- **Configuration des messages mobiles :** `DEP SMS`
- **Numéro de l&#39;expéditeur :** `01234567890`
- **Sous-Domaine :** `leave blank`
- **Numéro d&#39;opt-out :** `leave blank`

![Paramètres SMS avec numéro d&#39;expéditeur et type de message mobile](assets/configure-sms-channel-sms-settings-fields.png)



## Détails d’exécution

1. Sous Détails d’exécution, cliquez sur l’onglet **Campagne orchestrée**

   ![Onglet Campagne orchestrée sous Détails d’exécution](assets/configure-sms-channel-execution-details-tab.png)



2. Vérifiez que la case **Activé** est cochée

   ![Case à cocher activée activée cochée pour les campagnes orchestrées](assets/configure-sms-channel-enabled-checkbox.png)



3. Ensuite, sous la sous-section **Dimension d’exécution**, assurez-vous que les éléments suivants sont configurés comme suit :
   - **Diffuser sur le message par :** `Target + Secondary Dimension`
   - **Dimension De Profil Cible :** `dep-rel: Customer Account - customer_id`
   - **Dimension Secondaire :** `dep-rel: Customer Line`

   ![Paramètres de la dimension d’exécution avec la cible et la dimension secondaire](assets/configure-sms-channel-execution-dimension-setup.png)

   ![Dimension Secondaire défini sur dep-rel : ligne du client dans les paramètres de dimension d’exécution « Dimension Secondaire« ](assets/configure-sms-channel-secondary-dimension-detail.png "Dimension Secondaire")

   >[!NOTE]
   >
   >Ce paramètre indique aux campagnes orchestrées que lorsqu’elles envoient des messages, elles doivent diffuser un message par enregistrement correspondant au Dimension cible du profil.



4. Sous l’en-tête Adresse d’exécution , assurez-vous de sélectionner le bouton radio pour **Dimension Secondaire**, puis cliquez sur le bouton de modification sur le **Champ d’exécution du SMS**

   ![Adresse d’exécution définie sur Dimension Secondaire avec champ de modification](assets/configure-sms-channel-execution-address-selection.png)



5. Sur la pop-up, cliquez dans le schéma **dep-rel : Ligne client** et sélectionnez **Téléphone mobile**.

   ![Fenêtre contextuelle de schéma pour le dep-rel : schéma de la ligne client](assets/configure-sms-channel-customer-line-schema-popup.png)

   ![Champ de téléphone mobile sélectionné à partir du dep-rel : schéma de ligne client « Champ de téléphone mobile »](assets/configure-sms-channel-mobile-phone-field-selected.png "Champ de téléphone mobile")



6. Confirmez la dernière correspondance de la section Détails d’exécution ci-dessous

![Configuration des détails de l’exécution finale correspondant aux paramètres requis](assets/configure-sms-channel-final-execution-details.png)



## Envoyer et réviser

1. Cliquez sur le bouton **Envoyer** pour terminer la configuration et afficher un message de réussite

   ![Message de succès après l’envoi de la configuration du canal](assets/configure-sms-channel-submit-success-message.png)



2. Sur la page d’inventaire des configurations de canal, assurez-vous que le statut indique **Actif** avant de passer à autre chose

   ![Statut de configuration du canal affiché comme Actif](assets/configure-sms-channel-active-status.png)

   >[!CAUTION]
   >
   >Patientez jusqu’à ce que le statut devienne **Actif**, sinon les prochaines étapes de l’atelier échoueront



3. Lorsque l’état devient Actif , vous avez terminé.

>[!TIP]
>
>🚀 Booyah ! Votre canal SMS est maintenant en ligne et prêt à être utilisé.



## Récapituler

Vous savez maintenant comment configurer un canal SMS.  Notez que cette configuration est un SMS basé sur une API. Selon votre fournisseur, il peut donc utiliser d’autres méthodes d’authentification.

Vous pouvez en savoir plus [ici](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration) si vous êtes intéressé.
