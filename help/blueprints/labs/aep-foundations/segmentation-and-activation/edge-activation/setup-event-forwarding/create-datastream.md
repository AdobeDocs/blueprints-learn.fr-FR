---
title: Créer un flux de données
description: Créez et configurez un flux de données avec les services Transfert d’événement et Adobe Experience Platform pour acheminer les événements Edge entrants.
doc-type: article
solution: Experience Platform
exl-id: f7ada451-2f87-48f4-8673-7bfa0df9d0d3
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 1%

---


# Créer un flux de données

Un flux de données définit les services qui l’utiliseront.

- Lors de l’envoi de données à Edge, vous spécifiez le flux de données à utiliser
- Les données envoyées à ces flux de données peuvent ensuite agir en fonction du service configuré
  - Transfert d’événement
  - Adobe Experience Platform

## Créer un flux de données

1. Dans le rail de gauche, sous **Collecte de données** cliquez sur **Flux de données**
1. Cliquez ensuite sur **Nouveau flux de données** pour en créer un

![Liste Flux de données avec le bouton Nouveau flux de données en surbrillance](assets/create-datastream-new-datastream-button.png)

## Configurer le flux de données

Configurez le flux de données avec les informations suivantes :

1. Nom -> **flux de données SB + \&lt;nom du sandbox> (c’est-à-dire flux de données SB01)**
1. Schéma d’événement -> **dep : Web**
1. Activez toutes les options **activé** sous **Géolocalisation et recherche réseau**
1. Cliquez sur le bouton **Enregistrer** lorsque vous avez terminé

>[!WARNING]
>
>Ne cliquez pas sur Enregistrer et ajouter un mappage.  Si vous le faites accidentellement, annulez simplement

![Formulaire de configuration de train de données avec nom, schéma d’événement et options de recherche de géolocalisation définis](assets/create-datastream-configure-datastream-form.png "Configurez le train de données")



Une fois le flux de données enregistré, l’écran suivant s’affiche :

![Écran de confirmation affiché immédiatement après l’enregistrement du nouveau flux de données](assets/create-datastream-created-confirmation-screen.png "le flux de données créé sur l’écran final")

## Ajouter un service de transfert d’événement

Vous pouvez ainsi utiliser le transfert d’événement pour les données reçues par ce flux de données.



1. Cliquez sur **Ajouter un service**

   ![Page des détails du flux de données avec le bouton Ajouter un service en surbrillance](assets/create-datastream-add-service-button.png "Ajouter un service")

1. Configurez les éléments suivants :

   - Service -> Transfert d’événement
   - Propriété -> Sélectionnez la propriété que vous avez créée à l’étape précédente.  Son nom doit être le suivant : Propriété de transfert d’événement SB + \&lt;votre numéro de sandbox>
   - Environnement -> Développement

1. Lorsque vous avez terminé, cliquez sur **Enregistrer**

![Configuration du service de transfert d’événement avec la propriété et l’environnement de développement sélectionnés](assets/create-datastream-event-forwarding-service-config.png "Écran Configuration du transfert d’événement")



## Ajout d’un service Adobe Experience Platform

Vous pouvez ainsi envoyer des données au hub et accéder à un jeu de données pour les données reçues par ce flux de données.



1. Cliquez sur **Ajouter un service**

   ![Page des détails du flux de données avec le bouton Ajouter un service mis en surbrillance pour ajouter le service Adobe Experience Platform](assets/create-datastream-add-second-service-button.png "Ajoutez un nouveau service")

1. Configurez les éléments suivants :

   - Service -> Adobe Experience Platform
   - Jeu de données d’événement -> dep : Web
   - Jeu de données de profil -> prop : compte client
   - Sélectionnez Case à cocher -> Segmentation Edge .
   - Sélectionner la case à cocher -> Destination Personalization

   Configuration du service ![Adobe Experience Platform avec jeu de données d’événement, jeu de données de profil et cases à cocher de segmentation définis](assets/create-datastream-aep-service-config.png "Configurer le service")

1. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

1. Votre écran final devrait ressembler à ce qui suit, avec deux services présents. **Copiez** et **enregistrez** l’**identifiant de flux de données** sur votre ordinateur local (vous l’utiliserez ultérieurement dans Postman).

![Configuration finale du flux de données avec les services Transfert d’événement et Adobe Experience Platform répertoriés](assets/create-datastream-final-configuration-both-services.png "Configuration finale du flux de données")
