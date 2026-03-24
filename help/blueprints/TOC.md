---
user-guide-title: Objectifs commerciaux, cas d’utilisation, schémas d’architecture et plans directeurs de Customer Experience Orchestration
breadcrumb-title: Cas d’utilisation et plans directeurs
user-guide-description: explorez les principaux objectifs commerciaux, les modèles de cas d’utilisation et les cas d’utilisation du secteur pour Adobe Experience Platform et les applications. Les schémas et les plans directeurs d’architecture visuelle fournissent des références techniques pour l’intégration des systèmes, les flux de données et la conception de solutions, reliant ainsi la valeur commerciale à la mise en œuvre.
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
source-git-commit: abed39b6b6f63f2eef6cb36b400319910f8cf472
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 25%

---


# Plans directeurs d’orchestration de l’expérience client {#architecture}

+ [Plans directeurs d’orchestration de l’expérience client](/help/blueprints/overview.md)
+ Objectifs commerciaux clés pour AEP et les applications{#business-objectives}
   + [Présentation](/help/blueprints/business-objectives/overview.md)
   + Acquisition et croissance{#acquisition-growth}
      + [Acquérir de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)
      + [Augmenter la génération de leads](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)
      + [Augmenter l’engagement du site web](/help/blueprints/business-objectives/acquisition-growth/increase-website-engagement.md)
   + Chiffre d’affaires et monétisation{#revenue-monetization}
      + [Augmenter les taux de conversion](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)
      + [Augmenter le chiffre d’affaires et les ventes](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)
      + [Stimuler les ventes croisées et les ventes incitatives](/help/blueprints/business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)
      + [Augmenter la fidélité du client et la valeur de durée de vie](/help/blueprints/business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)
   + Coût et efficacité{#cost-efficiency}
      + [Réduire les coûts d’acquisition client](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)
      + [Optimiser les dépenses marketing et le retour sur investissement](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)
      + [Améliorer la qualité et la gouvernance des données](/help/blueprints/business-objectives/cost-efficiency/improve-data-quality-governance.md)
      + [Consolidation et modernisation de la technologie marketing](/help/blueprints/business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)
   + Expérience client{#customer-experience-objectives}
      + [Offrir Des Expériences Client Personnalisées](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)
      + [Amélioration de la fidélisation client](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)
      + [Améliorer l’intégration des clients](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)
      + [Récupérer les paniers et Parcours abandonnés](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)
   + Analytics et Insights{#analytics-insights}
      + [Amélioration des analyses et des rapports](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)
      + [Activer la prise de décision pilotée par les données](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)
      + [Amélioration de l’attribution marketing](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)
   + Qualification Et Ventes (B2B){#qualification-sales-b2b}
      + [Améliorer la qualification et la conversion des leads](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)
      + [Améliorer l’engagement client](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)
+ Modèles de cas d’utilisation{#use-case-patterns}
   + [Présentation](/help/blueprints/use-case-patterns/overview.md)
   + Création et activation d’audiences{#audience-building-activation}
      + [Audience Activation vers les destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md)
      + [Audience Collaboration avec correspondance de segments](/help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md)
      + [Transfert d’événement](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)
      + [Audience Activation B2B](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md)
   + Personnalisation{#personalization-patterns}
      + [Personalization Web de visiteur anonyme](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
      + [Personalization Web/App Connu Des Visiteurs](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
      + [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
      + [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
   + Gestion et orchestration des campagnes{#campaign-orchestration-patterns}
      + [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
      + [Messagerie déclenchée par événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
      + [Parcours Orchestré À Plusieurs Étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
      + [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
      + [Marketing et gestion de Parcours par groupe d&#39;achats](/help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md)
   + Analyse{#analysis-patterns}
      + [Génération de Customer Analytics et d’Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
      + [Analyses B2B](/help/blueprints/use-case-patterns/analysis/b2b-analytics.md)
   + Expérience de conversation{#conversational-experience-patterns}
      + [Expérience de conversation Brand Concierge](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)
+ Exemples de cas d’utilisation du secteur{#industry-use-cases}
   + [Catalogue de cas d’utilisation](/help/blueprints/industry-use-cases/use-case-catalog.md)
   + [Automobile](/help/blueprints/industry-use-cases/automotive/automotive-overview.md)
   + [B2B](/help/blueprints/industry-use-cases/b2b/b2b-overview.md)
   + [Services Financiers](/help/blueprints/industry-use-cases/financial-services/financial-services-overview.md)
   + [services de santé](/help/blueprints/industry-use-cases/healthcare/healthcare-overview.md)
   + [Assurance](/help/blueprints/industry-use-cases/insurance/insurance-overview.md)
   + [Médias et divertissement](/help/blueprints/industry-use-cases/media-entertainment/media-entertainment-overview.md)
   + [Grande distribution](/help/blueprints/industry-use-cases/retail/retail-overview.md)
   + [Télécommunications](/help/blueprints/industry-use-cases/telecommunications/telecommunications-overview.md)
   + [Technologie](/help/blueprints/industry-use-cases/technology/technology-overview.md)
   + [Voyage et hébergement](/help/blueprints/industry-use-cases/travel-hospitality/travel-hospitality-overview.md)
+ Schémas et plans directeurs d’architecture{#architecture-diagrams}
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
         + [Science des données personnalisées pour l’enrichissement des profils](/help/blueprints/audience-activation/data-science.md)
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
   + Customer Journey Analytics{#customer-journey-analytics}
      + [Présentation](/help/blueprints/customer-journey-analytics/overview.md)
      + [Customer Journey Analytics B2B](/help/blueprints/customer-journey-analytics/b2b-cja.md)
      + [Partage d’audiences CJA vers RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
      + [CJA et Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
      + [Analyse des données et intelligence](/help/blueprints/customer-journey-analytics/analysis.md)
   + Parcours client{#customer-journeys}
      + [Présentation](/help/blueprints/customer-journeys/overview.md)
      + Journey Optimizer{#journey-optimizer}
         + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
         + [AJO parcours](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
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
