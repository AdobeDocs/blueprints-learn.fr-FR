---
title: Scénario de personnalisation Web en ligne/hors ligne
description: Synchronisez la personnalisation Web avec le courrier électronique et d’autres personnalisations de canal connues et anonymes.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
translation-type: tm+mt
source-git-commit: 9b6c220a515c5abae22b58fe33558d7d2fed375d
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---



# Scénario de personnalisation Web en ligne/hors ligne

Synchronisez la personnalisation Web avec le courrier électronique et d’autres personnalisations de canal connues et anonymes.

## Cas d’utilisation

* Optimisation des landings page
* Ciblage comportemental et hors ligne des profils
* Personnalisation basée sur des vues antérieures de produit/contenu, d’affinité de produit/contenu, d’attributs environnementaux, de données d’audience tierces et de données démographiques, en plus des informations hors ligne telles que les transactions, les données de fidélité et de gestion de la relation client, et des informations modélisées

## Applications

*  de la plateforme de données clients en temps réel
* Adobe Target
* Adobe Audience Manager (facultatif) : Ajoute des données d’audience tierces, des graphiques de périphériques basés sur les coopératives, la possibilité de redimensionner des segments de plateformes dans Adobe Analytics et la possibilité de redimensionner des segments Adobe Analytics dans la plate-forme
* Adobe Analytics (facultatif) : Ajoute la possibilité de créer des segments à partir de données comportementales historiques et d’une segmentation affinée à partir des données Adobe Analytics

## Architecture

<img src="assets/onoff.svg" alt="Architecture de référence pour le scénario de personnalisation Web en ligne/hors ligne" style="border:1px solid #4a4a4a" />

## Gardiens

* Les segments partagés de l’Experience Platform à l’Audience Manager sont partagés dans les minutes qui suivent la réalisation du segment, que ce soit par le biais de la diffusion en continu ou de la méthode d’évaluation par lot. Il existe une synchronisation initiale de configuration de segment entre AEP et AAM d&#39;environ 4 heures pour que les adhésions au segment AEP commencent à se réaliser dans AAM profils. Une fois dans les profils AAM, les adhésions au segment AEP sont disponibles pour la même personnalisation de page via Adobe Target.
* Notez que pour les réalisations de segments survenant dans la synchronisation de configuration de segment de 4 heures entre AEP et AAM, ces réalisations de segments seront réalisées en AAM sur la tâche de segment de lot suivante en tant que segments &quot;existants&quot;.
* Partage de segments par lots à partir d’AEP : une fois par jour ou initié manuellement via l’API. Une fois que ces adhésions au segment sont réalisées, elles sont partagées avec AAM en quelques minutes et disponibles pour la personnalisation de la même page/page suivante dans Cible.
* La segmentation en flux continu est réalisée en ~ p95 5 min. Une fois que ces réalisations de segment se produisent, elles sont partagées avec AAM en quelques minutes et disponibles pour la personnalisation de la même page/page suivante dans la Cible.
* Par défaut, le service de partage de segments permet le partage d’un maximum de 75 audiences pour chaque suite de rapports Adobe Analytics. Si le client dispose d’une licence d’Audience Manager, il n’existe aucune limite quant au nombre d’audiences pouvant être partagées entre Adobe Analytics et Adobe Target, ou Audience Manager et Adobe Target.

## Conditions préalables à l’implémentation

| Application/Service | Bibliothèque requise | Notes |
|---|---|---|
| Adobe Target | Platform Web SDK*, at.js 0.9.1+ ou mbox.js 61+ | at.js est préférable car mbox.js n’est plus développé. |
| Adobe Audience Manager (facultatif) | Platform Web SDK* ou dil.js 5.0+ |  |
| Adobe Analytics (facultatif) | Platform Web SDK* ou AppMeasurement.js 1.6.4+ | Le suivi Adobe Analytics doit utiliser la collecte de données régionale. |
| Service d’identification des Experience Cloud | Platform Web SDK* ou VisitorAPI.js 2.0+ | (Recommandé) Utilisez l’Experience Platform Launch pour déployer le service d’ID afin de vous assurer que l’ID est défini avant tout appel d’application. |
| Experience Platform Mobile SDK (facultatif) | 4.11 ou version ultérieure pour iOS et Android™ |  |
| SDK Web Experience Platform | 1.0, la version actuelle du SDK Experience Platform contient [divers cas d’utilisation non encore pris en charge pour les applications Experience Cloud](https://github.com/adobe/alloy/projects/5) |  |


## Etapes de mise en oeuvre

1. [Mise en oeuvre du ](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) ciblage d’Adobe pour vos applications Web ou mobiles
1. [Mise en oeuvre de Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html)  (facultatif)
1. [Mise en oeuvre de Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)   (facultatif)
1. [Mise en oeuvre du Profil client en temps réel et Experience Platform](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. Mettre en oeuvre [Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html) ou [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
   >[!NOTE]
   >
   >Chaque application doit utiliser l’ID d’Experience Cloud et faire partie de la même organisation d’Experience Cloud pour permettre le partage des audiences entre les applications.
1. [Demande de mise en service pour le partage des Audiences entre Experience Platform et Adobe Target (Audiences partagées)](https://www.adobe.com/go/audiences)

## Diagrammes de flux de données d’implémentation

Le modèle de personnalisation Web/Mobile peut être mis en oeuvre à l’aide des SDK traditionnels spécifiques à l’application (par exemple, AppMeasurement.js) ou en utilisant le SDK Web/Mobile de la plate-forme et le SDK Edge Network.

### Platform Web/Mobile SDK et Edge Approach

<img src="assets/websdkflow.svg" alt="Architecture de référence pour Platform Web SDK/Mobile SDK et Edge Network Approach" style="border:1px solid #4a4a4a" />

### Approche SDK spécifique à l’application

<img src="assets/appsdkflow.png" alt="Architecture de référence pour l’approche du SDK spécifique à l’application" style="border:1px solid #4a4a4a" />

## Documentation connexe

* [Partage de segments Experience Platform avec l’Audience Manager et d’autres solutions Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)
* [Présentation de la segmentation des Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Segmentation en flux continu](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Présentation du créateur de segments Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Connecteur de source d&#39;Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html)
* [Partage de segments Adobe Analytics par le biais de AAM](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Documentation du SDK Web Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentation du service d’ID Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/home.html)
* [Documentation Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html)

## Publications de blog connexes

* [Plan directeur de la personnalisation Web à l’aide du Profil client en temps réel Adobe Experience Platform](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [Créer une expérience en ligne optimale : Enrichir le Profil unifié avec Requête Service](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [Intégration du moteur de prise de décision Adobe Experience Platform aux sites Web AEM](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [Service d&#39;identité de Adobe Experience Platform : comment résoudre le problème de l&#39;identité du client](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [Comment les Audiences prédictives Adobe Experience Platform améliorent les expériences personnalisées](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [SDK Web Adobe Experience Platform pour la gestion des Audiences](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Mise en oeuvre du Profil client en temps réel Adobe Experience Platform via notre Programme &quot;Client zéro&quot;](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [Comment Adobe Experience Platform peut aider les clients à personnaliser leurs messages mobiles en temps réel avec le service Journey Orchestration et un fournisseur de messagerie mobile](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [Segmentation en secondes : Comment Adobe Experience Platform a rendu le Profil des clients en temps réel réalisable](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [Créer une expérience en ligne optimale : Enrichir le Profil unifié avec Requête Service](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)

