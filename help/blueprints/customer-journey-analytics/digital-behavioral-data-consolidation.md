---
title: Analyse de parcours cross-canal
description: Analysez et extrayez des informations sur les interactions client tout au long du parcours client.
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
source-git-commit: 3c950cebaa25901ae50433775c510ed834d8bcd5
workflow-type: ht
source-wordcount: '622'
ht-degree: 100%

---

# Plan directeur pour l’analyse de parcours cross-canal

Ayez une vue consolidée unique du comportement des clients sur différents canaux en unifiant les données de diverses propriétés web, mobiles et hors ligne.

## Cas d’utilisation

* Analysez les interactions des clients sur ordinateurs et appareils mobiles pour comprendre le comportement des clients et extraire des informations pour optimiser les expériences client numériques.
* Analysez les interactions des clients sur tous les canaux, y compris les canaux numériques et hors ligne tels que les interactions d’assistance et les achats en magasin pour mieux comprendre et optimiser le parcours client. 

## Applications

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics (facultatif)

## Modèles d’intégration

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics → Adobe Experience Platform → Customer Journey Analytics

## Architecture

<img src="assets/CJA.svg" alt="Architecture de référence pour le plan directeur de Customer Journey Analytics" style="border:1px solid #4a4a4a" />

## Étapes d’implémentation

1. [Créez des schémas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) pour les données à ingérer.
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) pour les données à ingérer.
1. [Ingérez les données dans Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr).
Les données doivent être ingérées dans Platform avant d’être traitées dans Customer Journey Analytics. Pour plus d’informations sur l’ingestion de données et les types de sources de données, consultez la documentation suivante. [ Sources de données](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=fr) y compris le [connecteur de données Analytics](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=fr). [Tutoriel sur l’ingestion de données](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr)
1. Réalisez une analyse combinée des jeux de données d’événements cross-canal pour assurer qu’ils ont un identifiant d’espace de noms commun ou qu’ils sont recréés via la capacité d’assemblage de Customer Journey Analytics basée sur le champ. Pour plus d’informations sur l’assemblage basé sur l’identité dans Customer Journey Analytics, consultez la documentation sur les analyses cross-canal. [Assemblage basé sur l’identité](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/cca/overview.html?lang=fr)

   >[!NOTE]
   >
   >Customer Journey Analytics n’utilise actuellement pas le profil d’Experience Platform ou les services d’identités pour l’assemblage.

1. Effectuez toute préparation de données personnalisées ou réalisez sur les données l’assemblage d’identité basé sur le champ pour garantir qu’une clé commune à tous les ensembles de données de séries chronologiques est ingérée dans Customer Journey Analytics.
1. Fournissez aux données de recherche un ID principal pouvant être joint à un champ dans les données d’événement. Chaque ID représente une ligne dans la licence.
1. Définissez le même ID principal pour les données de profil que pour les données d’événement.
1. Configurez une connexion de données pour ingérer des données depuis Experience Platform vers Customer Journey Analytics. Une fois que les données arrivent dans le lac de données, elles sont traitées dans Customer Journey Analytics en 90 minutes.
1. Configurez une vue de données sur la connexion pour sélectionner les dimensions et les mesures spécifiques à inclure dans la vue. Les paramètres d’attribution et d’affectation sont également configurés dans la vue des données. Ces paramètres sont calculés au moment du rapport.
1. Créez un projet pour configurer des tableaux de bord et des rapports dans Analysis Workspace.

## Considérations de mise en œuvre

### Considérations relatives à l’assemblage basé sur l’identité

* Les données de série temporelle à fusionner doivent avoir le même espace de noms d’identifiant sur chaque enregistrement.
* Le processus d’assemblage de jeux de données disparates nécessite une clé principale de personne / entité commune à tous les jeux de données.
* Les unions basées sur des clés secondaires ne sont actuellement pas prises en charge.
* Le processus d’assemblage basé sur l’identité permet de ressaisir les identités dans les lignes en fonction des informations d’ID transitoires suivants, tels qu’un ID d’authentification. Cela permet de relier des données disparates à un identifiant unique pour une analyse au niveau de la personne plutôt qu’au niveau de l’appareil ou du cookie.
* L’assemblage a lieu une fois par semaine, avec une relecture après l’opération.

## FAQ

* Quels sont les impacts en aval des modèles de données dans Customer Journey Analytics ?

   Les objets et attributs du même champ XDM fusionnent en une seule dimension dans Customer Journey Analytics. Pour fusionner plusieurs attributs de divers jeux de données dans la même dimension Customer Journey Analytics, les jeux de données doivent référencer le même champ ou schéma XDM.

## Documentation connexe

* [Description de Customer Journey Analytics](https://helpx.adobe.com/fr/legal/product-descriptions/customer-journey-analytics.html)
* [Documentation sur Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html?lang=fr)
* [Tutoriels sur Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html?lang=fr)
