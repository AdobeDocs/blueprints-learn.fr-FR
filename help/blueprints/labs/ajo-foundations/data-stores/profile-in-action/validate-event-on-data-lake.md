---
hold: true
title: Événement de validation sur le lac de données
description: Découvrez comment interroger le lac de données pour vérifier qu’un événement web diffusé en continu a été écrit dans le jeu de données correct.
doc-type: article
solution: Experience Platform
exl-id: 14445089-aa3c-4cce-9d33-80032b6f9868
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# Événement de validation sur le lac de données

## Objectif d’apprentissage

Vérifiez que l’événement web a été écrit dans le lac de données Experience Platform.

## Valider l’événement

&#x200B;> [!NOTE]
>
>Les données finissent par apparaître dans le lac de données.  **Cela peut prendre jusqu’à 60 minutes**.  Nous savons que le jeu de données est activé pour le profil et que l’événement créera donc un fragment de profil.
>
>Vous pouvez rechercher et interroger le jeu de données web.

1. Accédez à **Requêtes** et **Créer une requête**

![Écran Créer une requête dans la section Requêtes](assets/validate-event-on-data-lake-create-query.png)

&#x200B;2. Copiez ce code SQL et collez-le dans votre requête.

```sql
SELECT identityMap['email'][0].id, * FROM dep_web
where identityMap['email'][0].id = 'henry.creel@emailsim.io'
```

&#x200B;3. **Exécuter** Requête

&#x200B;> [!NOTE]
>
>**À retenir** : les données finissent par apparaître dans le lac de données.  **Cela peut prendre jusqu’à 60 minutes**.
>
>Vous n’avez pas besoin d’attendre qu’il apparaisse. N’hésitez pas à revenir à cette étape et à vérifier ultérieurement.



![Résultats de la requête affichant l’événement web diffusé en continu dans le lac de données](assets/validate-event-on-data-lake-query-results.png)

## Récapituler

L’enregistrement de l’événement apparaît dans le jeu de données approprié.
