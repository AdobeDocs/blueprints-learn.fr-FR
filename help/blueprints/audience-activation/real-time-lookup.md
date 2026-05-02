---
title: Accès au profil Edge en temps réel pour les Personalization web et mobiles
description: '[!UICONTROL Profil client en temps réel] accédez à Edge pour fournir un contexte pour la personnalisation web et mobile en temps réel.'
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
exl-id: 61b81d00-c4bd-41b2-8161-683814947b56
TQID: https://experienceleague.adobe.com/H59c3UBbNCQFs3H0VL5iVDKKZ5D3CFt4ri2RVwNlq7s
product_v2: id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2: id: ba929a52-9339-4154-9487-317dc875a3c7
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: c4147b6e-073b-4d3c-9ab1-d60f2f4434efid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d3cdead0-685a-4489-9250-4bb709942f66id: e0eb8757-182f-49f3-94a4-1587d16f5094id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 631
ht-degree: 8%

---

# Accès au profil Edge en temps réel pour les Personalization web et mobiles

>[!TIP]
>Ce plan directeur est également disponible en tant que [ modèle de cas d’utilisation ](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md) sous Personalization.

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

## Diagramme d’architecture

<img src="assets/real-time-edge-lookup.svg" alt="Architecture de référence d’Edge Profile Access pour Web et Mobile Personalization" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Garde-fous

* [Mécanismes de sécurisation pour les données [!UICONTROL profil client en temps réel]](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Mécanismes de sécurisation d’Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Les profils Edge ont une durée de vie (TTL) de 14 jours. Si un utilisateur n’est pas actif sur Edge depuis 14 jours, le profil Edge peut expirer et doit être récupéré depuis le hub, ce qui peut avoir un impact sur la personnalisation de première page.
* La personnalisation Edge prend en charge l’évaluation de l’appartenance à une audience en temps réel pour les audiences qui répondent aux critères de segmentation Edge. Les audiences par lots et en flux continu à partir du hub sont également disponibles en périphérie avec la configuration appropriée.

## Documentation connexe

### Configurations de destination

* [Connexion Personalization personnalisée](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) - Guide de mise en œuvre du Principal
* [Présentation des destinations Personalization](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [Activer les audiences vers des destinations de personnalisation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [Recherche d’attributs de profil sur le serveur Edge en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### Documentation du SDK

* [Documentation Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Documentation Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/)
* [Documentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr)
* [Documentation Experience Platform Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [Réponses des commandes dans Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### Documentation sur les profils et la segmentation

* [Documentation [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Mécanismes de sécurisation de profil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

### Tutoriels

* [Personnalisation des accès suivants avec Real-Time CDP et Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [Configuration du flux de données](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=fr)
