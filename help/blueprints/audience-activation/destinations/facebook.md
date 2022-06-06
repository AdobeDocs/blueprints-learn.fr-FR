---
title: Activation des audiences personnalisées Facebook
description: Activation des audiences personnalisées Facebook.
solution: Real-time Customer Data Platform, Data Collection
kt: 7086
exl-id: b75a7a01-04ba-4617-960d-f73f7a9cc6c7
source-git-commit: 6fa38772f77ffd565580db55f8f2889b0e703949
workflow-type: ht
source-wordcount: '957'
ht-degree: 100%

---

# Activation des audiences personnalisées Facebook

Ingérez des données client à partir de plusieurs sources afin de créer une vue de profil unique du client, de segmenter ces profils en audiences conçues pour le marketing et la personnalisation, de partager ces audiences sur les réseaux publicitaires sociaux tels que Facebook afin de cibler et de personnaliser des campagnes en fonction de ces audiences.

## Cas d’utilisation

* Ciblage d’audience pour des audiences connues sur les réseaux sociaux et les destinations publicitaires.
* Personnalisation en ligne avec des attributs en ligne et hors ligne.

## Applications

* Real-time Customer Data Platform

## Architecture

<img src="../assets/facebook.svg" alt="Architecture de référence d’activation d’audience Facebook personnalisée" style="width:90%; border:1px solid #4a4a4a" />

## Étapes d’implémentation

1. Configurez les espaces de noms d’identité à utiliser dans les sources de données Profile.
   * Utilisez les espaces de noms prêts-à-l’emploi tels que Email, Email SHA256 Hash, le cas échéant.
   * Facebook comporte une liste des identités prises en charge. Pour activer les audiences personnalisées Facebook, l’une des identités prises en charge doit être présente dans les profils à activer.
   * Les identités suivantes sont actuellement prises en charge par Facebook : GAID, IDFA, phone_sha256, email_lc_sha256, extern_id.
   * Pour plus d’informations, consultez le [Guide de destination Facebook](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/social/facebook.html?lang=fr).
   * Créez des espaces de noms personnalisés dans lesquels les espaces de noms prêts à l’emploi ne sont pas disponibles pour les identités applicables.
1. Configurez les jeux de données et les schémas de source de données de profil.
   * Créez des schémas d’enregistrement de profil pour toutes les données de source d’enregistrement de profil.
      * Indiquez l’identité principale et les identités secondaires de chaque schéma.
      * Activez le schéma pour l’ingestion des profils.
   * Créez des jeux de données d’enregistrement de profil pour toutes les données de source d’enregistrement de profil, en attribuant le schéma associé.
      * Activez le jeu de données pour l’ingestion de profils.
   * Créez des schémas d’événement d’expérience de profil pour toutes les données sources basées sur des séries temporelles de profil.
      * Indiquez l’identité principale et les identités secondaires du schéma.
   * Activez le schéma pour l’ingestion des profils.
   * Créez des jeux de données d’événement d’expérience de profil pour toutes les données de source d’événement d’expérience de profil, en attribuant le schéma associé.
      * Activez le jeu de données pour l’ingestion de profils.
1. Ingérez les données source à l’aide d’un connecteur source dans le jeu de données associé configuré ci-dessus.
   * Configurez le compte du connecteur source avec les informations d’identification.
   * Configurez un flux de données pour ingérer les données du fichier source ou de l’emplacement du dossier selon une planification spécifiée dans le jeu de données spécifié.
   * Mappez tous les champs des données source au schéma cible.
   * Transformez tous les champs pour qu’ils soient dans un format adapté à l’ingestion dans Experience Platform.
      * Convertissez les dates.
      * Passez le texte en minuscules le cas échéant, par exemple pour une adresse électronique.
      * Adaptez les modèles (numéro de téléphone, par exemple).
      * Ajoutez des identifiants d’enregistrement uniques pour les enregistrements d’événement d’expérience s’ils ne sont pas présents dans les données source.
      * Transformez les tableaux et les champs de type map pour assurer le mappage et la modélisation corrects des tableaux et des mappages pour la segmentation dans Experience Platform.
1. Configurez la stratégie de fusion de profils pour garantir la configuration correcte du graphique d’identités et des jeux de données à inclure dans la fusion des profils.
1. Une fois les flux de données exécutés, vérifiez que l’ingestion des données de profil s’est déroulée sans erreur.
   * Inspectez le graphique d’identités de plusieurs profils afin de garantir que le traitement des relations d’identité a été correctement réalisé.
   * Inspectez les attributs et les événements de plusieurs profils pour garantir que l’ingestion des attributs et des événements vers les profils a été correctement réalisée.
1. Créez des segments pour créer des audiences de profil.
   * Créez des segments dans le créateur de segments à l’aide de règles par rapport aux attributs et aux événements.
   * Enregistrez le segment à des fins d’évaluation. Les segments sont évalués selon la planification spécifiée une fois par jour.
      * Si les règles de segment sont éligibles à la segmentation par flux, le segment est évalué lorsque de nouvelles données de diffusion en continu sont ingérées pour les profils. Les segments en flux continu seront également évalués une fois par jour lors de la segmentation par lots planifiée.
1. Assurez-vous que les résultats du segment sont comme prévu.
   * Examinez le nombre de résultats du segment pour les segments donnés.
   * Examinez le profil qui doit être inclus dans le segment pour vérifier que l’abonnement au segment est inclus dans la partie de l’abonnement au segment du profil.
1. Configurez la diffusion de l’audience vers la destination dans la configuration de la Destination.
   * Consultez le [Guide de destination Facebook](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/social/facebook.html?lang=fr) pour plus d’informations sur la configuration de la destination Facebook.
   * Lors de la configuration d’une destination, sélectionnez l’audience que vous souhaitez activer vers la destination.
   * Déterminez la date de début planifiée à laquelle vous souhaitez que le flux de données de destination commence à diffuser l’audience vers la destination.
   * Chaque destination comporte des attributs obligatoires et facultatifs qui seront envoyés.
      * Pour Facebook, l’une des identités requises doit être incluse et est utilisée pour faire correspondre les profils des audiences dans Experience Platform à un profil pouvant être ciblé par Facebook.
   * Chaque destination possède également un type de diffusion spécifié, qu’il s’agisse d’une diffusion en continu ou par lots, d’un payload basé sur les fichiers ou d’un payload JSON.
      * Pour Facebook, les appartenances aux audiences sont diffusées en continu vers un point d’entrée Facebook au format JSON.
      * Les abonnements à l’audience seront diffusés en continu après l’évaluation de la segmentation par flux ou par lots dans Experience Platform.
1. Assurez-vous que le flux de destination a diffusé l’audience vers la destination comme prévu.
   * Vérifiez l’interface de surveillance pour confirmer que l’audience a été diffusée avec le nombre de profils attendu. La taille de l’audience doit refléter le nombre attendu de profils activés, en notant que des destinations spécifiques telles que Facebook requièrent certains champs, tels qu’une identité de hachage d’e-mail. Si elles ne sont pas présentes dans le profil qui est membre de l’audience, elles ne sont pas activées vers la destination.
   * Recherchez les profils ignorés pour les identités de profil manquantes ou les attributs manquants qui étaient obligatoires.
   * Recherchez d’autres erreurs qui doivent être résolues.
1. Vérifiez que l’audience a été activée vers la destination de fin avec le nombre d’abonnements attendu pour l’audience.
   * Connectez-vous au portail d’audience personnalisée Facebook pour vérifier que l’audience de Real-time Customer Data Platform a été diffusée et que le taux de correspondance des profils de l’audience de Facebook correspond raisonnablement au nombre de profils de l’audience de Real-time Customer Data Platform.

## Garde-fous

[Garde-fous de profil et de segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

## Documentation connexe

Activation des audiences personnalisées Facebook - [Configuration de la destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/social/facebook.html?lang=fr)