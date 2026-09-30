---
title: Mappage des données
description: Comprenez pourquoi les mappages passthrough générés par l’IA/ML entre les champs sources et les champs de schéma doivent être soigneusement inspectés avant l’ingestion.
doc-type: overview-page
solution: Experience Platform
exl-id: 6c61093d-de03-4b76-9b4b-3e36962047da
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%
---

# Mappage des données

## Présentation

Dans l’écran Mappage , le moteur de recommandation AI/ML mappe automatiquement plusieurs attributs entre les champs du jeu de données source et les champs de schéma. Ces mappages automatisés sont appelés mappages passthrough , mais nécessitent une **inspection attentive**, car les erreurs et les mappages incorrects se produisent souvent.



![Écran de mappage affichant les recommandations contextuelles basées sur l’IA/ML pour les mappages passthrough](assets/overview-ai-ml-based-contextual-recommendations.png "recommandations contextuelles basées sur l’IA/ML")

>[!NOTE]
>
>Les recommandations AI/ML sont basées sur le contexte et votre écran peut être différent de la capture d’écran ci-dessus ou peut être différent de votre voisin

>[!NOTE]
>
>Notez que toutes les colonnes sources sont TOUJOURS traitées comme des chaînes
