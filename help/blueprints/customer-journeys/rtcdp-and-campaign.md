---
title: Real-Time CDP avec Adobe Campaign v7 et modèle d’intégration de Campaign Standard
description: Présente comment Adobe Experience Platform, le Real-Time Customer Profile et son outil de segmentation centralisé peuvent être utilisés avec Adobe Campaign pour diffuser des conversations personnalisées.
solution: Real-time Customer Data Platform, Campaign
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 163dd644b690c1f5554a3929e1f83c121e132df5
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 94%

---

# Real-Time CDP avec modèle d’intégration Adobe Campaign

Présente comment Adobe Experience Platform, le Real-Time Customer Profile et son outil de segmentation centralisé peuvent être utilisés avec Adobe Campaign pour diffuser des conversations personnalisées.

<br>

## Applications

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v7 ou Campaign Standard

<br>

## Architecture

<img src="assets/rtcdp-campaign-architecture.svg" alt="Architecture de référence pour la messagerie par lots et modèle d’intégration d’Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Conditions préalables

* Experience Platform et Campaign sont recommandés pour être configurés dans la même organisation IMS et utiliser Adobe Admin Console pour l’accès des utilisateurs. Cela garantit également que les clients peuvent utiliser le sélecteur de solution dans l’interface utilisateur marketing.

<br>

## Garde-fous

### Adobe Campaign

* Ne prend en charge que les déploiements d’une seule unité organisationnelle d’Adobe Campaign.
* Adobe Campaign est une source de confirmation pour tous les profils actifs, c’est-à-dire que les profils doivent exister dans Adobe Campaign et que de nouveaux profils ne doivent pas être créés en fonction des segments Experience Platform.
* Les workflows d’exportation de Campaign doivent être exécutés au plus toutes les 4 heures
* Les jeux de données et schémas XDM pour les adresses Adobe Campaign broadLog, trackingLogs et non livrables ne sont pas prêts à l’emploi et doivent être conçus et créés.

### Partage de segments de la plateforme de données clients Experience Platform

* Limite de 20 segments recommandée
* L’activation est limitée à une fois toutes les 24 heures.
* Seuls les attributs de schéma d’union sont disponibles pour l’activation (pas de prise en charge des événements de tableau / mappage / expérience)
* Limite de 20 attributs par segment recommandée
* Un fichier par segment de tous les profils avec des segments d’appartenance « réalisés » OU si l’appartenance au segment est ajoutée en tant qu’attribut dans le fichier, les profils « réalisés » et « sortis »
* Les exportations de segments incrémentielles et complètes sont prises en charge.
* Le cryptage des fichiers n’est pas pris en charge

<br>

## Étapes d’implémentation

### Adobe Experience Platform

#### Schéma / jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) dans Experience Platform, en fonction des données fournies par le client.
1. Créez des schémas Adobe Campaign pour les éléments broadLog, trackingLog, adresses non livrables et préférences de profil (facultatif).
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) dans Experience Platform pour les données à ingérer.
1. [Ajoutez des libellés d’utilisation des données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=fr) dans Experience Platform au jeu de données pour votre gouvernance.
1. [Créez des stratégies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=fr) pour appliquer la gouvernance sur les destinations.

#### Profil / identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Configurez des stratégies de fusion](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=fr) pour les différentes vues de [!UICONTROL profil client en temps réel] (facultatif).
1. Créez des segments pour utilisation dans Adobe Campaign.

#### Sources / destinations

1. [Sources et destinations Experience Platform et Campaign Standardes](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html)
1. [Sources et destinations Experience Platform et Campaign v7](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html)
1. [Ingérez des données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) à l’aide d’API de diffusion en continu et de connecteurs sources.
1. Configurez la destination de l’enregistrement blob [!DNL Azure] à utiliser avec Adobe Campaign.

#### Adobe Campaign

1. Configurez des schémas pour le profil, les données de recherche et les données de personnalisation de diffusion pertinentes.

>[!IMPORTANT]
>
>Il est essentiel de comprendre à ce stade quel est le modèle de données dans Experience Platform pour les données de profil et d’événement afin de savoir quelles données seront requises dans Adobe Campaign.

#### Importer des workflows

1. Chargez et ingérez les données de profil simplifiées sur le sFTP d’Adobe Campaign.
1. Chargez et ingérez les données d’orchestration et de personnalisation de la messagerie sur le sFTP d’Adobe Campaign.
1. Ingérez les segments d’Experience Platform à partir du blob [!DNL Azure] via des workflows.

#### Exporter des workflows

1. Renvoyez les journaux d’Adobe Campaign à Experience Platform via des workflows toutes les quatre heures (broadLog, trackingLog, adresses non livrables).
1. Renvoyez les préférences de profil à Experience Platform via des workflows créés par consultation toutes les quatre heures (facultatif).


### Configuration push mobile

* Deux approches sont prises en charge pour l’intégration aux appareils mobiles pour les notifications push :
   * SDK mobile Experience Platform
   * SDK Campaign Mobile
* Chemin du SDK mobile Experience Platform :
   * Tirez parti des balises Adobe et de l’extension Campaign Classic pour configurer votre intégration avec le SDK Mobile Experience Platform.
   * Vous avez besoin d’une connaissance pratique des balises d’Adobe et de la collecte de données.
   * Vous avez besoin d’une expérience du développement mobile avec les notifications push dans Android et iOS pour le déploiement du SDK, l’intégration avec FCM (Android) et APNS (iOS) pour obtenir un jeton push, la configuration de votre application pour recevoir des notifications push et gérer les interactions push.
* SDK Campaign Mobile
   * Veuillez suivre les étapes de la [Documentation du SDK Campaign] (SDK Mobile Campaign
Consultez la documentation de déploiement décrite ici)

   >[!IMPORTANT]
   >Si vous déployez le SDK Campaign et que vous travaillez avec d’autres applications Experience Cloud, vous devrez utiliser le SDK Mobile Experience Platform pour la collecte de données. Vous créez ainsi des appels côté client en double sur l’appareil.

## Documentation connexe

* [Documentation pour Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Documentation pour Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [Documentation pour Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr)
* [Documentation pour Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
