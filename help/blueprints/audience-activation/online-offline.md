---
title: Plan d'Audience Activation en ligne/hors ligne
description: Audience Activation en ligne / hors ligne
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 2fc1adc04a9ca2184c88970d5ba0785957327f68
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 63%

---

# Plan d&#39;Audience Activation en ligne/hors ligne

Utilisez les attributs et les événements hors ligne tels que les commandes hors ligne, les transactions, la gestion de la relation client (CRM) ou les données sur la fidélité, combinés avec le comportement en ligne pour le ciblage et la personnalisation en ligne.

Activez des audiences vers des destinations connues basées sur le profil telles que les fournisseurs de messagerie électronique, les réseaux sociaux et les destinations publicitaires

Le Plan d&#39;Audience Activation en ligne/hors ligne s&#39;aligne étroitement avec l&#39;Activation [d&#39;Audience et de Profil avec le Plan d&#39;application Experience Cloud](platform-and-applications.md). Des détails supplémentaires sont fournis dans le document [Audience et Activation Profil avec le plan des applications Experience Cloud](platform-and-applications.md).   spécifique aux intégrations entre applications Experience Platform et Experience Cloud.

## Cas d’utilisation

* Ciblage d’audience pour des audiences connues sur les réseaux sociaux et les destinations publicitaires.
* Personnalisation en ligne avec des attributs en ligne et hors ligne.
* Activez des audiences vers des canaux connus, tels que la messagerie électronique et les SMS.

## Applications

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]

## Architecture

### Audience Activation en ligne/hors ligne avec les destinations

<img src="assets/online_offline_activation.svg" alt="Architecture de référence pour le plan directeur des Audiences Activation en ligne/hors ligne" style="border:1px solid #4a4a4a" />
<br>

### Audience Activation en ligne/hors ligne avec les applications Experience Cloud

<img src="assets/activation+apps.svg" alt="Architecture de référence pour le plan d'Audience Activation en ligne/hors ligne avec les applications Experience Cloud" style="border:1px solid #4a4a4a" />

## Garde-fous

[Reportez-vous aux garde-fous comme indiqué sur la page Aperçu de l&#39;Activation des Audiences et des Profils.](overview.md)

## Étapes d’implémentation

1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) des schémas pour que les données soient assimilées.
1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) des jeux de données pour que les données soient assimilées.
1. [Configurez les identités et les espaces de noms d’identité corrects sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Ingérez les données dans Experience Platform.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. [Fournissez un partage de segment Real-time Customer Data Platform entre Experience Platform et Audience Manager pour les audiences définies dans Experience Platform à partager avec Audience Manager.](https://www.adobe.com/go/audiences)
1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr) des segments dans l’Experience Platform. Le système détermine automatiquement si le segment est évalué en tant que lot ou en tant que flux continu.
1. [Configurez les destinations pour le partage des attributs de profil et des appartenances à une audience vers les destinations souhaitées.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html)

## Considérations de mise en œuvre

* Le partage des données de profil avec les destinations nécessite que vous incluiez la valeur d’identité spécifique utilisée par la destination dans la payload de destination. Toute identité nécessaire pour une destination de cible doit être assimilée à Platform et configurée en tant qu&#39;identité pour le [!UICONTROL Profil client en temps réel].

* Pour les scénarios d’activation où les audiences sont partagées entre Experience Platform et Audience Manager, toutes les identités incluses dans le [!UICONTROL profil client en temps réel] sont partagées avec Audience Manager. Les audiences d’Experience Platform peuvent être partagées via les destinations d’Audience Manager lorsque les identités de destination requises sont incluses dans le [!UICONTROL profil client en temps réel], ou lorsque les identités du [!UICONTROL profil client en temps réel] peuvent être reliées aux identités de destination requises qui sont liées dans Audience Manager.

## Documentation connexe

* [Description de Real-time Customer Data Platform](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Directives sur le profil et la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=fr)

## Vidéos et tutoriels connexes

* [Présentation de Real-time Customer Data Platform ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=fr)
* [[!UICONTROL Vidéo de démonstration de Real-time Customer Data Platform ]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=fr)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
