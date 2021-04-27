---
title: Plan d'Audience Activation en ligne/hors ligne
description: Audience Activation en ligne / hors ligne
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 2f35195b875d85033993f31c8cef0f85a7f6cccc
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 35%

---

# Plan d&#39;Audience Activation en ligne/hors ligne

Utilisez les attributs et les événements hors ligne tels que les commandes hors ligne, les transactions, la gestion de la relation client (CRM) ou les données sur la fidélité, combinés avec le comportement en ligne pour le ciblage et la personnalisation en ligne.

Activez des audiences vers des destinations connues basées sur le profil telles que les fournisseurs de messagerie électronique, les réseaux sociaux et les destinations publicitaires

## Cas d’utilisation

* Ciblage d’audience pour des audiences connues sur les réseaux sociaux et les destinations publicitaires.
* Personnalisation en ligne avec des attributs en ligne et hors ligne.
* Activez des audiences vers des canaux connus, tels que la messagerie électronique et les SMS.

## Applications

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]

## Architecture

<img src="assets/onoff.svg" alt="Architecture de référence pour le plan directeur des Audiences Activation en ligne/hors ligne" style="border:1px solid #4a4a4a" />

## Garde-fous

* [Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

### Gardiens pour l’évaluation et l’Activation des segments

| Type de segmentation | Fréquence | Débit | Latence (évaluation des segments) | Latence (Activation de segment) | Charge utile Activation |
|-|-|-|-|-|-|-|-|-|
| Segmentation Edge | La segmentation Edge est actuellement en version bêta et permet une segmentation en temps réel valide à évaluer sur le réseau Edge Experience Platform pour une prise de décision en temps réel sur la même page via Adobe Target et Adobe Journey Optimizer. |  | ~100 ms | Disponible immédiatement pour la personnalisation en Adobe Target, pour les recherches de profil dans le Profil Edge et pour l&#39;activation via des destinations basées sur des cookies. | Appartenances aux Audiences disponibles sur le bord pour les recherches de profil et les destinations basées sur les cookies.<br>Audience Les adhésions et les attributs de Profil sont disponibles pour Adobe Target et Journey Optimizer.  |
| Segmentation en flux continu | Chaque fois qu’un nouveau événement ou enregistrement de diffusion en continu est assimilé au profil client en temps réel et que la définition de segment est un segment de diffusion en continu valide. <br>Voir la  [documentation sur la ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr) segmentation pour obtenir des instructions sur les critères de segmentation en flux continu. | Jusqu&#39;à 1500 événements par seconde.  | ~ p95 &lt;5min | Destinations de diffusion en continu : Les adhésions aux audiences en flux continu sont activées en moins de 10 minutes environ ou micro-par lot selon les exigences de la destination.<br>Destinations planifiées : Les abonnements aux audiences en flux continu sont activés par lots en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |
| Segmentation incrémentielle | Une fois par heure pour les nouvelles données qui ont été ingérées dans le profil client en temps réel depuis la dernière évaluation incrémentielle ou par lot. |  |  | Destinations de diffusion en continu : Les adhésions à des audiences incrémentielles sont activées dans un délai d&#39;environ 10 minutes ou par micro-lot en fonction des exigences de la destination.<br>Destinations planifiées : Les adhésions aux audiences incrémentielles sont activées par lot en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience et valeurs d’identité uniquement.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |
| Segmentation par lots | Une fois par jour, en fonction d&#39;un calendrier prédéfini du système, ou d&#39;un appel ad hoc lancé manuellement via l&#39;API. |  | Environ une heure par emploi pour un magasin de profils de 10 To, 2 heures par emploi pour un magasin de profils de 10 à 100 To. Les performances de la tâche de segment par lot dépendent du nombre de profils, de la taille des profils et du nombre de segments évalués. | Destinations de diffusion en continu : Les adhésions à l&#39;audience par lot sont activées dans les 10 heures suivant la fin de l&#39;évaluation de la segmentation ou par micro-lot selon les exigences de la destination.<br>Destinations planifiées : Les adhésions à l’audience par lot sont activées en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience et valeurs d’identité uniquement.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |

### Gardiens pour le partage d’Audiences entre applications

| Intégrations des applications d&#39;Audience | Fréquence | Débit/volume | Latence (évaluation des segments) | Latence (Activation de segment) |
|-|-|-|-|-|-||
| Plate-forme de données client en temps réel vers l&#39;Audience Manager | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | Dans les minutes qui suivent l&#39;achèvement de l&#39;évaluation du segment.<br>La synchronisation initiale de la configuration des audiences entre la plateforme de données client en temps réel et l’Audience Manager prend environ 4 heures.<br>Les adhésions d’audience réalisées au cours de la période de 4 heures sont consignées à l’Audience Manager sur la tâche de segmentation par lots suivante en tant qu’adhésions d’audience &quot;existantes&quot;. |
| Adobe Analytics à l&#39;Audience Manager |  | Par défaut, 75 audiences au maximum peuvent être partagées pour chaque suite de rapports Adobe Analytics. Si une licence d’Audience Manager est utilisée, il n’y a aucune limite au nombre d’audiences pouvant être partagées entre Adobe Analytics et Adobe Target ou Adobe Audience Manager et Adobe Target. |  |  |
| Adobe Analytics à la plateforme de données client en temps réel | Non disponible actuellement | Non disponible actuellement | Non disponible actuellement | Non disponible actuellement |





## Étapes d’implémentation

1. Configuration des schémas et des jeux de données dans Experience Platform.
1. Configurez les identités et les espaces de noms d’identité corrects sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.
1. Activez le schéma et les jeux de données pour le profil.
1. Ingérez les données dans Platform.
1. Fournissez [!UICONTROL Plate-forme de données client en temps réel] le partage de segments entre l’Experience Platform et l’Audience Manager pour que les audiences définies dans l’Experience Platform soient partagées à l’Audience Manager.
1. Créez des segments dans Experience Platform, pour une évaluation en lot ou en flux. Le système détermine automatiquement si le segment est évalué en tant que lot ou en tant que flux continu.
1. Configurez les destinations pour le partage des attributs de profil et des appartenances à une audience vers les destinations souhaitées.

## Considérations de mise en œuvre

* Le partage des données de profil avec les destinations nécessite que vous incluiez la valeur d’identité spécifique utilisée par la destination dans la payload de destination. Toute identité nécessaire pour une destination de cible doit être assimilée à Platform et configurée en tant qu&#39;identité pour le [!UICONTROL Profil client en temps réel].

* Pour les scénarios d’activation où les audiences sont partagées entre Experience Platform et Audience Manager, toutes les identités incluses dans le [!UICONTROL profil client en temps réel] sont partagées avec Audience Manager. Les audiences d’Experience Platform peuvent être partagées via les destinations d’Audience Manager lorsque les identités de destination requises sont incluses dans le [!UICONTROL profil client en temps réel], ou lorsque les identités du [!UICONTROL profil client en temps réel] peuvent être reliées aux identités de destination requises qui sont liées dans Audience Manager.

## Documentation connexe

* [Description de Real-time Customer Data Platform](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Directives sur le profil et la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=fr)

## Vidéos et tutoriels connexes

* [Présentation de Real-time Customer Data Platform ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=fr)
* [[!UICONTROL Vidéo de démonstration de Real-time Customer Data Platform ]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=fr)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr)
