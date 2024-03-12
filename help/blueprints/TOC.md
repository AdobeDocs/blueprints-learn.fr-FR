---
user-guide-title: Plans directeurs d’expérience digitale
breadcrumb-title: Plans directeurs
user-guide-description: Les plans directeurs sont des implémentations reproductibles qui apportent des réponses à des problèmes commerciaux établis et contiennent des schémas d’architecture, des considérations techniques et des liens vers de la documentation pertinente.
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: 3cb8d1566e0ce1356c864e360f660a739d0a472a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 90%

---


# Plans directeurs d’expérience digitale {#architecture}

+ [Plans directeurs des expériences numériques](/help/blueprints/overview.md)
+ Plans directeurs des secteurs verticaux {#vertical-blueprints}
   + [Présentation](/help/blueprints/vertical-blueprints/overview.md)
   + [Habillement](/help/blueprints/vertical-blueprints/apparel.md)
   + [Vente au détail](/help/blueprints/vertical-blueprints/retail.md)
   + [Télécommunications](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [Tourisme et hôtellerie](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ Aperçu de l’architecture {#architecture-overview}
   + [Adobe Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform et autres applications](/help/blueprints/experience-platform/platform-applications.md)
   + [Flux de données Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
   + Déploiement {#deployment}
      + [SDK web Experience Platform et Edge Network](/help/blueprints/experience-platform/deployment/websdk.md)
      + [SDK d’application](/help/blueprints/experience-platform/deployment/appsdk.md)
      + [Garde-fous](/help/blueprints/experience-platform/deployment/guardrails.md)
+ Activation des audiences et des profils {#audience-activation}
   + [Présentation](/help/blueprints/audience-activation/overview.md)
   + [Audience Activation anonyme (AAM)](/help/blueprints/audience-activation/anonymous.md)
   + Activation des clients connus (RTCDP) {#known-customer-audience-activation}
      + [Présentation](/help/blueprints/audience-activation/known.md)
      + [Activation des canaux Social et Advertising](/help/blueprints/audience-activation/advertising-activation.md)
      + [Activation vers des destinations de diffusion en continu de fichiers et d’entreprise](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Centre d’activité client](/help/blueprints/audience-activation/customer-activity.md)
      + [Correspondance de segment](/help/blueprints/audience-activation/segment-match.md)
   + [Activation avec les applications Experience Cloud](/help/blueprints/audience-activation/platform-and-applications.md)
   + Personnalisation web et mobile {#web-personalization}
      + [Présentation](/help/blueprints/audience-activation/web-personalization/overview.md)
      + [Personnalisation comportementale - Target](/help/blueprints//audience-activation/web-personalization/behavioral.md)
      + [Personnalisation des clients connus - Target et RTCDP](/help/blueprints/audience-activation/web-personalization/known-personalization.md)
      + [Gestion des décisions](/help/blueprints/audience-activation/web-personalization/decision-management-edge.md)
+ Activation et marketing B2B {#b2b-activation}
   + [Présentation](/help/blueprints/b2b/overview.md)
   + [Activation B2B](/help/blueprints/b2b/b2bactivation.md)
   + Plan directeur d’intégration de Marketo Engage et Workfront{#marketo-engage-and-workfront-integration-blueprint}
      + [Présentation](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [Ingestion et création](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [Lecture et approbation](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [Histoires de succès client](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ Contenu et commerce{#content-commerce}
   + [Adobe Commerce et RTCDP](/help/blueprints/content-commerce/commerce/commerce-rtcdp.md)
+ Customer Journey Analytics {#customer-journey-analytics}
   + [Présentation](/help/blueprints/customer-journey-analytics/overview.md)
   + [Partage d’audiences CJA vers RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA et Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ Parcours clients {#customer-journeys}
   + [Présentation](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer {#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + Gestion des décisions {#decision-management}
         + [Présentation](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [Gestion des décisions sur Edge](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [Gestion des décisions sur le hub](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer avec Adobe Campaign ](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [Messagerie tierce](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard {#campaign-standard}
      + [Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr){target="_blank"}
      + [Real-Time CDP avec Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=fr){target="_blank"}
   + Campaign v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP avec Adobe Campaign v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer avec Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campaign v7 {#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP avec Adobe Campaign v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer avec Adobe Campaign v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ Collecte de données, accès et export {#data-ingestion}
   + [Présentation](/help/blueprints/data-ingestion/overview.md)
   + [Collecte de données pour le transfert d’événement multi-sandbox](/help/blueprints/data-ingestion/multi-sandbox-event-forwarding.md)
   + [Préparation et ingestion des données](/help/blueprints/data-ingestion/ingestion.md)
   + [Accès aux données et export](/help/blueprints/data-ingestion/egress.md)
   + [Transfert d’événement](/help/blueprints/data-ingestion/server-side-collection.md)
+ Analyse des données, data intelligence et IA / ML {#data-exploration}
   + [Présentation](/help/blueprints/data-insights/overview.md)
   + [Analyse des données et data intelligence](/help/blueprints/data-insights/analysis.md)
   + [Data science personnalisée pour l’enrichissement de profil](/help/blueprints/data-insights/data-science.md)
