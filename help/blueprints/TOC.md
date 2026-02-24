---
user-guide-title: Plans directeurs d’orchestration de l’expérience client
breadcrumb-title: plans directeurs
user-guide-description: Les plans directeurs sont des implémentations reproductibles qui apportent des réponses à des problèmes commerciaux établis et contiennent des schémas d’architecture, des considérations techniques et des liens vers de la documentation pertinente.
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
source-git-commit: fb814fe6f5e4e774a96cbe75fea2499d849716b4
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 30%

---


# Plans directeurs d’orchestration de l’expérience client {#architecture}

+ [Plans directeurs d’orchestration de l’expérience client](/help/blueprints/overview.md)
+ Aperçu de l’architecture{#architecture-overview}
   + [Adobe Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform et applications](/help/blueprints/experience-platform/platform-applications.md)
   + [Flux de données Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
   + [Mécanismes de sécurisation d’Experience Platform](/help/blueprints/experience-platform/guardrails.md)
   + Déploiement{#deployment}
      + [Experience Platform Web SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [SDK d’application](/help/blueprints/experience-platform/deployment/appsdk.md)
+ Activation d’audience et de profil{#audience-activation}
   + [Basé sur l’appareil : ciblage d’audience anonyme avec Audience Manager](/help/blueprints/audience-activation/audience-manager.md)
   + Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}
      + [Activation de l’audience vers des destinations sociales et publicitaires](/help/blueprints/audience-activation/advertising-activation.md)
      + [Activation des audiences et des profils vers le plan directeur des destinations d’entreprise](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Accès au profil en temps réel pour les scénarios d’assistance et de vente](/help/blueprints/audience-activation/customer-activity.md)
      + [Accès aux profils Edge en temps réel pour la personnalisation web et mobile](/help/blueprints/audience-activation/real-time-lookup.md)
      + [Collaboration avec l’audience à l’aide de la correspondance de segments](/help/blueprints/audience-activation/segment-match.md)
      + [Personnalisation connue des clients avec Target](/help/blueprints/audience-activation/rtcdp-target.md)
+ Activation et marketing B2B{#b2b-activation}
   + [Présentation](/help/blueprints/b2b/overview.md)
   + [Activation B2B](/help/blueprints/b2b/b2bactivation.md)
   + [Activation du compte B2B](/help/blueprints/b2b/b2b-account-activation.md)
   + [Marketing de groupe et gestion de parcours](/help/blueprints/b2b/b2b-buying-group-journeys.md)
   + [Parcours B2B utilisant des données Marketo](/help/blueprints/b2b/b2b-journeys-with-marketo.md)
   + [Contrôleur de médias payants B2B](/help/blueprints/b2b/ajo-b2b-paid-media-controller.md)
   + Plan directeur d’intégration de Marketo Engage et Workfront{#marketo-engage-and-workfront-integration-blueprint}
      + [Présentation](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [Réception et création](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [Vérifier et approuver](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [Histoires de succès client](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ Contenu et commerce{#content-commerce}
   + [Adobe Commerce et Real-Time CDP](/help/blueprints/content-commerce/commerce/commerce-rtcdp.md)
+ Customer Journey Analytics{#customer-journey-analytics}
   + [Présentation](/help/blueprints/customer-journey-analytics/overview.md)
   + [Partage d’audiences CJA vers RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA et Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ Parcours client{#customer-journeys}
   + [Présentation](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer{#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
      + [Parcours AJO](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
      + [Campagnes AJO](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md)
      + [Messagerie tierce](/help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md)
   + Gestion des décisions{#decision-management}
      + [Présentation](/help/blueprints/customer-journeys/decision-management/decision-management-overview.md)
      + [Gestion des décisions sur Edge](/help/blueprints/customer-journeys/decision-management/decision-management-edge.md)
      + [Gestion des décisions sur le hub](/help/blueprints/customer-journeys/decision-management/decision-management-hub.md)
   + Campaign v8{#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md)
      + [Real-Time CDP avec Adobe [!DNL Campaign] v8](/help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer avec Adobe Campaign v8](/help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md)
   + Plans directeurs obsolètes{#deprecated-blueprints}
      + Campaign Standard{#campaign-standard}
         + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/en/docs/campaign-standard){target="_blank"}
         + [Real-Time CDP avec Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/en/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/get-started-sources-destinations)
      + Campaign v7{#campaign-v7}
         + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md)
+ Analyse des données, data intelligence et IA / ML{#data-exploration}
   + [Analyse des données et intelligence](/help/blueprints/data-insights/analysis.md)
   + [Science des données personnalisées pour l’enrichissement des profils](/help/blueprints/data-insights/data-science.md)
