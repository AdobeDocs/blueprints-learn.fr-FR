---
hold: true
title: Créer un flux de données
description: Découvrez comment créer et configurer un flux de données avec les services Adobe Experience Platform, Offer Decisioning et Journey Optimizer pour activer le traitement des événements Edge.
doc-type: article
solution: Experience Platform
exl-id: 37873340-476a-4303-886d-de4835bba8df
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Créer un flux de données

## Objectif d’apprentissage

Créez et configurez un flux de données avec les services requis pour activer le traitement des événements Edge.

Un flux de données définit les services qui l’utiliseront.

- Lors de l’envoi de données à Edge, vous spécifiez le flux de données à utiliser
- Les données envoyées à ces flux de données peuvent ensuite agir en fonction du service configuré
  - Adobe Experience Platform

## Créer un flux de données

1. Dans le rail de gauche, sous **Collecte de données** cliquez sur **Flux de données**
1. Cliquez ensuite sur **Nouveau flux de données** pour en créer un

![Liste Flux de données avec le bouton Nouveau flux de données en surbrillance](assets/create-datastream-new-datastream-button.png)

## Configurer le flux de données

Configurez le flux de données avec les informations suivantes :

1. Nom -> **flux de données SB + \&lt;nom du sandbox> (c’est-à-dire flux de données SB01)**
1. Schéma de mappage -> **dep : Web**
1. Activez toutes les options **activé** sous **Géolocalisation et recherche réseau** si vous souhaitez capturer ces informations.
1. Cliquez sur le bouton **Enregistrer** lorsque vous avez terminé

>[!WARNING]
>
>Ne cliquez pas sur Enregistrer et ajouter un mappage.  Si vous le faites accidentellement, annulez simplement

![Formulaire de configuration de train de données avec nom et champs de schéma de mappage](assets/create-datastream-configure-datastream-form.png "Configurez le train de données")



Une fois le flux de données enregistré, l’écran suivant s’affiche :

![Écran de confirmation après l’enregistrement du nouveau flux de données](assets/create-datastream-created-confirmation.png "le flux de données créé sur l’écran final")

## Ajout d’un service Adobe Experience Platform

Vous pouvez ainsi envoyer des données au hub et accéder à un jeu de données pour les données reçues par ce flux de données.

1. Cliquez sur le bouton bleu **Ajouter un service** situé au milieu de l’écran

![Bouton Ajouter un service sur l’écran de configuration du flux de données](assets/create-datastream-add-service-button.png)

2. Configurez les éléments suivants :
   - **Service** -> `Adobe Experience Platform`
   - **Jeu de données d’événement** -> `dep: Web`
   - **Jeu de données de profil** -> `dep: Customer Account`
   - **Sélectionner une case à cocher** -> `Offer Decisioning`
   - **Sélectionner une case à cocher** -> `Adobe Journey Optimizer`
3. Lorsque vous avez terminé, cliquez sur **Enregistrer**

Boîte de dialogue de configuration du service Adobe Experience Platform ![avec les champs d’événement et de jeu de données de profil](assets/create-datastream-configure-aep-service.png)

Le service est maintenant ajouté à votre flux de données

![Service Adobe Experience Platform ajouté au flux de données](assets/create-datastream-aep-service-added.png "Service Adobe Experience Platform ajouté au flux de données")

**Copiez** et **enregistrez** l’**identifiant de flux de données** sur votre ordinateur local (nous l’utiliserons ultérieurement dans Postman).

![Champ d’identifiant du flux de données à copier et enregistrer pour une utilisation ultérieure](assets/create-datastream-copy-datastream-id.png)

## Récapituler

Un flux de données fonctionnel doit être configuré avec le service Adobe Experience Platform.
