---
title: '[!DNL Journey Optimizer] - Orchestration des campagnes'
description: Permet aux professionnels du marketing de coordonner des communications marketing planifiées, basées sur une audience et à plusieurs étapes sur les canaux de messagerie sortants.
solution: Journey Optimizer
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 2%

---

# [!DNL Journey Optimizer] - Plan directeur d’orchestration de Campaign

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

[Lien du produit Campagnes orchestrées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/guardrails)

[Mécanismes de sécurisation et conseils sur la latence de bout en bout](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails)

<br>

## Documentation connexe

- [[!DNL Journey Optimizer] Campagnes orchestrées](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/orchestrated-campaigns-landing-page.html)
- [[!DNL Experience Platform] documentation ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=fr)
- [[!DNL Experience Platform] Documentation des balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
- [[!DNL Experience Platform Mobile SDK] documentation ](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] documentation ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] description du produit](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer.html)