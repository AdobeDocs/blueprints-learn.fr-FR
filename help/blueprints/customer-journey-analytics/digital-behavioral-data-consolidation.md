---
title: Analyse de Parcours entre Canaux
description: Analysez et obtenez des informations à partir des interactions des clients sur lʼensemble du parcours client.
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
translation-type: tm+mt
source-git-commit: b0664edc3d29d693d33eefc3b3c6da8bf7308224
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 2%

---

# Modèle d&#39;Analyse entre Parcours

Disposer d’une vue consolidée unique du comportement des clients sur différents canaux en unifiant les données issues de diverses propriétés web, mobiles et hors ligne.

## Cas d’utilisation

* Analysez les interactions des clients sur les ordinateurs de bureau et les appareils mobiles afin de comprendre le comportement des clients et d’extraire des informations pour optimiser les expériences client numériques.
* Analyser les interactions des clients entre les canaux, y compris les canaux numériques et hors ligne, tels que les interactions d&#39;assistance et les achats en magasin, afin de mieux comprendre et d&#39;optimiser le parcours client. 

## Applications

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics (facultatif)

## Modèles d’intégration

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics → Adobe Experience Platform → Customer Journey Analytics

## Architecture

<img src="assets/CJA.svg" alt="Architecture de référence du plan directeur Customer Journey Analytics" style="border:1px solid #4a4a4a" />

## Gardiens

Ingestion des données dans le Customer Journey Analytics :

* Extraction de données au lac : API ~ 7 Go/heure, connecteur source ~ 200 Go/heure, flux jusqu&#39;au lac ~ 15 minutes, connecteur source Adobe Analytics jusqu&#39;au lac ~ 45 minutes.
* Une fois les données publiées sur le lac de données, le traitement en Customer Journey Analytics peut prendre jusqu’à 90 minutes.

## Etapes de mise en oeuvre

1. Configurez des jeux de données et des schémas.
1. Envoi de données dans la plate-forme.
Les données doivent être ingérées dans la plateforme avant d’être traitées dans le Customer Journey Analytics.
1. Analyser les jeux de données de événement sur plusieurs canaux à analyser en union pour s&#39;assurer qu&#39;ils ont un ID d&#39;espace de nommage commun ou qu&#39;ils sont récupérés grâce à la fonction de raccordement basée sur les champs du Customer Journey Analytics. 

   >[!NOTE]
   >
   >Customer Journey Analytics n’utilise actuellement pas les services Profil Experience Platform ou Identity pour l’assemblage.

1. Effectuez toute préparation personnalisée des données ou l&#39;utilisation de l&#39;assemblage d&#39;identité basé sur les champs sur les données pour garantir qu&#39;une clé commune entre les jeux de données de séries chronologiques soit assimilée à un Customer Journey Analytics.
1. Attribuez aux données de recherche un Principal ID pouvant être joint à un champ dans les données du événement. Compte sous forme de lignes dans la licence.
1. Définissez le même ID Principal pour les données de profil que l’ID Principal des données de événement.
1. Configurez une connexion aux données pour assimiler les données de l’Experience Platform au Customer Journey Analytics. Une fois les données arrivées dans le lac de données, elles se transforment en Customer Journey Analytics dans les 90 minutes.
1. Configurez une vue de données sur la connexion pour sélectionner les dimensions et mesures spécifiques à inclure dans la vue. Les paramètres d’attribution et d’attribution sont également configurés dans la vue de données. Ces paramètres sont calculés au moment du rapport.
1. Créez un projet pour configurer des tableaux de bord et des rapports dans Analysis Workspace.

## Considérations relatives à la mise en oeuvre

### Points à prendre en compte concernant le crénage d’identité

* Les données de série chronologique à unifier doivent avoir le même espace de nommage d’ID sur chaque enregistrement.
* Le processus d&#39;union d&#39;unification des jeux de données disparates nécessite une clé de personne/entité Principale commune dans tous les jeux de données.
* Actuellement, les unions Secondaires basées sur des clés ne sont pas prises en charge.
* Le processus d’assemblage d’identité basé sur les champs permet de saisir des identités dans des lignes en fonction d’enregistrements d’ID transitoires ultérieurs, tels qu’un ID d’authentification. Cela permet de résoudre des enregistrements disparates en un seul identifiant pour l’analyse au niveau de la personne plutôt qu’au niveau du périphérique ou du cookie.
* Le piqûre se produit une fois par semaine, avec une relecture après le point de suture.

## FAQ

* Quels sont les impacts en aval des modèles de données en Customer Journey Analytics ?

   Les objets et les attributs d’un même champ XDM fusionnent en une seule dimension dans le Customer Journey Analytics. À  fusionner plusieurs attributs de divers jeux de données dans la même dimension de Customer Journey Analytics, les jeux de données doivent référencer le même champ ou schéma XDM.

## Documentation connexe

* [Description du produit Customer Journey Analytics](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Documentation Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Didacticiels Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
