---
title: Adobe Commerce - Plan directeur RTCDP
description: Intégration de Adobe Experience Platform à Adobe Commerce pour créer une vue unique de clients et personnaliser intelligemment les expériences sur un storefront numérique et entre canaux.
solution: Real-Time Customer Data Platform, Commerce
exl-id: e2fc5e1c-c865-4c24-9b82-861a34aba487
source-git-commit: 80a4716a7ed64ec30b9c60b3444affc5bd8984e4
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---

# Adobe Commerce et RTCDP

L’extension [!DNL Data Connection] permet aux clients Adobe Commerce de s’intégrer facilement à Adobe Experience Platform pour enrichir le profil client et personnaliser les expériences dans le storefront numérique et d’autres canaux.

## Fonctionnalités techniques activées

* Données de storefront (côté client, telles que l’ajout au panier, les abandons de panier, etc.) collectées et envoyées dans n’importe quel produit Adobe Experience Cloud.
* Statut de la commande du back-office pour tout produit Adobe Experience Cloud
* Les commandes historiques peuvent être envoyées à Adobe Experience Platform
* Partage et personnalisation des audiences RTCDP vers Adobe Commerce

## Conditions préalables

Pour utiliser l’extension [!DNL Data Connection], vous devez disposer des éléments suivants :

* Adobe Commerce 2.4.4 ou version ultérieure
* Adobe ID et ID d’organisation
* Adobe Experience Platform/RTCDP
* [Adobe de la couche de données client (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). La collecte de données ACDL est requise pour collecter les données d’événement de vitrine.

## Étapes d’intégration

### Collecte de données d’Adobe Commerce vers Adobe Experience Platform

* [Installez ](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/install.html) l’extension [!DNL Data Connection].
* [Connectez-vous](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) à votre compte d’Adobe et affichez-le pour confirmer l’ID d’organisation. L’ID d’organisation est l’ID associé à votre société Experience Cloud configurée. Cet identifiant est une chaîne alphanumérique de 24 caractères, suivie de @AdobeOrg (obligatoire).
* [Créez ou mettez à jour ](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/update-xdm.html) votre schéma XDM avec des groupes de champs spécifiques à Commerce.
* [Créez un jeu de données](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basé sur le schéma que vous avez créé ou mis à jour. Ce jeu de données contiendra les données Commerce que vous envoyez.
* [ Créez un flux de données ](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) et sélectionnez le schéma XDM contenant les groupes de champs spécifiques à Commerce.
* [Connexion aux services Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).
* [Connectez-vous à Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/connect-data.html).

### Connexion à la destination Commerce à partir de Adobe Experience Platform pour le partage d’audiences

Pour vous connecter à la destination Adobe Commerce :

* Dans l’ [interface Adobe Experience Platform](https://experience.adobe.com/platform/), accédez à Destinations > Catalogue.
* Sélectionnez Personalization.
* Sélectionnez la destination Adobe Commerce pour la mettre en surbrillance, puis sélectionnez Configurer.
* Suivez les étapes décrites dans le [tutoriel de configuration de destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html).

## Données d’usine

* Événements Storefront (Browser/App)
* Événements de back-office
* Historique des données de commande

Pour obtenir la liste complète des événements pris en charge, reportez-vous à la section [Événements Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html)

## Architecture

<img src="../commerce/assets/commerce_rtcdp.png" alt="Architecture d’Adobe Commerce RTCDP" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Guides de mise en oeuvre associés

| Guide | Lien |
|:----|:----|
| Connecteur Platform | [ &lbrace;Adobe Commerce Experience Platform connector overview](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html) |
| Destination Commerce | [Connexion Adobe Commerce dans RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html) |
| Edge Personalization | [Activer les audiences vers les destinations de personnalisation de périphérie](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html) |
