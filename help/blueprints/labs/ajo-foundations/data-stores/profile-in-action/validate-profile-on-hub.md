---
hold: true
title: Valider le profil sur le hub
description: Découvrez comment rechercher un profil sur le Hub de profils clients en temps réel et vérifier ses événements et l’appartenance à un segment après un événement diffusé en continu.
doc-type: article
solution: Experience Platform
exl-id: f1c8b1ac-e57c-48c6-aa91-5c83f79ce7e3
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---


# Valider le profil sur le hub

## Objectif d’apprentissage

Vérifiez que l’événement a entraîné une mise à jour du profil et une qualification du segment dans le profil en temps réel sur le Hub.

## Recherche du profil sur le hub

Dans Adobe Experience Platform, recherchez le profil que vous venez d’envoyer à partir de l’événement que vous venez d’envoyer dans Edge Network.

1. Accédez à **Client** -> **Profils** -> **Parcourir** pour effectuer la recherche à l’aide des informations suivantes :
   - **Politique de fusion** -> `Default Timebased`
   - **Espace de noms d’identité** -> `Email`
   - **Valeur de l’identité** -> `henry.creel@emailsim.io`
1. Cliquez sur **Afficher** pour rechercher le profil

![Parcourir l’écran du profil avec les champs de recherche d’identité et de politique de fusion](assets/validate-profile-on-hub-browse-profile-lookup.png)



## Vérifier le profil Hub

1. Cliquez sur le **Identifiant du profil** pour ouvrir le profil
1. Cliquez d’abord sur l’onglet **Attributs** et sur le bouton radio **Hub** pour afficher le profil **Hub**

![Profil Hub affiché dans l’onglet Attributs](assets/validate-profile-on-hub-attributes-tab.png)


## Valider les événements

1. Cliquez sur **Événements** dans le volet de navigation supérieur pour afficher l’événement que vous venez d’envoyer

![Onglet Événements affichant l’événement diffusé sur le profil](assets/validate-profile-on-hub-events-tab.png)

## Validation des segments

### Via JSON

1. Cliquez sur l’en-tête **Attributs** et Afficher **JSON**.

![Vue JSON des attributs de profil affichant segmentMembership](assets/validate-profile-on-hub-json-view.png)

2. Recherchez **segmentMembership**.  Il doit ressembler à ceci (vos identifiants seront différents) :

```json
  "segmentMembership": {
    "ups": {
      "ce0b8386-ef2a-4244-8ad0-1a72d6494181": {
        "status": "realized",
        "lastQualificationTime": "2025-12-15T23:11:49Z"
      },
      "8ce516fe-920a-4f9d-b92b-0403890a8491": {
        "status": "realized",
        "lastQualificationTime": "2025-12-12T15:01:01Z"
      }
    }
```

>[!NOTE]
>
>**Comment lire segmentMembership ?**
>
>[](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/segmentation)
>
>**ups :** il s’agit de la clé de mappage pour les différents types d’audiences pris en charge par AEP.  La clé ups contient les audiences créées par le créateur de règles.  Les autres audiences sont contenues dans d’autres clés (AAM, par exemple).
>
>**lastQualificationTime** Date et heure de la dernière qualification de ce profil pour le segment
>
>**statut**
>
>*réalisé* : le profil est qualifié pour le segment.
>*quitté* : le profil quitte le segment dans le cadre de la requête actuelle.
>
>

### Via l’interface utilisateur

1. Un moyen plus facile de vérifier que le profil s’est qualifié pour les audiences est de consulter l’onglet **Appartenance à l’audience** (vous devriez au moins voir ces éléments) :
   - dep : diffusion en continu de tout événement (au cours de l’heure)
   - dep : tout événement Edge (dans l’heure)

![Onglet Appartenance à l’audience affichant les segments qualifiés](assets/validate-profile-on-hub-audience-membership-tab.png)

>[!NOTE]
>
>**Pourquoi aucune audience par lots ?**
>
>Vous ne devriez pas voir **dep: Any Event Batch (within the day)** qualifié pour car nous avons diffusé en continu des données et l’évaluation des lots se produit une fois par jour.

## Récapituler

Un profil existe sur le Hub et est qualifié pour l’audience attendue.
