---
title: Intégration d’Adobe Real-Time CDP et d’Adobe Target
description: Découvrez comment les audiences Real-Time Customer Data Platform et le contexte de profil s’intègrent à Adobe Target via Edge Network.
landing-page-description: Découvrez comment les audiences Real-Time Customer Data Platform et le contexte de profil s’intègrent à Adobe Target via Edge Network.
short-description: Découvrez comment les audiences Real-Time Customer Data Platform et le contexte de profil s’intègrent à Adobe Target via Edge Network.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
    internal-label: Segmentation
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
    internal-label: Audiences
  - id: ba929a52-9339-4154-9487-317dc875a3c7
    internal-label: Use cases
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
subfeature_v2:
  - id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342
    internal-label: Segments
  - id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16
    internal-label: B2B
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
    internal-label: Audiences
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
    internal-label: at.js
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 17%
---
# Intégration d’Adobe Real-Time CDP et d’Adobe Target

Cette architecture montre comment [!DNL Real-Time Customer Data Platform] et [!DNL Adobe Target] s’intégrer via Edge Network. Il vous permet de choisir entre l’évaluation des audiences en temps réel à la périphérie et le partage d’audiences par lots ou en flux continu avec Target.

## Applications

* [!DNL Real-Time Customer Data Platform]
* [!DNL Adobe Target]
* [!DNL Experience Platform] Edge Network
* API Experience Platform Web SDK ou Edge Network Server

## Choisir une approche d’intégration

### Évaluation des audiences en temps réel à la périphérie

Utilisez cette approche lorsque [!DNL Adobe Target] avez besoin d’audiences évaluées par Edge et d’attributs de profil pour la personnalisation de la même page ou de la page suivante. Implémentez l’API Web SDK ou Edge Network Server et configurez un flux de données en activant les services [!DNL Adobe Target] et [!DNL Experience Platform].

### Partage d’audiences par lots et en flux continu vers Target

Utilisez cette approche lorsque les audiences évaluées dans [!DNL Real-Time Customer Data Platform] doivent être disponibles dans [!DNL Adobe Target] sans évaluation Edge en temps réel. Configurez la destination [!DNL Adobe Target] dans le sandbox de production par défaut. L’implémentation de l’API Web SDK ou Edge Network Server est requise uniquement pour l’évaluation Edge en temps réel ou les recherches d’espaces de noms d’identité personnalisés.

## Diagramme d’architecture

Ce diagramme montre les points d’intégration principaux entre la collecte de données, Edge Network, [!DNL Real-Time Customer Data Platform] et [!DNL Adobe Target].

![Architecture pour l’intégration de Real-Time Customer Data Platform et Adobe Target](assets/real_time_cdp_target.png){zoomable="yes"}

## Diagramme de flux de données

Cette séquence montre comment une requête client atteint Edge Network, évalue les audiences et le contexte du profil, envoie une requête de personnalisation à [!DNL Adobe Target] et renvoie l’expérience résultante au client.

![Flux de données pour l’intégration de Real-Time Customer Data Platform et Adobe Target](assets/real_time_cdp_target_data_flow_detail.png){zoomable="yes"}

## Considérations relatives à la mise en œuvre

* [!DNL Adobe Target] et [!DNL Real-Time Customer Data Platform] doivent utiliser la même organisation IMS.
* La destination [!DNL Adobe Target] prend en charge le sandbox de production par défaut dans [!DNL Real-Time Customer Data Platform].
* Pour les recherches d’espace de noms d’identité personnalisées Edge, utilisez Web SDK ou l’API du serveur Edge Network et incluez chaque identité dans le mappage d’identité.
* Si vous utilisez at.js, l’intégration de profil ne prend en charge que l’espace de noms d’identité ECID.

## Documentation connexe

### Configuration de l’intégration

* [Connexion Adobe Target pour Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=fr)
* [Configuration du flux de données Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=fr)

### Implémentation à la périphérie

* [Documentation Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr)
* [Documentation Experience Platform Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [Documentation du service Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=fr)

### Évaluer les audiences

* [Présentation de la segmentation Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr)
* [Segmentation en temps réel](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=fr)
* [Segmentation par flux](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Configuration de la politique de fusion](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=fr#create-a-merge-policy)
