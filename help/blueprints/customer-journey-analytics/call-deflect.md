---
title: Scénario d'Analyse par défaut d'appel
description: Analysez le comportement des clients avant de contacter le centre d’appels.
solution: Experience Platform, Customer Journey Analytics
kt: 7209
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# Scénario d&#39;Analyse de l&#39;Parcours de défection d&#39;appel

Analysez le comportement d’un client sur un ordinateur de bureau ou sur un périphérique mobile avant de contacter le centre d’appels. Identifiez les opportunités d&#39;amélioration du parcours client en comprenant les actions que vos clients essaient de réaliser, le contenu qu&#39;ils vues et les termes qu&#39;ils recherchent avant de contacter l&#39;assistance clientèle. Déterminez le contenu et les outils en libre-service qui peuvent être améliorés pour aider vos clients à résoudre les problèmes sans avoir à appeler.

## Cas d’utilisation

* Analyser le comportement des clients avant de contacter l&#39;assistance clientèle
* Découvrir les opportunités d&#39;amélioration des capacités en libre-service

## Applications

* Adobe Experience Platform
* Customer Journey Analytics

## Modèles d’intégration

* Adobe Experience Platform → Customer Journey Analytics

## Architecture

<img src="assets/CJA.svg" alt="Architecture de référence du plan directeur Customer Journey Analytics" style="border:1px solid #4a4a4a" />

## Gardiens

Ingestion des données dans le Customer Journey Analytics :

* Extraction de données au lac : API ~ 7 Go/heure, connecteur source ~ 200 Go/heure, flux vers le lac ~ 15 minutes, connecteur source Analytics vers le lac ~ 45 minutes.
* Une fois les données publiées sur le lac de données, le traitement en Customer Journey Analytics peut prendre jusqu’à 90 minutes.

## Etapes de mise en oeuvre

1. Configurez des jeux de données et des schémas.
1. Envoi de données dans la plate-forme.
Les données doivent être ingérées dans la plate-forme avant leur assimilation dans le Customer Journey Analytics.
1. Analyser les jeux de données de événement sur plusieurs canaux.
Les jeux de données analysés en union doivent avoir un ID d&#39;espace de nommage commun ou être récupérés par l&#39;intermédiaire de la fonction de raccordement basée sur les champs du Customer Journey Analytics. 

   >[!NOTE]
   >
   >Customer Journey Analytics n’utilise actuellement pas les services Profil Experience Platform ou Identity pour l’assemblage.

1. Effectuez toute préparation personnalisée des données ou l&#39;utilisation de l&#39;assemblage d&#39;identité basé sur le champ sur les données, afin de garantir qu&#39;une clé commune entre les jeux de données de séries chronologiques soit assimilée au Customer Journey Analytics.
1. Indiquez un identifiant Principal pour les données de recherche, qui peuvent être jointes à un champ dans les données du événement. Compte sous forme de lignes dans la licence.
1. Définissez le même ID Principal sur les données de profil que l’ID Principal des données de événement.
1. Configurez une connexion aux données pour assimiler les données de l’Experience Platform au Customer Journey Analytics. Une fois les données arrivées dans le lac de données, elles se transforment en Customer Journey Analytics dans les 90 minutes.
1. Configurez une vue de données sur la connexion pour sélectionner les dimensions et mesures spécifiques à inclure dans la vue. Les paramètres d’attribution et d’attribution sont également configurés dans la vue de données. Ces paramètres sont calculés au moment du rapport.
1. Créez un projet pour configurer des tableaux de bord et des rapports dans Analysis Workspace.

## Considérations relatives à la mise en oeuvre

### Points à prendre en compte concernant le crénage d’identité

* Les données de séries chronologiques à unifier doivent avoir le même espace de nommage d’ID sur chaque enregistrement. Pour connecter les données du centre d’appels aux données anonymes du périphérique, l’ID numérique doit être lié à l’ID d’appel. Ce lien peut se produire par le biais de plusieurs mécanismes possibles :
   * Numéro de numérotation unique pour ce visiteur pour cette période, accompagné d’une table de choix pour suivre la relation.
   * Exigez que l’utilisateur s’authentifie avant de demander de l’assistance et liez cette authentification à un identifiant déterminé par l’agent d’appel (par exemple, le numéro de téléphone ou le courriel).
   * Utilisez un partenaire d&#39;intégration pour vous aider à taper des identifiants de périphérique en ligne avec des identifiants connus liés à la demande de prise en charge.
* Le processus d&#39;union d&#39;unification des jeux de données disparates nécessite une clé de personne/entité Principale commune dans tous les jeux de données.
* Actuellement, les unions Secondaires basées sur des clés ne sont pas prises en charge.
* Le processus d’assemblage d’identité basé sur les champs permet de saisir des identités dans des lignes en fonction d’enregistrements d’ID transitoires ultérieurs, tels qu’un ID d’authentification. Ce processus permet de résoudre des enregistrements disparates en un seul identifiant pour l’analyse au niveau de la personne plutôt qu’au niveau du périphérique ou du cookie.
* Le piqûre se produit une fois par semaine, avec une relecture après le point de suture.

## FAQ

* Quels sont les impacts en aval des modèles de données en Customer Journey Analytics ?

   Les objets et les attributs d’un même champ XDM fusionnent en une seule dimension dans le Customer Journey Analytics. Pour fusionner plusieurs attributs de divers jeux de données dans la même dimension CJA, les jeux de données doivent référencer le même champ ou schéma XDM.

## Documentation connexe

* [Description du produit Customer Journey Analytics](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Documentation Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Didacticiels Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
