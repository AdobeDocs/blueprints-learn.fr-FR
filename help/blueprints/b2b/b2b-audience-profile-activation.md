---
title: Activation des audiences et des profils B2B
description: Diffusez des audiences basées sur un compte et des personnes avec Real-Time Customer Data Platform B2B edition pour l’activation sur plusieurs canaux et destinations.
solution: Real-Time Customer Data Platform
source-git-commit: 7f0b624616480cf563142c08eb0598d1dd55d551
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 5%
---

# Activation des audiences et des profils B2B

Utilisez **Real-Time Customer Data Platform B2B edition** pour rassembler les données de compte, d’opportunité et de personne dans des profils B2B unifiés, puis activez les audiences de personnes et les audiences de compte sur des destinations telles que LinkedIn, Marketo Engage et le stockage dans le cloud. Ce plan directeur décrit comment concevoir des schémas B2B, créer des audiences à entités multiples et les exporter pour les activer sur plusieurs canaux et destinations, ainsi que pour l’orchestration et l’analyse dans des applications telles que **Journey Optimizer B2B edition** et **Customer Journey Analytics B2B edition**.

## Cas d’utilisation

- Créez des audiences de personnes pour le ciblage et la personnalisation sur plusieurs canaux en fonction des données B2B, y compris les comptes, les opportunités et les prospects.
- Créez des audiences d’entités multiples qui combinent des attributs au niveau du compte et de l’opportunité avec un comportement au niveau de la personne en utilisant une approche **segment-de-segments** (par exemple, « Personnes qui ont visité la page de tarification au cours des 3 derniers jours et qui sont des décideurs dans les opportunités à l’étape X pour les comptes du secteur Y »).
- Activez les audiences de personnes et de comptes vers des destinations d’Experience Platform et de stockage dans le cloud, telles que Marketo Engage, les audiences correspondantes LinkedIn, le ciblage par correspondance des clients Google, DV360, The Trade Desk, Amazon Ads, Bombora et Demandbase, pour le ciblage, la personnalisation, la sensibilisation des ventes et les analyses.

## Applications

- Real-Time Customer Data Platform B2B edition
- (Facultatif) **Customer Journey Analytics B2B edition**
- (Facultatif) **Journey Optimizer B2B edition**

## Modèles d’intégration

Les modèles d’intégration B2B standard pour ce plan directeur incluent :

- **Engagement B2B et sources CRM → destinations de → B2B de RTCDP**

  L’engagement B2B et les systèmes CRM tels que Marketo Engage, Salesforce et Microsoft Dynamics envoient des prospects/contacts, des comptes et des opportunités dans **Real-Time CDP B2B edition** à l’aide des schémas B2B standard. À partir de là, les audiences de personnes et de comptes sont activées vers les destinations, notamment :

  - Marketo Engage
  - Audiences appariées LinkedIn / LinkedIn
  - Correspondance client et DV360 Google
  - Le Trade Desk
  - Amazon Ads
  - Trade Desk CRM, Criteo, Bing et d’autres plateformes publicitaires
  - Destinations de stockage dans le cloud telles qu’Amazon S3, ADLS et Snowflake pour une utilisation en aval

- Sources d’intention et d’événement **B2B → audiences → destinations de → B2B de RTCDP**

  Sources d’intention et d’événement B2B telles que l’intention de Bombora, l’intention de Demandbase, PathFactory et RainFocus diffusent les événements d’intention et d’engagement dans le B2B de RTCDP. Ces événements sont mappés à des schémas B2B standard et utilisés pour créer des audiences de comptes et d’utilisateurs qui peuvent être activées vers des destinations publicitaires et marketing.

Plusieurs sources de données B2B peuvent être utilisées pour mapper les données de compte, de prospect, d’opportunité et de personne au B2B edition de Real-Time Customer Data Platform à l’aide des schémas et des relations **B2B** standard.

## Architecture

<img src="assets/b2b-audience-profile-activation.png" alt="Architecture de référence pour le plan directeur de l’activation des audiences et des profils B2B" style="border:1px solid #4a4a4a"  width="100%" />

## Garde-fous

Reportez-vous aux mécanismes de sécurisation et à la documentation d’éligibilité suivants lors de la conception d’audiences et de profils B2B :

- [Mécanismes de sécurisation pour Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Cas d’utilisation de segmentation pour Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/segmentation/b2b)
- [Mécanismes de sécurisation des profils et de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mise à jour des critères d’éligibilité de la segmentation en flux continu](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/eligibility-criteria-update)

### Prise en charge de plusieurs instances et de l’organisation IMS

Le tableau suivant décrit les modèles pris en charge pour mapper les instances Experience Platform et Marketo Engage.

#### Marketo en tant que source de données pour Experience Platform

- Plusieurs instances Marketo Engage vers une instance Experience Platform sont prises en charge.
- Non prise en charge d’une instance de Marketo Engage vers de nombreuses instances d’Experience Platform.
- Prise en charge d’une instance de Marketo Engage vers une instance d’Experience Platform et plusieurs sandbox.

#### Marketo comme destination vers Experience Platform

- Experience Platform est pris en charge sur de nombreuses instances Marketo Engage.
- De nombreuses instances Experience Platform vers une instance Marketo Engage sont prises en charge.

#### Mécanismes de sécurisation du profil et de la segmentation Experience Platform

Consultez les mécanismes de sécurisation du profil et de la segmentation Experience Platform ici : [Mécanismes de sécurisation des profils et de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails).

Les segments qui incluent des entités B2B telles que des comptes, des prospects ou des opportunités reposent sur des relations à entités multiples et sont évalués dans **lot**. En revanche, la **segmentation en flux continu** est prise en charge pour les audiences limitées à des personnes et des événements qui n’incorporent pas d’entités B2B. Pour les scénarios d’activation B2B en temps quasi réel, pensez à utiliser des audiences B2B évaluées par lots comme entrées pour les audiences en flux continu ou Edge, lorsque cela est pris en charge.

#### Experience Platform - Connecteur Marketo Engage Source

- Consultez la documentation [ici](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

#### Experience Platform - Connecteur de destination Marketo

- Consultez la documentation [ici](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage-connection).

#### Garde-fous de destination

- Reportez-vous à la documentation sur la destination pour obtenir des conseils spécifiques sur chaque destination : [Mécanismes de sécurisation de destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails).
- Pour les destinations publicitaires telles que Facebook, Google Customer Match &amp; DV360, Microsoft Bing, The Trade Desk, Amazon Ads, Bombora, Demandbase, etc., assurez-vous que les identifiants que vous choisissez dans votre schéma et votre stratégie d’identité (e-mail, ID de publicité mobile, champs d’adresse, ID de compte) s’alignent sur les fonctionnalités de mappage et les identités prises en charge pour ces destinations.

## Étapes de mise en œuvre

Pour obtenir des conseils sur l’implémentation et la configuration du B2B edition de Real-Time Customer Data Platform, consultez la documentation de Real-Time CDP B2B edition : [B2B edition de Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview).

Deux schémas d’implémentation sont courants :

- Ingérez des données et des profils B2B à partir de Marketo Engage (et de son CRM connecté) dans RTCDP B2B edition.
- Ingérez des données B2B directement à partir de systèmes CRM ou d’autres systèmes B2B dans RTCDP B2B edition à l’aide des connecteurs source appropriés.

Dans le cadre des mises à niveau de l’architecture B2B de RTCDP, certains modèles précédemment utilisés sont désormais obsolètes pour les entités B2B. Pour plus d’informations, consultez la documentation détaillée [ici](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade).

## Considérations relatives à la mise en œuvre

Recommandations sur les principales considérations et configurations du plan directeur.

- **Intégration de CRM avec et sans Marketo**

  - Si l’implémentation utilise Marketo Engage comme source et que Marketo Engage est connecté au CRM, les données du CRM synchronisées dans Marketo (par exemple, leads/contacts, comptes, opportunités) seront transmises à RTCDP B2B edition via le connecteur source Marketo.
  - Si d’autres tables ou attributs CRM ne sont pas transmis par Marketo (par exemple, des objets personnalisés ou des champs supplémentaires), connectez directement la source CRM à Experience Platform à l’aide des connecteurs source CRM et mappez ces tables aux schémas et relations B2B standard.
  - Concevez l’ingestion CRM + Marketo ensemble pour éviter les représentations en double ou conflictuelles des entités B2B dans RTCDP B2B et vous assurer que toutes les entités B2B sont conformes aux schémas standard.

## Documentation connexe

- [B2B edition de Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
- [Prise en main de Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en)
- [Mécanismes de sécurisation pour Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Schémas dans Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Mises à niveau de l’architecture vers Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform)
- [Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)
- [Adobe Experience Platform - Connecteur Marketo Source](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Adobe Experience Platform - Connecteur de destination Marketo](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-platform-segment-to-a-marketo-static-list)
- [Garde-fous de destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
