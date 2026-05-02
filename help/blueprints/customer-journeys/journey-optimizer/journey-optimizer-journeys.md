---
title: '[!DNL Journey Optimizer] - Message déclenché et plan directeur Adobe Experience Platform'
description: Exécutez des expériences et messages déclenchés à l’aide d’Adobe Experience Platform, que vous pouvez utiliser comme une plateforme centrale pour la diffusion en continu des données, les profils client et la segmentation.
solution: Journey Optimizer
exl-id: 70573eb9-cd69-4fe6-b2ae-dae81665a308
TQID: https://experienceleague.adobe.com/MuodOvJ52G9lmUAmsuj06q1aTXkRg7W0Bj6nxLp96N8
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
  - id: fe96aceb-8194-4a8a-a6b0-75302d02804d
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 12%

---

# [!DNL Journey Optimizer] - Plan directeur des Parcours

>[!TIP]
>Ce plan directeur est également disponible en tant que [&#x200B; modèle de cas d’utilisation &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) sous Gestion et orchestration des campagnes.

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

[Lien du produit Mécanismes de sécurisation [!DNL Journey Optimizer]](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=fr)

<br>

## Documentation connexe

- [Documentation [!DNL Experience Platform]](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
- [Documentation sur les balises [!DNL Experience Platform]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
- [Documentation [!DNL Experience Platform Mobile SDK]](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
- [Documentation [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
- [Description du produit [!DNL Journey Optimizer]](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
