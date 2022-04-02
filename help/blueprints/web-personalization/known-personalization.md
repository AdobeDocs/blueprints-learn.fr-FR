---
title: Présentation de Web/Mobile Personalization
description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
landing-page-description: Synchronisez la personnalisation web avec la messagerie électronique et d’autres personnalisations de canal connu ou anonyme.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: b050017505b8d77fcf507e4dec147b66c561779a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Personalization Web/Mobile avec données client connues

## Cas d’utilisation

* Personnalisation en ligne avec des données client connues
* Optimisation de la page de destination
* Personnalisation en fonction des vues précédentes de produit ou de contenu, de l’affinité produit/contenu, des attributs environnementaux et des données démographiques, en plus des informations hors ligne telles que les transactions, les données de fidélité et de gestion de la relation client (CRM), ainsi que des informations modélisées
* Partagez et ciblez des audiences définies dans Real-time Customer Data Platform sur les sites web et les applications mobiles à l’aide d’Adobe Target.

## Applications

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (facultatif) : Ajoute des données d’audience tierces, une représentation graphique des appareils basée sur Co-op.
* Adobe Analytics (facultatif) : ajoute la possibilité de créer des segments basés sur des données comportementales historiques et une segmentation fine à partir des données d’Adobe Analytics.

## Modèles d’intégration

| # | Motif d’intégration | Fonctionnalité | Conditions préalables |
|---|---|---|---|
| 1 | Évaluation des segments en temps réel sur le serveur Edge partagé de Real-time Customer Data Platform vers Target | <ul><li>Évaluez les audiences en temps réel pour une personnalisation de même page ou de page suivante sur Edge.</li><li>En outre, tous les segments évalués en flux continu ou par lots seront également projetés sur le réseau Edge pour être inclus dans l’évaluation et la personnalisation des segments Edge.</li></ul> | <ul><li>Le SDK web/mobile doit être mis en œuvre.</li><li>Le flux de données doit être configuré dans Experience Edge avec l’extension Target et l’extension Experience Platform activée.</li><li>La destination Target doit être configurée dans les destinations Real-time Customer Data Platform.</li><li>L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.</li></ul> |
| 2 | Diffusion en continu et partage d’audiences par lots de Real-time Customer Data Platform vers Target via l’approche Edge | <ul><li>Partagez des audiences en continu et par lots à partir de Real-time Customer Data Platform vers Target par le biais d’Edge Network. Les audiences évaluées en temps réel nécessitent la mise en oeuvre de WebSDK et de réseau Edge.</li></ul> | <ul><li>Le SDK Web/Mobile n’est pas nécessaire pour le partage d’audiences par lots et en flux continu vers Target, bien qu’il soit nécessaire pour activer l’évaluation des segments de périphérie en temps réel.</li><li>Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge.</li><li>Pour les recherches d’espace de noms d’identité personnalisé sur Edge, le déploiement du SDK web est requis et chaque identité doit être définie en tant qu’identité dans la carte d’identité.</li><li>La destination Target doit être configurée dans les destinations Real-time Customer Data Platform.</li><li>L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.</li></ul> |
| 3 | Partage d’audiences en continu et par lots à partir de Real-time Customer Data Platform vers Target et Audience Manager par le biais d’un service de partage d’audience | <ul><li>Ce modèle d’intégration peut être exploité lorsque vous souhaitez enrichir davantage des données et des audiences tierces en Audience Manager.</li></ul> | <ul><li>Le SDK Web/Mobile n’est pas nécessaire pour le partage d’audiences par lots et en flux continu vers Target, bien qu’il soit nécessaire pour activer l’évaluation des segments de périphérie en temps réel.</li><li>Si vous utilisez AT.js, seule la recherche de profil par rapport à l’ECID est prise en charge.</li><li>Pour les recherches d’espace de noms d’identité personnalisé sur Edge, le déploiement du SDK web est requis et chaque identité doit être définie en tant qu’identité dans la carte d’identité.</li><li>La projection de l’audience par un service de partage d’audience doit être configurée.</li><li>La destination Target doit être configurée dans les destinations Real-time Customer Data Platform.</li><li>L’intégration à Target requiert la même organisation IMS que pour l’instance Experience Platform.</li></ul> |

## Partage d’audiences en temps réel, en flux continu et par lots vers Adobe Target

Architecture

<img src="assets/RTCDP+Target.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a" />

Détails de la séquence

<img src="assets/RTCDP+Target_flow.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a" />

Architecture d’aperçu

<img src="assets/personalization_with_apps.png" alt="Architecture de référence pour le plan directeur de personnalisation web en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a"/>

## Modèles d’implémentation

Le Personalization client connu est pris en charge par plusieurs méthodes d’implémentation.

### Modèle de mise en oeuvre 1 - Réseau Edge avec SDK Web/Mobile (approche recommandée)

Utilisation du réseau Edge avec le SDK web/mobile. La segmentation de périphérie en temps réel nécessite l’approche de mise en oeuvre du SDK Web/Mobile ou de l’API Edge.

[Reportez-vous au plan directeur du SDK web et mobile d’Experience Platform](../data-ingestion/websdk.md)

### Modèle de mise en oeuvre 2 - SDK spécifiques à l’application

Utilisation de SDK traditionnels spécifiques aux applications (par exemple, AT.js et AppMeasurement.js). L’évaluation des segments de Real-time Edge n’est pas prise en charge à l’aide de cette approche de mise en oeuvre. Cependant, le partage en continu et par lots d’audiences à partir du hub Experience Platform est pris en charge à l’aide de cette approche d’implémentation.

[Reportez-vous au plan directeur de SDK spécifique à l’application.](../data-ingestion/appsdk.md)

### Étapes d’implémentation

1. [Implémentez Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=fr) pour vos applications web ou mobiles
1. [La mise en œuvre de l’Experience Platform et [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=fr) vous garantit que les audiences créées sont activées sur Edge en configurant la variable [stratégie de fusion](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=fr#create-a-merge-policy) comme active sur Edge.
1. Implémentez le [SDK web Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=fr). Le SDK web Experience Platform est nécessaire pour la segmentation Edge en temps réel, mais pas pour le partage d’audiences par lots et en flux continu à partir de Real-time Customer Data Platform vers Target. Notez que la prise en charge de la segmentation en temps réel via le SDK mobile et l’API n’est actuellement pas disponible.
1. [Configuration du réseau Edge avec un flux de données Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=fr)
1. [Activation d’Adobe Target en tant que destination dans Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=fr)
1. (Facultatif) [Mise en oeuvre de Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=fr) (facultatif)
1. (Facultatif) [Demande d’attribution de privilèges d’accès pour le partage d’audiences entre Experience Platform et Adobe Target (audiences partagées)](https://www.adobe.com/go/audiences) pour partager des audiences de l’Experience Platform vers Target.

## Garde-fous

[Référez-vous aux garde-fous décrits sur la page de présentation des plans directeurs de personnalisation web et mobile.](overview.md)

## Considérations de mise en œuvre

Conditions préalables requises pour les identités

* Toute identité principale peut être exploitée lors de l’utilisation du modèle d’implémentation 1 tel que décrit ci-dessus avec le réseau Edge et le SDK web. La personnalisation de la première connexion nécessite que l’identité principale du jeu de requêtes de personnalisation corresponde à l’identité principale du profil tiré de Real-time Customer Data Platform. La combinaison des identités entre les appareils anonymes et les clients connus est traitée sur le hub et projetée ultérieurement vers Edge.
* Le partage d’audiences à partir d’Adobe Experience Platform vers Adobe Target nécessite l’utilisation d’ECID comme identité lors de l’utilisation du service de partage d’audience, tel qu’indiqué dans le scénario de cas d’utilisation 3 ci-dessus.
* D’autres identités peuvent également être utilisées pour partager des audiences Experience Platform vers Adobe Target à l’aide d’Audience Manager. Experience Platform active les audiences vers Audience Manager à l’aide des espaces de noms pris en charge suivants : IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Notez qu’Audience Manager et Target résolvent les abonnements aux audiences par le biais de l’identité ECID. Par conséquent, l’ECID est toujours requis pour le partage d’audience final vers Adobe Target.

## Documentation connexe

### Documentation du SDK

* [Documentation pour le SDK web d’Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentation pour les balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr)
* [Documentation sur le service Experience Cloud ID](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=fr)

### Documentation de la connexion

* [Connexion Adobe Target pour Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Configuration du flux de données Edge](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
* [Partage de segments Experience Platform avec Audience Manager et d’autres solutions Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=fr)

### Documentation sur la segmentation

* [Présentation de la segmentation dans Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=fr)
* [Segmentation en temps réel](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=fr)
* [Segmentation en streaming](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Partage de segments Adobe Analytics via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=fr)
* [Configuration des stratégies de fusion](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)

### Tutoriels

* [Personnalisation par « Prochain accès » avec Real-Time CDP et Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=fr)

### Articles de blog connexes

* [Adobe annonce la personnalisation améliorée des pages similaires avec Adobe Target et Real-time Customer Data Platform](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
