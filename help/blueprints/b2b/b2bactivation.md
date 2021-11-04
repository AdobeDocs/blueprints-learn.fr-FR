---
title: Activation B2B
description: Diffusez des audiences basées sur des comptes et des expériences client axées sur les profils avec Real-time Customer Data Platform ​.
solution: Experience Platform, Real-time Customer Data Platform
kt: 9311
exl-id: null
source-git-commit: d811d82418d477372caa9e5b0b67af197275d459
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 5%

---

# Audience B2B et activation de profil

Utilisez les informations de compte, d’opportunité et de prospect liées à un client individuel pour créer des profils b2b exploitables afin d’améliorer la personnalisation et le ciblage sur l’ensemble des canaux.

## Cas d’utilisation

* Créez des audiences de personnes pour le ciblage et la personnalisation sur plusieurs canaux par rapport aux données B2B, y compris des comptes, des opportunités et des pistes.
* Activez les audiences vers n’importe quelle destination Experience Platform pour le ciblage et la personnalisation.

## Applications

* Real-time Customer Data Platform Édition B2B

## Modèles d’intégration

* Sources de données B2B (Marketo, Salesforce, etc.) -> Real-time Customer Data Platform Édition B2B -> Destinations Diverses sources de données B2B peuvent être utilisées pour mapper les données de compte, de prospect, d’opportunité et de personne à l’édition B2B de Real-time Customer Data Platform.

## Architecture

<img src="assets/b2b-activation.svg" alt="Architecture de référence du plan directeur d’activation B2B" style="border:1px solid #4a4a4a" />
<br>

## Garde-fous

Notez que les barrières de sécurité et les étapes de mise en oeuvre liées au Marketo Engage ne sont pertinentes que lorsque Marketo Engage est utilisé comme source et/ou destination.

### Prise en charge de plusieurs instances et de l’organisation IMS :

Le tableau suivant décrit les modèles pris en charge pour mapper les instances Experience Platform et Marketo Engage.

#### Marketo comme source de données à Experience Platform :

* Plusieurs instances de Marketo Engage sur une instance d’Experience Platform sont prises en charge.
* Plusieurs instances de Marketo Engage à de nombreuses instances d’Experience Platform ne sont pas prises en charge.
* Une instance de Marketo Engage pour de nombreuses instances d’Experience Platform n’est pas prise en charge.
* Une instance de Marketo Engage à une instance d’Experience Platform et plusieurs environnements de test sont pris en charge.

#### Marketo comme destination de l’Experience Platform :

* Experience Platform à de nombreuses instances de Marketo Engage est pris en charge
* De nombreuses instances d’Experience Platform vers une instance de Marketo Engage sont prises en charge

#### Barrières de sécurité de la segmentation et du profil Experience Platform :

* Voir les garde-fous de profil et de segmentation pour les Experience Platform - [Instructions de profil et de segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* Les segments B2B qui incluent des comptes, des prospects et des opportunités utilisent des relations multi-entités, ce qui fait que l’évaluation des segments devient un lot. La segmentation par flux est prise en charge pour les segments qui sont limités aux personnes et aux événements.

#### Experience Platform - Marketo Engage Source Connector :

* Le renvoi historique peut prendre jusqu’à 7 jours, selon le volume de données.
* Les mises à jour et les modifications continues des données depuis Marketo sont envoyées à Experience Platform via l’API de diffusion en continu, qui peut durer jusqu’à 5 minutes environ pour le profil, et environ 15 minutes au lac de données selon le volume.

#### Experience Platform - Marketo Destination Connector :

* Le partage de segments en flux continu de Real-time Customer Data Platform vers Marketo Engage peut prendre jusqu’à 5 minutes.
* La segmentation par lots est partagée une fois par jour selon le planning de segmentation Experience Platform. Les segments B2B qui incluent des comptes, des prospects et des opportunités utilisent des relations multi-entités, ce qui entraîne le traitement par lot du segment.

#### Barrières de sécurité du Marketo Engage :

* Les contacts et les pistes doivent être ingérés et définis directement dans Marketo Engage pour que l’audience Real-time Customer Data Platform corresponde à un contact et à un prospect Marketo Engage.

#### Barrières de sécurité des destinations

* Reportez-vous à la documentation de destination pour obtenir des instructions spécifiques sur les destinations. [Instructions de destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en)


## Étapes d’implémentation

Pour plus d’informations sur la mise en oeuvre et la configuration de l’édition B2B de Real-time Customer Data Platform, voir l’édition B2B de la documentation de Real-time Customer Data Platform. [Édition B2B de Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

Il existe deux modèles de mise en oeuvre possibles. La possibilité d’ingérer des données B2B et des profils à partir de Marketo Engage ou la possibilité d’ingérer des données B2B à partir d’autres sources de données CRM.

## Considérations de mise en œuvre

Conseils sur les principales considérations et configurations du plan directeur.

* Intégration CRM avec et sans Marketo : Si l’implémentation utilise Marketo Engage comme source et que Marketo Engage est connecté au CRM, utilisez le connecteur source Marketo dans Experience Platform pour ingérer les données CRM dans Experience Platform. Utilisez le connecteur source Experience Platform si des tables supplémentaires doivent être ingérées. Si l’implémentation n’utilise pas Marketo Engage comme source, connectez la source CRM directement à AEP à l’aide du connecteur de l’Experience Platform source CRM.
* Il n’est pas recommandé de lancer des pistes et de prendre en charge l’édition B2B de Real-time Customer Data Platform uniquement. Pour ce cas pratique, il est recommandé d’utiliser un outil de préparation des pistes (tel que Marketo Engage).
* Le connecteur de destination du Marketo Engage pour AEP qui envoie des audiences à Marketo Engage pour activation, envoie uniquement des adresses électroniques et des ECID. Il ne crée pas de piste si le contact n’existe pas déjà. Il est donc nécessaire d’ingérer le profil et les données de piste dans Marketo Engage.

## Documentation connexe

* [Édition B2B de Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=en)
* [Adobe Experience Platform - Connecteur source Marketo](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=fr)
* [Adobe Experience Platform - Connecteur de destination Marketo](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=en)