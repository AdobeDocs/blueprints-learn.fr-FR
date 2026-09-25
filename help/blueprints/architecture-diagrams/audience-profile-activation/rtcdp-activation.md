---
title: Activation d’Adobe Real-Time CDP
description: Référence d’architecture pour activer les audiences et les données de profil d’Adobe Real-Time CDP vers des destinations publicitaires, sociales, de stockage dans le cloud et d’entreprise.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%
---
# Activation d’Adobe Real-Time CDP

Cette architecture montre comment Adobe [!DNL Real-Time Customer Data Platform] ([!DNL Real-Time CDP]) active des audiences et des données de profil vers des destinations publicitaires, sociales, de stockage dans le cloud et d’entreprise par le biais de flux de données en flux continu et par lots.

## Activation des audiences et des profils

L’architecture illustre le chemin d’activation partagé entre les audiences et les profils [!DNL Real-Time CDP] et les applications de destination. Elle comprend l’activation de destination pour les plateformes publicitaires et sociales, ainsi que les destinations d’entreprise utilisées pour le stockage, l’analyse et les workflows d’application en aval.

![Architecture d’activation des audiences et des profils &#x200B;](assets/real_time_cdp_activation.png){width="1000" zoomable="yes"}

## Modèles de cas d’utilisation pris en charge

L’architecture ci-dessus prend en charge les modèles de cas d’utilisation suivants :

- [Activation des audiences vers les destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) — Activez les audiences évaluées vers les destinations publicitaires, sociales, de stockage dans le cloud, de gestion de la relation client et autres destinations d’entreprise.
- [Personnalisation web anonyme des visiteurs](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) — Prend en charge l’activation des audiences et la personnalisation basée sur les profils sur les canaux numériques.

## Flux de données de Principal et points d’intégration

- Ingérez des données client provenant de plusieurs sources dans [!DNL Real-Time CDP].
- Unifiez les attributs d’identité et de profil dans [!DNL Real-Time Customer Profile].
- Évaluez les profils en audiences pour l’activation.
- Diffusez en continu ou par lots les modifications d’audience et de profil vers des destinations publicitaires, sociales, de stockage dans le cloud et d’entreprise.
- Utilisez les données de profil et d’audience activées dans les workflows de marketing, de vente, d’assistance, d’analyse et de personnalisation en aval.

## Informations complémentaires

- [Destinations Adobe Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Activer les audiences vers les destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Mécanismes de sécurisation d’Adobe Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview)
