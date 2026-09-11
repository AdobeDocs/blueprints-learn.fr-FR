---
hold: true
title: Erreurs de débogage
description: Utilisez les diagnostics d’erreur de prévisualisation pour examiner une exécution de flux de données ayant échoué et distinguer les erreurs de format INGEST des avertissements de conversion du MAPPEUR.
doc-type: article
solution: Experience Platform
exl-id: beee191b-a860-494c-873f-ab2e407ffbf5
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---


# Erreurs de débogage

## Aperçu des diagnostics d’erreur

Au bout de quelques minutes, vous remarquerez que le **Statut** indique un échec. Accédez aux détails de l’échec pour déterminer ce qui l’a provoqué.

1. Cliquez sur la date **Début de l’exécution du flux de données**.
1. Cliquez sur le **Aperçu des diagnostics d’erreur** pour afficher les détails spécifiques de chaque ligne qui échoue

![Statut d’exécution du flux de données affichant un échec](assets/debugging-errors-dataflow-run-failure.png "Échec de l’exécution du flux de données")

![Lien Aperçu des diagnostics d’erreur sur l’écran Détails de l’exécution du flux de données](assets/debugging-errors-preview-error-diagnostics-link.png "Aperçu du diagnostic d’erreur")



L’écran qui s’affiche maintenant vous montre un tas de détails sur ce que les codes d’erreur signifient avec le message d’erreur complet et la ligne qui a échoué.

![Écran de détails des diagnostics d’erreur affichant les codes d’erreur, les messages et l’aperçu du diagnostic de ligne](assets/debugging-errors-error-diagnostics-detail-screen.png "erreur ayant échoué")

>[!NOTE]
>
>Faites défiler l’écran vers la droite pour afficher les données source associées à ce code d’erreur



## Compréhension des types d’erreurs

### Erreur INGEST-XXXX-XXX

Cette erreur se produit, car **person.bornDayAndMonth** est attendu au format d’un mois à deux chiffres plus un jour à deux chiffres (en d’autres termes, le 27 avril doit être formaté comme 04-27)

```none
The value (9-27) does not conform to the specified
regex pattern: [0-1][0-9]-[0-9][0-9] in field: 
person.birthDayAndMonth of type: String
```

>[!CAUTION]
>
>Notez que person.bornDayAndMonth n’est pas un champ obligatoire, mais la non-conformité à l’expression régulière est traitée par le système comme un « problème de corruption des données » et constitue une erreur grave.



### Erreur MAPPER-XXXX-XXX

Cette erreur se produit, car le champ source de **createDate** contient des valeurs de chaîne de `Created on 2022-04-22T19:34:17Z`. Cette valeur ne peut pas être convertie automatiquement en date en raison du texte au début : `Created on`. Un champ calculé doit être utilisé pour nettoyer les données.

```none
Error transforming data for destination path 
_dep.account.createDate. Details: Unable to convert 
Created on 2023-09-24T10:19:58Z to schema type DATE_TIME
```

&#x200B;> [!NOTE]
>
>Cette erreur n’est pas grave, car elle entraîne uniquement des avertissements lors du mappage. L’exécution du flux de données n’échoue pas pour cette raison. Cet atelier ne corrige donc pas cette erreur.
