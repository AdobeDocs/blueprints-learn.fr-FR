---
title: Formules de classement
description: Découvrez comment les formules de classement ajustent dynamiquement le score de priorité d’un élément de décision par profil à l’aide d’expressions mathématiques conditionnelles.
doc-type: article
solution: Experience Platform
exl-id: 08183f1a-8db6-43c5-8b2e-05fa3d9c0f8d
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Formules de classement

## Objectif d’apprentissage

À la fin de cette leçon, vous serez en mesure de :

- Définir une formule de classement et expliquer ce qu’elle ajuste
- Expliquer la structure if/then d’une règle de formule de classement
- Expliquez pourquoi chaque configuration de formule de classement nécessite une formule par défaut
- Déterminer le résultat lorsque deux éléments de décision arrivent sur le même score de priorité ajusté

## Matériaux nécessaires

- 12 cartes à jouer (Jack, Reine, Roi de chaque couleur)
- 12 pense-bêtes, remplis à la fois de nom d’attribut et de valeurs des leçons précédentes

## Conférence

Cette leçon comporte plusieurs séries de réorganisation de vos cartes à la main — d&#39;abord par priorité d&#39;origine, puis par deux formules de classement différentes appliquées à différents profils types — afin que vous puissiez voir comment le même ensemble d&#39;éléments se redistribue selon qui le demande.

>[!VIDEO](https://video.tv.adobe.com/v/3502209/)

## Principaux points à retenir

- Une formule de classement ajuste dynamiquement le score de priorité d’un élément de décision sur une base par profil, en fonction des attributs de profil ou de l’événement d’expérience déclencheur
- Les formules prennent en charge les calculs mathématiques de base (ajout, soustraction, multiplication, division) et peuvent référencer le score de priorité d’origine de l’élément de décision en tant que variable
- La logique de règle : si une condition relative au profil ou à l’accès est vraie, ajustez la priorité des éléments de décision qui répondent à certains critères d’élément
- Chaque configuration de formule de classement nécessite une formule par défaut pour les éléments de décision auxquels aucune règle d&#39;ajustement n&#39;a accès
- Lorsque deux éléments de décision arrivent sur le même score de priorité ajusté, la prise de décision les ordonne de manière aléatoire
