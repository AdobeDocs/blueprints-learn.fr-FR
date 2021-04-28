---
title: Plan directeur de la personnalisation Web en ligne/hors ligne
description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
translation-type: tm+mt
source-git-commit: 9a52c5f9513e39b31956aaa0f30cad1426b63a95
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 48%

---

# Plan directeur de la personnalisation Web/mobile en ligne/hors ligne

Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.

## Cas d’utilisation

* Optimisation de la page de destination
* Ciblage comportemental et hors ligne des profils
* Personnalisation en fonction des vues précédentes de produit ou de contenu, de l’affinité produit / contenu, des attributs environnementaux, des données d’audience tierces et des données démographiques en plus des informations hors ligne telles que les transactions, les données de fidélité et de gestion de la relation client (CRM), ainsi que des informations modélisées.

## Applications

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (facultatif) : ajoute des données d’audience tierces, un graphique d’appareil basé sur la coopération, la possibilité de faire apparaître des segments Platform dans Adobe Analytics et la possibilité de faire apparaître des segments Adobe Analytics dans Platform
* Adobe Analytics (facultatif) : ajoute la possibilité de créer des segments basés sur des données comportementales historiques et une segmentation fine à partir des données d’Adobe Analytics

## Architecture

<img src="assets/onoff.svg" alt="Architecture de référence du plan directeur de la personnalisation Web en ligne/hors ligne" style="border:1px solid #4a4a4a" />

## Garde-fous

### Gardiens pour l’évaluation et l’Activation des segments

| Type de segmentation | Fréquence | Débit | Latence (évaluation des segments) | Latence (Activation de segment) |
|---|---|---|---|---|
| Segmentation Edge | La segmentation Edge est actuellement en version bêta et permet une segmentation en temps réel valide à évaluer sur le réseau Edge Experience Platform pour une prise de décision en temps réel sur la même page via Adobe Target et Adobe Journey Optimizer. |  | ~100 ms | Disponible immédiatement pour la personnalisation en Adobe Target, pour les recherches de profil dans le Profil Edge et pour l’activation via des destinations basées sur des cookies. |
| Segmentation en streaming | Chaque fois qu’un nouveau événement ou enregistrement de diffusion en continu est assimilé au profil client en temps réel et que la définition de segment est un segment de diffusion en continu valide. <br>Voir la  [documentation sur la ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr) segmentation pour obtenir des instructions sur les critères de segmentation en flux continu. | Jusqu’à 1 500 événements par seconde. | ~ p95 &lt;5min | Une fois que ces réalisations de segments se produisent, elles sont partagées avec l’Audience Manager et le service de partage d’audiences en quelques minutes et disponibles pour la personnalisation de la même page/page suivante dans Adobe Target. |
| Segmentation incrémentielle | Une fois par heure pour les nouvelles données qui ont été ingérées dans le profil client en temps réel depuis la dernière évaluation incrémentielle ou par lot. |  |  | Une fois ces adhésions de segments réalisées, elles sont partagées avec l’Audience Manager et le service de partage d’audiences en quelques minutes et disponibles pour la personnalisation de la même page/page suivante dans Adobe Target. |
| Segmentation par lots | Une fois par jour, en fonction d’un calendrier prédéfini du système, ou d’un appel ad hoc lancé manuellement via l’API. |  | Environ une heure par emploi pour un magasin de profils de 10 To, 2 heures par emploi pour un magasin de profils de 10 à 100 To. Les performances de la tâche de segment par lot dépendent du nombre de profils, de la taille des profils et du nombre de segments évalués. | Une fois ces adhésions de segments réalisées, elles sont partagées avec l’Audience Manager et le service de partage d’audiences en quelques minutes et disponibles pour la personnalisation de la même page/page suivante dans Adobe Target. |

### Gardiens pour le partage d’audiences entre applications


| Modèle d&#39;intégration de partage d&#39;Audiences | Détails | Fréquence | Débit | Latence (évaluation des segments) | Latence (Activation de segment) |
|---|---|---|---|---|---|
| Plate-forme de données client en temps réel vers l’Audience Manager |  | Dépend du type de segmentation : voir le tableau des garde-fous de segmentation ci-dessus. | Dépend du type de segmentation : voir le tableau des garde-fous de segmentation ci-dessus. | Dépend du type de segmentation : voir le tableau des garde-fous de segmentation ci-dessus. | Dans les minutes qui suivent l&#39;achèvement de l&#39;évaluation du segment.<br>La synchronisation initiale de la configuration des audiences entre la plateforme de données client en temps réel et l’Audience Manager prend environ 4 heures.<br>Les adhésions d’audience réalisées au cours de la période de 4 heures sont consignées à l’Audience Manager sur la tâche de segmentation par lots suivante en tant qu’adhésions d’audience &quot;existantes&quot;. |
| Adobe Analytics à l&#39;Audience Manager | Par défaut, 75 audiences au maximum peuvent être partagées pour chaque suite de rapports Adobe Analytics. Si une licence d’Audience Manager est utilisée, il n’y a aucune limite au nombre d’audiences pouvant être partagées entre Adobe Analytics et Adobe Target ou Adobe Audience Manager et Adobe Target. |  |  |  |  |
| Adobe Analytics vers la plateforme de données client en temps réel | Non disponible actuellement. |  |  |  |  |

## Modèles d’implémentation

Le modèle de personnalisation Web/Mobile peut être mis en oeuvre par les approches suivantes, comme indiqué ci-dessous.

1. Utilisation du [!UICONTROL Platform Web SDK] ou du [!UICONTROL Platform Mobile SDK] et du [!UICONTROL Edge Network].
1. Utilisation de kits SDK spécifiques aux applications (par exemple, AppMeasurement.js)

### 1. Plateforme Web/Mobile SDK et approche Edge

<img src="assets/websdkflow.svg" alt="Architecture de référence pour l'approche [!UICONTROL Platform Web SDK] ou [!UICONTROL Platform Mobile SDK] et [!UICONTROL Edge Network]" style="border:1px solid #4a4a4a" />

### 2. Approche SDK spécifique à l&#39;application

<img src="assets/appsdkflow.png" alt="Architecture de référence pour l’approche d’utilisation d’un SDK spécifique à l’application" style="border:1px solid #4a4a4a" />

## Conditions préalables à la mise en œuvre

| Application / service | Bibliothèque requise | Notes |
|---|---|---|
| Adobe Target | [!UICONTROL Platform Web SDK]*, at.js 0.9.1+ ou mbox.js 61+ | at.js est recommandé car mbox.js n’est plus en cours de développement. |
| Adobe Audience Manager (facultatif) | [!UICONTROL Platform Web SDK]* ou dil.js 5.0+ |  |
| Adobe Analytics (facultatif) | [!UICONTROL Platform Web SDK]* ou AppMeasurement.js 1.6.4+ | Le tracking d’Adobe Analytics doit utiliser la collecte de données régionale (RDC). |
| Service d’identités d’Experience Cloud | [!UICONTROL Platform Web SDK]* ou VisitorAPI.js 2.0+ | (Recommandé) Utilisez Experience Platform Launch pour déployer le service d’identités afin de vous assurer que l’identité est définie avant tout appel d’application |
| SDK mobile Experience Platform (facultatif) | 4.11 ou plus récent pour iOS et Android™ |  |
| SDK web Experience Platform | 1.0, la version actuelle du SDK Experience Platform comprend [des cas d’utilisation qui ne sont pas encore pris en charge pour les applications Experience Cloud](https://github.com/adobe/alloy/projects/5) |  |


## Étapes d’implémentation

1. [Implémentez Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=fr) pour vos applications web ou mobiles
1. [Implémentez Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=fr) (facultatif)
1. [Implémentez Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=fr) (facultatif)
1. [[!UICONTROL Implémentez Experience Platform et le profil client en temps réel]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=fr)
1. Implémentez [le service d’identités d’Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=fr) ou [le SDK web d’Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr)
   >[!NOTE]
   >
   >Chaque application doit utiliser l’Experience Cloud ID et faire partie de la même organisation Experience Cloud pour que soit possible le partage d’audience entre les applications.
1. [Demandez l’approvisionnement pour le partage d’audience entre Experience Platform et Adobe Target (audiences partagées)](https://www.adobe.com/go/audiences)

## Documentation connexe

* [Partage de segments Experience Platform avec Audience Manager et d’autres solutions Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=fr)
* [Présentation de la segmentation dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr)
* [Segmentation en streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Présentation du créateur de segments d’Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=fr)
* [Connecteur source d’Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)
* [Documentation pour le SDK web d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentation sur le service d’identités d’Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=fr)
* [Documentation pour Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html?lang=fr)

## Articles de blog connexes

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
