---
title: Plans directeurs de la gestion des décisions
description: Proposez des offres personnalisées sur l’ensemble des parcours clients.
solution: Experience Platform, Journey Optimizer
exl-id: 1bc9335c-5321-4d0c-939e-4f402e2e8f51
source-git-commit: e6ac3607ea3909acf921125cc5f8fd44c0b3e0f6
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 86%

---

# Journey Optimizer - Plans directeurs de la gestion des décisions

Pour en savoir plus sur la gestion des décisions, consultez la [documentation produit](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=fr).

Reportez-vous à la documentation suivante pour les garde-fous liés à la gestion de la décision. [Barrières de sécurité de la gestion de la décision](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails#decision-management)

La gestion des décisions Adobe est un service fourni dans le cadre d’Adobe Journey Optimizer. Ce plan directeur décrit les cas d’utilisation et les fonctionnalités techniques de l’application et fournit une analyse approfondie des différents composants architecturaux et des considérations qui entrent en compte dans la gestion des décisions.

Journey Optimizer vous permet de proposer la meilleure offre et la meilleure expérience à vos clients sur tous les points de contact au bon moment. La gestion des décisions facilite la personnalisation avec une bibliothèque centralisée d’offres marketing et un moteur de décision qui applique des règles et des contraintes aux profils en temps réel riches créés par Adobe Experience Platform, pour vous aider à envoyer à vos clients la bonne offre au bon moment.

La fonctionnalité de gestion des décisions comprend principalement deux éléments :

* La bibliothèque centralisée des offres, c’est-à-dire l’interface dans laquelle vous créez et gérez les différents éléments qui composent vos offres, et définissez leurs règles et contraintes
* Le moteur de décision d’offre qui tire parti des données Adobe Experience Platform et des profils clients en temps réel, ainsi que de la bibliothèque des offres, qui permet de sélectionner l’heure, le client et le canal de diffusion de l’offre

<img src="../assets/offers_overview.png" alt="Gestion des décisions" style="width:100%; border:1px solid #4a4a4a" />

La gestion des décisions peut être déployée de deux façons, sur Edge ou sur le hub. Chacune de ces méthodes présente un ensemble d’interfaces et de protocoles spécifiques pour le fonctionnement du service, comme indiqué dans les plans directeurs respectifs référencés ci-dessous. Vous trouverez des informations supplémentaires dans la [documentation sur la gestion des décisions](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html?lang=fr).

## Gestion des décisions sur le hub

La première par le biais du hub Adobe Experience Platform, qui est une architecture centrale de centre de données. L’architecture du hub est la mieux adaptée aux expériences client qui ne demandent pas de faible latence et un débit élevé, mais qui nécessitent une vue plus complète du profil client. Par exemple, les décisions d’offre sont fournies pour les kiosques ou les expériences assistées par l’agent, comme dans les centres d’appel ou dans les interactions avec la personne. Les offres insérées dans les emails, les SMS ou les notifications push et autres campagnes sortantes sont également alimentées par l’approche « hub ». Pour en savoir plus sur la gestion des décisions sur le hub, reportez-vous au plan directeur [Gestion des décisions sur le hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=fr).

* L’éligibilité des offres peut prendre en compte le profil client en temps réel complet, y compris tous les attributs et événements d’expérience.

### Cas d’utilisation de la gestion des décisions sur le hub

* Offres personnalisées dans les kiosques et dans les expériences en magasin
* Offres personnalisées par le biais d’une expérience assistée par agent, telles que des centres d’appel ou des interactions commerciales
* Offres incluses dans les e-mails ou SMS, ou autres interactions sortantes
* Exécution de parcours cross-canal : offre une cohérence entre les canaux web, mobile, par e-mail et les autres canaux d’interaction par le biais d’Adobe Journey Optimizer

### Considérations techniques de la gestion des décisions sur le hub

* Accès au profil client en temps réel complet, y compris aux abonnements, aux attributs et aux événements d’expérience de l’audience.

## Gestion des décisions sur Edge   

La deuxième approche est via l’expérience [!DNL Edge Network], qui est une infrastructure géographiquement distribuée à l’échelle mondiale qui permet de proposer des expériences de sous-seconde et de milliseconde rapides. L’expérience client finale est exécutée par l’infrastructure Edge au plus proche de la localisation géographique des consommateurs afin de minimiser la latence. La gestion des décisions sur Edge est conçue pour fournir des expériences client en temps réel, telles que des demandes de personnalisation entrantes web ou mobile. Pour en savoir plus sur la gestion des décisions sur Edge, reportez-vous au plan directeur [Gestion des décisions sur Edge](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=fr).

### Cas d’utilisation de la gestion des décisions sur Edge

* Personnalisation en ligne via des expériences entrantes web ou mobiles
* Exécution de parcours cross-canal : offre une cohérence entre les canaux web, mobile, par e-mail et les autres canaux d’interaction par le biais d’Adobe Journey Optimizer

### Considérations techniques de la gestion des décisions sur le Edge

* Accès au profil en temps réel Edge. Seules les audiences projetées et les attributs de profil sur Edge seront disponibles dans le profil.

## Documentation connexe

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=fr)
* [Gestion des décisions Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=fr)
* [Description du produit Adobe Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
* [Description du produit de gestion des décisions Adobe](https://helpx.adobe.com/fr/legal/product-descriptions/offer-decisioning-app-service.html)
