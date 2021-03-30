---
title: Plan directeur du centre d'Activité client
description: Recherches sur le Profil client en temps réel afin de fournir un contexte pour le support et les ventes assistés par l’agent.
solution: Experience Platform, Data Collection
kt: 7195
translation-type: tm+mt
source-git-commit: c4bd4bbd40f2ae6b9ab980c5274a6e2007d976d3
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Plan directeur du centre d&#39;Activité client

Le plan directeur du centre d’Activités client montre comment les applications externes peuvent accéder au [!UICONTROL Profil client en temps réel ] de Adobe Experience Platform.

Les applications externes peuvent accéder à R[!UICONTROL Profils client en temps réel] avec une demande de GET d&#39;API. Les attributs, les événements, les adhésions aux segments et les fonctions basées sur les modèles stockées dans le profil peuvent alors être utilisés dans ces applications externes non Adobes.

Grâce à cette fonctionnalité, vous pouvez afficher un contexte riche lorsqu’un client appelle votre centre d’appels. Les agents d&#39;assistance peuvent avoir une visibilité sur la valeur de durée de vie du client, la propension à déclencher ou l&#39;exposition à des campagnes marketing, par exemple. Les agents commerciaux peuvent également bénéficier d&#39;un meilleur contexte ou d&#39;une meilleure connaissance de leur client.

>[!NOTE]
>
>La latence actuelle prise en charge par l’API de recherche de profil est d’environ 500 millisecondes, ce qui rend cette approche inadaptée à l’intégration du profil avec des moteurs de décision en temps réel tels que la personnalisation Web ou mobile de la même page.

## Cas d’utilisation

* Fournir un contexte plus profond aux consommateurs pour les interactions prises en charge par les agents, telles que les expériences d’assistance et de vente. Grâce à la recherche de profil dans l’Experience Platform, les agents peuvent recevoir davantage de contexte sur le consommateur, par exemple des achats récents, des interactions de campagne, des propensions, des adhésions à l’audience et d’autres attributs et connaissances stockés dans le profil client en temps réel.

## Architecture

<img src="assets/cah.svg" alt="Architecture de référence pour le plan directeur du centre d'Activité client" style="border:1px solid #4a4a4a" />

## Gardiens

* [Gardiens pour les données de Profil client en temps réel](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Etapes de mise en oeuvre

1. Configurez des jeux de données et des schémas.
1. Configurer [!UICONTROL Profils client en temps réel] : configurez le schéma et le jeu de données pour [!UICONTROL Profil client en temps réel] et configurez une stratégie de fusion et des identités.
1. Envoyez des données dans la plate-forme et traitez-les dans [!UICONTROL Profil client en temps réel].
1. Utilisez l’API Entité pour rechercher un attribut profil, depuis l’entité d’enregistrement ou l’entité de événement d’expérience.

## Documentation connexe

* [Description du produit Adobe Experience Platform Activation](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [Documentation sur le Profil client en temps réel](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=en)
* [Gardiens de profil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [API de recherche de profil](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
