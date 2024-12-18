---
user-guide-title: Plans directeurs d’expérience digitale
breadcrumb-title: Plans directeurs
user-guide-description: Les plans directeurs sont des implémentations reproductibles qui apportent des réponses à des problèmes commerciaux établis et contiennent des schémas d’architecture, des considérations techniques et des liens vers de la documentation pertinente.
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: 6a13de73d7f61295092faccfc21172f5e188331d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 54%

---


# Plans directeurs d’expérience digitale {#architecture}

+ [Plans directeurs des expériences numériques](/help/blueprints/overview.md)
+ Plans directeurs verticaux de l’industrie{#vertical-blueprints}
   + [Présentation](/help/blueprints/vertical-blueprints/overview.md)
   + [Habillement](/help/blueprints/vertical-blueprints/apparel.md)
   + [Vente au détail](/help/blueprints/vertical-blueprints/retail.md)
   + [Télécommunications](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [Voyage et hospitalité](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ Aperçu de l’architecture {#architecture-overview}
   + [Adobe Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform et applications](/help/blueprints/experience-platform/platform-applications.md)
   + [Flux de données Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
   + Déploiement {#deployment}
      + [SDK Web Experience Platform &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [SDK d’application](/help/blueprints/experience-platform/deployment/appsdk.md)
      + [Garde-fous](/help/blueprints/experience-platform/deployment/guardrails.md)
+ Activation des audiences et des profils {#audience-activation}
   + [Présentation](/help/blueprints/audience-activation/overview.md)
   + [Activation d’audience anonyme ](/help/blueprints/audience-activation/anonymous.md)
   + Activation des clients connus (RTCDP) {#known-customer-audience-activation}
      + [Présentation](/help/blueprints/audience-activation/known.md)
      + [Activation des canaux sociaux et publicitaires](/help/blueprints/audience-activation/advertising-activation.md)
      + [Activation vers des destinations de diffusion en continu de fichiers et d’entreprise](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Centre d’activités client](/help/blueprints/audience-activation/customer-activity.md)
      + [Correspondance de segment](/help/blueprints/audience-activation/segment-match.md)
   + [Activation avec des applications Experience Cloud](/help/blueprints/audience-activation/platform-and-applications.md)
   + Personnalisation web et mobile {#web-personalization}
      + [Présentation](/help/blueprints/audience-activation/web-personalization/overview.md)
      + [Personnalisation comportementale - Target](/help/blueprints//audience-activation/web-personalization/behavioral.md)
      + [Personnalisation connue des clients - Target et RTCDP](/help/blueprints/audience-activation/web-personalization/known-personalization.md)
      + [Gestion des décisions](/help/blueprints/audience-activation/web-personalization/decision-management-edge.md)
+ Activation et marketing B2B {#b2b-activation}
   + [Présentation](/help/blueprints/b2b/overview.md)
   + [Activation B2B](/help/blueprints/b2b/b2bactivation.md)
   + [Activation du compte B2B](/help/blueprints/b2b/b2b-account-activation.md)
   + [Gestion des parcours et marketing basé sur les groupes d’achat](/help/blueprints/b2b/b2b-buying-group-journeys.md)
   + Plan directeur d’intégration de Marketo Engage et Workfront{#marketo-engage-and-workfront-integration-blueprint}
      + [Présentation](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [Inprise et création](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [Réviser et approuver](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [Histoires de succès client](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ Contenu et Commerce{#content-commerce}
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
      + [Messages tiers](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard {#campaign-standard}
      + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr){target="_blank"}
      + [Real-Time CDP avec Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=fr){target="_blank"}
   + Campaign v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP avec Adobe [!DNL Campaign] v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer avec Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campaign v7 {#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP avec Adobe [!DNL Campaign] v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer avec Adobe [!DNL Campaign] v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ Collecte de données, accès et export {#data-ingestion}
   + [Présentation](/help/blueprints/data-ingestion/overview.md)
   + [Collecte de données pour le transfert d’événement multi-sandbox](/help/blueprints/data-ingestion/multi-sandbox-event-forwarding.md)
   + [Préparation et ingestion des données](/help/blueprints/data-ingestion/ingestion.md)
   + [Accès aux données et exportation](/help/blueprints/data-ingestion/egress.md)
   + [Transfert d’événement](/help/blueprints/data-ingestion/server-side-collection.md)
+ Analyse des données, data intelligence et IA / ML {#data-exploration}
   + [Présentation](/help/blueprints/data-insights/overview.md)
   + [Analyse et intelligence des données](/help/blueprints/data-insights/analysis.md)
   + [Science des données personnalisées pour l’enrichissement des profils](/help/blueprints/data-insights/data-science.md)
