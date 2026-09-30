---
title: Configurer le transfert d’événement
description: Découvrez comment le transfert d’événement utilise des propriétés, des éléments de données, des règles et des flux de données pour transférer des événements Edge vers un point d’entrée tiers.
doc-type: overview-page
solution: Experience Platform
exl-id: da3d1c7f-3642-4de7-a297-fc36d09e7336
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%
---

# Configurer le transfert d’événement

Le transfert d’événement se trouve sur Edge et nous permet de créer un ensemble de règles et de transformations légères pour envoyer des événements à n’importe quel point d’entrée.

À cette étape, nous allons transférer tous les événements que nous envoyons dans Edge vers un webhook. Le webhook agit comme un proxy pour un tiers et nous permet de voir ce qui se passe.

Pour configurer ce paramètre, nous allons configurer :

- Une propriété qui contient toutes les extensions, les éléments de données et les règles nécessaires pour décider quoi transférer et où
  - Un élément de données pour référencer l’événement entrant ou l’analyser en plusieurs composants individuels si nécessaire
  - Une règle pour ajouter des conditions sur ce qu’il faut transférer, transformer la payload et où l’envoyer
- Un flux de données qui configure les services qui l’utiliseront (par exemple, Transfert d’événement et AEP)
  - Les données envoyées à ces flux de données peuvent ensuite agir en fonction du service configuré (par exemple, transférer un événement et envoyer des données à un jeu de données)
