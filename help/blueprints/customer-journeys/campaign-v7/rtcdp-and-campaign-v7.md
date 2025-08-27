---
title: Modèle d’intégration de Real-Time CDP avec  [!DNL Campaign] v7 et Campaign Standard
description: Montre comment le Adobe Experience Platform, ainsi que son profil client en temps réel et son outil de segmentation centralisé peuvent être utilisés avec Adobe [!DNL Campaign] pour proposer des conversations personnalisées.
solution: Real-Time Customer Data Platform, [!DNL Campaign]
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 10d49e3b712fc9d4ecdf41defe6e62dde2a86b72
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 42%

---

# [!DNL Real-Time Customer Data Platform] avec modèle d’intégration [!DNL Campaign]

Montre comment Adobe [!DNL Experience Platform], ainsi que son profil client en temps réel et son outil de segmentation centralisé peuvent être utilisés avec Adobe [!DNL Campaign] pour proposer des conversations personnalisées.

## Applications

* Adobe [!DNL Experience Platform Real-Time Customer Data Platform]
* Adobe [!DNL Campaign] v7 ou [!DNL Campaign Standard]

## Architecture

<img src="assets/rtcdp-campaign-architecture.svg" alt="Architecture de référence du modèle d’intégration de la messagerie par lots et d’Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Conditions préalables

* Il est recommandé de configurer Experience Platform et [!DNL Campaign] dans la même organisation IMS et d’utiliser Adobe Admin Console pour l’accès utilisateur. Cela garantit également que les clients peuvent utiliser le sélecteur de solution dans l’interface utilisateur marketing.

## Garde-fous

Les sections suivantes décrivent les mécanismes de sécurisation pour cette intégration.

### Adobe [!DNL Campaign]

* Ne prend en charge que les déploiements d’Adobe [!DNL Campaign] d’entités organisationnelles uniques
* Adobe [!DNL Campaign] est une source de vérité pour tous les profils actifs, ce qui signifie que les profils doivent exister dans Adobe [!DNL Campaign] et que les nouveaux profils ne doivent pas être créés en fonction de segments Experience Platform.
* [!DNL Campaign] workflows d’exportation à exécuter au plus toutes les 4 heures
* Le schéma XDM et les jeux de données pour Adobe [!DNL Campaign] broadLog, trackingLogs et adresses non délivrables ne sont pas prêts à l’emploi et doivent être conçus et créés

### Partage de segments Real-Time Customer Data Platform

* Pour plus d&#39;informations, consultez la section Connecteur de destination RTCDP [!DNL Campaign] - [Connexion RTCDP Campaign](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=fr)

* Voir [ Mécanismes de sécurisation par défaut pour  [!DNL Real-Time Customer Profile Data]  segmentation ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

## Étapes de mise en œuvre

Les sections suivantes décrivent les étapes d’implémentation pour chaque application.

### Adobe Experience Platform

#### Schéma/jeux de données

1. [Configurez des profils individuels, des événements d’expérience et des schémas multi-entités](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=fr) dans Experience Platform, en fonction des données fournies par le client.
1. Créez des schémas de [!DNL Campaign] Adobe pour broadLog, trackingLog, les adresses de non-délivrabilité et les préférences de profil (facultatif).
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) dans Experience Platform pour les données à ingérer.
1. [Ajoutez des libellés d’utilisation des données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=fr) dans Experience Platform au jeu de données pour votre gouvernance.
1. [Créez des stratégies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=fr) pour appliquer la gouvernance sur les destinations.

#### Profil/identité

1. [Créez des espaces de noms spécifiques au client](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Ajoutez des identités aux schémas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr).
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Configurez des stratégies de fusion](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=fr) pour les différentes vues de [!UICONTROL profil client en temps réel] (facultatif).
1. Créez des segments pour l’utilisation d’Adobe [!DNL Campaign].

#### Sources/destinations

1. [Sources et destinations Experience Platform et  [!DNL Campaign]  standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=fr)
1. [Sources et destinations Experience Platform et [!DNL Campaign] v7](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html?lang=fr)
1. [Ingérez des données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=fr) à l’aide des API de streaming et des connecteurs sources.
1. Configurez [!DNL Azure] destination de stockage d’objets blob à utiliser avec Adobe [!DNL Campaign].

#### Adobe [!DNL Campaign]

1. Configurez des schémas pour le profil, les données de recherche et les données de personnalisation de diffusion pertinentes.

>[!IMPORTANT]
>
>Il est essentiel de comprendre à ce stade quel est le modèle de données dans Experience Platform pour les données de profil et d’événement afin de savoir quelles données seront requises dans Adobe [!DNL Campaign].

#### Importer des workflows

1. Chargement et ingestion de données de profil simplifiées sur Adobe [!DNL Campaign] sFTP.
1. Charger et ingérer des données de personnalisation de messagerie et d’orchestration dans Adobe [!DNL Campaign] sFTP.
1. Ingérez les segments d’Experience Platform à partir du blob [!DNL Azure] via des workflows.

#### Exporter des workflows

1. Renvoyer les logs Adobe [!DNL Campaign] à Experience Platform par le biais de workflows toutes les quatre heures (broadLog, trackingLog, adresses de non-délivrabilité).
1. Renvoyez les préférences de profil à Experience Platform via des workflows créés par consultation toutes les quatre heures (facultatif).

### Configuration des notifications push mobiles

* Deux approches sont prises en charge pour l’intégration aux appareils mobiles pour les notifications push :
   * SDK mobile Experience Platform
   * [!DNL Campaign] Mobile SDK
* Chemin du SDK mobile Experience Platform :
   * Tirez parti d’Adobe Tags et de l’extension [!DNL Campaign Classic] pour configurer votre intégration à Experience Platform Mobile SDK.
   * Vous avez besoin d’une connaissance pratique des balises d’Adobe et de la collecte de données.
   * Vous avez besoin d’une expérience du développement mobile avec les notifications push dans Android et iOS pour le déploiement du SDK, l’intégration avec FCM (Android) et APNS (iOS) pour obtenir un jeton push, la configuration de votre application pour recevoir des notifications push et gérer les interactions push.
* [!DNL Campaign] Mobile SDK
   * Voir la documentation de Campaign Classic SDK [](https://developer.adobe.com/client-sdks/solution/adobe-campaign-classic/)

>[!IMPORTANT]
>
>Si vous déployez le SDK [!DNL Campaign] et que vous travaillez avec d’autres applications Experience Cloud, l’utilisation du SDK mobile Experience Platform pour la collecte de données sera nécessaire. Vous créez ainsi des appels côté client en double sur l’appareil.

## Documentation connexe

* [Documentation Adobe [!DNL Experience Platform] ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [[!DNL Campaign Classic] documentation ](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [[!DNL Campaign Standard] documentation ](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr)
* [[!DNL Experience Platform] Documentation de Launch](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [[!DNL Experience Platform] Documentation de Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
