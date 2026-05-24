---
title: Modèles de cas d’utilisation
description: Découvrez les modèles de cas d’utilisation pour l’implémentation de Adobe Experience Platform et d’applications afin d’atteindre des objectifs commerciaux clés.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
exl-id: 58caa6ad-0d1c-4290-9614-c68c9c9028bb
source-git-commit: e79d9d6490e4f50c4611dd879b53f0e63a90cd65
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Modèles de cas d’utilisation

Les modèles de cas d’utilisation définissent des approches d’implémentation répétables pour Adobe Experience Platform et les applications. Chaque modèle décrit une fonctionnalité spécifique, le plan d’exécution qui la fournit, les applications impliquées et les [objectifs commerciaux clés](/help/blueprints/business-objectives/overview.md) qu’il prend en charge.

Utilisez les tableaux ci-dessous pour déterminer le modèle correspondant à vos besoins en matière d’implémentation, puis suivez le lien vers la référence complète d’implémentation, y compris les options, les phases, les conseils de décision et la documentation d’Experience League.

## Création et activation d’audiences

Les modèles suivants vous aident à créer, évaluer et activer des segments d’audience sur plusieurs canaux et destinations.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Activation des audiences vers les destinations](audience-building-activation/audience-activation-to-destinations.md) | Évaluer et publier des segments d’audience vers des destinations externes à des fins de ciblage ou de suppression | [!DNL Real-Time CDP] |
| [Audience Collaboration](audience-building-activation/audience-collaboration-segment-match.md) | Partagez et faites correspondre des segments d’audience dans des sandbox ou des organisations à l’aide de la correspondance de segments | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Transfert d’événement ](audience-building-activation/event-forwarding.md) | Transférer les données d’événement en temps réel collectées via Edge Network vers des destinations hors Adobe | [!DNL Experience Platform] (Edge Network, transfert d’événement) |
| [Recherche de profil en temps réel pour l’assistance et les ventes](audience-building-activation/real-time-profile-lookup.md) | Recherches de profil client en temps réel fournissant un contexte pour l’assistance assistée par un agent et les scénarios de vente | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Science des données personnalisées pour l’enrichissement des profils](audience-building-activation/data-science-profile-enrichment.md) | Ingérez des informations basées sur la science des données dans Experience Platform pour enrichir le profil client en temps réel | [!DNL Experience Platform] |

## Personnalisation

Les modèles suivants offrent des expériences personnalisées aux visiteurs connus et inconnus sur les surfaces web et d’application.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Personnalisation web anonyme des visiteurs](personalization/anonymous-visitor-web-personalization.md) | Diffuser du contenu personnalisé basé sur des signaux comportementaux en session pour des visiteurs non identifiés | [!DNL Journey Optimizer] (canal web), [!DNL Real-Time CDP] |
| [Personnalisation web/d’application de visiteurs connus](personalization/known-visitor-web-app-personalization.md) | Diffuser du contenu, des offres ou des promotions personnalisés à des visiteurs identifiés en fonction du profil en temps réel et de l’appartenance à un segment | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | Utilisez une logique de décision centralisée pour sélectionner la meilleure offre ou le contenu suivant pour un profil sur l’ensemble des canaux | [!DNL Journey Optimizer] (prise de décision), [!DNL Real-Time CDP] |
| [Recommandation comportementale](personalization/behavioral-recommendation.md) | Générer des recommandations d’éléments et de contenu à l’aide de stratégies de sélection et de modèles de classement | [!DNL Journey Optimizer] (prise de décision), [!DNL Real-Time CDP] |
| [Accès au profil Edge pour Web/Mobile Personalization](personalization/edge-profile-access.md) | Accès aux profils Edge en temps réel pour une personnalisation web et mobile à débit élevé et à faible latence | [!DNL Real-Time CDP], [!DNL Experience Platform] (Edge Network) |
| [Partage d’audiences avec Adobe Target](personalization/audience-sharing-with-target.md) | Partagez des profils et des audiences Real-Time CDP avec Adobe Target pour une personnalisation web et mobile connue des clients | [!DNL Real-Time CDP], [!DNL Target], [!DNL Experience Platform] |

## Gestion et orchestration des campagnes

Les modèles suivants couvrent la diffusion de messages planifiée, déclenchée et à plusieurs étapes sur plusieurs canaux.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Activation des messages sortants par lots](campaign-management-orchestration/batch-outbound-message-activation.md) | Évaluez une audience, puis diffusez un message sortant planifié dans une seule exécution par lots | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Messages déclenchés par un événement](campaign-management-orchestration/event-triggered-messaging.md) | Détecter un événement système ou comportemental en temps réel, puis envoyer un message contextuel au profil de déclenchement | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| parcours orchestré à plusieurs étapes](campaign-management-orchestration/multi-step-orchestrated-journey.md)[ | Guidez un profil à travers un parcours multi-touch de branchement avec des attentes, des conditions et plusieurs actions de message | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| parcours cross-canal avec prise de décision](campaign-management-orchestration/cross-channel-journey-with-decisioning.md)[ | Orchestrer un parcours à plusieurs étapes intégrant une prise de décision en temps réel pour sélectionner un canal, un contenu ou une offre optimal | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Orchestration par lots et messagerie transactionnelle de Campaign v8](campaign-management-orchestration/campaign-v8-orchestration.md) | Exécution de campagnes par lots, orchestration multipoint, gestion des données pilotée par ETL et messagerie transactionnelle sur Campaign v8 | [!DNL Campaign] v8 |
| [Intégration de messagerie tierce à Journey Optimizer](campaign-management-orchestration/third-party-messaging.md) | Intégrer Journey Optimizer à des systèmes de messagerie tiers pour des communications personnalisées via l’API REST | [!DNL Journey Optimizer] |

## Analyse

Les modèles suivants prennent en charge l’analyse cross-canal des comportements et des performances.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Customer Analytics et génération d’insight](analysis/customer-analytics-insight-generation.md) | Créer des espaces de travail d’analyse cross-canal, des mesures calculées et des tableaux de bord pour l’analyse du comportement et des performances | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |

## Activation et marketing B2B

Les modèles suivants traitent des scénarios marketing spécifiques au B2B : audiences basées sur un compte, orchestration des groupes d’achats et analyses B2B.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Activation de l’audience B2B](b2b/account-audience-activation.md) | Activer les audiences B2B basées sur les comptes sur les canaux web, e-mail et publicitaires | [!DNL Real-Time CDP] B2B edition |
| [Marketing et gestion de parcours par groupe d&#39;achat](b2b/buying-group-marketing.md) | Développez des parcours au niveau du compte qui qualifient les prospects en groupes d’achat afin d’améliorer l’efficacité du marketing B2B | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |
| [Analyse B2B](b2b/account-analytics.md) | Incluez des informations au niveau du compte B2B dans l’analyse des parcours client cross-canal | [!DNL Customer Journey Analytics] B2B edition, [!DNL Real-Time CDP] B2B edition |
| Parcours B2B utilisant des données Marketo](b2b/marketo-data-journeys.md)[ | Déployez Journey Optimizer B2B edition avec les données Marketo pour orchestrer les parcours des groupes d’achats et l’engagement des comptes | [!DNL Journey Optimizer] B2B edition, [!DNL Marketo Engage] [!DNL Real-Time CDP] B2B edition |
| [Contrôleur de médias payants B2B ](b2b/paid-media-orchestration.md) | Orchestrez des campagnes média payantes B2B à l’aide de la logique de cascade pour affecter des comptes aux campagnes et activer les destinations | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |
| [Réception et création de Marketo et Workfront](b2b/campaign-intake-and-creation.md) | Automatisez la réception des demandes de campagne marketing et la création de programmes Marketo Engage à l’aide de Workfront Forms et de Fusion | [!DNL Marketo Engage], [!DNL Workfront], [!DNL Workfront Fusion] |
| [Marketo et Workfront : vérifier et approuver](b2b/campaign-review-and-approval.md) | Intégrer des workflows de relecture et d’approbation Workfront à des ressources de messagerie Marketo Engage à l’aide de l’automatisation Fusion | [!DNL Marketo Engage], [!DNL Workfront], [!DNL Workfront Fusion] |

## Expérience de conversation

Les modèles suivants permettent des interactions conversationnelles sécurisées par la marque et optimisées par l’IA sur les propriétés numériques.

| Modèle | Fonction de Principal | Solutions principales |
| --- | --- | --- |
| [Expérience de conversation ](conversational-experience/brand-concierge-conversational-experience.md) | Transformer les propriétés numériques en expériences de conversation optimisées par l’IA et sécurisées par la marque qui guident la découverte des clients | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |

## Sélecteur de scénario

Utilisez ce guide lorsqu’un scénario peut correspondre à plusieurs modèles. Répondez aux questions sur l’embranchement pour trouver le modèle principal, puis étendez éventuellement l’élément avec les modèles répertoriés.

### Reconquête avec offre d’incitation

*Un client périmé n&#39;a pas acheté en 90 jours. Vous souhaitez les réengager avec une offre ciblée.*

- **La sélection des offres est-elle dynamique (différents clients reçoivent différentes offres en fonction de l&#39;éligibilité ou du classement) ?**
   - Oui → [Offer Decisioning](personalization/offer-decisioning.md) comme couche d’offre, encapsulée dans [parcours orchestré en plusieurs étapes](campaign-management-orchestration/multi-step-orchestrated-journey.md) pour la séquence de réengagement
   - Pas de (même offre à tous les clients admissibles ayant expiré) → [parcours orchestré à plusieurs étapes](campaign-management-orchestration/multi-step-orchestrated-journey.md) seul

### Suivi après achat

*Un client vient de terminer un achat. Vous souhaitez envoyer une confirmation, une recommandation de vente croisée et une notification de récompense de fidélité.*

- **La séquence nécessite-t-elle un embranchement adaptatif en fonction des événements en temps réel (par exemple, récompense demandée, produit examiné) ?**
   - Oui → [parcours orchestré à plusieurs étapes](campaign-management-orchestration/multi-step-orchestrated-journey.md)
   - Pas d’activation (séquence fixe, pas d’embranchement) → [Message sortant par lots activé](campaign-management-orchestration/batch-outbound-message-activation.md)
- **Inclut-il des recommandations de produits personnalisées ?**
   - Oui → étendre avec [recommandation comportementale](personalization/behavioral-recommendation.md) au niveau du calque de contenu

### Personnalisation du jalon de fidélité

*Un client atteint un nouveau niveau de fidélité. Vous souhaitez afficher du contenu web personnalisé et envoyer un message de félicitations.*

- **Le contenu web est-il personnalisé (contenu différent par niveau ou segment) ?**
   - Oui → [personnalisation web/app des visiteurs connus](personalization/known-visitor-web-app-personalization.md) pour la surface web
- **Le message sortant est-il une séquence d’envoi unique ou une séquence de maturation ?**
   - Envoi unique → [messagerie déclenchée par un événement](campaign-management-orchestration/event-triggered-messaging.md)
   - Séquence → [parcours orchestré à plusieurs étapes](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### Campagne de réengagement

*Un segment d’utilisateurs inactifs nécessite une séquence de réactivation multipoint.*

- **Les messages individuels doivent-ils effectuer une sélection à partir de plusieurs variantes d’offres en temps réel ?**
   - Oui → [parcours cross-canal avec prise de décision](campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
   - Aucun → [parcours orchestré à plusieurs étapes](campaign-management-orchestration/multi-step-orchestrated-journey.md)
