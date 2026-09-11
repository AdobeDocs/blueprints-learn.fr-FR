---
hold: true
title: Obtenir les groupes de champs standard
description: Exécutez une requête dans l’API du registre des schémas globaux pour rechercher et enregistrer les $id des groupes de champs XDM standard nécessaires à la création d’un schéma de profil client.
doc-type: article
solution: Experience Platform
exl-id: 62017ece-eef2-4785-afed-5c690c00ed02
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Obtenir les groupes de champs standard

>[!NOTE]
>
>**« Groupe de champs »** était auparavant appelé **« Mixin »** ces termes peuvent donc être utilisés de manière interchangeable dans les requêtes d’API et le guide.



## Demander des groupes de champs standard XDM

1. Cliquez sur `Step 1 - Get XDM Standard Field Groups` appel API dans le dossier `XDM Schema Lab -> Create Schema`
1. Exécutez l’appel en cliquant sur le bouton `Send` .



**Requête**

![Étape 1 - Obtenir la requête API des groupes de champs standard XDM](assets/get-standard-field-groups-step-1-request.jpeg "Étape 1 - Requête")

>[!NOTE]
>
>Notez l’utilisation de `global` valeur dans l’URL des requêtes ci-dessous :
>
>https\://platform.adobe.io/data/foundation/schemaregistry/**global**/mixins
>
>`global` est utilisé pour demander uniquement des composants standard XDM (groupe de champs/mixin dans ce cas). Le registre XDM d’Experience Platform comporte deux types de propriétaires : Adobe et Client (c’est-à-dire personnalisé).
>
>- Les objets créés par Adobe utilisent toujours le mot `global` dans toute liste XDM ou requête de recherche
>- Les objets créés par le client (c’est-à-dire personnalisés) utilisent toujours le mot `tenant` dans toute liste XDM ou tout appel de recherche



**Réponse**

![Réponse de l’API répertoriant les groupes de champs standard XDM](assets/get-standard-field-groups-step-1-response.png "Étape 1 Réponse")


## Identifier les groupes de champs standard XDM obligatoires

Un schéma est toujours composé d’un ou de plusieurs groupes de champs et d’une classe .  Pour le schéma Profil individuel de connexion 5G, recherchez les groupes de champs XDM standard requis pour le schéma.

- Détails démographiques
- Coordonnées personnelles
- Détails relatifs au consentement et aux préférences



1. Rechercher le groupe de champs `Demographic Details` dans la réponse de l’appel
1. Copiez le `$id` du groupe de champs et enregistrez-le quelque part pour vous y référer ultérieurement
1. Répétez les étapes 1 et 2 pour les deux autres groupes de champs répertoriés ci-dessus

![Groupe de champs Détails démographiques situé dans la réponse de l’API](assets/get-standard-field-groups-demographic-details-field-group.png)

>[!WARNING]
>
>Ne continuez pas tant que vous n’avez pas enregistré les trois (3) `$ids` quelque part.  Ils seront nécessaires ultérieurement pour créer le schéma Compte client
