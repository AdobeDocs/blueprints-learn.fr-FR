---
title: Adobe Commerce - Plan directeur RTCDP
description: Intégration de Adobe Experience Platform à Adobe Commerce pour créer une vue unique de clients et personnaliser intelligemment les expériences sur un storefront numérique et entre canaux.
solution: Real-Time Customer Data Platform, Commerce
source-git-commit: abb946358ceeee1af427c5b362ed2f48f733a6c9
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# Adobe Commerce et RTCDP

Cette expérience intégrée permet aux clients Adobe Commerce de s’intégrer facilement à Adobe Experience Platform pour enrichir le profil client et personnaliser les expériences dans le storefront numérique et d’autres canaux.

## Fonctionnalités techniques activées

* Données Storefront (côté client) collectées et envoyées dans n’importe quel produit Adobe Experience Cloud. (ajout au panier, abandons de panier, etc.)
* Statut de la commande du back-office pour tout produit Adobe Experience Cloud
* Les commandes historiques peuvent être envoyées à Adobe Experience Platform
* Partage et personnalisation des audiences RTCDP vers Adobe Commerce

## Conditions préalables

Pour utiliser le connecteur Experience Platform, vous devez disposer des éléments suivants :

* Adobe Commerce 2.4.4 ou version ultérieure
* Adobe ID et ID d’organisation
* Adobe Experience Platform/RTCDP
* [Adobe de la couche de données client (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=en). La collecte de données ACDL est requise pour collecter les données d’événement de vitrine.

## Étapes d’intégration

### Collecte de données d’Adobe Commerce vers Adobe Experience Platform

* [Installer](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) l’extension du connecteur Experience Platform.
* [Se connecter](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) dans votre compte d’Adobe et affichez pour confirmer l’ID d’organisation. L’ID d’organisation est l’ID associé à votre société Experience Cloud configurée. Cet identifiant est une chaîne alphanumérique de 24 caractères, suivie de @AdobeOrg (obligatoire).
* [Créer ou mettre à jour](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/update-xdm.html?lang=en) votre schéma XDM avec des groupes de champs spécifiques à Commerce.
* [Création d’un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=en#create-a-dataset) en fonction du schéma que vous avez créé ou mis à jour. Ce jeu de données contiendra les données Commerce que vous envoyez.
* [Création d’un flux de données](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce.
* [Connexion à Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en).
* [Connexion à Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/connect-data.html?lang=en).

### Connexion à la destination Commerce de Adobe Experience Platform pour le partage d’audiences

Pour vous connecter à la destination Adobe Commerce :

* Dans le [Interface de Adobe Experience Platform](https://experience.adobe.com/platform/), accédez à Destinations > Catalogue.
* Sélectionnez Personnalisation.
* Sélectionnez la destination Adobe Commerce pour la mettre en surbrillance, puis sélectionnez Configurer.
* Suivez les étapes décrites dans la section [tutoriel sur la configuration des destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html?lang=en).

## Données d’usine

* Événements Storefront(Browser/App)
* Événements de back-office
* Historique des données de commande

Pour obtenir la liste complète des événements pris en charge, reportez-vous à [Événements de commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/event-forwarding/events.html?lang=en)

## Architecture

<img src="../commerce/assets/commerce_rtcdp.png" alt="Architecture d’Adobe Commerce RTCDP" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Guides de mise en oeuvre associés

| Guide  | Lien |
|:----|:----|
| Connecteur Platform | [Présentation du connecteur Adobe Commerce Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/overview.html?lang=en) |
| Destination du commerce | [Connexion Adobe Commerce dans RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html?lang=en) |
| Personnalisation Edge | [Activation des audiences vers des destinations de personnalisation de périphérie](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html?lang=en) | |
