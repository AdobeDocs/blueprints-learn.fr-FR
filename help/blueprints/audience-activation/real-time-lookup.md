---
title: Accès au profil Edge en temps réel pour les Personalization web et mobiles
description: '[!UICONTROL Profil client en temps réel] accédez à Edge pour fournir un contexte pour la personnalisation web et mobile en temps réel.'
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
source-git-commit: 2fad3a8a9210d703130f251b0bd7cc4c0b7cbd32
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 6%

---

# Accès au profil Edge en temps réel pour les Personalization web et mobiles

Le plan directeur Accès au profil Real-time Edge pour le Web et Mobile Personalization montre comment les applications web et mobiles peuvent accéder à Adobe Experience Platform [!UICONTROL profil client en temps réel] à la périphérie pour une personnalisation à débit élevé et à faible latence.

Les applications peuvent accéder aux attributs de profil en temps réel et aux audiences à la périphérie avec une latence en millisecondes. Les attributs, les appartenances aux audiences et les fonctionnalités pilotées par les modèles stockés dans le profil en tant qu’attributs sont accessibles en temps réel pour la personnalisation de la même page et de la page suivante sur les canaux web et mobiles.

Grâce à cette fonctionnalité, vous pouvez proposer des expériences hautement personnalisées sur vos sites web et applications mobiles en fonction du profil client en temps réel, notamment des audiences dérivées de comportements en temps réel, des attributs ingérés par le profil client en temps réel et des informations calculées.

>[!NOTE]
>
>L’accès au profil Edge est spécialement conçu pour les cas d’utilisation à débit élevé et à faible latence, tels que la personnalisation entrante web/mobile et la prise de décision d’offres en temps réel. Pour les scénarios de débit inférieur, tels que l’assistance assistée par un agent ou les interactions de vente, l’API de recherche de profil Hub est plus appropriée. Consultez le [plan directeur de l’accès au profil en temps réel pour les scénarios d’assistance et de vente](customer-activity.md) pour obtenir un accès au profil basé sur le hub.

## Applications

* Real-time Customer Data Platform
* Collecte de données Adobe Experience Platform (Web SDK / Mobile SDK)
* API du serveur Edge Network

## Cas d’utilisation

* Personnalisation en temps réel sur les canaux web et mobiles pour les expériences client connues
* Personnalisation de la même page et de la page suivante en fonction des attributs de profil et des audiences en temps réel
* Personnalisation du contenu et des offres basée sur les profils clients, y compris les données comportementales en temps réel, les attributs et les informations calculées
* Intégration aux moteurs de personnalisation, aux systèmes de gestion de contenu et aux applications externes pour une prise de décision en temps réel
* Tests et optimisation du contenu avec le contexte de profil en temps réel

## Conditions préalables

Ce plan directeur nécessite l’utilisation de l’une des méthodes de collecte de données suivantes si vous souhaitez que le profil soit mis à jour en temps réel avec des données en flux continu. Il est possible d’obtenir un accès en temps réel au profil Edge sans avoir à collecter des données directement au profil Edge ; les données peuvent être collectées au hub et projetées au profil Edge également. Notez qu’une latence supplémentaire sera ajoutée pour les données collectées dans le Hub, puis projetées vers Edge.

* Utilisez [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html) si vous souhaitez collecter des données sur votre site Web.
* Utilisez [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) si vous souhaitez collecter des données à partir de votre application mobile.
* Utilisez l’API [Edge Network Server](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr) si vous n’utilisez pas Web SDK ou Mobile SDK, ou si vous implémentez une connexion serveur à serveur plus directe.

>[!IMPORTANT]
>
>Avant d’implémenter la personnalisation Edge, lisez le guide sur la manière d’[activer les données d’audience vers des destinations de personnalisation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). Ce guide vous guide tout au long des étapes de configuration requises pour les cas d’utilisation de la personnalisation de la même page et de la page suivante, sur plusieurs composants Experience Platform.

## Diagramme d’architecture

<img src="assets/real-time-edge-lookup.svg" alt="Architecture de référence d’Edge Profile Access pour Web et Mobile Personalization" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Garde-fous

* [Garde-fous pour les données de [!UICONTROL profil client en temps réel]](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Mécanismes De Sécurisation Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Les profils Edge ont une durée de vie (TTL) de 14 jours. Si un utilisateur n’est pas actif sur Edge depuis 14 jours, le profil Edge peut expirer et doit être récupéré depuis le hub, ce qui peut avoir un impact sur la personnalisation de première page.
* La personnalisation Edge prend en charge l’évaluation de l’appartenance à une audience en temps réel pour les audiences qui répondent aux critères de segmentation Edge. Les audiences par lots et en flux continu à partir du hub sont également disponibles en périphérie avec la configuration appropriée.

## Modèles de mise en œuvre

La personnalisation Edge peut être mise en œuvre à l’aide de la destination [Connexion Personalization personnalisée](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) dans Real-time Customer Data Platform. Cette destination prend en charge plusieurs méthodes de collecte de données en fonction de votre cas d’utilisation.

### Modèle 1 : personnalisation basée sur l’appartenance à une audience avec Web SDK/Mobile SDK

* Utilisez Adobe Experience Platform Web SDK ou Mobile SDK avec Edge Network pour la personnalisation basée sur l’appartenance à une audience.
* Cette approche offre une faible latence et les meilleures performances pour la personnalisation Edge en fonction des adhésions à l’audience.
* La segmentation Edge en temps réel nécessite l’implémentation de Web/Mobile SDK.
* Web SDK et Mobile SDK **seuls prennent en charge la personnalisation basée sur l’appartenance à l’audience uniquement**.
* [Consultez le Plan directeur d’Experience Platform Web and Mobile SDK](../experience-platform/deployment/websdk.md) pour une implémentation basée sur SDK.
* Pour l’implémentation de Mobile SDK, l’extension [Adobe Journey Optimizer - Decisioning](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/) doit être installée dans Mobile SDK.

### Modèle 2 : personnalisation basée sur les attributs avec l’API du serveur Edge Network (obligatoire pour les attributs de profil)

>[!IMPORTANT]
>
>**Exigences de personnalisation basées sur les attributs :** si vous souhaitez effectuer une personnalisation en fonction des attributs de profil (et pas seulement de l’appartenance à l’audience), vous **devez** utiliser l’[API Edge Network Server](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr) avec une intégration authentifiée côté serveur, que vous utilisiez également Web SDK ou Mobile SDK pour la collecte de données.

* Permet l’intégration à des moteurs de personnalisation tiers et à la personnalisation basée sur le réseau CDN.
* L’API du serveur Edge Network est **obligatoire** pour récupérer en toute sécurité les attributs de profil pour la personnalisation.
* Vous pouvez récupérer les attributs de profil via l’API du serveur Edge Network en ajoutant une intégration côté serveur qui utilise le même flux de données que celui que vous utilisez déjà pour votre implémentation de Web ou Mobile SDK.
* Tous les appels API du serveur Edge Network pour les attributs de profil doivent être effectués dans un contexte authentifié pour protéger les données sensibles.
* Ce modèle permet à la fois la personnalisation basée sur l’appartenance à une audience et la personnalisation basée sur les attributs.
* Adapté aux cas d’utilisation de la personnalisation côté serveur, aux intégrations basées sur des API et aux scénarios nécessitant un accès aux attributs de profil.

## Étapes de mise en œuvre

1. [Créez des schémas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=fr) pour les données à ingérer.
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) pour les données à ingérer.
1. [Configurez les identités et les espaces de noms d’identité corrects](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr) sur le schéma pour vous assurer que les données ingérées peuvent être regroupées dans un profil unifié.
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Ingérez des données](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=fr) dans Experience Platform.
1. [Configurez les politiques de fusion](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=fr) pour garantir une combinaison d’identités et une fusion de profils correctes.
1. [Configurer un flux de données](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=fr) dans la collecte de données Experience Platform avec la configuration de destination activée. Le flux de données détermine dans quel flux de données de collecte de données les audiences seront incluses dans la réponse à la page.
1. Implémentez [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html) ou [Mobile SDK](https://developer.adobe.com/client-sdks/home/) sur les propriétés web et mobiles pour la collecte de données.
1. Configurez la segmentation Edge pour les audiences qui nécessitent une évaluation en temps réel. [Documentation sur la segmentation Edge](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=fr).
1. Dans le catalogue des destinations, configurez la destination [Connexion Personalization personnalisée](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) :
1. [Activer les audiences vers la destination de personnalisation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). Sélectionnez les audiences à activer vers la destination.
1. (Facultatif pour la personnalisation basée sur les attributs) Si vous devez effectuer une personnalisation en fonction des attributs de profil en plus de l’appartenance à l’audience, implémentez l’[API Edge Network Server](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr) avec une intégration authentifiée côté serveur à l’aide du même flux de données. Cela est **obligatoire** pour accéder aux attributs de profil.
1. Implémentez une logique de personnalisation dans votre application web/mobile pour utiliser les données d’audience et les attributs de profil exportés :
   * Si vous utilisez les balises dans Adobe Experience Platform, utilisez la fonctionnalité [envoi de l’événement terminé](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=fr) pour accéder à `event.destinations` variable avec les données exportées.
   * Si vous n’utilisez pas de balises, utilisez les [réponses de commande](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html) pour analyser la réponse JSON à partir de Adobe Experience Platform et récupérer les identifiants d’audience et les attributs de profil.

## Considérations relatives à la mise en œuvre

### Considérations relatives aux identités

* Toute identité principale peut être utilisée pour la personnalisation Edge lors de l’utilisation de Web SDK ou de Mobile SDK avec Edge Network.
* Pour la première personnalisation de connexion avec des données client connues, la demande de personnalisation doit utiliser une identité principale correspondant à l’identité client connue dans Real-time Customer Data Platform. Si l’identifiant principal est défini sur ECID ou sur une identité anonyme qui n’a pas encore été regroupée avec le profil client connu, l’assemblage des identités prend du temps, ce qui peut avoir une incidence sur la disponibilité des données de profil historiques pour la personnalisation.
* Les profils Edge doivent être initialisés avant de pouvoir être utilisés pour la personnalisation. Les nouveaux visiteurs ou les visiteurs récurrents dont le profil Edge a expiré (durée de vie de 14 jours) peuvent bénéficier d’une personnalisation initiale basée sur des données de profil limitées jusqu’à ce que le profil Edge soit entièrement renseigné.

### Personnalisation basée sur les attributs

>[!IMPORTANT]
>
>Les attributs de profil peuvent contenir des données sensibles. Pour protéger ces données, vous **devez** utiliser l’[API du serveur Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr) lors de la configuration de la destination Personalization personnalisée pour la personnalisation basée sur les attributs. Tous les appels de l’API du serveur Edge Network doivent être effectués dans un contexte authentifié.

* Pour la personnalisation basée sur les attributs à l’aide d’attributs de profil, vous devez ajouter une intégration côté serveur à l’API du serveur Edge Network qui utilise le même flux de données que celui utilisé pour votre implémentation de Web ou Mobile SDK.
* Vous devez configurer les attributs de profil à inclure dans la projection Edge via la configuration de destination de connexion Personalization personnalisée.
* **Web SDK et Mobile SDK prennent uniquement en charge la personnalisation basée sur l’appartenance à l’audience**. L’API du serveur Edge Network est **obligatoire** pour récupérer en toute sécurité les attributs de profil pour la personnalisation.
* Si vous n’implémentez pas l’API du serveur Edge Network pour l’accès aux attributs, la personnalisation sera basée sur l’appartenance à l’audience uniquement.
* La réponse de l’API pour Custom Personalization with Attributes comprend une section `attributes` en plus des segments d’audience.

### Considérations relatives à l’audience

* Les audiences évaluées par le biais de la segmentation par lots ou en flux continu sur le hub sont projetées vers le Edge et peuvent être utilisées pour la personnalisation.
* Les audiences qui répondent aux critères de segmentation Edge sont évaluées en temps réel sur le serveur Edge pour la personnalisation de même page.
* Configurez les audiences appropriées pour l’évaluation Edge en fonction de leur utilisation dans les cas d’utilisation de la personnalisation en temps réel.

## Documentation connexe

### Configurations de destination

* [Connexion Personalization personnalisée](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) - Guide de mise en œuvre du Principal
* Présentation des destinations Personalization [](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [Activer les audiences vers des destinations de personnalisation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [Rechercher des attributs de profil sur le serveur Edge en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### Documentation du SDK

* [Documentation pour le SDK web d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://developer.adobe.com/client-sdks/home/)
* [Documentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [Réponses des commandes dans Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### Documentation sur les profils et la segmentation

* Documentation sur [[!UICONTROL le profil client en temps réel]](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Garde-fous pour le profil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

### Tutoriels

* [Personnalisation par « Prochain accès » avec Real-Time CDP et Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [Configuration du flux de données](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=fr)
