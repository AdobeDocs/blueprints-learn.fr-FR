---
title: Messagerie déclenchée et plan directeur Adobe Experience Platform
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 37416aafc997838888edec2658d2621d20839f94
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 81%

---

# Messagerie déclenchée et plan directeur Adobe Experience Platform

Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.

## Cas d’utilisation

* Messages déclenchés
* Confirmations d’enregistrement
* Abandon de panier et de formulaire de demande
* Messages déclenchés par l’emplacement

## Architecture

<img src="assets/triggered.svg" alt="Architecture de référence pour le schéma de messagerie et de Adobe Experience Platform déclenchés" style="border:1px solid #4a4a4a" />

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

1. Configurez des profils individuels, des événements d’expérience et des schémas multi-entités dans Experience Platform en fonction des données fournies par le client.
1. Créez des schémas Adobe Campaign pour les éléments suivants : wideLog, trackingLog, adresses non livrables et préférences de profil (facultatif).
1. Ajoutez des étiquettes d’utilisation des données au jeu de données pour la gouvernance.
1. Créez des stratégies pour appliquer la gouvernance sur les destinations.

#### Profil / identité

1. Créez des espaces de noms spécifiques au client.
1. Ajoutez des identités aux schémas.
1. Activez les schémas et les jeux de données pour le profil.
1. Configurez des règles de fusion pour les différentes vues de [!UICONTROL Profil client en temps réel] (facultatif).
1. Créez des segments pour l’utilisation de Adobe Campaign.

#### Sources / destinations

1. Ingérez des données dans Experience Platform à l’aide d’API de diffusion en continu et de connecteurs source.
1. Configurez la destination de l&#39;enregistrement blob [!DNL Azure] à utiliser avec Adobe Campaign.

#### Déploiement d’applications mobiles

1. Mise en oeuvre du SDK Adobe Campaign pour Adobe Campaign Classic ou du SDK Experience Platform pour Adobe Campaign Standard. Si l’Experience Platform Launch est présent, il est recommandé d’utiliser l’extension Adobe Campaign Classic ou Adobe Campaign Standard avec le SDK Experience Platform.


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
* [Documentation de Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=fr)
* [Documentation Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=fr)
* [Documentation pour Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=fr)
* [Documentation pour le SDK mobile d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
