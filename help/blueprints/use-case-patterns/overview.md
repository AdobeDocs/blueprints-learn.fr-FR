---
title: Modèles de cas d’utilisation
description: Découvrez les modèles de cas d’utilisation pour l’implémentation de Adobe Experience Platform et d’applications afin d’atteindre des objectifs commerciaux clés.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---


# Modèles de cas d’utilisation

Les modèles de cas d’utilisation définissent des approches d’implémentation répétables pour Adobe Experience Platform et les applications. Chaque modèle décrit une fonctionnalité spécifique, la chaîne de fonctions qui la fournit, les applications impliquées et les [objectifs commerciaux clés](/help/blueprints/business-objectives/overview.md) qu’il prend en charge.

Utilisez les tableaux ci-dessous pour déterminer le modèle correspondant à vos besoins en matière d’implémentation, puis suivez le lien vers la référence complète d’implémentation, y compris les options, les phases, les conseils de décision et la documentation d’Experience League.

## Création et activation d’audiences

Les modèles suivants vous aident à créer, évaluer et activer des segments d’audience sur plusieurs canaux et destinations.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Audience Activation vers les destinations](audience-building-activation/audience-activation-to-destinations.md) | Évaluer et publier des segments d’audience vers des destinations externes à des fins de ciblage ou de suppression | [!DNL Real-Time CDP] |
| [ Audience Collaboration avec correspondance de segments ](audience-building-activation/audience-collaboration-segment-match.md) | Partagez et faites correspondre des segments d’audience dans des sandbox ou des organisations à l’aide de la correspondance de segments | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Transfert d’événement](audience-building-activation/event-forwarding.md) | Transférer les données d’événement en temps réel collectées via Edge Network vers des destinations hors Adobe | [!DNL Experience Platform] (Edge Network, transfert d’événement) |
| [Activation d’audience B2B](audience-building-activation/b2b-audience-activation.md) | Activer les audiences B2B basées sur les comptes sur les canaux web, e-mail et publicitaires | [!DNL Real-Time CDP] B2B edition |

## Personnalisation

Les modèles suivants offrent des expériences personnalisées aux visiteurs connus et inconnus sur les surfaces web et d’application.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Personalization Web de visiteur anonyme](personalization/anonymous-visitor-web-personalization.md) | Diffuser du contenu personnalisé basé sur des signaux comportementaux en session pour des visiteurs non identifiés | [!DNL Journey Optimizer] (canal web), [!DNL Real-Time CDP] |
| [Web/App Personalization pour visiteurs connus](personalization/known-visitor-web-app-personalization.md) | Diffuser du contenu, des offres ou des promotions personnalisés à des visiteurs identifiés en fonction du profil en temps réel et de l’appartenance à un segment | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | Utilisez une logique de décision centralisée pour sélectionner la meilleure offre ou le contenu suivant pour un profil sur l’ensemble des canaux | [!DNL Journey Optimizer] (prise de décision), [!DNL Real-Time CDP] |
| [Recommandation comportementale](personalization/behavioral-recommendation.md) | Générer des recommandations d’éléments et de contenu à l’aide de stratégies de sélection et de modèles de classement | [!DNL Journey Optimizer] (prise de décision), [!DNL Real-Time CDP] |

## Gestion et orchestration des campagnes

Les modèles suivants couvrent la diffusion de messages planifiée, déclenchée et à plusieurs étapes sur plusieurs canaux.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Activation des messages sortants par lots](campaign-management-orchestration/batch-outbound-message-activation.md) | Évaluez une audience, puis diffusez un message sortant planifié dans une seule exécution par lots | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Messagerie déclenchée par un événement](campaign-management-orchestration/event-triggered-messaging.md) | Détecter un événement système ou comportemental en temps réel, puis envoyer un message contextuel au profil de déclenchement | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Parcours orchestré en plusieurs étapes](campaign-management-orchestration/multi-step-orchestrated-journey.md) | Guidez un profil à travers un parcours multi-touch de branchement avec des attentes, des conditions et plusieurs actions de message | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Parcours cross-canal avec prise de décision](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | Orchestrer un parcours à plusieurs étapes intégrant une prise de décision en temps réel pour sélectionner un canal, un contenu ou une offre optimal | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Marketing et gestion de Parcours par groupe d’achats](campaign-management-orchestration/buying-group-based-marketing.md) | Développez des parcours au niveau du compte qui qualifient les prospects en groupes d’achat afin d’améliorer l’efficacité du marketing B2B | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Analyse

Les modèles suivants prennent en charge l’analyse cross-canal des comportements et des performances.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Customer Analytics et génération Insight](analysis/customer-analytics-insight-generation.md) | Créer des espaces de travail d’analyse cross-canal, des mesures calculées et des tableaux de bord pour l’analyse du comportement et des performances | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [B2B Analytics](analysis/b2b-analytics.md) | Incluez des informations au niveau du compte B2B dans l’analyse des parcours client cross-canal | [!DNL Customer Journey Analytics] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Expérience de conversation

Les modèles suivants permettent des interactions conversationnelles sécurisées par la marque et optimisées par l’IA sur les propriétés numériques.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Expérience de conversation Brand Concierge](conversational-experience/brand-concierge-conversational-experience.md) | Transformer les propriétés numériques en expériences de conversation optimisées par l’IA et sécurisées par la marque qui guident la découverte des clients | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |
