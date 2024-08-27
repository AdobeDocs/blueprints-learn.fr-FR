---
title: Plan directeur de l’activation de profil et de l’audience B2B
description: Proposez des audiences basées sur les comptes et des expériences client centrées sur les profils grâce à Real-time Customer Data Platform.
solution: Real-Time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: 3dfdb1a237995e7f17e280e24f8865e992d9eb5f
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 52%

---

# Plan directeur de l’activation de profil et de l’audience B2B

Utilisez les informations de compte, d’opportunités et de prospects liées à un client individuel pour créer des profils B2B exploitables afin d’améliorer la personnalisation et le ciblage sur l’ensemble des canaux.

## Cas d’utilisation

* Créez des audiences de personnes pour le ciblage et la personnalisation sur plusieurs canaux liées aux données B2B, parmi lesquelles des informations de comptes, d’opportunités et de prospects.
* Activez les audiences vers n’importe quelle destination Experience Platform à des fins de ciblage et de personnalisation.
* Créez des audiences de comptes (par exemple, des listes d’entreprises) et ciblez ces sociétés par le biais de destinations comme LinkedIn qui acceptent des listes d’entreprises en tant qu’entrée ou exportent vers des destinations de stockage dans le cloud pour un ciblage et une diffusion commerciale.

## Applications

* Édition B2B Real-time Customer Data Platform

## Modèles d’intégration

* Sources de données B2B (Marketo, Salesforce, etc.) -> Real-time Customer Data Platform Édition B2B -> Destinations
* Diverses sources de données B2B peuvent être utilisées pour mapper des données de compte, de prospect, d’opportunité et de personne à l’édition B2B de Real-time Customer Data Platform.

## Architecture

![Architecture de référence du plan directeur d’activation B2B](assets/b2b-activation.png)

## Garde-fous

* Notez que les garde-fous de sécurité et les étapes de mise en œuvre liées à Marketo Engage ne sont pertinentes que lorsque Marketo Engage est utilisé comme source ou comme destination.

* Pour plus d’informations et de garde-fous sur le modèle de données, la taille et la segmentation, reportez-vous au [document sur les garde-fous de déploiement](../experience-platform/deployment/guardrails.md)


### Prise en charge de plusieurs instances et de l’organisation IMS :

Le tableau suivant décrit les modèles pris en charge pour mapper les instances Experience Platform et Marketo Engage.

#### Marketo en tant que source de données à destination d’Experience Platform :

* Prise en charge de plusieurs instances de Marketo Engage vers une instance d’Experience Platform.
* Non prise en charge d’une instance de Marketo Engage vers de nombreuses instances d’Experience Platform.
* Prise en charge d’une instance de Marketo Engage vers une instance d’Experience Platform et plusieurs sandbox.

#### Marketo en tant que destination vers Experience Platform :

* Prise en charge d’Experience Platform vers de nombreuses instances de Marketo Engage
* Prise en charge de nombreuses instances d’Experience Platform vers une instance de Marketo Engage

#### Garde-fous de segmentation et de profil Experience Platform :

* Consultez les garde-fous de profil et de segmentation pour Experience Platform - [Garde-fous de profil et de segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* Les segments B2B qui incluent des comptes, des prospects et des opportunités utilisent des relations multi-entités, ce qui fait que l’évaluation des segments est gérée par lot. La segmentation par flux est prise en charge pour les segments limités aux personnes et aux événements.
* Inclure un segment b2b par lot en tant qu’entrée d’un segment en continu ou en périphérie pour prendre en charge les cas d’utilisation de segments b2b par flux. L’adhésion au segment par lot est basée sur le dernier résultat d’évaluation quotidien de la segmentation par lots.

#### Experience Platform - Connecteur source Marketo Engage :

* Le renvoi historique peut prendre jusqu’à 7 jours, selon le volume de données.
* Les mises à jour et modifications continues des données depuis Marketo sont envoyées à Experience Platform via l’API de diffusion en continu, qui peut prendre jusqu’à 10 minutes de retard au profil et peut prendre jusqu’à 60 minutes au lac de données en fonction du volume.

#### Experience Platform - Connecteur de destination Marketo :

* Le partage de segments en flux continu de Real-time Customer Data Platform vers Marketo Engage peut prendre jusqu’à 15 minutes. Le renvoi des profils qui existaient déjà dans le segment avant l’activation pour la première fois peut prendre jusqu’à 24 heures.
* La segmentation par lots est partagée une fois par jour selon le planning de segmentation d’Experience Platform. Les segments B2B qui utilisent des relations multi-entités, par exemple, les segments qui utilisent des données dans les objets de compte et d’opportunité, sont toujours exécutés en mode batch.

#### Garde-fous Marketo Engage :

* Les contacts et les prospects doivent être ingérés et définis directement dans Marketo Engage pour que l’audience Real-time Customer Data Platform corresponde à un contact et à un prospect Marketo Engage.
* La destination Marketo RTCDP peut éventuellement créer de nouvelles pistes dans Marketo pour les clients qui se trouvent dans un segment mais qui n’existent pas dans Marketo.

#### Garde-fous de destination

* Reportez-vous à la documentation de destination pour obtenir des instructions spécifiques sur celles-ci. [Garde-fous de destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=fr)


## Étapes de mise en œuvre

Pour plus d’informations sur la mise en œuvre et la configuration de l’édition B2B de Real-time Customer Data Platform, consultez l’édition B2B de la documentation de Real-time Customer Data Platform. [Édition B2B de Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=fr)

Il existe deux modèles de mise en œuvre possibles. La possibilité d’ingérer des données B2B et des profils à partir de Marketo Engage ou la possibilité d’ingérer des données B2B à partir d’autres sources de données CRM.

## Considérations relatives à la mise en œuvre

Recommandations sur les principales considérations et configurations du plan directeur.

* Intégration CRM avec et sans Marketo :
Si l’implémentation utilise Marketo Engage comme source et que le Marketo Engage est connecté au CRM, les données du CRM passent automatiquement par la même connexion, supprimant la nécessité de connecter directement le CRM à Platform, à moins qu’il n’y ait d’autres objets de données CRM qui ne soient pas transmis par Marketo. Utilisez le connecteur source Experience Platform si des tableaux supplémentaires doivent être ingérés. Si l’implémentation n’utilise pas Marketo Engage comme source, connectez la source CRM directement à Platform à l’aide du connecteur de l’Experience Platform source CRM.
* Le connecteur de destination du Marketo Engage pour Platform, qui envoie les audiences vers Marketo Engage pour activation, partage les membres de l’audience en fonction des adresses électroniques et des ECID correspondants. Il a la possibilité de créer un prospect si le contact n&#39;existe pas déjà. Lors de la création d’une piste, jusqu’à 50 attributs de profil (attributs de tableau ou de mappage) dans Real-time Customer Data Platform peuvent être mappés aux champs Personne dans Marketo.

## Documentation connexe

* [Édition B2B de Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=fr)
* [Prise en main de Real-time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [Barrières de sécurité pour Real-time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html)
* [Adobe Experience Platform - Connecteur source Marketo](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=fr)
* [Adobe Experience Platform - Connecteur de destination Marketo](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html)
