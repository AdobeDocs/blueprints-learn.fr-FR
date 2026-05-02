---
title: Plan directeur de la gestion des décisions sur Edge
description: Diffusez des offres personnalisées à vos clients sur l’ensemble des canaux, y compris dans les expériences web et mobiles en temps réel.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
TQID: https://experienceleague.adobe.com/SwjKOJIL5WidXtVuLCNbBpNz3mhe0EvD93IhMfxI1oY
product_v2: id: cb954087-f4fc-4456-afb9-e939cabcdc79id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: c132d929-fa62-4271-803e-b823be07b914id: d998adac-2f81-400b-a669-d07bb196e4ebid: daec7ead-f475-492a-a3b3-02ae08565d6fid: df64005d-8f9a-422e-ba4d-c6f6dc3454b4id: fe338112-e2ce-4876-8989-fc4d497613f1
subfeature_v2: id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: c18d9e03-ac7d-4811-9c92-3e92ddc70adeid: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 492
ht-degree: 67%

---

# Journey Optimizer - [!DNL Decision Management] sur le plan directeur d’Edge

>[!TIP]
>Ce plan directeur est également disponible en tant que [ modèle de cas d’utilisation ](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) sous Personalization.

[!DNL Decision Management] est un service fourni dans le cadre de [!DNL Journey Optimizer]. Ce plan directeur décrit les cas d’utilisation et les fonctionnalités techniques de l’application et fournit une analyse approfondie des différents composants architecturaux et des considérations qui entrent en compte dans la gestion des décisions.

>[!MORELIKETHIS]
>
>Pour en savoir plus sur [!DNL Decision Management], consultez la [présentation du plan directeur](decision-management-overview.md) ou consultez la [documentation du produit](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=fr).

[!DNL Decision Management] peut être déployé de deux manières. La première est via le [!DNL Experience Platform] Hub, qui est une architecture de centre de données unique. L’approche de type « hub » permet d’exécuter, de personnaliser et de diffuser les offres avec une latence en secondes. L’architecture du hub est donc mieux adaptée aux expériences client qui ne demandent pas de latence inférieure à une seconde, par exemple pour les prises de décisions sur les offres pour les kiosques ou les expériences assistées par agent, telles que dans les centres d’appel ou les interactions en personne.

La deuxième approche passe par Experience Platform [!DNL Edge Network], une infrastructure géographiquement distribuée à l’échelle mondiale qui permet d’offrir des expériences rapides pendant moins d’une seconde et pendant des millisecondes. Expérience client finale exécutée par l’infrastructure Edge la plus proche de la géolocalisation des clients afin de minimiser la latence. [!DNL Decision Management] sur Edge est conçu pour offrir des expériences client en temps réel. Il s’agit notamment des expériences telles que les demandes de personnalisation entrantes web ou mobiles.

Ce plan directeur couvrira les détails de la gestion des décision sur Edge.

Pour en savoir plus sur la gestion des décisions sur le hub, reportez-vous au plan directeur [Gestion des décisions sur le hub](decision-management-hub.md).

## Cas d’utilisation de la gestion des décisions sur Edge

* Cas d’utilisation de la diffusion en continu où la latence du contexte de profil est strictement inférieure à 15 minutes et où l’exécution de la gestion des décisions est inférieure à la seconde.
* Personnalisation en ligne via des expériences entrantes web ou mobiles
* Exécution de parcours cross-canal : offre une cohérence entre les canaux web, mobile, par e-mail et les autres canaux d’interaction par le biais d’Adobe Journey Optimizer

## Architecture

<img src="images/offers_edge.svg" alt="Plan directeur de la gestion des décisions concernant l’architecture de référence sur Edge" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Modèles d’intégration

| Intégration | Description |
| :-- | :--- |
| [Gestion des décisions avec Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=fr) | La gestion des décisions peut être intégrée à Adobe Target afin que les offres puissent être testées et diffusées en tant qu’expériences Target. |

## Garde-fous

* Pour en savoir plus sur les garde-fous Journey Optimizer, consultez [Garde-fous Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=fr).

* Pour en savoir plus sur les garde-fous de la gestion des décisions, consultez la [description du produit de gestion des décisions](https://helpx.adobe.com/fr/legal/product-descriptions/offer-decisioning-app-service.html).

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## Documentation connexe

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=fr)
* [Gestion des décisions Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=fr)
* [Description du produit Adobe Journey Optimizer](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
* [Description du produit Gestion des décisions Adobe](https://helpx.adobe.com/fr/legal/product-descriptions/offer-decisioning-app-service.html)
