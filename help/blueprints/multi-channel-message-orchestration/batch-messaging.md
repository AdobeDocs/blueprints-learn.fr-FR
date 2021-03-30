---
title: Messagerie par lots et scénario Adobe Experience Platform
description: Exécutez des campagnes de messagerie par lots et planifiées à l’aide de Adobe Experience Platform en tant que hub central pour les profils et la segmentation des clients.
solution: Experience Platform, Campaign
kt: 7196
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# Messagerie par lots et scénario Adobe Experience Platform

Exécutez des campagnes de messagerie par lots et planifiées à l’aide de Adobe Experience Platform en tant que hub central pour les profils et la segmentation des clients.

## Cas d’utilisation

* Campagnes par courriel planifiées
* Campagnes d’intégration et de marketing de relance

## Applications

* Adobe Experience Platform
* Adobe Campaign Classic ou Standard

## Modèles d’intégration

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## Architecture

<img src="assets/aepbatch.svg" alt="Architecture de référence pour le scénario de messagerie par lots et de Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Gardiens

* Prend uniquement en charge les déploiements d&#39;une seule unité d&#39;organisation Campaign
* Campaign est une source de vérité pour tous les profils principaux, ce qui signifie que les profils doivent exister dans Campaign et que les nouveaux profils ne doivent pas être créés sur la base de segments Experience Platform.
* La concrétisation de l’appartenance à un segment par l’Experience Platform est latente pour le traitement par lot (1 par jour) et la diffusion en continu (environ 5 minutes).

**Partage de segments de la plateforme de données clientes en temps réel sur la campagne :**

* Recommandation d&#39;une limite de 20 segments
* L&#39;Activation est limitée à toutes les 24 heures.
* Seuls les attributs de schéma d’union disponibles pour l’activation (aucune prise en charge des événements de baie/cartes/expériences).
* Recommandation d’un maximum de 20 attributs par segment
* Un fichier par segment de tous les profils avec une appartenance de segment &quot;réalisée&quot; OU si l&#39;appartenance de segment est ajoutée en tant qu&#39;attribut dans le fichier à la fois profils &quot;réalisée&quot; et &quot;sortie&quot;
* Les exportations incrémentielles ou complètes de segments sont prises en charge
* Le chiffrement de fichier n&#39;est pas pris en charge
* Workflows d&#39;exportation Campaign à exécuter toutes les 4 heures au maximum
* Voir [Gardiens pour l&#39;Experience Platform pour l&#39;assimilation des profils et des données](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Etapes de mise en oeuvre

### Adobe Experience Platform

#### Schéma / Jeu de données

1. Configurez des schémas individuels de profil, de événement d’expérience et de plusieurs entités dans l’Experience Platform, en fonction des données fournies par le client.
1. Créez des schémas Campaign pour wideLog, trackingLog, les adresses non livrables et les préférences de profil (facultatif).
1. Ajoutez des étiquettes d’utilisation des données au jeu de données pour la gouvernance.
1. Créez des stratégies qui appliquent la gouvernance sur les destinations.

#### Profil / Identité

1. Créez des espaces de nommage spécifiques au client.
1. Ajouter des identités aux schémas.
1. Activez les schémas et les jeux de données pour le profil.
1. Configurez des règles de fusion pour les différentes vues du Profil client en temps réel (facultatif).
1. Créez des segments pour l’utilisation de la campagne.

#### Sources / Destinations

1. Envoi de données dans l’Experience Platform à l’aide d’API de diffusion en continu et de connecteurs source.
1. Configurez la destination de l&#39;enregistrement blob [!DNL Azure] à utiliser avec Campaign.

#### Déploiement d’applications mobiles

1. Mise en oeuvre du SDK Campaign pour le SDK Campaign Classic ou Experience Platform pour le Campaign Standard. Si l’Experience Platform Launch est présent, il est recommandé d’utiliser l’extension Campaign Classic/Standard avec le SDK Experience Platform.

#### Campaign

1. Configurez des schémas pour le profil, les données de recherche et les données de personnalisation des diffusions pertinentes.

>[!IMPORTANT]
>
>Il est essentiel de comprendre à ce stade quel est le modèle de données dans l&#39;Experience Platform pour les données de profil et de événement afin que vous sachiez quelles données seront nécessaires à Campaign.

#### Importer des workflows

1. Chargez et assimilez des données de profil simplifiées sur Campaign sFTP.
1. Chargez et assimilez les données d’orchestration et de personnalisation des messages sur Campaign sFTP.
1. Insérez des segments Experience Platform à partir de l&#39;objet blob [!DNL Azure] via des workflows.

#### Workflows d’exportation

1. Renvoyez les journaux Campaign à l’Experience Platform par workflows toutes les quatre heures (largeLog, trackingLog, adresses non livrables).
1. Renvoyer les préférences de profil à l’Experience Platform par l’intermédiaire de workflows conçus pour la consultation toutes les quatre heures (facultatif).


## Documentation connexe

* [Documentation de Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Documentation Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Documentation Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentation Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Documentation du SDK Experience Platform Mobile](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
