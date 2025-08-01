---
title: Plan directeur de la gestion des décisions sur Edge
description: Diffusez des offres personnalisées à vos clients sur l’ensemble des canaux, y compris dans les expériences web et mobiles en temps réel.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 68%

---

# Journey Optimizer - [!DNL Decision Management] sur le plan directeur d’Edge

[!DNL Decision Management] est un service fourni dans le cadre de [!DNL Journey Optimizer]. Ce plan directeur décrit les cas d’utilisation et les fonctionnalités techniques de l’application et fournit une analyse approfondie des différents composants architecturaux et des considérations qui entrent en compte dans la gestion des décisions.

>[!MORELIKETHIS]
>
>Pour en savoir plus sur [!DNL Decision Management], consultez la [présentation du plan directeur](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=fr) ou consultez la [documentation du produit](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=fr).

[!DNL Decision Management] peut être déployé de deux manières. La première est via le [!DNL Experience Platform] Hub, qui est une architecture de centre de données unique. L’approche de type « hub » permet d’exécuter, de personnaliser et de diffuser les offres avec une latence en secondes. L’architecture du hub est donc mieux adaptée aux expériences client qui ne demandent pas de latence inférieure à une seconde, par exemple pour les prises de décisions sur les offres pour les kiosques ou les expériences assistées par agent, telles que dans les centres d’appel ou les interactions en personne.

La deuxième approche passe par Experience Platform [!DNL Edge Network], une infrastructure géographiquement distribuée à l’échelle mondiale qui permet d’offrir des expériences rapides pendant moins d’une seconde et pendant des millisecondes. Expérience client finale exécutée par l’infrastructure Edge la plus proche de la géolocalisation des clients afin de minimiser la latence. [!DNL Decision Management] sur Edge est conçu pour offrir des expériences client en temps réel. Il s’agit notamment des expériences telles que les demandes de personnalisation entrantes web ou mobiles.

Ce plan directeur couvrira les détails de la gestion des décision sur Edge.

Pour en savoir plus sur la gestion des décisions sur le hub, reportez-vous au plan directeur [Gestion des décisions sur le hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=fr).

## Cas d’utilisation de la gestion des décisions sur Edge

* Cas d’utilisation de la diffusion en continu où la latence du contexte de profil est strictement inférieure à 15 minutes et où l’exécution de la gestion des décisions est inférieure à la seconde.
* Personnalisation en ligne via des expériences entrantes web ou mobiles
* Exécution de parcours cross-canal : offre une cohérence entre les canaux web, mobile, par e-mail et les autres canaux d’interaction par le biais d’Adobe Journey Optimizer

## Architecture

<img src="../assets/offers_edge.svg" alt="Plan directeur de la gestion des décisions concernant l’architecture de référence sur Edge" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Modèles d’intégration

| Intégration | Description |
| :-- | :--- |
| [Gestion des décisions avec Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=fr) | La gestion des décisions peut être intégrée à Adobe Target afin que les offres puissent être testées et diffusées en tant qu’expériences Target. |

## Garde-fous

* Pour en savoir plus sur les garde-fous Journey Optimizer, consultez [Garde-fous Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=fr).

* Pour en savoir plus sur les garde-fous de la gestion des décisions, consultez la [description du produit de gestion des décisions](https://helpx.adobe.com/fr/legal/product-descriptions/offer-decisioning-app-service.html).

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## Documentation connexe

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=fr)
* [Gestion des décisions Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=fr)
* [Description du produit Adobe Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
* [Description du produit de gestion des décisions Adobe](https://helpx.adobe.com/fr/legal/product-descriptions/offer-decisioning-app-service.html)
