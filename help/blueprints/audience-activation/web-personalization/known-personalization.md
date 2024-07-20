---
title: Présentation de Web/Mobile Personalization - Adobe Target et RTCDP
description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
landing-page-description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
short-description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 845655a275cdb6d4a9cd397ec7c3515cbf02d321
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 80%

---


# Plan directeur de la personnalisation web/mobile avec des données de client connu

## Cas d’utilisation

* Personnalisation en ligne avec des données client connu
* Optimisation de la page de destination
* Personnalisation en fonction des vues précédentes de produit ou de contenu, de l’affinité produit/contenu, des attributs environnementaux et des données démographiques, en plus des informations hors ligne telles que les transactions, les données de fidélité et de gestion de la relation client (CRM), ainsi que des informations modélisées
* Partagez et ciblez des audiences définies dans Real-time Customer Data Platform sur les sites web et les applications mobiles à l’aide d’Adobe Target.

## Applications

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (facultatif) : ajoute des données d’audience tierces.
* Adobe Analytics ou Customer Journey Analytics (facultatif) : permet de créer des segments en fonction des données client historiques et comportementales avec une segmentation précise.

### Documentation de référence

* [Connexion Adobe Target pour Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Configuration du flux de données Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=fr)
* [Partage de segments Experience Platform avec Audience Manager et d’autres solutions Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=fr)


## Modèles d’intégration

| Motif d’intégration | Fonctionnalité | Conditions préalables |
|---|---|---|
| Évaluation des segments en temps réel sur le serveur Edge partagé de Real-time Customer Data Platform vers Target | <ul><li>Évaluez les audiences en temps réel pour une personnalisation de même page ou de page suivante sur Edge.</li><li>En outre, tous les segments évalués en flux continu ou par lots seront également projetés vers le [!DNL Edge Network] pour être inclus dans l’évaluation et la personnalisation des segments Edge.</li></ul> | <ul><li>Le SDK Web/Mobile doit être mis en oeuvre pour l’API de serveur [!DNL Edge Network]</li><li>Le flux de données doit être configuré dans Experience Edge avec l’extension Target et l’extension Experience Platform activées.</li><li>La destination Target doit être configurée dans les destinations Real-time Customer Data Platform.</li><li>L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.</li></ul> |
| Diffusion en continu et partage d’audiences par lots de Real-time Customer Data Platform vers Target via l’approche Edge | <ul><li>Partagez des audiences en continu et par lots de Real-time Customer Data Platform vers Target par le biais de [!DNL Edge Network]. Les audiences évaluées en temps réel nécessitent la mise en oeuvre du SDK Web et de [!DNL Edge Network].</li></ul> | <ul><li>L’implémentation du SDK web/mobile et de l’API Edge de Target n’est pas requise pour le partage d’audiences RTCDP par lots et en streaming vers Target, bien que cela soit nécessaire pour permettre l’évaluation de segments périphériques en temps réel décrite ci-dessus.</li><li>Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge.</li><li>Pour les recherches d’espace de noms d’identité personnalisé sur Edge, le déploiement de l’API WebSDK/Edge est requis et chaque identité doit être définie en tant qu’identité dans la carte d’identité.</li><li>La destination Target doit être configurée dans les destinations Real-time Customer Data Platform. Seul le sandbox de production par défaut dans RTCDP est pris en charge.</li><li>L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.</li></ul> |
| Partage d’audiences en continu et par lots à partir de Real-time Customer Data Platform vers Target et Audience Manager par le biais d’un service de partage d’audience | <ul><li>Ce modèle d’intégration peut être utilisé lorsque vous souhaitez enrichir davantage des données et des audiences tierces dans Audience Manager.</li></ul> | <ul><li>Le SDK web/mobile n’est pas requis pour le partage d’audiences par lots et en continu vers Target, bien qu’il soit nécessaire pour activer l’évaluation de segments en temps réel en périphérie.</li><li>Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge.</li><li>Pour les recherches d’espace de noms d’identité personnalisé sur Edge, le déploiement de l’API WebSDK/Edge est requis et chaque identité doit être définie en tant qu’identité dans la carte d’identité.</li><li>La projection de l’audience par un service de partage d’audience doit être configurée.</li><li>L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.</li><li>Seules les audiences du sandbox de production par défaut prennent en charge le core service de partage d’audience.</li></ul> |

## Partage d’audiences en temps réel, en flux continu et par lots vers Adobe Target

Architecture

<img src="assets/RTCDP+Target.svg" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Détails de la séquence

<img src="assets/RTCDP+Target_flow.svg" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Architecture d’aperçu

<img src="assets/personalization_with_apps.svg" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Modèles de mise en œuvre

La personnalisation par client connu est prise en charge par plusieurs méthodes d’implémentation.

### Modèle de mise en oeuvre 1 - [!DNL Edge Network] avec SDK Web/Mobile ou [!DNL Edge Network] API (approche recommandée)

* Utilisation de [!DNL Edge Network] avec le SDK Web/Mobile. La segmentation Edge en temps réel nécessite d’adopter le modèle d’implémentation du SDK web/mobile ou de l’API Edge.
* [ Reportez-vous au Blueprint de SDK Web et mobile Experience Platform ](../../experience-platform/deployment/websdk.md) pour la mise en oeuvre basée sur le SDK.
* Pour une utilisation dans le SDK mobile, consultez la section [Adobe Journey Optimizer - L’extension Decisioning](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer-decisioning) doit être installée dans le SDK mobile.
* [ Reportez-vous à l’ [!DNL Edge Network] API serveur](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr) pour une implémentation basée sur l’API d’Adobe Target avec le profil Edge.

### Modèles de mise en œuvre 2 - SDK spécifiques aux applications

Utilisation de SDK traditionnels spécifiques aux applications (par exemple, AT.js et AppMeasurement.js). L’évaluation des segments Edge en temps réel n’est pas prise en charge dans cette méthode d’implémentation. Cependant, le partage des audiences en continu et par lots à partir du hub Experience Platform est pris en charge dans cette méthode d’implémentation.

[Reportez-vous à la documentation d’Adobe Target Connector](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[ Consultez le plan directeur du SDK spécifique à l’application ](../../experience-platform/deployment/appsdk.md)

## Considérations relatives à la mise en œuvre

Conditions préalables requises pour les identités

* Toute identité principale peut être utilisée lors de l’utilisation du modèle de mise en oeuvre 1 décrit ci-dessus avec le SDK [!DNL Edge Network] et web. La première personnalisation de connexion nécessite que l’identité principale du jeu de requêtes de personnalisation corresponde à l’identité principale du profil de Real-time Customer Data Platform.

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

### Articles de blog connexes

* [Adobe annonce la personnalisation améliorée des pages similaires avec Adobe Target et Real-time Customer Data Platform](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform's Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our "Customer Zero" Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
