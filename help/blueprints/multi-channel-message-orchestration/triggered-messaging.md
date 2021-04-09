---
title: Messagerie déclenchée et plan directeur Adobe Experience Platform
description: Exécutez les messages et expériences déclenchés en utilisant Adobe Experience Platform comme centre central de diffusion en continu des données, profils client et segmentation.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 2404d871a852df8fed3adb97a79cc15e994db762
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 1%

---

# Messagerie déclenchée et plan directeur Adobe Experience Platform

Exécutez les messages et expériences déclenchés en utilisant Adobe Experience Platform comme centre central de diffusion en continu des données, profils client et segmentation.

## Cas d’utilisation

* Messages déclenchés
* Confirmation d&#39;enregistrement
* Abandons du panier et du formulaire de demande
* Messages déclenchés par l&#39;emplacement

## Architecture

<img src="assets/triggered.svg" alt="Architecture de référence pour le scénario Messagerie déclenchée et Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Modèles d’intégration

* Adobe Experience Platform -> Journey Orchestration

## Conditions préalables

* Adobe Experience Platform
* Journey Orchestration

## Gardiens

### Journey Orchestration

* Voir le lien pour [plus de détails sur les limitations](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en#starting-with-journeys)
* Le plafonnement est disponible par le biais de la configuration de l’API pour s’assurer que le système de destination n’est pas saturé au point d’échec. Le plafonnement signifie que les messages qui dépassent le plafond sont complètement ignorés et ne sont jamais envoyés. Le ralentissement n’est toujours pas pris en charge.
   * connexions max : Nombre maximal de connexions http/s qu&#39;une destination peut gérer
   * nombre maximal d&#39;appels : Nombre maximal d&#39;appels à effectuer dans le paramètre periodInMs
   * periodInMs : Temps en millisecondes
* Les parcours d’appartenance à un segment initiés peuvent fonctionner en deux modes :
   * segments de lot (actualisés toutes les 24 heures)
   * Segments de diffusion en flux continu (&lt;qualification de 5 minutes)
* Segments de lot : Veillez à comprendre le volume quotidien des utilisateurs qualifiés et à ce que le système de destination puisse gérer le débit d&#39;éclatement par parcours et sur tous les parcours.
* Segments de diffusion en continu : Veiller à ce que l&#39;éclatement initial des qualifications de profil puisse être traité avec le volume de qualification de diffusion en continu quotidien par parcours et sur tous les parcours
* La destination finale doit prendre en charge l’API REST et la charge utile JSON
* Ne prend pas actuellement en charge l&#39;Offer decisioning
* Voir [Gardiens pour l&#39;Experience Platform pour l&#39;assimilation des profils et des données](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

### Campaign Standard

* Ne peut prendre en charge que 14 tps (50 k/h) de débit
* Les parcours lancés par l’appartenance à un segment ne sont pas pris en charge
* Les événements de réaction aux messages transactionnels ouverts/clics sont pris en charge dans Journey Orchestration.
* Actuellement, les journaux de messagerie transactionnelle ne sont pas synchronisés en mode natif avec l&#39;Experience Platform, ce qui nécessite une configuration manuelle. Il est recommandé d’exporter les journaux au plus toutes les quatre heures.


## Etapes de mise en oeuvre

### Adobe Experience Platform

#### Schéma/jeux de données

1. Configurez des schémas individuels de profil, de événement d’expérience et de plusieurs entités dans l’Experience Platform en fonction des données fournies par le client.
1. Créez des schémas Campaign pour les éléments suivants : wideLog, trackingLog, adresses non livrables et préférences de profil (facultatif).
1. Ajoutez des étiquettes d’utilisation des données au jeu de données pour la gouvernance.
1. Créez des stratégies pour appliquer la gouvernance sur les destinations.

#### Profil/identité

1. Créez des espaces de nommage spécifiques au client.
1. Ajouter des identités aux schémas.
1. Activez les schémas et les jeux de données pour le profil.
1. Configurez des règles de fusion pour les différentes vues de [!UICONTROL Profil client en temps réel] (facultatif).
1. Créez des segments pour l’utilisation de la campagne.

#### Sources/Destinations

1. Envoi de données dans l’Experience Platform à l’aide d’API de diffusion en continu et de connecteurs source.
1. Configurez la destination de l&#39;enregistrement blob [!DNL Azure] à utiliser avec Campaign.

#### Déploiement d’applications mobiles

1. Mise en oeuvre du SDK Campaign pour le SDK Campaign Classic ou Experience Platform pour le Campaign Standard. Si l’Experience Platform Launch est présent, il est recommandé d’utiliser l’extension Campaign Classic/Standard avec le SDK Experience Platform.


### Journey Orchestration

1. Les données de diffusion en continu utilisées pour lancer un parcours client doivent d’abord être configurées dans le Journey Orchestration pour obtenir un ID d’orchestration. Cet ID d’orchestration est ensuite fourni au développeur pour l’utiliser avec l’assimilation.
1. Configurez des sources de données externes.
1. Configurez des actions personnalisées.

### Campaign Standard

1. Configurez les modèles de messagerie avec les paramètres de personnalisation appropriés.
1. Configurez les journaux de messagerie transactionnelle d’exportation des workflows. La recommandation est d&#39;exécuter au plus toutes les quatre heures.


## Documentation connexe

* [Documentation de Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Documentation Journey Orchestration](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=en)
* [Documentation Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Documentation Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentation Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Documentation du SDK Experience Platform Mobile](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
