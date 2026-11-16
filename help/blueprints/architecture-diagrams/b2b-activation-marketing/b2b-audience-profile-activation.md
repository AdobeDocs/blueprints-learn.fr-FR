---
title: Activation des audiences et des profils B2B
description: Diffusez des audiences basées sur un compte et des personnes avec Real-Time Customer Data Platform B2B edition pour l’activation sur plusieurs canaux et destinations.
solution: Real-Time Customer Data Platform
product_v2:
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
source-git-commit: ea991411ae0339bb4a1a36ac994fa76097d37307
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 4%
---

# Activation des audiences et des profils B2B

Utilisez **Real-Time Customer Data Platform B2B edition** pour rassembler les données de compte, d’opportunité et de personne dans des profils B2B unifiés, puis activez les audiences de personnes et les audiences de compte sur des destinations telles que LinkedIn, Marketo Engage et le stockage dans le cloud. Ce plan directeur décrit comment concevoir des schémas B2B, créer des audiences à entités multiples et les exporter pour les activer sur plusieurs canaux et destinations, ainsi que pour l’orchestration et l’analyse dans des applications telles que **Journey Optimizer B2B Edition** et **Customer Journey Analytics B2B edition**.

## Cas d’utilisation

- Créez des audiences de personnes pour le ciblage et la personnalisation sur plusieurs canaux en fonction des données B2B, y compris les comptes, les opportunités et les prospects.
- Créez des audiences d’entités multiples qui combinent des attributs au niveau du compte et de l’opportunité avec un comportement au niveau de la personne en utilisant une approche de **segment de segments** (par exemple, « Personnes qui ont visité la page de tarification au cours des 3 derniers jours et qui sont des décideurs dans les opportunités à l’étape X pour les comptes du secteur Y »).
- Activez les audiences de personnes vers des destinations Experience Platform prises en charge pour le ciblage et la personnalisation, et les audiences de comptes vers des destinations publicitaires et de stockage dans le cloud prises en charge pour le ciblage, la portée des ventes et l’analyse. La prise en charge de la destination diffère selon le type d’audience. Consultez [Destinations d’audience de compte](#account-audience-destinations) pour l’activation du compte.

### Cas d’utilisation basés sur des comptes

- **Combler les lacunes du groupe d&#39;achat :** Créer une audience de comptes sans contacts dans des rôles tels que CMO ou CIO. Activez-le vers les audiences correspondantes LinkedIn ou une autre destination publicitaire prise en charge, puis utilisez le ciblage par fonction/titre de la destination pour atteindre de nouveaux contacts dans ces rôles.
- **Vendre à des prix supérieurs ou croisés à d’autres divisions d’un client existant :** Créez une audience de compte qui a acheté le produit X il y a entre 3 et 9 mois, mais qui ne possède pas encore le produit Y. Activez-la vers des destinations publicitaires prises en charge ou exportez-la vers le stockage dans le cloud pour les ventes et la sensibilisation marketing.
- **Entreprises cibles utilisant des produits concurrents :** Utilisez les données de partenaire ou d&#39;intention pour identifier les comptes utilisant le produit d&#39;un concurrent, même si aucun contact n&#39;est connu. Activez l’audience du compte vers les destinations publicitaires prises en charge pour atteindre les contacts de ces sociétés.

## Applications

- Real-Time Customer Data Platform B2B edition
- (Facultatif) **Customer Journey Analytics B2B edition**
- (Facultatif) **Journey Optimizer B2B Edition**

## Modèles d’intégration

Les modèles d’intégration B2B standard pour ce plan directeur incluent :

- **Engagement B2B et sources CRM → destinations de → B2B RTCDP**

  L’engagement B2B et les systèmes CRM tels que Marketo Engage, Salesforce et Microsoft Dynamics envoient des prospects/contacts, des comptes et des opportunités dans **Real-Time CDP B2B edition** à l’aide des schémas et des relations B2B standard. À partir de là, les audiences de personnes sont activées vers les destinations prises en charge, notamment :

  - Marketo Engage
  - Audiences appariées LinkedIn / LinkedIn
  - Correspondance client et DV360 Google
  - Le Trade Desk
  - Amazon Ads
  - Trade Desk CRM, Criteo, Bing et d’autres plateformes publicitaires
  - Destinations de stockage dans le cloud telles qu’Amazon S3, ADLS et Snowflake pour une utilisation en aval

  Les audiences de compte utilisent le même modèle de données B2B unifié et sont activées séparément pour les destinations publicitaires et de fichiers prises en charge répertoriées sous [Destinations d’audience de compte](#account-audience-destinations).

- **Sources d’intention et d’événement B2B → → audiences → destinations RTCDP B2B**

  Sources d’intention et d’événement B2B telles que l’intention de Bombora, l’intention de Demandbase, PathFactory et RainFocus diffusent les événements d’intention et d’engagement dans le B2B de RTCDP. Ces événements sont mappés à des schémas B2B standard et utilisés pour créer des audiences de comptes et d’utilisateurs qui peuvent être activées vers des destinations publicitaires et marketing. Par exemple, les comptes montrant l’intention sur des sujets concurrents peuvent être activés vers des destinations de compte prises en charge telles que Bombora et Demandbase.

Plusieurs sources de données B2B peuvent être utilisées pour mapper les données de compte, de prospect, d’opportunité et de personne au B2B edition de Real-Time Customer Data Platform à l’aide des **schémas et relations B2B standard**.

## Architecture

![Architecture de référence pour le plan directeur d’activation des audiences et des profils B2B](assets/b2b-audience-profile-activation.png){width="1000" zoomable="yes"}

## Destinations d’audience de compte

Les audiences de compte peuvent être activées pour les destinations publicitaires et de stockage dans le cloud suivantes :

- Audiences correspondantes LinkedIn
- Bombora
- Demandbase
- Azure Data Lake Storage Gen2
- Zone de destination des données
- SFTP
- Azure Blob
- AWS S3

Consultez la section [Activer les audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en) pour connaître les dernières destinations prises en charge et les mappages obligatoires. Les destinations personnes-audience répertoriées dans les modèles d’intégration ne prennent pas nécessairement en charge les audiences de compte.

## Garde-fous

Reportez-vous aux mécanismes de sécurisation et à la documentation d’éligibilité suivants lors de la conception d’audiences et de profils B2B :

- [Mécanismes de sécurisation pour Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [Activer les audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
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

Les segments qui incluent des entités B2B telles que des comptes, des prospects ou des opportunités reposent sur des relations à entités multiples et sont évalués dans **lot**. En revanche, la **segmentation en flux continu** est prise en charge pour les audiences limitées aux personnes et aux événements qui n’incorporent pas d’entités B2B. Pour les scénarios d’activation B2B en temps quasi réel, pensez à utiliser des audiences B2B évaluées par lots comme entrées pour les audiences en flux continu ou Edge, lorsque cela est pris en charge.

#### Experience Platform - Connecteur Marketo Engage Source

- Consultez la documentation [ici](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

#### Experience Platform - Connecteur de destination Marketo

- Consultez la documentation [ici](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage-connection).

#### Garde-fous de destination

- Consultez la documentation sur la destination pour obtenir des conseils spécifiques sur chaque destination : [Mécanismes de sécurisation des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails).
- Pour les destinations publicitaires telles que Facebook, Google Customer Match &amp; DV360, Microsoft Bing, The Trade Desk, Amazon Ads, Bombora, Demandbase, etc., assurez-vous que les identifiants que vous choisissez dans votre schéma et votre stratégie d’identité (e-mail, ID de publicité mobile, champs d’adresse, ID de compte) s’alignent sur les fonctionnalités de mappage et les identités prises en charge pour ces destinations.

## Étapes de mise en œuvre

Pour obtenir des conseils sur l’implémentation et la configuration du B2B edition du Real-Time Customer Data Platform, consultez la documentation de Real-Time CDP B2B edition : [B2B edition du Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview).

Deux schémas d’implémentation sont courants :

- Ingérez des données et des profils B2B à partir de Marketo Engage (et de son CRM connecté) dans RTCDP B2B edition.
- Ingérez des données B2B directement à partir de systèmes CRM ou d’autres systèmes B2B dans RTCDP B2B edition à l’aide des connecteurs source appropriés.

Dans le cadre des mises à niveau de l’architecture B2B de RTCDP, certains modèles précédemment utilisés sont désormais obsolètes pour les entités B2B. Pour plus de détails, consultez la documentation détaillée [ici](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade).

Pour la création et l’activation d’une audience de compte, voir :

- [Créer des audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en).
- [Activer les audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en).
- [Mappages obligatoires pour les audiences correspondantes LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en#required-mappings).

## Considérations relatives à la mise en œuvre

Recommandations sur les principales considérations et configurations du plan directeur.

- **Intégration de CRM avec et sans Marketo**

  - Si l’implémentation utilise Marketo Engage comme source et que Marketo Engage est connecté au CRM, les données du CRM synchronisées dans Marketo (par exemple, leads/contacts, comptes, opportunités) seront transmises à RTCDP B2B edition via le connecteur source Marketo.
  - Si d’autres tables ou attributs CRM ne sont pas transmis par Marketo (par exemple, des objets personnalisés ou des champs supplémentaires), connectez directement la source CRM à Experience Platform à l’aide des connecteurs source CRM et mappez ces tables aux schémas et relations B2B standard.
  - Concevez l’ingestion CRM + Marketo ensemble pour éviter les représentations en double ou conflictuelles des entités B2B dans RTCDP B2B et vous assurer que toutes les entités B2B sont conformes aux schémas standard.

- **Taille minimale de l’audience des audiences correspondantes LinkedIn**

  LinkedIn Matched Audiences requiert une taille minimale d’audience (par exemple, 300 membres correspondants). Si une audience de compte activé ne répond pas à cette exigence, élargissez la définition de l’audience pour augmenter la taille de l’audience pouvant être mise en correspondance avant de lancer une campagne. Consultez la [documentation relative à la destination LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin?lang=en) pour connaître la configuration requise actuelle.

## Documentation connexe

- [B2B edition de Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
- [Prise en main de Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en)
- [Tutoriel sur la création et l’activation d’audiences de compte](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data?lang=en)
- [Créer des audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [Activer les audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Connecteur de destination LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin?lang=en)
- [Mécanismes de sécurisation pour Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Schémas dans Real-Time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Mises à niveau de l’architecture vers Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform)
- [Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)
- [Adobe Experience Platform - Connecteur Marketo Source](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Adobe Experience Platform - Connecteur de destination Marketo](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-platform-segment-to-a-marketo-static-list)
- [Garde-fous de destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
