---
hold: true
title: Politiques de décision
description: Découvrez comment les politiques de décision appliquent des stratégies de sélection à un canal de diffusion et comment les méthodes de combinaison individuelles ou groupées modifient l’ordre d’offre.
doc-type: article
solution: Experience Platform
exl-id: 21dc67fd-76ac-4b82-ae78-be024c7bfc55
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Politiques de décision

## Objectif d’apprentissage

À la fin de cette leçon, vous serez en mesure de :

- Expliquez ce qu’une politique de décision configure et où elle est appliquée.
- Définir un package de décision et ce qu’il comprend
- Différencier les méthodes individuelles et groupées de combinaison de plusieurs stratégies de sélection
- Expliquez comment la limitation de la fréquence interagit avec le nombre d’éléments de décision renvoyés par une politique

## Matériaux nécessaires

- 12 cartes à jouer (Jack, Reine, Roi de chaque couleur)
- 13 notes autocollantes
  - 12 remplies de nom d’attribut et de valeurs des leçons précédentes
  - Un nouveau pense-bête pour suivre les demandes

## Conférence

Il s’agit de la simulation la plus longue et la plus impliquée du cours. Vous simulerez le comportement réel de la politique de décision en effectuant des « demandes » répétées, en suivant les impressions par rapport aux limites de fréquence et en regardant les cartes tomber et être remplacées, puis vous appliquerez tout à un scénario commercial réel en comparant la combinaison de stratégies de sélection individuelles et groupées.

>[!VIDEO](https://video.tv.adobe.com/v/3502211/)

## Principaux points à retenir

- Une politique de décision applique des stratégies de sélection à un canal de diffusion AJO réel, configuré sur un nœud de canal dans un parcours ou une section de canal d’une campagne
- Une politique peut n’utiliser aucune, une ou plusieurs stratégies de sélection. Sans aucune, elle renvoie les éléments par score de priorité d’origine, filtrés par éligibilité au niveau de l’élément
- Une politique de décision ainsi que son canal de diffusion sont appelés ensemble un package de décision, c’est-à-dire la configuration qui réside sur le hub ou le edge
- Avec une combinaison individuelle, la collection de chaque stratégie est classée séparément, puis les listes sont empilées ; avec une combinaison, tous les éléments sont regroupés dans une seule liste et les doublons utilisent la plus élevée de leurs deux notes
- Les mêmes entrées peuvent produire des ordres finaux radicalement différents en fonction des individus par rapport aux groupes
- Le capping de la fréquence limite directement le nombre d’éléments disponibles à renvoyer. Planifiez donc suffisamment d’éléments de secours non limités pour remplir chaque emplacement
