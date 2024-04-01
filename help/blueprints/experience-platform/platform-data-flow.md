---
title: Diagrammes d’architecture des flux de données Experience Platform
description: Ce schéma d’architecture montre comment les données entrent et sortent d’Adobe Experience Platform.
solution: Data Collection
kt: 7198
thumbnail: null
exl-id: 5016f657-dd55-4ab7-859d-c97bc5edff76
source-git-commit: cf7721ea01579182fdb200aad448be6fc94b34cf
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 90%

---

# Diagrammes de l’architecture de flux de données Adobe Experience Platform

## Diagramme de flux de données

Le schéma ci-dessous illustre les différents chemins d’accès pour l’ingestion et la sortie de données d’Adobe Experience Platform.

<img src="assets/aep_data_flow.svg" alt="Flux de données Experience Platform" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Modèles d’entrée et de sortie de données

Pour obtenir une liste détaillée de tous les modèles d’ingestion, de collecte et d’entrée de données, voir le [Plan directeur de la préparation et de l’ingestion des données](../data-ingestion/ingestion.md).

Pour obtenir une liste détaillée de tous les modèles de sortie et d’accès aux données, voir le [Plan directeur de l’accès aux données et de leur export](../data-ingestion/egress.md).

## Mécanismes de sécurisation de l’ingestion des données

Le diagramme ci-dessous illustre les principaux garde-fous de performance et la latence de l’ingestion de données dans Adobe Experience Platform.

<img src="deployment/assets/aep_data_flow_guardrails.svg" alt="Flux de données Experience Platform" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" class="modal-image" />