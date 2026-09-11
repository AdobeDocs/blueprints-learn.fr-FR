---
title: Tester la campagne
description: Découvrez comment exécuter une campagne orchestrée en mode test et pourquoi un canal e-mail basé sur un profil AEP génère des erreurs de diffusion qu’un canal basé sur relationnel évite.
doc-type: article
solution: Experience Platform
exl-id: e77ae8ab-f18f-4683-8fdd-ba4f4629d96c
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---


# Tester la campagne

## Objectif

Dans les étapes suivantes, vous exécuterez la campagne en mode test pour confirmer que celle-ci fonctionne comme prévu avant de la publier. Dans ce cas, le mode test n’envoie pas réellement d’e-mails, mais il permet de vérifier l’ensemble du flux et d’identifier les problèmes rapidement.

## Démarrer le workflow

1. Une fois les deux flux d&#39;email configurés, la campagne ressemble à ce qui suit. Cliquez sur le bouton **Démarrer** pour exécuter la campagne en **Mode test**

   ![Cliquez sur Démarrer pour lancer la campagne en mode Test](assets/test-the-campaign-click-start-test-mode.png)

   >[!NOTE]
   >
   >Comme mentionné dans le Lab précédent, le Mode test permet de valider l&#39;exécution de la campagne et les résultats des différentes activités. Chaque activité est exécutée de manière séquentielle jusqu’à ce que la fin du flux soit atteinte.



2. L&#39;exécution du test de toutes les activités de la campagne démarre et vérifie les résultats

![Test d&#39;exécution des activités de campagne en cours](assets/test-the-campaign-verify-execution-results.png)



## #1 du rapport d’e-mail

1. Pour tester la diffusion e-mail, cliquez sur l’activité **E-mail utilisant l’attribut de profil** et, dans le volet de droite, cliquez sur **Exécuter le test**

   ![Exécuter un test pour l’e-mail à l’aide de l’activité Attribut de profil](assets/test-the-campaign-run-test-profile-attribute.png)

2. Attendez le message de confirmation, puis cliquez sur **Afficher le rapport** pour afficher les détails du test d’e-mail

   ![Cliquez sur Afficher le rapport pour afficher les détails du test d’e-mail](assets/test-the-campaign-view-report-1.png)

3. La page Rapport sur les e-mails présente les statistiques des campagnes et le statut d’exécution. Le test d’e-mail permet de vérifier l’activité pour s’assurer qu’il n’y a aucune erreur et qu’elle n’envoie pas d’e-mails. Cela prend généralement environ \~**5** minutes.

   ![Page de rapport sur les e-mails avec les statistiques de campagne](assets/test-the-campaign-campaign-statistics-1.png)

   >[!NOTE]
   >
   >Vous devrez peut-être actualiser la page plusieurs fois pour afficher le résultat final du test.



4. Une fois le test d’e-mail terminé, les résultats sont présentés. Il existe un certain pourcentage d’erreurs. Cliquez sur **Afficher plus** pour en connaître la raison.

   ![Taux d’erreur avec le lien Afficher plus](assets/test-the-campaign-error-rate-view-more.png)

5. La raison en est la `Email address not found in profile`

![Raison : adresse e-mail introuvable dans le profil](assets/test-the-campaign-email-not-found-reason.png)

>[!NOTE]
>
>Étant donné que l’option **Adresse de diffusion** configurée pour l’activité E-mail, **E-mail à l’aide de l’attribut de profil** a été configurée pour utiliser l’attribut de profil `personalEmail.address`, une dépendance a été créée sur le **profil AEP**.
>
>Sur les **38** ID de client qualifiés du schéma relationnel, le système n’a pu trouver que les profils AEP correspondants **7**. Pour les **31** restants, les profils AEP n’existaient pas, ce qui a provoqué le message d’erreur `Email address not found in profile`.
>
>Il est important de se rappeler que les données du lac de données et du magasin relationnel sont conservées **cohérentes** lors de l’utilisation d’attributs de profil AEP dans des campagnes orchestrées.



## #2 du rapport d’e-mail

1. Répétez le même processus pour l’activité **E-mail à l’aide de Target Dimension**

   ![Exécuter un test d’e-mail à l’aide de l’activité Dimension cible](assets/test-the-campaign-run-test-target-dimension.png)

2. Attendez le message de confirmation, puis cliquez sur **Afficher le rapport** pour afficher les détails du test d’e-mail

   ![Cliquez sur Afficher le rapport pour afficher les détails du test d’e-mail](assets/test-the-campaign-view-report-2.png)

3. Une fois le test d’e-mail terminé, les résultats sont présentés. Dans ce cas, il n’y aura aucune erreur

![Statistiques de campagne sans erreur](assets/test-the-campaign-campaign-statistics-2.png)

>[!NOTE]
>
>Étant donné que la variable **Adresse de diffusion** pour l’activité E-mail **E-mail à l’aide de Target Dimension** a été configurée pour utiliser la `dep_rel_customer_account.email`, à partir du schéma relationnel, il n’y avait aucune dépendance aux profils AEP ou à leurs attributs.
>
>Tous les ID de client qualifiés **38** possèdent des e-mails correspondants dans le magasin relationnel et peuvent être ciblés sans erreur.



## Arrêter le workflow

Cliquez sur le bouton **Arrêter** pour arrêter le **Mode test** de la campagne

>[!TIP]
>
>Les deux configurations de canal e-mail ont été testées au sein de la même campagne et des différences ont été observées entre l’utilisation d’un attribut de profil AEP et l’utilisation du Dimension Target dans la configuration de canal e-mail.
>
>Félicitations, ceci conclut le laboratoire de diffusion des messages.

## Récapituler

Vous avez maintenant vu comment tester la campagne créée pour comprendre le flux et le comportement. Ici, les nuances de l’utilisation des différents paramètres de configuration du canal e-mail ont été bien comprises lors de l’exécution du flux de test.

Vous pouvez en savoir plus sur le mode test de la campagne [ici](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/launch/start-monitor-campaigns), si vous êtes intéressé.
