---
user-guide-title: Objectifs commerciaux, cas d’utilisation, schémas d’architecture et plans directeurs de Customer Experience Orchestration
breadcrumb-title: Cas d’utilisation et plans directeurs
user-guide-description: explorez les principaux objectifs commerciaux, les modèles de cas d’utilisation et les cas d’utilisation du secteur pour Adobe Experience Platform et les applications. Les schémas et les plans directeurs d’architecture visuelle fournissent des références techniques pour l’intégration des systèmes, les flux de données et la conception de solutions, reliant ainsi la valeur commerciale à la mise en œuvre.
product: Adobe Experience Platform
mini-toc-levels: 3
role: Developer, User
nudge: orange
source-git-commit: 7f0b624616480cf563142c08eb0598d1dd55d551
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 15%
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
    + [Recherche de profil en temps réel pour l’assistance et les ventes](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md)
    + [Science des données personnalisées pour l’enrichissement des profils](/help/blueprints/use-case-patterns/audience-building-activation/data-science-profile-enrichment.md)
  + Personnalisation{#personalization-patterns}
    + [Personalization Web de visiteur anonyme](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
    + [Personalization Web/App Connu Des Visiteurs](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
    + [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
    + [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
    + [Accès au profil Edge pour Web/Mobile Personalization](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md)
    + [Partage d’audiences avec Adobe Target](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md)
  + Gestion et orchestration des campagnes{#campaign-orchestration-patterns}
    + [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
    + [Messagerie déclenchée par événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
    + [Parcours Orchestré À Plusieurs Étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
    + [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
    + [Orchestration par lots et messagerie transactionnelle de Campaign v8](/help/blueprints/use-case-patterns/campaign-management-orchestration/campaign-v8-orchestration.md)
    + [Intégration de la messagerie tierce à Journey Optimizer](/help/blueprints/use-case-patterns/campaign-management-orchestration/third-party-messaging.md)
  + Analyse{#analysis-patterns}
    + [Génération de Customer Analytics et d’Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
  + Activation et marketing B2B{#b2b-patterns}
    + [Audience Activation B2B](/help/blueprints/use-case-patterns/b2b/account-audience-activation.md)
    + [Marketing et gestion de Parcours par groupe d&#39;achats](/help/blueprints/use-case-patterns/b2b/buying-group-marketing.md)
    + [Analyses B2B](/help/blueprints/use-case-patterns/b2b/account-analytics.md)
    + [Parcours B2B à l’aide des données Marketo](/help/blueprints/use-case-patterns/b2b/marketo-data-journeys.md)
    + [Contrôleur de médias payants B2B AJO](/help/blueprints/use-case-patterns/b2b/paid-media-orchestration.md)
    + [Marketo et Workfront Intake et Create](/help/blueprints/use-case-patterns/b2b/campaign-intake-and-creation.md)
    + [Marketo et Workfront - Vérifier et approuver](/help/blueprints/use-case-patterns/b2b/campaign-review-and-approval.md)
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
    + [Activation des audiences et des profils B2B](/help/blueprints/b2b/b2b-audience-profile-activation.md)
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

+ Ateliers pratiques{#labs}
  + [Présentation pratique de Labs](/help/blueprints/labs/overview.md)
  + Ateliers pratiques{#workshops}
    + AEP Foundations{#aep-foundations}
      + [Présentation](/help/blueprints/labs/aep-foundations/overview.md)
      + [Configuration](/help/blueprints/labs/aep-foundations/setup.md)
      + Configuration du sandbox{#aep-sandbox}
        + [Configuration de Developer Console](/help/blueprints/labs/aep-foundations/sandbox-setup/developer-console-setup.md)
        + [Instructions de déploiement](/help/blueprints/labs/aep-foundations/sandbox-setup/deployment-instructions.md)
      + Configuration de Postman{#aep-postman}
        + [Installation de Postman](/help/blueprints/labs/aep-foundations/postman-setup/postman-installation.md)
        + [Fichier d’environnement](/help/blueprints/labs/aep-foundations/postman-setup/environment-file.md)
        + [Collection d’API](/help/blueprints/labs/aep-foundations/postman-setup/api-collection.md)
        + [Accès aux sandbox](/help/blueprints/labs/aep-foundations/postman-setup/sandbox-access.md)
        + [Jeton d’accès](/help/blueprints/labs/aep-foundations/postman-setup/access-token.md)
      + Real-Time Customer Profile{#aep-rtcp}
        + [Conférences](/help/blueprints/labs/aep-foundations/real-time-customer-profile/lectures.md)
        + Inspecter le profil{#aep-rtcp-inspect}
          + [Présentation](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/overview.md)
          + [Principes de base de Profile](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-basics.md)
          + [Stratégies de fusion](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/merge-policies.md)
          + [API de profil et d’identité](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-and-identity-apis.md)
      + Méthodologie LID{#aep-lid}
        + [Conditions préalables](/help/blueprints/labs/aep-foundations/lid-methodology/prerequisites.md)
        + [Libellé](/help/blueprints/labs/aep-foundations/lid-methodology/label.md)
        + Identifier{#aep-lid-identify}
          + [Présentation](/help/blueprints/labs/aep-foundations/lid-methodology/identify/overview.md)
          + [Partie 1 - Autres types de tableau](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-1-remaining-table-types.md)
          + [Partie 2 - Champs clés](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-2-key-fields.md)
        + [Dénormaliser](/help/blueprints/labs/aep-foundations/lid-methodology/denormalize.md)
      + Modélisation XDM{#aep-xdm}
        + [Conférences](/help/blueprints/labs/aep-foundations/xdm-modeling/lectures.md)
        + Modélisation de l’interface utilisateur{#aep-xdm-ui}
          + [Présentation](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/overview.md)
          + [Connexion et navigation](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/login-and-browse.md)
          + [Objets standard du modèle](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-standard-objects.md)
          + [Objets personnalisés du modèle](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-custom-objects.md)
          + [Configuration d’pour le profil](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/configure-for-profile.md)
        + Modélisation des API{#aep-xdm-api}
          + [Présentation](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/overview.md)
          + Créer un schéma{#aep-xdm-api-build}
            + [Présentation](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/overview.md)
            + [Obtenir les groupes de champs standard](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-standard-field-groups.md)
            + [Créer des groupes de champs personnalisés](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-custom-field-groups.md)
            + [Get Profile Class](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-profile-class.md)
            + [Créer Un Schéma](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-schema.md)
            + [Afficher le schéma](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/view-schema.md)
            + [Modifier le schéma - Correctif JSON](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/modify-schema-json-patch.md)
          + Marquer les champs d’identité{#aep-xdm-api-identity}
            + [Présentation](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/overview.md)
            + [Créer une identité de Principal](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-primary-identity.md)
            + [Créer D’Autres Identités](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-other-identities.md)
            + [Afficher le schéma](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/view-schema.md)
          + Définir les relations{#aep-xdm-api-relationships}
            + [Présentation](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/overview.md)
            + [Obtenir l’ID du schéma de plan](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/get-plan-schema-id.md)
            + [Créer une relation de schéma](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-schema-relationship.md)
            + [Créer une identité de référence de plan](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-plan-reference-identity.md)
            + [Afficher le schéma](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/view-schema.md)
          + [Récapituler](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/recap.md)
        + Bonus Labs{#aep-xdm-bonus}
          + [Automatisation avec des API](/help/blueprints/labs/aep-foundations/xdm-modeling/bonus-labs/automate-with-apis.md)
      + Ingestion de données{#aep-ingestion}
        + [Conférences](/help/blueprints/labs/aep-foundations/data-ingestion/lectures.md)
        + [Présentation du Lab](/help/blueprints/labs/aep-foundations/data-ingestion/lab-overview.md)
        + [Exemples de fichiers](/help/blueprints/labs/aep-foundations/data-ingestion/sample-files.md)
        + Ingestion par lots{#aep-ingestion-batch}
          + [Présentation](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/overview.md)
          + [Créer un flux de données](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-dataflow.md)
          + Mappage des données{#aep-ingestion-batch-mapping}
            + [Présentation](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/overview.md)
            + [Correction Des Mappages De Passthrough](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/fix-passthrough-mappings.md)
            + [Champs Calculés](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/calculated-fields.md)
            + [Vérifier le jeu de mappages final](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/check-final-mapping-set.md)
          + [Exécuter le flux de données](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/run-dataflow.md)
          + [Erreurs de débogage](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/debugging-errors.md)
          + [Créer un flux de données](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-a-new-dataflow.md)
          + [Correction des erreurs](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/fixing-errors.md)
          + [Vérification et validation](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/verification-and-validation.md)
        + Ingestion de flux{#aep-ingestion-stream}
          + [Présentation](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/overview.md)
          + [Configuration de Source](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/setup-source.md)
          + [Configurer le mappage](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/configure-mapping.md)
          + [Vérifier le jeu de mappages final](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/check-final-mapping-set.md)
          + [Diffusion d’un profil](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/stream-a-profile.md)
          + [Vérifier le profil ingéré](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verify-ingested-profile.md)
          + [Erreurs de surveillance et de débogage](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/monitoring-and-debugging-errors.md)
          + [Vérification et validation](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verification-and-validation.md)
        + Bonus Labs{#aep-ingestion-bonus}
          + [Correction des erreurs MAPPER pour CreateDate](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/fix-mapper-errors-for-createdate.md)
          + [Diffusion d’un événement de commande](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/stream-an-order-event.md)
          + Utilisation de Data Landing Zone{#aep-ingestion-dlz}
            + [Présentation](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/overview.md)
            + [Configuration de Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/setup-source.md)
            + [Créer des mappages](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/create-mappings.md)
            + [Planifier le flux de données](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/schedule-dataflow.md)
            + [Réessayer un flux de données en échec](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/retry-a-failed-dataflow.md)
            + Charger les ordres{#aep-ingestion-dlz-orders}
              + [Présentation](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/overview.md)
              + [Configuration de Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/setup-source.md)
              + [Mappages initiaux](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/initial-mappings.md)
              + [Mappages de copie d’objet](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/object-copy-mappings.md)
              + [Vérifier et planifier le flux de données](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/verify-and-schedule-dataflow.md)
      + Segmentation et activation{#aep-segmentation}
        + [Conférence](/help/blueprints/labs/aep-foundations/segmentation-and-activation/lecture.md)
        + Activation d’Edge{#aep-segmentation-edge}
          + [Présentation](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/overview.md)
          + [Création d’une audience Edge](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/create-edge-audience.md)
          + [Envoi d’un événement Edge](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/send-an-edge-event.md)
          + Configurer le transfert d’événement{#aep-segmentation-edge-ef}
            + [Présentation](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/overview.md)
            + [Créer une propriété](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-property.md)
            + [Créer un flux de données](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-datastream.md)
      + Création d’audience{#aep-audiences}
        + Cas d’utilisation 1 - Acquisition{#aep-uc1}
          + [Présentation](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/overview.md)
          + Configurer les destinations{#aep-uc1-destinations}
            + [Configurer la destination Personalization personnalisée](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-custom-personalization-destination.md)
            + [Configurer La Destination De Diffusion En Continu](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-streaming-destination.md)
          + [Créer l’audience 1](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-1.md)
          + [Créer l’audience 2](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-2.md)
          + [Créer l’audience 3](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-3.md)
          + [Envoi d’un événement Edge](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/send-an-edge-event.md)
          + [Examen de la pensée critique](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/critical-thinking-review.md)
        + Cas d’utilisation 2 - montée en gamme{#aep-uc2}
          + [Présentation](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/overview.md)
          + [Prétravail](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/pre-work.md)
          + [Option 1 - Utilisation des audiences pour l’agrégation](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-1-using-audiences-to-aggregate.md)
          + [Option 2 - Utilisation De Préagrégats](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-2-use-pre-aggregates.md)
          + [Examen de la pensée critique](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/critical-thinking-review.md)
        + Cas d’utilisation 3 - Sensibilisation{#aep-uc3}
          + [Présentation](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/overview.md)
          + [Cas d’utilisation de build 3](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/build-use-case-3.md)
          + [Examen de la pensée critique](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/critical-thinking-review.md)
        + Bonus Labs{#aep-audiences-bonus}
          + [Envoyer l’événement de commande au hub](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-order-event-to-hub.md)
          + [Envoyer l’événement web au hub](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-web-event-to-hub.md)
          + [Surveiller Votre Événement](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/monitor-your-event.md)
    + AJO Foundations{#ajo-foundations}
      + [Présentation](/help/blueprints/labs/ajo-foundations/overview.md)
      + [Configuration](/help/blueprints/labs/ajo-foundations/setup.md)
      + Configuration du sandbox{#ajo-sandbox}
        + [Configuration de Developer Console](/help/blueprints/labs/ajo-foundations/sandbox-setup/developer-console-setup.md)
        + [Instructions de déploiement](/help/blueprints/labs/ajo-foundations/sandbox-setup/deployment-instructions.md)
      + Configuration de Postman{#ajo-postman}
        + [Installation de Postman](/help/blueprints/labs/ajo-foundations/postman-setup/postman-installation.md)
        + [Importer le fichier d’environnement](/help/blueprints/labs/ajo-foundations/postman-setup/import-environment-file.md)
        + [Importer la collection d’API](/help/blueprints/labs/ajo-foundations/postman-setup/import-api-collection.md)
      + Blocs de création d’architecture{#ajo-architecture}
        + [Conférence](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/lecture.md)
        + Mappage des cas d’utilisation à l’architecture{#ajo-architecture-mapping}
          + [Présentation](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/overview.md)
          + [Présentation du Lab](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-introduction.md)
          + [Exercice pratique](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-exercise.md)
          + [Révision du Lab](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-review.md)
      + Magasins de données{#ajo-data-stores}
        + [Conférence sur le profil client en temps réel](/help/blueprints/labs/ajo-foundations/data-stores/real-time-customer-profile-lecture.md)
        + Profil en action{#ajo-profile}
          + [Présentation](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/overview.md)
          + [Connexion et navigation](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/login-and-browse.md)
          + [Créer un flux de données](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/create-datastream.md)
          + [Envoi d’un événement web Edge](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/send-an-edge-web-event.md)
          + [Valider le profil sur le hub](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-hub.md)
          + [Valider le profil sur Edge](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-edge.md)
          + [Valider l’événement sur le lac de données](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-event-on-data-lake.md)
          + [Validation de l’instantané de profil](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-snapshot.md)
          + [Résumé](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/summary.md)
        + [Conférence sur le magasin relationnel](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-lecture.md)
        + Magasin relationnel en action{#ajo-relational}
          + [Présentation](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/overview.md)
          + [Parcourir les schémas](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/browse-schemas.md)
          + [Dimension de Profile Target](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/profile-target-dimension.md)
          + [Lecture d’audience](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/read-an-audience.md)
          + [Résumé](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/summary.md)
        + Configurer les canaux e-mail{#ajo-email}
          + [Présentation](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/overview.md)
          + [Configuration d’pour le profil](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-profile.md)
          + [Configurer pour le relationnel](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-relational.md)
          + [En attente du statut Actif](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/waiting-for-active-status.md)
      + Campagnes orchestrées{#ajo-campaigns}
        + [Conférence sur la diffusion des messages](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-lecture.md)
        + Diffusion de messages en action{#ajo-campaigns-delivery}
          + [Présentation](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/overview.md)
          + [Créer une campagne](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/create-a-campaign.md)
          + [Création d’une audience](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/build-an-audience.md)
          + [Ajouter une activité Branchement](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-fork-activity.md)
          + [Ajouter des activités d’e-mail](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-email-activities.md)
          + [Tester la campagne](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/test-the-campaign.md)
          + [Résumé](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/summary.md)
        + [Conférence sur les blocs de création de workflow](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/workflow-building-blocks-lecture.md)
        + Lancement téléphonique phare{#ajo-campaigns-flagship}
          + [Présentation](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/overview.md)
          + [Configurer le canal SMS](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/configure-sms-channel.md)
          + [Création d’une campagne orchestrée](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/create-an-orchestrated-campaign.md)
          + [Création d’une audience](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/build-an-audience.md)
          + [Branchement du résultat](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/fork-the-result.md)
          + [Enregistrer l’audience](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/save-the-audience.md)
          + [Filtrer les lignes](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/filter-the-lines.md)
          + [Composer le SMS](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/compose-the-sms.md)
          + [Exécution du workflow](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/run-the-workflow.md)
          + [Résumé](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/summary.md)
      + Parcours{#ajo-journeys}
        + [Conférence](/help/blueprints/labs/ajo-foundations/journeys/lecture.md)
        + Excitation après achat{#ajo-journeys-post-purchase}
          + [Présentation](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/overview.md)
          + [Configurer l’événement](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-event.md)
          + [Configurer l’action personnalisée](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-custom-action.md)
          + [Créer un Parcours](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/build-journey.md)
          + [Parcours de test](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/test-journey.md)
          + [Envoyer un événement](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/send-an-event.md)
          + [Valider l’événement ingéré](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-event-ingested.md)
          + [Validation du Parcours](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-journey.md)
          + [Résumé](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/summary.md)
      + Prise de décision.{#ajo-decisioning}
        + [Experience Edge](/help/blueprints/labs/ajo-foundations/decisioning/experience-edge.md)
        + Présentation de la prise de décision{#ajo-decisioning-explained}
          + [Présentation](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/overview.md)
          + [Introduction](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/introduction.md)
          + [XDM d’élément de décision](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-xdm.md)
          + [Création d’élément de décision](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-creation.md)
          + [Collections](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/collections.md)
          + [Formules de classement](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/ranking-formulas.md)
          + [Stratégies de sélection](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/selection-strategies.md)
          + [Politiques de décision](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-policies.md)
          + [Mécanismes de sécurisation, modèles d’IA prenant des décisions sur l’avenir](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/guardrails-ai-models-decisioning-future.md)
        + Navigation abandonnée{#ajo-decisioning-abandoned}
          + [Présentation](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/overview.md)
          + [Créer une règle de décision](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-decision-rule.md)
          + [Créer Des Attributs D’Offre](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-attributes.md)
          + [Créer Des Éléments D’Offre](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-items.md)
          + [Créer Une Collection D’Offres](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-collection.md)
          + [Créer Une Formule De Classement](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-ranking-formula.md)
          + [Créer une stratégie de sélection](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-selection-strategy.md)
          + [Créer Un Canal D’Expérience Basé Sur Le Code](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-code-based-experience-channel.md)
          + [Création du Parcours](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-the-journey.md)
          + [Prise de décision et CBE en action](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/decisioning-and-cbes-in-action.md)
          + [Résumé](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/summary.md)
      + Création de contenu avec l’IA{#ajo-content-ai}
        + [Conférence](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/lecture.md)
        + [Présentation](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/overview.md)
        + [Gestion des marques](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-management.md)
        + [Création de fragments de contenu](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-fragments.md)
        + [Créer un modèle de contenu](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-template.md)
        + [Création de l’e-mail](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/creating-the-email.md)
        + [Assistant IA et Personalization de contenu](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/ai-assistant-and-content-personalization.md)
        + [Personalization et expérimentation de contenu](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/personalization-and-content-experimentation.md)
        + [Simulation de contenu](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/content-simulation.md)
        + [Alignement des marques](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-alignment.md)
        + [Tester l’e-mail](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/test-the-email.md)
        + [Résumé](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/summary.md)
