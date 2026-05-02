---
title: '[!DNL Journey Optimizer] - Orchestration des campagnes'
description: Permet aux professionnels du marketing de coordonner des communications marketing planifiées, basées sur une audience et à plusieurs étapes sur les canaux de messagerie sortants.
solution: Journey Optimizer
exl-id: a8ff16f8-146d-4e1f-9bd0-9eda6af0c69b
TQID: https://experienceleague.adobe.com/aPDagEC1zZdi-Bz29fFf6g5Uy8v4qMPhDA47Cdwl-Sw
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 358
ht-degree: 6%

---

# [!DNL Journey Optimizer] - Plan directeur d’orchestration de Campaign

>[!TIP]
>Ce plan directeur est également disponible en tant que [&#x200B; modèle de cas d’utilisation &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) sous Gestion et orchestration des campagnes.

L’orchestration des campagnes d’AJO permet aux spécialistes marketing de concevoir et d’exécuter des communications planifiées, basées sur l’audience et à plusieurs étapes sur les canaux sortants tels que les e-mails, les SMS, les notifications push et le publipostage direct. Contrairement aux Parcours AJO, qui réagissent aux comportements individuels des clients à l’aide de données en temps réel du profil client en temps réel, les campagnes sont des efforts marketing coordonnés qui ciblent les audiences à intervalles planifiés. Ensemble, les campagnes et les parcours offrent des approches complémentaires : les campagnes pilotent les stratégies d’engagement de la marque, tandis que les parcours offrent des expériences personnalisées et réactives.

<br>

## Architecture

<img src="images/ajo-campaigns-architecture.svg" alt="Architecture de référence Plan directeur de l’orchestration des campagnes Adobe Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### Architecture D’Exécution Des Messages

<img src="images/ajo-campaigns-message-sending-architecture.png" alt="Architecture de référence Plan directeur de l’orchestration des campagnes Adobe Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### Magasin Relationnel - Latence D’Ingestion Des Données

<img src="images/ajo-campaigns-data-ingestion-architecture.png" alt="Architecture de référence Plan directeur de l’orchestration des campagnes Adobe Journey Optimizer" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Considérations architecturales pour les Parcours

- **Architecture des données** : l’orchestration d’AJO Campaign utilise une base de données relationnelle sous-jacente pour la création et l’orchestration d’audiences
- **Intégration d’Audience Portal** : intégré de manière native à Audience Portal dans le profil client en temps réel pour lire les audiences existantes et enregistrer de nouvelles audiences dans lors de la création de campagnes
- **Création d’une audience à la demande** : créez, évaluez et exécutez immédiatement une audience pour les cas d’utilisation marketing urgents
- **Intégration du profil client en temps réel :** source de vérité pour l’historique de consentement et de communication ; prend en charge la conception de « profil maigre » pour la personnalisation.
- **Envoi de messages à entités multiples :** possibilité d’envoyer plusieurs messages par profil dans une seule diffusion (par exemple, envoyer un message par réservation à l’adresse e-mail du client)
- **Segmentation d’entités multiples** : commencez à créer une audience à partir de n’importe quelle entité du magasin relationnel (c’est-à-dire produit, inventaire, plan, etc.)

<br>

## Garde-fous

[Lien du produit Campagnes orchestrées](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/guardrails)

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails)

<br>

## Documentation connexe

- [[!DNL Journey Optimizer] des campagnes orchestrées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/orchestrated-campaigns-landing-page.html)
- [Documentation [!DNL Experience Platform]](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
- [Documentation sur les balises [!DNL Experience Platform]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
- [Documentation [!DNL Experience Platform Mobile SDK]](https://experienceleague.adobe.com/docs/mobile.html?lang=fr)
- [Documentation [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=fr)
- [Description du produit [!DNL Journey Optimizer]](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)
