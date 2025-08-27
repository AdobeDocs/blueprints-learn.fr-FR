---
title: '[!DNL Journey Optimizer] - Message déclenché et plan directeur Adobe Experience Platform'
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Journey Optimizer
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 9%

---

# [!DNL Journey Optimizer] - Plan directeur des Parcours

Les Parcours Adobe Journey Optimizer sont des workflows basés sur des événements en temps réel qui proposent des expériences personnalisées et en plusieurs étapes basées sur le comportement individuel des clients. Elles prennent en charge un large éventail de canaux, notamment les e-mails, les SMS, les notifications push, la messagerie in-app, les expériences basées sur du code et les intégrations personnalisées basées sur des API, ce qui permet aux marques d’interagir avec les clients en fonction du contexte, sur leurs points de contact préférés.

<br>

## Architecture

<img src="images/ajo-journeys-architecture.svg" alt="Architecture de référence Adobe Journey Optimizer - Plan directeur Parcours" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Considérations architecturales pour les Parcours

- **Fraîcheur du profil** : les Parcours AJO s’appuient sur les mises à jour en temps réel du profil client. Assurez-vous que les sources de données alimentant Adobe Experience Platform (AEP) sont configurées pour une ingestion à faible latence afin de conserver la précision des profils.
- **Traitement des événements évolutif :** assurez-vous que l’infrastructure peut gérer des volumes élevés de déclencheurs de parcours et de diffusion de messages.
- **Intégration modulaire :** concevez des API et des actions personnalisées pour connecter AJO à des systèmes externes à des fins de personnalisation dynamique.
- **Résolution d’identités** : l’assemblage précis des identités des clients sur les appareils et les canaux est essentiel. Les identités mal alignées peuvent conduire à des parcours rompus ou mal dirigés.
- **Minutage de qualification du segment** : les parcours basés sur l’audience dépendent de l’appartenance à un segment. Comprenez à quelle fréquence les segments sont évalués et comment cette synchronisation affecte l’entrée sur le parcours et la personnalisation.
- **Conditions d&#39;entrée de Parcours** : les profils doivent remplir des conditions spécifiques pour entrer dans un parcours. Ces conditions doivent être soigneusement conçues pour éviter les exclusions involontaires ou les chevauchements.
- **Évaluation de l’audience et latence** : les étapes Lecture d’audience dépendent des évaluations de segment dans Adobe Experience Platform, qui peuvent ne pas se produire en temps réel. Concevez des parcours avec la conscience de la fréquence d’évaluation et de la latence afin d’éviter les retards dans la qualification des audiences et d’assurer une personnalisation rapide.

<br>

## Garde-fous

[[!DNL Journey Optimizer] Lien du produit Mécanismes de sécurisation](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

<br>

## Documentation connexe

- [[!DNL Experience Platform] documentation ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
- [[!DNL Experience Platform] Documentation des balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
- [[!DNL Experience Platform Mobile SDK] documentation ](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] documentation ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] description du produit](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)