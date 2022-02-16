---
title: Personnalisation web/mobile à l’aide de données en ligne et hors ligne
description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
landing-page-description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 91db73c9fb14d461ee62444199c3d053bd094639
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 68%

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
* Adobe Audience Manager (facultatif) : Ajoute des données d’audience tierces, un graphique d’appareil basé sur la coopération, la possibilité d’afficher les audiences Real-time Customer Data Platform dans Adobe Analytics et la possibilité d’afficher les audiences Adobe Analytics dans Real-time Customer Data Platform.
* Adobe Analytics (facultatif) : ajoute la possibilité de créer des segments basés sur des données comportementales historiques et une segmentation fine à partir des données d’Adobe Analytics

## Modèles d’intégration

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
<td class="tg-73oq">Évaluation des segments en temps réel de Real-time Customer Data Platform sur Edge partagée avec Target</td>
    <td class="tg-0lax">- Évaluez les audiences en temps réel pour une personnalisation de même page ou de page suivante sur Edge.</td>
    <td class="tg-73oq">- La destination Target doit être configurée dans les destinations Real-time Customer Data Platform.<br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.<br>- Le SDK web doit être implémenté.<br>- L’implémentation du SDK mobile et basée sur l’API n’est actuellement pas disponible.</td> 
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">Diffusion Real-time Customer Data Platform en continu et partage d’audiences par lots vers Target via l’approche Edge</td>
    <td class="tg-0lax">- Partagez des audiences en continu et par lots de Real-time Customer Data Platform vers Target par le biais du réseau Edge. Les audiences évaluées en temps réel nécessitent l’évaluation de l’audience en temps réel et le SDK web tels que décrits dans le motif d’intégration 1.</td>
    <td class="tg-73oq">- La destination Target doit être configurée dans les destinations Real-time Customer Data Platform.<br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.<br>Le SDK web n’est pas requis. <br>- Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge. <br>- Pour les recherches d’espaces de noms d’identité personnalisés sur Edge, le déploiement du SDK Web est requis et chaque identité doit être définie en tant qu’identité dans la carte d’identité.</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">Partage en continu et par lots d’audiences Real-time Customer Data Platform vers Target et l’Audience Manager via l’approche du service de partage d’audiences</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">- Partagez des audiences en continu et par lots de Real-time Customer Data Platform vers Target et l’Audience Manager via le service de partage d’audience. Les audiences évaluées en temps réel nécessitent l’évaluation de l’audience en temps réel et le SDK web tels que décrits dans le motif d’intégration 1.</span></td>
    <td class="tg-73oq">- La projection de l’audience par un service de partage d’audience doit être configurée.<br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.<br>- L’identité doit être résolue sur l’ECID et pouvoir être partagée sur Edge pour que Target puisse agir dessus.<br>- Le déploiement de WebSDK n’est pas nécessaire pour cette intégration.</td>
  </tr>
</tbody>
</table>


## Architecture

Architecture détaillée

<img src="assets/RTCDP+Target.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a" />

Diagramme de séquence

<img src="assets/RTCDP+Target_flow.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a" />

<br>

<img src="assets/RTCDP+Target_sequence.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a" />


Architecture d’aperçu

<img src="assets/personalization_with_apps.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a"/>

## Garde-fous

[Référez-vous aux garde-fous décrits sur la page de présentation des plans directeurs de personnalisation web et mobile.](overview.md)

## Modèles d’implémentation

Le plan directeur de personnalisation web / mobile peut être mis en œuvre par les approches suivantes, comme indiqué ci-dessous.

1. Utilisation du [!UICONTROL SDK web Experience Platform] ou du [!UICONTROL SDK mobile Experience Platform] et de [!UICONTROL Edge Network]. [Reportez-vous au plan directeur du SDK web et mobile d’Experience Platform](../data-ingestion/websdk.md)
1. Utilisation de SDK traditionnels spécifiques aux applications (par exemple, AppMeasurement.js)
<img src="assets/app_sdk_flow.png" alt="Architecture de référence pour l’approche d’utilisation d’un SDK spécifique à l’application" style="width:80%; border:1px solid #4a4a4a" />

## Considérations de mise en œuvre

Conditions préalables requises pour les identités

* Toute identité Principale peut être utilisée lors de l’utilisation du modèle d’intégration 1 décrit ci-dessus avec le réseau Edge et le SDK WebSDK. La personnalisation de la première connexion nécessite que l’identité Principale du jeu de requêtes de personnalisation corresponde à l’identité Principale du profil de Real-time Customer Data Platform. La combinaison des identités entre les appareils anonymes et les clients connus est traitée sur le hub et projetée ultérieurement vers le edge. Par conséquent, si l’identité Principale est définie comme identifiant de l’appareil, les données clients connues ne s’appliqueront pas avant les sessions suivantes où les profils anonymes et connus ont été unifiés.
* Le partage d’audiences de Adobe Experience Platform vers Adobe Target nécessite l’utilisation d’ECID comme identité lors de l’utilisation du service de partage d’audience, comme indiqué dans le modèle d’intégration 3 ci-dessus.
* D’autres identités peuvent également être utilisées pour partager des audiences Experience Platform vers Adobe Target à l’aide d’Audience Manager. Experience Platform active les audiences vers Audience Manager à l’aide des espaces de noms pris en charge suivants : IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Notez qu’Audience Manager et Target résolvent les abonnements aux audiences par le biais de l’identité ECID. Par conséquent, l’ECID est toujours requis pour le partage d’audience final vers Adobe Target.

## Étapes d’implémentation

1. [Implémentez Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=fr) pour vos applications web ou mobiles
1. [Implémentez Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=fr) (facultatif)
1. [Implémentez Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=fr) (facultatif)
1. [Implémentez Experience Platform et le [!UICONTROL profil client en temps réel]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=fr)
1. Implémentez [le service d’identités d’Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=fr) ou [le SDK web d’Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr). Le SDK Web Experience Platform est requis pour la segmentation Edge en temps réel, mais pas pour le partage d’audiences par lots et en flux continu de Real-time Customer Data Platform vers Target. Notez que la prise en charge de la segmentation en temps réel via le SDK Mobile et l’API n’est actuellement pas disponible.
1. [Activez Adobe Target en tant que destination dans Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=fr) ou pour l’approche de partage d’audience [Demandez l’attribution de privilèges d’accès pour le partage d’audiences entre Experience Platform et Adobe Target (audiences partagées)](https://www.adobe.com/go/audiences) pour partager des audiences à partir d’Experience Platform vers Target.

## Documentation connexe

### Documentation

* [Connexion Adobe Target pour Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Partage de segments Experience Platform avec Audience Manager et d’autres solutions Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=fr)
* [Documentation pour le SDK web d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentation sur le service Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=fr)
* [Présentation de la segmentation dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr)
* [Segmentation en streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Présentation du créateur de segments d’Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=fr)
* [Connecteur source d’Audience Manager](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)

### Tutoriels

* [Personnalisation à l’accès suivant avec la plateforme de données clients en temps réel et Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=en)

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
