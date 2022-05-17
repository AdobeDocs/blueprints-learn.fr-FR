---
title: Présentation des Offers decisionings
description: Diffuser des offres personnalisées sur l’ensemble des parcours clients.
solution: Experience Platform, Journey Optimizer
exl-id: f6271802-faab-4ffc-92d6-4c4d7d423ed4
source-git-commit: 8842b8637a30151577a93653c16b4d37e2cf7c27
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 2%

---

# Journey Optimizer - Aperçu des Offers decisionings

Pour en savoir plus sur la gestion de la décision, consultez la documentation du produit. [ICI](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

Adobe Decision Management est un service fourni dans le cadre de Adobe Journey Optimizer. Ce plan directeur décrit les cas d’utilisation et les fonctionnalités techniques de l’application et fournit une analyse approfondie des différents composants architecturaux et des considérations qui constituent l’Offer decisioning.

Journey Optimizer est utilisé pour offrir la meilleure offre et la meilleure expérience à vos clients sur tous les points de contact au bon moment. Offer Decisioning facilite la personnalisation avec une bibliothèque centrale d’offres marketing et un moteur de décision qui applique des règles et des contraintes aux profils en temps réel riches créés par Adobe Experience Platform pour vous aider à envoyer à vos clients la bonne offre au bon moment.

La fonctionnalité de gestion des décisions se compose de deux composants principaux :

* La bibliothèque des offres centralisée, qui est l’interface dans laquelle vous créez et gérez les différents éléments qui composent vos offres, et définissez leurs règles et contraintes.
* Moteur de décision d’offre qui tire parti des données Adobe Experience Platform et des profils clients en temps réel, ainsi que de la bibliothèque des offres, afin de sélectionner l’heure, les clients et les canaux auxquels les offres seront diffusées.

<img src="../assets/offers_overview.png" alt="Offer Decisioning" style="width:100%; border:1px solid #4a4a4a" />

La gestion des décisions peut être déployée de deux façons, en périphérie ou via le hub. Chacune de ces méthodes comporte un ensemble spécifique d’interfaces et de protocoles pour le fonctionnement du service, comme indiqué dans les plans directeurs respectifs référencés ci-dessous. Vous trouverez des détails supplémentaires dans la documentation de la gestion des décisions. [ICI](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html).

## Gestion des décisions sur le hub

La première est via le hub Adobe Experience Platform, qui est une architecture centrale de centre de données. Dans l’approche &quot;hub&quot;, les offres sont exécutées, personnalisées et diffusées dans une latence supérieure à 500 ms. L’architecture du hub est donc mieux adaptée aux expériences client qui ne demandent pas de latence inférieure à une seconde. Par exemple, les décisions d’offre sont fournies pour les kiosques ou les expériences assistées par l’agent, telles que dans les centres d’appel ou les interactions avec la personne. Les offres insérées dans les emails, les SMS ou les notifications push et autres campagnes sortantes sont également optimisées par l&#39;approche hub (hub). Pour en savoir plus sur la gestion des décisions sur le hub, reportez-vous à la section [Gestion des décisions sur le hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html?lang=en) plan directeur.

### Cas d’utilisation de la gestion des décisions sur le hub

* Offres personnalisées dans les kiosques et dans les expériences de magasin.
* Offres personnalisées par le biais d’une expérience assistée par l’agent, telles que des centres d’appel ou des interactions commerciales.
* Offres incluses dans les emails, SMS ou autres interactions sortantes.
* Exécution de parcours cross-canal : offre une cohérence entre les canaux web, mobile, email et autres canaux d’interaction via Adobe Journey Optimizer.

## Gestion des décisions à la périphérie

La seconde approche consiste à utiliser le réseau Experience Edge, qui est une infrastructure géographiquement répartie mondialement et qui sert des expériences de sous-seconde et de milliseconde rapides. Expérience client finale exécutée par l’infrastructure de périphérie la plus proche de la géolocalisation des consommateurs afin de minimiser la latence. La gestion des décisions sur l’Edge est conçue pour fournir des expériences client en temps réel telles que des demandes de personnalisation entrantes sur le web ou mobile. Pour en savoir plus sur la gestion de la décision sur Edge, reportez-vous à la section [Gestion des décisions à la périphérie](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=en) plan directeur.

### Cas d’utilisation de la gestion des décisions sur le serveur Edge

* Personnalisation en ligne via des expériences entrantes web ou mobiles.
* Exécution de parcours cross-canal : offre une cohérence entre les canaux web, mobile, email et autres canaux d’interaction via Adobe Journey Optimizer.

## Documentation connexe

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Gestion des décisions Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Description du produit Adobe Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
* [Description du produit Adobe Offer Decisioning](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
