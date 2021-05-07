---
title: Plan directeur pour Adobe Experience Platform et la diffusion de messages déclenchés
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 01f70fe432d7be38b71889ae19c0d5fe4cf0f78a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Plan directeur pour Adobe Experience Platform et la diffusion de messages déclenchés

Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.

## Cas d’utilisation

* Messages déclenchés
* Confirmations d’enregistrement
* Abandon de panier et de formulaire de demande
* Messages déclenchés par l’emplacement

## Architecture

<img src="assets/triggered.svg" alt="Architecture de référence pour les messages déclenchés et le plan directeur d’Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Modèles d’intégration

* Adobe Experience Platform -> Journey Orchestration

## Conditions préalables

* Adobe Experience Platform
* Journey Orchestration

## Garde-fous

### Journey Orchestration

* Voir le lien pour [plus de détails sur les limitations](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=fr#starting-with-journeys)
* La limitation est disponible par le biais de la configuration de l’API pour assurer que le système de destination n’est pas saturé au point d’échec. La limitation signifie que les messages qui vont au-delà du plafond sont ignorés et ne sont jamais envoyés. Le ralentissement n’est pas encore pris en charge.
   * connexions max : nombre maximal de connexions http/s qu’une destination peut gérer
   * nombre max d’appels : nombre maximal d’appels qu’on peut effectuer dans le paramètre periodInMs
   * periodInMs : temps en millisecondes
* Les parcours initiés d’appartenance à un segment peuvent fonctionner suivant deux modes :
   * segments de lot (actualisés toutes les 24 heures)
   * segments de diffusion en flux continu (qualification de moins de 5 minutes)
* Segments de lot : veillez à comprendre le volume quotidien des utilisateurs qualifiés et à ce que le système de destination puisse gérer le débit d’éclatement par parcours et sur tous les parcours.
* Segments de diffusion en continu : veillez à ce que l’éclatement initial des qualifications de profil puisse être traité avec le volume de qualification de diffusion en continu quotidien par parcours et sur tous les parcours
* La destination finale doit prendre en charge l’API REST et la payload JSON
* Ne prend actuellement pas en charge Offer Decisioning
* Voir [garde-fous pour l’ingestion de profils et de données dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

### Adobe Campaign Standard

* Ne peut prendre en charge que 14 tps (50 000/h) de débit
* Les parcours initiés d’appartenance à un segment ne sont pas pris en charge
* Les événements de réaction aux messages transactionnels ouverts / cliqués sont pris en charge dans Journey Orchestration.
* Actuellement, les journaux de messagerie transactionnelle ne sont pas synchronisés en mode natif avec Experience Platform, ce qui nécessite une configuration manuelle. Il est recommandé d’exporter les journaux au plus toutes les quatre heures.


## Étapes d’implémentation

### Adobe Experience Platform

#### Schéma / jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités dans Experience Platform, en fonction des données fournies par le client.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. Créez des schémas Adobe Campaign pour les éléments broadLog, trackingLog, adresses non livrables et préférences de profil (facultatif).
1. [Créez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) des ensembles de données dans l’Experience Platform pour que les données soient assimilées.
1. [Ajoutez les ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) étiquettes d’utilisation des données dans l’Experience Platform au jeu de données pour la gouvernance.
1. [Créez des stratégies pour appliquer la gouvernance sur les destinations.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html)

#### Profil / identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Activez les schémas et les jeux de données pour le Profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Configurez ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) des stratégies de fusion pour les différentes vues du Profil [!UICONTROL  client en temps ] réel (facultatif).
1. Créez des segments pour utilisation dans Adobe Campaign.

#### Sources / destinations

1. [Envoi de données dans la ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) plate-forme Experience à l’aide d’API de diffusion en continu et de connecteurs source.1. Configurez la destination de l’enregistrement  [!DNL Azure] blob à utiliser avec Adobe Campaign.

#### Déploiement d’applications mobiles

1. Utilisez le SDK Adobe Campaign pour Adobe Campaign Classic ou le SDK Experience Platform pour Adobe Campaign Standard. Si vous disposez d’Experience Platform Launch, il est recommandé d’utiliser l’extension Adobe Campaign Classic ou Adobe Campaign Standard avec le SDK Experience Platform.


### Adobe Journey Orchestration

1. Les données de diffusion en continu utilisées pour lancer un parcours client doivent d’abord être configurées dans Journey Orchestration pour obtenir un ID d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser lors de l’ingestion.
1. Configurez des sources de données externes.
1. Configurez des actions personnalisées.

### Adobe Campaign Standard

1. Configurez les modèles de messagerie avec les paramètres de personnalisation appropriés.
1. Configurez les journaux de messagerie transactionnelle d’exportation des workflows. Il est recommandé d’actualiser les journaux au plus toutes les quatre heures.


## Documentation connexe

* [Documentation pour Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation pour Adobe Journey Orchestration](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=fr)
* [Documentation pour Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [Documentation pour Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr)
* [Documentation pour Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
