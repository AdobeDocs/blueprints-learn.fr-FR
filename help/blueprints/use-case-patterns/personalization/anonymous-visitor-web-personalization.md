---
title: Personalization Web de visiteur anonyme
description: Découvrez comment diffuser du contenu web personnalisé aux visiteurs et visiteuses non identifiés en fonction de signaux comportementaux au cours de la session.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: e2446801-ffce-40e6-bfe9-abec623c9201
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 4%

---

# Personnalisation web des visiteurs anonymes

Ce guide décrit le modèle de cas d’utilisation de la personnalisation web pour les visiteurs anonymes, qui utilise [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) et [!DNL Adobe Experience Platform] (AEP) pour fournir du contenu web personnalisé aux visiteurs anonymes (non identifiés) en fonction de signaux comportementaux au cours de la session. Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de comprendre le rôle de ce modèle, les objectifs commerciaux qu’il prend en charge, les cas d’utilisation tactiques qu’il permet et les applications Adobe impliquées.

Le modèle fonctionne avec des données limitées : uniquement ce qui peut être observé dans la session en cours et tout profil Edge anonyme accumulé à partir de visites précédentes avec le même appareil ou cookie. Cela le rend adapté à la personnalisation en haut de funnel lorsque le visiteur ne dispose d’aucun compte ou ne s’est pas authentifié.

## Modèle de cas d’utilisation

La section suivante décrit le modèle de base et le plan d’exécution pour ce cas d’utilisation.

**Personalization Web de visiteur anonyme**

Diffusez du contenu personnalisé basé sur des signaux comportementaux en session pour les visiteurs et visiteuses non identifiés via le canal web AJO.

**Plan d’exécution : Configuration de la surface web** > Évaluation des règles comportementales > Diffusion de contenu > Tracking des impressions > Rapports

## Présentation du cas d’utilisation

Le Personalization Web de visiteur anonyme répond au besoin de l’entreprise de fournir un contenu pertinent et personnalisé aux visiteurs et visiteuses du site Web qui n’ont pas encore été identifiés (c’est-à-dire qui ne se sont pas connectés, qui n’ont aucune identité connue et qui ne peuvent pas être résolus en un profil client unifié). Malgré ces limitations, une personnalisation significative est possible à l’aide de signaux comportementaux en session : pages vues, temps passé sur le site, profondeur de défilement, source de référence, emplacement géographique, type d’appareil et paramètres de campagne UTM.

Ce modèle utilise les surfaces de canal web d’AJO et les expériences basées sur du code pour modifier le contenu de la page en temps réel. La segmentation d’Edge est la méthode d’évaluation principale, car les décisions doivent être prises avec une latence inférieure à la seconde lorsque le visiteur navigue sur le site. Le [!DNL Web SDK] collecte des signaux comportementaux et les envoie au [!DNL AEP Edge Network], où les règles d’audience évaluées par Edge déterminent la variante de contenu à diffuser.

Contrairement à la personnalisation web/de l’application d’un visiteur connu, qui utilise le profil unifié complet et l’appartenance à un segment, ce modèle est limité aux données observables dans la session en cours et à tout profil Edge anonyme associé à l’ECID du visiteur ([!DNL Experience Cloud ID]). Cette distinction est essentielle pour la planification de l’implémentation : les signaux comportementaux disponibles pour la personnalisation sont limités à ce que le [!DNL Web SDK] capture et à ce qui persiste dans le magasin de profils Edge entre les sessions via l’ECID basé sur les cookies.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**[Augmenter l’engagement du site web](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

Améliorez le temps passé sur le site, les pages par session et l’interaction avec le contenu web par le biais d’expériences pertinentes adaptées aux signaux anonymes des visiteurs.

| KPI |
| --- |
| Temps passé sur la page (web) |
| Engagement |
| Taux de conversion |

**[Offrir des expériences personnalisées aux clients](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Adapter le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus, même pour les visiteurs qui ne se sont pas encore identifiés.

| KPI |
| --- |
| Engagement |
| Taux de conversion |
| Satisfaction du client (CSAT) |

**[Augmentation des taux de conversion](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Améliorez le pourcentage de visiteurs et de prospects qui effectuent les actions souhaitées telles que les achats, les inscriptions ou les envois de formulaire en présentant le contenu le plus pertinent en fonction du contexte comportemental.

| KPI |
| --- |
| Taux de conversion |
| Conversion du lead |
| Coût par lead |

## Exemples de cas d’utilisation tactiques

Les exemples suivants illustrent des scénarios spécifiques où ce modèle peut être appliqué.

- **Test A/B des titres des pages de destination basé sur la source de référence** — Testez différents titres pour les visiteurs provenant de Google, des médias sociaux ou du trafic direct afin d’optimiser l’engagement par le canal d’acquisition
- **Recommandations d’affinité catégorielle basées sur le comportement de navigation** — Affichez les recommandations de produits ou de contenus basées sur les pages consultées au cours de la session en cours pour augmenter les taux de découverte et de conversion
- **Offre de sortie-intention pour les visiteurs sur le point de partir** — Présentez une offre promotionnelle ou un formulaire de capture de piste lorsque des signaux comportementaux indiquent que le visiteur est sur le point d’abandonner le site
- **Bannière promotionnelle géo-ciblée** — Affichez des promotions spécifiques à un emplacement, du contenu de localisateur de magasin ou des offres régionales en fonction de l’emplacement géographique du visiteur
- **Optimisation de la disposition du contenu spécifique à l’appareil** — Adaptez la disposition du contenu, la taille des images et l’emplacement du CTA selon que le visiteur se trouve sur un ordinateur, une tablette ou un appareil mobile
- **Messages de bienvenue pour les nouveaux visiteurs et les visiteurs récurrents** — Différenciez l’expérience des nouveaux visiteurs de celle des visiteurs anonymes récurrents à l’aide de la persistance ECID entre les sessions
- **Recommandations de contenu basées sur les pages consultées de la session en cours** — Faites apparaître de manière dynamique les articles, produits ou ressources associés en fonction des pages que le visiteur a déjà consultées
- **Bannière principale dynamique basée sur les paramètres de campagne UTM** — Personnalisez la bannière principale pour qu’elle corresponde au message ou à la contenu créatif de la campagne de référence

## Indicateurs clés de performance

Utilisez les indicateurs de performance clés suivants pour mesurer l’efficacité de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’impression Personalization | Pourcentage de pages vues éligibles pour lesquelles du contenu personnalisé a été diffusé | rapport de campagne AJO : impressions/nombre total de pages vues |
| Taux de clic publicitaire (CTR) | Pourcentage d’impressions de contenu personnalisé qui génèrent un clic | Rapport de campagne AJO : clics/impressions |
| Effet élévateur d’engagement | Augmentation du temps passé sur la page, des pages par session ou de la profondeur de défilement pour le contenu personnalisé par rapport au contenu par défaut | comparaison de l’espace de travail CJA : cohorte personnalisée et contrôle |
| Taux de conversion | Pourcentage de visiteurs et visiteuses exposés à du contenu personnalisé qui effectuent l’action souhaitée | analyse de CJA funnel : impression > interaction > conversion |
| Réduction du taux de rebond | Diminution du nombre de sessions d’une seule page pour les visiteurs qui reçoivent du contenu personnalisé | analyse des sessions CJA : delta de taux de rebond pour les sessions personnalisées par rapport aux sessions par défaut |
| Taux de succès de l’expérience | Pourcentage de tests A/B qui génèrent un résultat gagnant statistiquement significatif | Rapport d’expérience AJO : les expériences atteignent le seuil de confiance |

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Journey Optimizer] (AJO)** : configuration de la surface de canal web, création de contenu (expériences web et basées sur du code), exécution de campagnes, expérimentation de contenu (tests A/B), prise de décision (sélection de contenu dynamique) et création de rapports
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** : segmentation Edge pour l’évaluation d’audiences en temps réel en fonction de signaux comportementaux en session ; gestion anonyme des profils Edge
- **[!DNL Adobe Experience Platform] (AEP)** : [!DNL Web SDK] pour la collecte de signaux comportementaux, [!DNL Edge Network] pour le routage des données en temps réel et la diffusion de la personnalisation, configuration des trains de données

## Architecture

L’architecture de référence suivante illustre la manière dont les signaux de visiteur anonyme sont collectés en périphérie, évalués par rapport aux règles d’audience et utilisés pour diffuser du contenu personnalisé.

![Architecture de référence pour l’activation et la personnalisation anonymes des audiences](/help/blueprints/audience-activation/assets/anonymous_activation.png)

## Documentation connexe

Les ressources Experience League ci-après fournissent des détails supplémentaires sur les fonctionnalités utilisées dans ce modèle de cas d’utilisation.

**Expériences de canal web et basées sur du code**

- [Prise en main du canal web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Créer des expériences web](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Canal d’expérience basé sur le code](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Configuration de l’expérience basée sur le code](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**Audiences et segmentation**

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization et contenu**

- [Ajouter une personnalisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Syntaxe de Personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Contenu dynamique](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Utiliser des modèles de contenu d’e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Utilisation des fragments de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**Expérimentation de contenu**

- [Prise en main de l’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Créer une expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport d’expérience de contenu](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Calculs statistiques](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**Gestion des décisions**

- [Présentation de la gestion des décisions](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Créer des emplacements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Créer des règles de décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Création d’offres personnalisées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Créer des offres de secours](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Créer des collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Créer des décisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Stratégies de classement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Diffuser des offres dans les messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**Campagnes**

- [Commencer avec les campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Créer une campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]et collecte de données**

- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation des balises](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**Identité et profil**

- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**modélisation des données**

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Rapports et analyses**

- [Rapport dynamique de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Rapport global de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Utilisation de Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**Gouvernance et confidentialité des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**Mécanismes de sécurisation**

- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
