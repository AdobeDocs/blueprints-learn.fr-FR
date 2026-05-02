---
title: Audience Activation vers les destinations sociales et Advertising
description: Découvrez comment ingérer des données client provenant de plusieurs sources afin de créer une vue de profil unique du client.
solution: Real-Time Customer Data Platform, Data Collection
kt: 7086
exl-id: b75a7a01-04ba-4617-960d-f73f7a9cc6c7
TQID: https://experienceleague.adobe.com/GNc9ZMx62nCAEYtB1TP3buZonF6GQKBfoYLNepSzDHM
product_v2:
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: ba929a52-9339-4154-9487-317dc875a3c7
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 174
ht-degree: 45%

---

# Audience Activation vers les destinations sociales et Advertising

>[!TIP]
>Ce plan directeur est également disponible en tant que [modèle de cas d’utilisation](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) sous Création et activation d’audience.

Ingérez des données client à partir de plusieurs sources afin de créer une vue de profil unique du client. Vous pouvez segmenter ces profils afin de créer des audiences pour le marketing et la personnalisation. Partagez ensuite ces audiences avec les réseaux publicitaires tels que Facebook et Google pour cibler et personnaliser les campagnes par rapport à ces audiences.

## Cas d’utilisation

* Ciblage d’audience pour des audiences connues sur les réseaux sociaux et les destinations publicitaires.
* Personnalisation en ligne avec des attributs en ligne et hors ligne.

## Applications

* Real-time Customer Data Platform

## Architecture

<img src="./assets/social_activation.svg" alt="Architecture de référence d’activation d’audience Facebook personnalisée" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Garde-fous

[Mécanismes de sécurisation des profils et de la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

## Documentation connexe

Activation des audiences personnalisées Facebook - [Configuration de la destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/social/facebook.html?lang=fr)

Activation du ciblage par liste de clients Google - [Configuration de la destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/google-customer-match.html?lang=fr)