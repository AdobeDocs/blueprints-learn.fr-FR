---
hold: true
title: Ingestion par lots
description: Charger les données du compte client par ingestion par lots dans le lac de données et le profil tout en corrigeant les erreurs de mappage et de qualité des données.
doc-type: overview-page
solution: Experience Platform
exl-id: 76830e79-8fc0-4fda-98b1-2c1de19e8158
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Ingestion par lots

## Objectifs d’apprentissage

Dans cet exercice, vous allez charger les données du compte client à partir d’un connecteur source basé sur des fichiers vers le lac de données d’AEP, puis vers Profile. Voici ce que vous apprendrez :

1. Présentation des mappages passthrough
1. Correction des mappages passthrough générés par ML
1. Utilisation de l’aperçu des données sources pour vérifier les problèmes de qualité des données
1. Planification d’une exécution de flux de données
1. Traitement des erreurs provenant de valeurs manquantes dans les champs obligatoires
1. Traitement des erreurs provenant d’erreurs de correspondance de type de données
1. Traitement des erreurs d’ingestion de données et récupération à la suite d’un tel échec
1. Utilisation itérative des données de test pour générer un jeu de mappages complet.

>[!NOTE]
>
>Si vous n’avez pas terminé la création du schéma de compte client dans les exercices pratiques précédents, vous pouvez accéder au catalogue de schémas et utiliser **dep: Customer Account** à la place
