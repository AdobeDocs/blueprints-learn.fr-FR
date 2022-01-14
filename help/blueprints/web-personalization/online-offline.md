---
title: Personnalisation web/mobile à l’aide de données en ligne et hors ligne
description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
landing-page-description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 070c78ee3cf32e70af90c6cbcdd77d5258a32fb7
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 93%

---

# Personnalisation web/mobile à l’aide de données en ligne et hors ligne

Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.

## Cas d’utilisation

* Optimisation de la page de destination
* Ciblage comportemental et hors ligne des profils
* Personnalisation en fonction des vues précédentes de produit ou de contenu, de l’affinité produit / contenu, des attributs environnementaux, des données d’audience tierces et des données démographiques en plus des informations hors ligne telles que les transactions, les données de fidélité et de gestion de la relation client (CRM), ainsi que des informations modélisées.
* Partagez et ciblez des audiences définies dans Real-time Customer Data Platform sur les sites web et les applications mobiles à l’aide d’Adobe Target.

## Applications

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (facultatif) : ajoute des données d’audience tierces, un graphique des appareils basé sur la coopération, la possibilité de faire apparaître des segments Platform dans Adobe Analytics et la possibilité de faire apparaître des segments Adobe Analytics dans Platform
* Adobe Analytics (facultatif) : ajoute la possibilité de créer des segments basés sur des données comportementales historiques et une segmentation fine à partir des données d’Adobe Analytics

## Motifs d’intégration

<table class="tg" style="undefined;table-layout: fixed; width: 790px">
<colgroup>
<col style="width: 20px">
<col style="width: 276px">
<col style="width: 229px">
<col style="width: 265px">
</colgroup>
<thead>
  <tr>
    <th class="tg-y6fn">#</th>
    <th class="tg-f7v4">Motif d’intégration</th>
    <th class="tg-y6fn">Fonctionnalité</th>
    <th class="tg-f7v4">Conditions préalables</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">Diffusion en continu et partage d’audience par lots à partir de RTCDP vers Target et Audience Manager par le biais d’un service de partage d’audience</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">- Partagez des audiences en continu et par lots à partir de la plateforme RTCDP vers Target et Audience Manager par le biais d’un service de partage d’audience. Les audiences évaluées en temps réel nécessitent l’évaluation de l’audience en temps réel et le SDK web tels que décrits dans le motif d’intégration 3.</span></td>
    <td class="tg-73oq">- La projection de l’audience par un service de partage d’audience doit être configurée.<br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.<br>- L’identité doit être résolue sur l’ECID et pouvoir être partagée sur Edge pour que Target puisse agir dessus. AAM dispose d’une liste distincte d’identités approuvées pour lesquelles établir une correspondance<br>- Le déploiement du SDK web n’est pas nécessaire pour cette intégration.</td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">Diffusion en continu et partage d’audience par lots à partir de RTCDP vers Target par le biais d’Edge</td>
    <td class="tg-0lax">- Partagez des audiences en continu et par lots à partir de la plateforme RTCDP vers Target via Edge Network. Les audiences évaluées en temps réel nécessitent l’évaluation de l’audience en temps réel et le SDK web tels que décrits dans le motif d’intégration 3.</td>
    <td class="tg-73oq"><span style="text-decoration:none">- Actuellement en version bêta</span><br>- La destination cible doit être configurée dans les destinations RTCDP.<br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.<br>Le SDK web n’est pas requis. Le SDK web et AT.js sont pris en charge. <br>- Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge. <br>- Pour les recherches d’espace de noms d’identifiant personnalisé sur Edge, le déploiement du SDK web est requis et chaque identité doit être définie en tant qu’identité dans la carte d’identité.</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq">Évaluation des segments en temps réel à partir de RTCDP sur Edge partagé vers Target via Edge Network à l’aide du SDK web.</td>
    <td class="tg-0lax">- Évaluez les audiences en temps réel pour une personnalisation de même page ou de page suivante sur Edge.</td>
    <td class="tg-73oq"><span style="text-decoration:none">- Actuellement en version bêta</span><br>- La destination cible doit être configurée dans les destinations RTCDP.<br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.<br>- Le SDK web doit être implémenté.<br>- Également pris en charge via l’API.</td>
  </tr>
</tbody>
</table>


## Architecture

Architecture d’aperçu

<img src="assets/RTCDP+Target.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a" />

Architecture de flux de processus

<img src="assets/RTCDP+Target_flow.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a" />

Architecture détaillée

<img src="assets/personalization_with_apps.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a"/>

## Garde-fous

[Référez-vous aux garde-fous décrits sur la page de présentation des plans directeurs de personnalisation web et mobile.](overview.md)

## Modèles d’implémentation

Le plan directeur de personnalisation web / mobile peut être mis en œuvre par les approches suivantes, comme indiqué ci-dessous.

1. Utilisation du [!UICONTROL SDK web Experience Platform] ou du [!UICONTROL SDK mobile Experience Platform] et de [!UICONTROL Edge Network].
1. Utilisation de SDK traditionnels spécifiques aux applications (par exemple, AppMeasurement.js)

### 1. Approche d’utilisation d’Edge et du SDK web ou mobile de Platform

[Reportez-vous au plan directeur du SDK web et mobile d’Experience Platform](../data-ingestion/websdk.md)

### 2. Approche d’utilisation d’un SDK spécifique à l’application

<img src="assets/app_sdk_flow.png" alt="Architecture de référence pour l’approche d’utilisation d’un SDK spécifique à l’application" style="width:80%; border:1px solid #4a4a4a" />

## Conditions préalables à la mise en œuvre

Conditions préalables requises pour les identités

* Le partage d’audiences à partir d’Adobe Experience Platform vers Adobe Target nécessite l’utilisation de l’ECID en tant qu’identité.
* D’autres identités peuvent également être utilisées pour partager des audiences Experience Platform vers Adobe Target à l’aide d’Audience Manager. Experience Platform active les audiences vers Audience Manager à l’aide des espaces de noms pris en charge suivants : IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Notez qu’Audience Manager et Target résolvent les abonnements aux audiences par le biais de l’identité ECID. Par conséquent, l’ECID est toujours requis pour le partage d’audience final vers Adobe Target.

| Application / service | Bibliothèque requise | Notes |
|---|---|---|
| Adobe Target | [!UICONTROL SDK web Experience Platform]*, at.js 0.9.1+ ou mbox.js 61+ | at.js est recommandé car mbox.js n’est plus en cours de développement. |
| Adobe Audience Manager (facultatif) | [!UICONTROL SDK web Experience Platform]* ou dil.js 5.0+ |  |
| Adobe Analytics (facultatif) | [!UICONTROL SDK web Experience Platform]* ou AppMeasurement.js 1.6.4+ | Le tracking d’Adobe Analytics doit utiliser la collecte de données régionale (RDC). |
| Service Experience Cloud ID | [!UICONTROL SDK web Experience Platform]* ou VisitorAPI.js 2.0+ | (Recommandé) Utilisez Experience Platform Launch pour déployer le service d’identités afin de vous assurer que l’identité est définie avant tout appel d’application |
| SDK mobile Experience Platform (facultatif) | 4.11 ou plus récent pour iOS et Android™ |  |
| SDK web Experience Platform | 1.0, la version actuelle du SDK Experience Platform comprend [des cas d’utilisation qui ne sont pas encore pris en charge pour les applications Experience Cloud](https://github.com/adobe/alloy/projects/5) |  |




## Étapes d’implémentation

1. [Implémentez Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=fr) pour vos applications web ou mobiles
1. [Implémentez Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=fr) (facultatif)
1. [Implémentez Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=fr) (facultatif)
1. [Implémentez Experience Platform et le [!UICONTROL profil client en temps réel]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=fr)
1. Implémentez [le service d’identités d’Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=fr) ou [le SDK web d’Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr)
1. [Activation d’Adobe Target en tant que destination dans Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) ou pour l’approche de partage d’audience [Demande d’attribution de privilèges d’accès pour le partage d’audiences entre Experience Platform et Adobe Target (audiences partagées)](https://www.adobe.com/go/audiences) pour partager des audiences de l’Experience Platform vers Target.
   >[!NOTE]
   >
   >Lors de l’utilisation du service de partage d’audience entre RTCDP et Adobe Target, les audiences doivent être partagées à l’aide de l&#39;Experience Cloud ID et faire partie de la même organisation Experience Cloud. La prise en charge d’identités autres qu’ECID nécessite l’utilisation du SDK web et du réseau Experience Edge Network.


## Documentation connexe

* [Partage de segments Experience Platform avec Audience Manager et d’autres solutions Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=fr)
* [Présentation de la segmentation dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr)
* [Segmentation en streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Connexion Adobe Target pour Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Présentation du créateur de segments d’Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=fr)
* [Connecteur source d’Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)
* [Documentation pour le SDK web d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentation sur le service Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=fr)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)

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
