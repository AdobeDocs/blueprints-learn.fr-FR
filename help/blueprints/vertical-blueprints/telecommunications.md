---
title: Secteur des télécommunications - Journey Optimizer pour les messages déclenchés
description: Offrez à vos clients des offres personnalisées en temps réel tout en bénéficiant d’une intégration efficace à la clientèle, pour vous assurer de leur fidélité à long terme.
solution: Journey Optimizer
kt: 9486
exl-id: fa4a6569-3972-4b97-91f1-7ca8ffd3c5b3
source-git-commit: 1a0ce987fc615080bb78fb8ecf60c96e362a95c0
workflow-type: ht
source-wordcount: '333'
ht-degree: 100%

---

# Problématique relative au secteur des télécommunications

Avant de mettre en œuvre ce plan directeur, les campagnes par e-mail « ajouter une nouvelle ligne » des entreprises de télécommunications reposaient sur la conversion ou non de l’utilisateur, et ne vérifiait ce point qu’après un délai d’attente de 7 jours. Seulement une fois ce critère satisfait, d’autres points de contact étaient lancés.

Cette limitation devait être résolue afin de permettre un suivi plus rapide des utilisateurs qui souhaitaient ajouter une ligne avant le délai d’attente actuel de 7 jours.

## L’approche d’Adobe

* Les données Adobe Analytics permettant d’identifier les utilisateurs qui n’ont pas pu effectuer la conversion pour ajouter une nouvelle ligne sont incluses en tant que source de données pouvant être utilisées dans Adobe Journey Optimizer.
* Adobe Journey Optimizer utilise une règle au moment où le client reçoit un message « abandon » personnalisé conçu pour l’encourager à effectuer une conversion en ajoutant une nouvelle ligne à son compte.


## Valeur commerciale offerte

| Objectifs | Stratégies | Valeur débloquée |
|---|---|---|
| **Augmentation des taux de conversion de campagnes **<br></br>** Augmentation du chiffre d’affaires annuel du compte**</ul> | <ul><li>Créez un segment en temps quasi réel pour les utilisateurs qui ont montré un intérêt pour l’ajout d’une ligne, mais qui n’ont pas encore été convertis.</li><li>Accélérez le suivi des clients non convertis avec un second point de contact destiné aux clients non convertis mais intéressés. </li><li>Utilisez une stratégie de test permettant de mesurer les performances des parcours et d’optimiser la conversion par e-mail.</li></ul> | <ul><li><strong>Des expériences pertinentes de haute qualité :</strong> grâce à l’implémentation de Journey Orchestration, les clients reçoivent de messages plus pertinents, ce qui réduit le volume des listes d’e-mails.</li><li><strong>Journey Orchestration, sur-mesure :</strong> un parcours personnalisé et plus chronologique peut être créé pour augmenter les conversions et le chiffre d’affaires total.</li></ul> |

## Plan directeur principal : activation des audiences avec des applications Experience Cloud

### Description

<ul><li>Envoi de messages déclenchés et en flux continu à l’aide d’Adobe Experience Platform en tant que hub central pour la diffusion en flux continu de données, de profils clients et de segmentation, à l’aide de Journey Orchestration pour l’orchestration en flux continu des parcours et la diffusion des messages</li></ul>

### Applications Experience Cloud

<ul><li>Adobe Journey Optimizer</li></ul>

### Architecture du plan directeur

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=fr"><img alt="image représentant une entreprise de télécommunications présentant à ses clients des offres personnalisées en temps réel tout en bénéficiant d’une intégration efficace à la clientèle, pour s’assurer de leur fidélité à long terme." src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/ajo-architecture.svg"/></a>
