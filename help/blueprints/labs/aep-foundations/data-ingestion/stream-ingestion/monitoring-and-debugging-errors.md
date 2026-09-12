---
title: Erreurs de surveillance et de débogage
description: Utilisez le tableau de bord de surveillance de bout en bout de la diffusion en continu pour identifier et interpréter les erreurs INGEST, DCVS et MAPPER dans un flux de données en continu.
doc-type: article
solution: Experience Platform
exl-id: 268abf15-14ac-45e3-8cd7-8d180ee5b1e3
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# Erreurs de surveillance et de débogage

>[!NOTE]
>
>La surveillance de l’ingestion par flux se produit au niveau du flux de données, ce qui signifie que lorsque vous la visualisez dans l’interface utilisateur, vous visualisez le lac de données.  Cela signifie que des lots s’affichent (les micro-lots qui sont traités hors du pipeline de diffusion en continu) environ toutes les 60 minutes.  Ainsi, si vous ne voyez pas vos données dans le profil client en temps réel, vous devez attendre jusqu’à 60 minutes pour diagnostiquer le problème.



## Afficher le tableau de bord de surveillance

1. Accédez à **Surveillance->Streaming de bout en bout** et localisez votre **Flux de données** :

   ![Recherche du flux de données en continu dans la section Surveillance](assets/monitoring-and-debugging-errors-locate-your-dataflow-in-monitoring.png "Recherchez votre flux de données dans Surveillance")



1. Vous pouvez prévisualiser l’onglet **tableau de bord** pour afficher les mesures de pipeline relatives aux workflows d’ingestion par lots.

![Onglet Tableau de bord affichant les mesures de tous les workflows d’ingestion par lots](assets/monitoring-and-debugging-errors-dashboard-tab-metrics.png "L’onglet Tableau de bord affiche les mesures de tous les workflows d’ingestion par lots")

>[!NOTE]
>
>Cet écran de surveillance vous permet de voir le statut de vos différentes exécutions de flux de données.  Notez les différentes mesures disponibles dans le panneau supérieur.  Ces mesures peuvent s’avérer extrêmement utiles pour comprendre l’intégrité de votre pipeline de données dans Experience Platform



## Erreurs de débogage

1. Si votre flux de données comportait des erreurs car vous n’aviez pas suivi les instructions, les éléments suivants s’affichent.

   ![Échecs signalés pour un flux de données en continu avec des erreurs de mappage](assets/monitoring-and-debugging-errors-failures-reported.png "Échecs signalés")



1. Si vous cliquez sur les Échecs, vous obtenez l&#39;écran suivant :

   ![Écran de diagnostics d’erreur affichant les détails des erreurs INGEST, DCVS et MAPPER](assets/monitoring-and-debugging-errors-preview-error-diagnostics.png "Aperçu des diagnostics d’erreur")

   >[!NOTE]
   >
   >Un microlot réussi peut prendre plus de 15 minutes, car il peut s’avérer nécessaire de disposer de temps pour écrire les enregistrements dans le lac de données.



1. Analysez le message d&#39;erreur, identifiez les **champs source/cible** et recherchez le code :

   - **INGEST XXXX** - Il s’agit d’une erreur grave due à une corruption des données ou à des problèmes de formatage, c’est-à-dire qu’il ne suit pas un format RegEx.
   - **DCVS XXXX** - Cette erreur s’affiche avec les champs `required`. Si les valeurs n’existent pas ou sont mappées de manière incorrecte (et non dans la liste d’énumérations), ces lignes sont ignorées.
   - **MAPPEUR XXXX** - Avertissements et aucune ligne n’est ignorée. Cependant, les valeurs peuvent avoir été rendues « nulles ». Vous devez donc vérifier qu’elles n’ont pas d’impact sur les activités en aval.

1. Pour récupérer après les erreurs, vous devez accéder à **Sources->Flux de données->Nom du flux de données->Mettre à jour le flux de données** et corriger vos mappages.

>[!NOTE]
>
>Vous devez charger à nouveau le fichier d’exemple JSON en le supprimant d’abord et en l’ajoutant de nouveau, de sorte que le mappeur soit maintenant actualisé avec une nouvelle copie pour validation.

![Accéder à Sources > Flux de données > Nom du flux de données > Mettre à jour le flux de données pour corriger les mappages](assets/monitoring-and-debugging-errors-update-dataflow-navigation.png "cliquez sur Mettre à jour le flux de données")
