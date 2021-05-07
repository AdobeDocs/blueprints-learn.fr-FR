---
title: Plan directeur d’analyse de déviation d’appel
description: Analysez le comportement d’un client avant qu’il ne contacte le centre d’appel.
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 9fe9d67c5f97b633e45155bd54e2006f1b797332
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Plan directeur d’analyse du parcours de déviation des appels

Analysez le comportement d’un client sur son ordinateur et son mobile avant qu’il ne contacte le centre d’appel. Identifiez les opportunités pour améliorer le parcours client en comprenant les actions que vos clients tentent de réaliser, les contenus qu’ils consultent et les termes qu’ils recherchent avant de contacter le service clientèle. Déterminez le contenu et les outils en libre-service qui peuvent être améliorés pour aider vos clients à résoudre les problèmes sans devoir appeler.

## Cas d’utilisation

* Analysez le comportement des clients avant qu’ils ne contactent le service clientèle
* Découvrez des opportunités pour améliorer les capacités en libre-service

## Applications

* Adobe Experience Platform
* Customer Journey Analytics

## Modèles d’intégration

* Adobe Experience Platform → Customer Journey Analytics

## Architecture

<img src="assets/CJA.svg" alt="Architecture de référence pour le plan directeur de Customer Journey Analytics" style="border:1px solid #4a4a4a" />

## Étapes d’implémentation

1. [Créez des schémas pour les données à ingérer.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. [Créez des jeux de données pour les données à ingérer.](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html)
1. [Ingérez les données dans Experience Platform.
](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
Les données doivent être ingérées dans Platform avant d’être ingérées dans Customer Journey Analytics.
1. Analysez les jeux de données d’événements cross-canal.
Les jeux de données analysés en union doivent avoir un identifiant d’espace de noms commun ou être recréés via la capacité d’assemblage basée sur le champ de Customer Journey Analytics. 

   >[!NOTE]
   >
   >Customer Journey Analytics n’utilise actuellement pas le profil d’Experience Platform ou les services d’identités pour l’assemblage.

1. Effectuez toute préparation de données personnalisées ou réalisez sur les données l’assemblage d’identité basé sur le champ pour garantir qu’une clé commune à tous les ensembles de données de séries chronologiques est ingérée dans Customer Journey Analytics.
1. Fournissez un identifiant principal pour les données de recherche, qui peut être joint à un champ dans les données d’événement. Chaque ID représente une ligne dans la licence.
1. Définissez le même ID principal pour les données de profil que pour les données d’événement.
1. Configurez une connexion de données pour ingérer des données depuis Experience Platform vers Customer Journey Analytics. Une fois que les données arrivent dans le lac de données, elles sont traitées dans Customer Journey Analytics en 90 minutes.
1. Configurez une vue de données sur la connexion pour sélectionner les dimensions et les mesures spécifiques à inclure dans la vue. Les paramètres d’attribution et d’affectation sont également configurés dans la vue des données. Ces paramètres sont calculés au moment du rapport.
1. Créez un projet pour configurer des tableaux de bord et des rapports dans Analysis Workspace.

## Considérations de mise en œuvre

### Considérations relatives à l’assemblage basé sur l’identité

* Les données de série temporelle à fusionner doivent avoir le même espace de noms d’identifiant sur chaque enregistrement. Pour connecter les données du centre d’appel à des données d’appareil anonyme, l’identifiant numérique doit être relié à l’identifiant d’appel. Cette liaison peut être réalisée à travers divers mécanismes possibles :
   * Le numéro d’appel étant un numéro unique pour ce visiteur pour cette période, avec une table de recherche pour suivre la relation.
   * Exigez de l’utilisateur qu’il s’authentifie avant de demander une assistance et associez cette authentification à un identifiant déterminé par l’agent d’appel (par exemple, numéro de téléphone ou e-mail).
   * Utilisez un partenaire d’intégration pour vous aider à saisir des identifiants d’appareil en ligne avec des identifiants connus liés à la demande d’assistance.
* Le processus d’assemblage de jeux de données disparates nécessite une clé principale de personne / entité commune à tous les jeux de données.
* Les unions basées sur des clés secondaires ne sont actuellement pas prises en charge.
* Le processus d’assemblage basé sur l’identité permet de ressaisir les identités dans les lignes en fonction des informations d’ID transitoires suivants, tels qu’un ID d’authentification. Cela permet de relier des données disparates à un identifiant unique pour une analyse au niveau de la personne plutôt qu’au niveau de l’appareil ou du cookie.
* L’assemblage a lieu une fois par semaine, avec une relecture après l’opération.

## FAQ

* Quels sont les impacts en aval des modèles de données dans Customer Journey Analytics ?

   Les objets et attributs du même champ XDM fusionnent en une seule dimension dans Customer Journey Analytics. Pour fusionner plusieurs attributs de divers jeux de données dans la même dimension CJA, les jeux de données doivent référencer le même champ ou schéma XDM.

## Documentation connexe

* [Description de Customer Journey Analytics](https://helpx.adobe.com/fr/legal/product-descriptions/customer-journey-analytics.html)
* [Documentation sur Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html?lang=fr)
* [Tutoriels sur Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html?lang=fr)
