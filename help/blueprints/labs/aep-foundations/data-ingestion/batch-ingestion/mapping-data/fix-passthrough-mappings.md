---
hold: true
title: Correction des mappages passthrough
description: Identifiez et corrigez les mappages de passage AI/ML incorrects, tels que les affectations de champ cible en double ou incohérentes, avant de valider.
doc-type: article
solution: Experience Platform
exl-id: b06cc091-661e-4ff4-b6e5-f16bc5128b6b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# Correction des mappages passthrough

## Supprimer les mappages spécifiques

Certaines des données sources dont vous disposez doivent être gérées à l’aide de champs calculés.  Pour y remédier, supprimez-les des mappages et validez à nouveau les mappages.

1. Supprimez les données source suivantes des mappages :
   - date\_naissance
   - source
   - sms\_optIn
1. Revalidez les mappages en cliquant sur le bouton de validation .

![Bouton Valider utilisé pour revalider les mappages après l’abandon de champs](assets/fix-passthrough-mappings-re-validate-mappings-using-validate-button.png "Revalider les mappages à l’aide du bouton valider")

>[!NOTE]
>
>Après avoir cliqué sur Valider , des erreurs peuvent toujours être présentes



## Mauvais exemple de mappage

Bien que les recommandations d’IA/ML soient utiles, elles sont parfois erronées.  Si vous examinez vos recommandations, vous pouvez trouver ces types d’erreurs que vous devez corriger

>[!NOTE]
>
>Vous trouverez ci-dessous quelques exemples de mappages non valides que vous pouvez voir dans votre propre sandbox. D’autres erreurs peuvent également s’afficher.

## Dupliquer les mappages

Dans ce scénario, vous constatez que le programme de recommandation AI/ML a mappé deux champs sources différents au même champ cible **person.name.lastName**



![Deux champs sources différents mappés au même champ cible person.name.lastName](assets/fix-passthrough-mappings-person-lastname-mapped-twice.png "person.name.lastName sont mappés deux fois dans ce mappage")

![Exemple de mappage passthrough en double impliquant le champ plan_name](assets/fix-passthrough-mappings-plan-name-duplicate-mapping.png)



## Mappages incorrects

Ce mappage semble correct, mais après un examen plus approfondi, **email** n’est pas le même que **emailFormat**

![Le mappage où l’e-mail est incorrectement mappé au lieu de emailFormat](assets/fix-passthrough-mappings-email-mapped-incorrectly.png "email semble être correctement mappé, mais il est incorrect conformément aux exigences")

Et celui-ci où **email\_optIn** ne correspond pas correctement à l’objet de consentement incorrect

![email_optIn mal mappé à un objet de consentement incorrect](assets/fix-passthrough-mappings-email-optin-wrong-consent-object.png "email_optIn semble être mappé correctement, mais est incorrect conformément aux exigences")



## Correction des mappages passthrough

Pour corriger les mappages passthrough qui pointent incorrectement vers le mauvais champ cible, procédez comme suit.

### Exemple

1. Commencez avec un mapping non valide et cliquez sur la zone du champ cible. Par exemple, dans le mappage ci-dessous, le champ **person.name.lastName** n’est pas mappé correctement et est mappé à **planName**
1. Dans le panneau Schéma cible qui s’ouvre à droite, choisissez le champ cible approprié et sélectionnez **\_devbc.plan.name**
1. Le champ cible doit maintenant être mis à jour dans la zone champ cible
1. Après avoir corrigé chaque erreur de ce type, vous devez appuyer sur le bouton **Valider** afin de vous assurer que vous réduisez ces types d’erreurs et que vous n’en introduisez pas de nouvelles.



![Parcourir la liste des mappages pour corriger chaque erreur de mappage](assets/fix-passthrough-mappings-work-through-mapping-errors.png "Parcourez le mappage et corrigez les erreurs de mappage")



![Panneau de schéma cible permettant de sélectionner le champ approprié pour corriger un mappage passthrough](assets/fix-passthrough-mappings-choose-correct-target-field.png "Sélectionnez le champ cible approprié et vérifiez qu’il correspond aux exigences de passthrough")

>[!WARNING]
>
>Ne passez pas à l’étape suivante tant que vous n’avez pas résolu toutes vos erreurs de mappage
