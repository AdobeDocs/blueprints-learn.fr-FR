---
title: Accès au profil en temps réel pour les scénarios d’assistance et de vente
description: Recherches de [!UICONTROL profil client en temps réel] pour fournir un contexte pour l’aide et les ventes assistées par un agent.
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
TQID: https://experienceleague.adobe.com/Ci9pUbGCLQ9uhlQ9l1na7A2NiI9CpCRMLrUSN6lSOnU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: ba929a52-9339-4154-9487-317dc875a3c7
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
  - id: ee602049-8a18-43df-9299-a689a025a371
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 54%

---

# Accès au profil en temps réel pour les scénarios d’assistance et de vente

>[!TIP]
>Ce plan directeur est également disponible en tant que [modèle de cas d’utilisation](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md) sous Création et activation d’audience.

Le plan directeur Accès au profil en temps réel pour les scénarios d’assistance et de vente montre comment les applications externes peuvent accéder à Adobe Experience Platform [!UICONTROL profil client en temps réel].

Les applications externes peuvent accéder aux profils à travers une requête GET d’API. Les attributs, événements, abonnements aux segments, et fonctionnalités basées sur des modèles stockés dans le profil peuvent ensuite être utilisés dans ces applications externes.

Avec cette fonctionnalité, vous pouvez faire apparaître un contexte riche lorsqu’un client contacte votre centre d’appel. Les agents du service clientèle peuvent avoir une visibilité sur la valeur de durée de vie du client, sa propension au désabonnement ou son exposition à des campagnes marketing, par exemple. Les agents commerciaux peuvent également bénéficier de plus de contexte ou d’une meilleure compréhension de leur client.

>[!NOTE]
>
>La recherche de profil sur le hub n’est pas destinée aux cas d’utilisation à débit élevé et à faible latence, tels que la personnalisation entrante web/mobile. La recherche de profil sur le hub est destinée aux scénarios de faible latence tels que l’assistance assistée par un agent ou les interactions de vente. Pour les scénarios à faible latence et à débit élevé, tels que la personnalisation web/mobile ou la prise de décision sur les offres en temps réel, le profil Edge doit être exploité. Le profil Edge permet un accès en temps réel via la [connexion Personalization personnalisée](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/personalization/custom-personalization) de Real-time Customer Data Platform.

## Cas d’utilisation

* Fournissez un contexte client plus étoffé aux interactions prises en charge par l’agent, telles que les expériences vécues par le client en matière de service clientèle et de vente. À travers la recherche de profil dans Adobe Experience Platform, les agents peuvent recevoir plus de contexte sur le consommateur, comme les achats récents, les interactions de campagne, les propensions, les abonnements et d’autres attributs et informations stockés dans le profil client en temps réel.

## Architecture

<img src="assets/customer_activity_hub.svg" alt="Architecture de référence pour le plan directeur du centre d’activité client" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Garde-fous

* [Mécanismes de sécurisation pour les données [!UICONTROL profil client en temps réel]](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

## Documentation connexe

* [Description du produit Activation de Adobe Experience Platform](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-platform0.html)
* [Documentation [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=fr)
* [Mécanismes de sécurisation de profil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [API de recherche de profil](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
