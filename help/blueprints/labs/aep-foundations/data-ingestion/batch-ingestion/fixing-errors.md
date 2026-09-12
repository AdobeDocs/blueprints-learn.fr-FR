---
title: Correction des erreurs
description: Corrigez une expression de champ calculé pour une erreur de formatage de date, puis confirmez le succès à l’aide des mesures de surveillance Sources, Identités et Profils .
doc-type: article
solution: Experience Platform
exl-id: 7a3d0c15-4d58-497e-bfa5-9421d5d2eea7
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# Correction des erreurs

## Fixer le jour et le mois de naissance

1. Cliquez sur l’icône de flèche en regard du champ calculé renseignant le champ XDM **person.bornDayAndMonth**

   ![Éditeur d’expression de champ calculé pour le correctif bornDayAndMonth](assets/fixing-errors-update-the-calculated-expression.png)

1. Mettez à jour l’expression à l’aide du code de champ calculé ci-dessous et cliquez sur **Aperçu**

   ```none
   concat(date_part("mm", date(birth_Date, "M/d/yyyy")).toString(),"-", date_part("dd", date(birth_Date, "M/d/yyyy")).toString())
   ```

   >[!NOTE]
   >
   >Les données doivent apparaître sous la forme d’un mois à 2 chiffres et d’un jour à 2 chiffres (par exemple, le 27 avril affiché sous la forme 04-27). Les paramètres `mm` et `dd` ajoutent une marge intérieure de 0.

1. Si tout semble correct **Enregistrez** le champ calculé

1. Cliquez ensuite sur **Terminer** pour exécuter l’ingestion du flux de données.



## Valider l’ingestion

Au bout de quelques minutes, l’exécution du flux de données devrait s’exécuter et vous devriez voir une réussite.

![Statut d’exécution du flux de données indiquant une ingestion de compte client réussie](assets/fixing-errors-successful-customer-account-ingestion.png "Ingestion de compte client réussie")



## Écran de surveillance

1. Accédez à l’écran de surveillance en cliquant sur le rail de gauche sur l’icône **Surveillance** sous la section **Gestion des données**.
1. Cliquez sur la vignette **Sources**, puis faites défiler la barre inférieure pour afficher les détails de l’exécution du flux de données. Notez ce qui suit :
   - **Enregistrements reçus :** 20 enregistrements ont été reçus de la source pour traitement
   - **Enregistrements ingérés :** 20 enregistrements ont été ingérés dans le lac de données après le mappage et le traitement des données.
   - **Échec des enregistrements :** Vous devriez voir un 0 ici. Cela représente le nombre total d’erreurs INGEST et DCVS. Cela exclut les avertissements du MAPPEUR.
   - **Taux d&#39;ingestion :** il s&#39;agit du ratio des enregistrements ingérés par rapport aux enregistrements reçus. 100 % des enregistrements reçus ont été traités avec succès

![Carte Sources sur l’écran de surveillance affichant les enregistrements reçus, ingérés et en échec](assets/fixing-errors-sources-ingestion-metrics.png "Mesures d’ingestion des sources")

>[!NOTE]
>
>Lorsque l’ingestion de données partielle est activée, le **Taux d’ingestion** pour une exécution de flux de données spécifique peut être &lt;100 % jusqu’au seuil que vous avez défini dans les détails du flux de données. N’oubliez pas non plus que le taux de réussite sera de 100 % pour les exécutions de flux de données pour lesquelles aucune donnée n’a été ingérée.

>[!NOTE]
>
>Les enregistrements ne peuvent pas être perdus.
>
>**Enregistrements reçus** = **Enregistrements ingérés** + **Enregistrements ayant échoué**
>
>**Taux d’ingestion = Enregistrements ingérés / Enregistrements reçus**
>
>**Seuil d’ingestion partielle = Enregistrements en échec / Enregistrements reçus**



## Identités

Cliquez sur la carte **Identités**, puis faites défiler la barre inférieure pour afficher les détails granulaires de l’exécution du flux de données. Notez ce qui suit sur Identity Service :

- **Enregistrements reçus :** 20 enregistrements ont été reçus par le *magasin d’identités*, car il surveillait les nouveaux lots, c’est-à-dire que le jeu de données était marqué pour le profil.
- **Enregistrements ingérés :** 20 enregistrements ont été ingérés (c.-à-d. traités pour les informations d’identité)
- **Enregistrements ignorés :** aucun, car nous n’avions pas d’enregistrements d’identité uniques ou d’enregistrements avec de nouvelles relations d’identité.
- **Taux de succès (disponible uniquement dans la carte) :** Il s’agit du ratio des enregistrements reçus par rapport aux enregistrements ingérés.
- **Identités ajoutées :** 40 identités (20 chacune pour l&#39;ID de client et 20 pour l&#39;adresse e-mail) ont été ajoutées au graphique d&#39;identité global pour le profil client en temps réel
- **Graphiques créés :** 20 graphiques uniques ont été créés en fonction des enregistrements traités (c’est-à-dire des relations trouvées dans chaque ligne de données)
- **Graphiques mis à jour :** permet de savoir si des identités ont été ajoutées à un graphique.

![Carte Identités sur l’écran de surveillance affichant les mesures du graphique d’identités](assets/fixing-errors-identity-service-ingestion-metrics.png "mesures d’ingestion du service d’identités")



## Profils

Cliquez sur la vignette **Profils**, puis faites défiler la barre inférieure pour afficher les détails de l’exécution du flux de données. Notez ce qui suit sur le service de profil :

- **Enregistrements reçus :** 20 enregistrements ont été reçus par la banque de profils pour traitement
- **Échec des enregistrements :** aucun enregistrement n’a échoué. Mais s’ils avaient échoué, vous savez que c’était une ingestion dans le problème de Profile.
- **Fragments de profil créés :** 20 fragments de profil ont été créés
- **Fragments de profil mis à jour :** 20 fragments de profil au total ont été touchés
- **Taux de réussite :** Il s’agit de 100 %. Il s’agit du ratio enregistrements ayant échoué par rapport aux enregistrements reçus.

>[!NOTE]
>
>Notez que la mesure **Enregistrements ignorés** n’est pas disponible pour le profil.

![Carte Profils sur l’écran de surveillance affichant les mesures de fragment de profil](assets/fixing-errors-profile-service-ingestion-metrics.png "mesures d’ingestion du service de profil")

>[!NOTE]
>
>Notez qu’il existe une carte Destination avec des mesures similaires à celles que nous avons explorées dans cet atelier. Ces mesures n’ont de sens qu’une fois que vous avez activé une audience ou un jeu de données.
