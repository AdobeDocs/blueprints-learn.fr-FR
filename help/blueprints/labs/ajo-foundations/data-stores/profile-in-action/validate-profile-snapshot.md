---
title: Validation de l’instantané de profil
description: Découvrez comment interroger le jeu de données d’instantanés de profil et comprendre pourquoi une mise à jour de profil nouvellement diffusée n’apparaît pas avant le prochain traitement par lots quotidien.
doc-type: article
solution: Experience Platform
exl-id: 1e7befcf-d952-47a2-86d9-33ef71eec57a
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Validation de l’instantané de profil

## Objectif d’apprentissage

Vérifiez que le profil n’apparaît pas encore dans le jeu de données d’instantanés de profil.

## Utiliser le jeu de données d’instantanés de profil

1. Dans le volet de navigation de gauche, sous la section Gestion des données , cliquez sur **Jeux de données** puis sur l’onglet **Parcourir** situé sur le rail supérieur

   ![Onglet Parcourir des jeux de données dans la section Gestion des données](assets/validate-profile-snapshot-datasets-browse-tab.png)

2. Dans la **zone de recherche** saisissez `profile`, puis **cliquez sur la ligne** avec le titre « Profile-Snapshot... ». et dans le rail de droite **copiez le nom de la table** et collez-le à un emplacement auquel vous pourrez faire référence à l’étape suivante.

   >[!NOTE]
   >
   >Vous devrez peut-être effacer tous les filtres si vous ne voyez pas le « Profile-Snapshot... » jeu de données.



   ![Résultats de la recherche pour le jeu de données Profile-Snapshot](assets/validate-profile-snapshot-dataset-search.png)

3. Revenez à Query Editor et copiez et collez le code SQL ci-dessous dans l’éditeur

   ```sql
   select
     identityMap,
     segmentID,
     segmentMembershipUps[segmentID] ['lastQualificationTime'],
     segmentMembershipUps[segmentID] ['status'],
     current_timestamp
   from
     (
    select
      identityMap,
      explode (map_keys (segmentMembership['ups'])) as segmentID,
      segmentMembership['ups'] as segmentMembershipUps
    from
   
    where
      map_keys (segmentMembership['ups']) is not null
    limit 100
     )
     --where identityMap['email'][0].id = 'henry.creel@emailsim.io'
     limit 50
   ```

4. Mettez à jour le nom de la table et l’adresse e-mail comme indiqué ci-dessous :
   - **Nom de la table :** à la ligne 14, copiez et collez le nom de la table d’instantanés de profils entre le `from` et le `where`
   - **Adresse e-mail :** pour l’instant, à la ligne 19, saisissez la même adresse e-mail que celle que vous avez utilisée pour envoyer votre événement web (nous avons utilisé henry.creel\@emailsim.io, sauf si vous l’avez modifiée).
     - Pour le moment, nous avons fait un commentaire (laissez tomber). Lorsque la requête s&#39;exécute et que vous recherchez Henry, vous ne le trouvez pas.

   ![Éditeur de requêtes avec le nom de la table d’instantanés de profil et l’adresse e-mail à mettre à jour](assets/validate-profile-snapshot-update-query-table-name.png)

5. **Exécutez** la requête en cliquant sur la flèche en haut à gauche.
6. Les résultats sont les suivants (mais si vous cherchez Henry, vous ne le trouvez pas)

![Les résultats de la requête n’indiquent aucune correspondance pour le profil diffusé dans l’instantané](assets/validate-profile-snapshot-query-results-no-match.png)

>[!NOTE]
>
>**Pourquoi aucun résultat pour Henry ?**
>
>**Rappel** : l’instantané de profil est une **réflexion** ou un instantané de ce qui existait dans le profil à un **moment spécifique**. La tâche est exécutée **quotidiennement** et est utilisée à des fins en aval, comme AJO. Puisque vous venez de diffuser ces données en continu, l’instantané de profil ne les contient pas encore.  Ce sera demain.

## Récapituler

Sachez que les jeux de données d’instantanés sont mis à jour sur un traitement par lots planifié plutôt que immédiatement.
