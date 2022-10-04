---
user-guide-title: Plans directeurs d’expérience digitale
breadcrumb-title: Plans directeurs
user-guide-description: Les plans directeurs sont des implémentations reproductibles qui apportent des réponses à des problèmes commerciaux établis et contiennent des schémas d’architecture, des considérations techniques et des liens vers de la documentation pertinente.
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: f8116387105cf1fe0adfc148562529d62ca90cfc
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 92%

---


# Plans directeurs d’expérience digitale {#architecture}

+ [Présentation](/help/blueprints/overview.md)
+ Plans directeurs verticaux du secteur{#vertical-blueprints}
   + [Présentation](/help/blueprints/vertical-blueprints/overview.md)
   + [Habillement](/help/blueprints/vertical-blueprints/apparel.md)
   + [Vente au détail](/help/blueprints/vertical-blueprints/retail.md)
   + [Télécommunications](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [Tourisme et hôtellerie](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ Aperçu de l’architecture {#architecture-overview}
   + [Adobe Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform et autres applications](/help/blueprints/experience-platform/platform-applications.md)
   + [Flux de données Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
   + Modèles de déploiement{#deployment}
      + [SDK web Experience Platform et Edge Network](/help/blueprints/data-ingestion/websdk.md)
      + [SDK d’application](/help/blueprints/data-ingestion/appsdk.md)
+ Activation des audiences et des profils {#audience-activation}
   + [Présentation](/help/blueprints/audience-activation/overview.md)
   + [Activation d’audience anonyme  (AAM)](/help/blueprints/audience-activation/anonymous.md)
   + Activation des clients connus (RTCDP) {#known-customer-audience-activation}
      + [Présentation](/help/blueprints/audience-activation/known.md)
      + Activation des canaux Social et Advertising {#audience-activation}
         + [Activation des audiences personnalisées Facebook](/help/blueprints/audience-activation/destinations/facebook.md)
         + [Activation du ciblage par liste de clients Google](/help/blueprints/audience-activation/destinations/gcm.md)
      + [Activation vers des destinations de diffusion en continu de fichiers et d’entreprise](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Centre d’activité client](/help/blueprints/audience-activation/customer-activity.md)
      + [Correspondance de segment](/help/blueprints/audience-activation/segment-match.md)
   + [Activation avec les applications Experience Cloud](/help/blueprints/audience-activation/platform-and-applications.md)
+ Activation et marketing B2B {#b2b-activation}
   + [Présentation](/help/blueprints/b2b/overview.md)
   + [Activation B2B](/help/blueprints/b2b/b2bactivation.md)
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
      + [Journey Optimizer avec Adobe Campaign](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [Messagerie tierce](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP avec Adobe Campaign v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
   + Campaign v7 {#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP avec Adobe Campaign v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
+ Ingestion des données et exportation de données{#data-ingestion}
   + [Présentation](/help/blueprints/data-ingestion/overview.md)
   + [Préparation et ingestion des données](/help/blueprints/data-ingestion/ingestion.md)
   + [Transfert d’événement](/help/blueprints/data-ingestion/server-side-collection.md)
   + [Collecte de données sur plusieurs sandbox](/help/blueprints/data-ingestion/multi-sandbox-data-collection.md)
+ Analyse des données, data intelligence et IA / ML {#data-exploration}
   + [Présentation](/help/blueprints/data-insights/overview.md)
   + [Analyse des données et data intelligence](/help/blueprints/data-insights/analysis.md)
   + [Data science personnalisée pour l’enrichissement de profil](/help/blueprints/data-insights/data-science.md)
+ Personnalisation web et mobile {#web-personalization}
   + [Présentation](/help/blueprints/web-personalization/overview.md)
   + [Personnalisation comportementale  - Target](/help/blueprints/web-personalization/behavioral.md)
   + [Personnalisation des clients connus - Target et RTCDP](/help/blueprints/web-personalization/known-personalization.md)
   + [Gestion des décisions](/help/blueprints/web-personalization/decision-management-edge.md)