---
title: Diagrammes Experience Platform (AEP) et architecture des applications
description: Affichez les diagrammes d’architecture qui montrent la manière dont Adobe Experience Platform (AEP) est lié à d’autres applications et services applicatifs Experience Cloud.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 495a2480828e2c6b4caa41226f4fe67437b081c1
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 10%

---

# Diagrammes d’architecture de Adobe Experience Platform et des applications

Ces diagrammes d’architecture montrent la manière dont Experience Platform (AEP) est lié à d’autres applications et services applicatifs Experience Cloud.

>[!MORELIKETHIS]
>
>[Configurations d’intégration pour les intégrations d’applications Experience Cloud](https://experienceleague.adobe.com/docs/integrations-learn/experience-cloud/overview.html?lang=fr).


## Diagramme d’architecture

Ce schéma d’architecture montre comment Adobe Experience Platform se rattache aux autres applications et services applicatifs Adobe Experience Cloud.

<img src="assets/aep+apps.svg" alt="Experience Platform et autres applications" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Diagramme de présentation

<img src="assets/aep+apps_overview.svg" alt="Experience Platform et autres applications" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Diagramme d’architecture détaillé

<img src="assets/aep+apps_detailed.svg" alt="Experience Platform et autres applications" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

>[!VIDEO](https://video.tv.adobe.com/v/3422780/?quality=12&learn=on&captions=fre_fr)

## Intégrations des applications AEP et Experience Cloud

| Application | D’Experience Platform vers l’application | De l’application vers Experience Platform |
|------------------------------|-----------------------------------|-----------------------------------|
| **Ad Cloud** | - Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Ad Cloud pour le ciblage via Audience Manager. | - Aucune intégration actuelle |
| **Analytics** | - Les données collectées via le SDK Web/Mobile peuvent être transférées vers Adobe Analytics. | - Les données collectées par Analytics peuvent être envoyées au lac de données et au magasin de profils d’Experience Platform. [Connecteur de données Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=fr) |
| **Audience Manager** | - Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Audience Manager pour activation vers des destinations de cookies tiers. | - Les données collectées et évaluées ainsi que l’appartenance à l’audience d’Audience Manager peuvent être partagées avec le lac de données et le magasin de profils d’Experience Platform. [Connecteur source d’Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=fr) |
| **Adobe Campaign** | - Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Campaign Classic pour lancer des campagnes. | - Les données d’interaction et de campagne collectées par Campaign peuvent être ingérées dans Experience Platform pour une utilisation ultérieure dans la création d’audiences, Customer Journey Analytics et Query Service. |
| **Campaign Standard** | - Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Campaign Standard pour lancer des campagnes. | - Les données d’interaction et de campagne collectées par Campaign peuvent être ingérées dans Experience Platform pour une utilisation ultérieure. |
| **Customer Journey Analytics** | - Les données collectées et ingérées dans le lac de données Experience Platform peuvent être traitées dans Customer Journey Analytics. <br> - Les données de profil et d’audience de Real-time Customer Data Platform peuvent être ingérées dans CJA. [Intégration de RTCDP à CJA](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=fr) | - Créez des audiences dans CJA et partagez les résultats des audiences avec Real-time Customer Data Platform. [Publication d’audience CJA](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=fr) |
| **Experience Manager** | - Vous pouvez accéder au profil Experience Platform côté serveur pour offrir des expériences personnalisées dans Experience Manager. | - Aucune intégration en cours, les interactions effectuées sur les sites Experience Manager sont collectées via les SDK web et mobile d’Experience Platform. |
| **Journey Optimizer** | - Les événements de données et les profils ingérés dans Experience Platform sont rendus disponibles pour Journey Optimizer. | - Les données d’interaction et de campagne générées par Journey Optimizer sont collectées dans Experience Platform pour une utilisation ultérieure. |
| **Adobe Commerce** | - Les profils et les audiences créés dans Real-time Customer Data Platform peuvent être utilisés pour la personnalisation dans Adobe Commerce. | - Les données natives d’Adobe Commerce peuvent être envoyées à Experience Platform via un connecteur source Adobe Commerce. |
| **Marketo** | - Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Marketo pour lancer des campagnes et mettre à jour des objets. | - Les comptes, contacts et données de campagne Marketo sont ingérés dans Experience Platform pour une analyse plus approfondie. [Connecteur Marketo Engage](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=fr) |
| **Real-Time CDP** | - Les données ingérées dans Experience Platform constituent la source des profils clients en temps réel qui alimentent Real-time Customer Data Platform. | - Les mesures d’audience et de profil sont envoyées au lac de données Experience Platform pour obtenir des informations. |
| **Target** | - Les audiences et les attributs de profil de Real-time Customer Data Platform peuvent être partagés avec Target pour la personnalisation. | - Les données collectées pour les expériences Target peuvent être envoyées à Experience Platform pour la création et l’analyse d’audiences. |
