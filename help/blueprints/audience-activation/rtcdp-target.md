---
title: Real-time Customer Data Platform et Adobe Target
description: Intégrez des profils et des audiences RTCDP à Adobe Target.
landing-page-description: Intégrez des profils et des audiences RTCDP à Adobe Target.
short-description: Intégrez des profils et des audiences RTCDP à Adobe Target.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: b634e14af3ea60e0f4cc9e84a0ef896df293a8c7
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 32%

---


# Intégration de Real-time Customer Data Platform à Adobe Target

## Cas d’utilisation

* Personnalisation en ligne avec des données client connu
* Optimisation de la page de destination
* Personnalisation en fonction des vues précédentes de produit ou de contenu, de l’affinité produit/contenu, des attributs environnementaux et des données démographiques, en plus des informations hors ligne telles que les transactions, les données de fidélité et de gestion de la relation client (CRM), ainsi que des informations modélisées
* Partager et cibler des audiences définies dans Real-time Customer Data Platform sur des sites web et des applications mobiles à l’aide d’Adobe Target

## Applications

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target

### Documentation de référence

* [Connexion Adobe Target pour Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Configuration du flux de données Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=fr)

## Modèles d’intégration

| Motif d’intégration | Fonctionnalité | Conditions préalables |
|--------------------|------------|---------------|
| **Évaluation des segments en temps réel sur Edge, partagée de Real-time Customer Data Platform vers Target** | - Évaluez les audiences en temps réel pour la personnalisation de la même page ou de la page suivante sur Edge. <br>- Tous les segments évalués en flux continu ou par lots seront également projetés dans Edge Network pour être inclus dans l’évaluation et la personnalisation des segments Edge. | - Web/Mobile SDK doit être implémenté pour l’API Edge Network Server. <br>- Le flux de données doit être configuré dans Experience Edge avec l’extension Target et Experience Platform activée. <br>- La destination cible doit être configurée dans les destinations Real-time Customer Data Platform. <br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform. |
| **Partage d’audiences par lots et en flux continu depuis Real-time Customer Data Platform vers Target via l’approche Edge** | - Partagez des audiences en continu et par lots à partir de Real-time Customer Data Platform vers Target par le biais d’Edge Network. <br>- Les audiences évaluées en temps réel nécessitent l’implémentation de Web SDK et d’Edge Network. | - L’implémentation de l’API Web/Mobile SDK ou Edge de Target n’est pas nécessaire pour partager des audiences RTCDP par lots et en flux continu avec Target, mais elle est nécessaire pour permettre l’évaluation des segments Edge en temps réel. <br>- Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge. <br>- Pour les recherches d’espace de noms d’identité personnalisées sur Edge, le déploiement de l’API Web SDK/Edge est obligatoire et chaque identité doit être définie comme identité dans le mappage d’identités. <br>- La destination cible doit être configurée dans les destinations de Real-time Customer Data Platform. Seul le sandbox de production par défaut dans RTCDP est pris en charge. <br>- L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform. |
| **Partage d’audiences par lots et en flux continu depuis Real-time Customer Data Platform vers Target et Audience Manager via l’approche du service de partage d’audience** | - Ce modèle d’intégration peut être utilisé lorsque vous souhaitez un enrichissement supplémentaire à partir de données et d’audiences tierces dans Audience Manager. | - Le SDK web/mobile n’est pas nécessaire pour partager des audiences par lots et en flux continu avec Target, mais il est nécessaire pour activer l’évaluation des segments Edge en temps réel. <br>- Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge. <br>- Pour les recherches d’espace de noms d’identité personnalisées sur Edge, le déploiement de l’API Web SDK/Edge est obligatoire et chaque identité doit être définie comme identité dans le mappage d’identités. <br>- La projection d’audience via le service de partage d’audience doit être configurée. <br>- L’intégration à Target nécessite la même organisation IMS que l’instance Experience Platform. <br>- Seules les audiences du sandbox de production par défaut prennent en charge le service principal de partage d’audiences. |

## Partage d’audiences en temps réel, en flux continu et par lots vers Adobe Target

Architecture

![Architecture de référence du plan directeur de Personalization web en ligne/hors ligne](assets/RTCDP+Target.svg)

Détails de la séquence

![Architecture de référence du plan directeur de Personalization web en ligne/hors ligne](assets/RTCDP+Target_flow.svg)

Architecture d’aperçu

![Architecture de référence du plan directeur de Personalization web en ligne/hors ligne](assets/personalization_with_apps.svg)

## Modèles de mise en œuvre

La personnalisation par client connu est prise en charge par plusieurs méthodes d’implémentation.

### Modèle d’implémentation 1 : [!DNL Edge Network] avec l’API Web/Mobile SDK ou [!DNL Edge Network] (approche recommandée)

* Utilisation du [!DNL Edge Network] avec le SDK Web/Mobile. La segmentation Edge en temps réel nécessite d’adopter le modèle d’implémentation du SDK web/mobile ou de l’API Edge.
* [Reportez-vous au Plan directeur d’Experience Platform Web and Mobile SDK](../experience-platform/deployment/websdk.md) pour la mise en œuvre basée sur SDK.
* Pour une utilisation dans Mobile SDK, l’extension [Adobe Journey Optimizer - Decisioning](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/) doit être installée.
* [Reportez-vous à la section [!DNL Edge Network] API du serveur](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr) pour une implémentation basée sur l’API d’Adobe Target avec le profil Edge.

### Modèles de mise en œuvre 2 - SDK spécifiques aux applications

Utilisation de SDK traditionnels spécifiques aux applications (par exemple, AT.js et AppMeasurement.js). L’évaluation des segments Edge en temps réel n’est pas prise en charge dans cette méthode d’implémentation. Cependant, le partage des audiences en continu et par lots à partir du hub Experience Platform est pris en charge dans cette méthode d’implémentation.

[Consultez la documentation du connecteur Adobe Target](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[Reportez-vous au plan directeur SDK spécifique à l’application](../experience-platform/deployment/appsdk.md)

## Considérations relatives à la mise en œuvre

* Il est possible d’utiliser n’importe quelle identité principale lors de l’utilisation du modèle d’implémentation 1 décrit ci-dessus avec [!DNL Edge Network] et Web SDK.
* La première personnalisation de connexion avec des données client connues qui ont été précédemment ingérées dans RTCDP nécessite que la demande de personnalisation ait une identité principale correspondant au graphique d’identité client connu dans Real-time Customer Data Platform. Si l’identifiant principal est défini sur ECID ou sur une identité qui n’a pas encore été regroupée avec le profil client connu, il faudra plusieurs minutes pour que l’assemblage d’identités soit réalisé sur le serveur Edge et pour que la personnalisation sur le serveur Edge inclue les données client connues précédemment ingérées.
* Les profils Edge ont actuellement une durée de vie de 14 jours. Par conséquent, si un utilisateur ne s’est pas connecté ou n’est pas actif depuis 14 jours sur le serveur Edge, le profil sur le serveur Edge peut avoir expiré. Par conséquent, le serveur Edge doit récupérer le profil à partir du hub pour que la vue de profil historique soit activée afin d’alimenter la personnalisation qui inclut les attributs et les segments de profil précédemment ingérés, cela entraînera une personnalisation avec la vue historique des profils sur les pages vues suivantes par rapport à la première connexion.

## Documentation connexe

### Documentation du SDK

* [Documentation pour le SDK web d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [Documentation sur le service Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=fr)

### Documentation sur la segmentation

* [Présentation de la segmentation dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr)
* [Segmentation en temps réel](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=fr)
* [Segmentation en streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)
* [Configuration des stratégies de fusion](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=fr#create-a-merge-policy)

### Tutoriels

* [Personnalisation par « Prochain accès » avec Real-Time CDP et Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=fr)
