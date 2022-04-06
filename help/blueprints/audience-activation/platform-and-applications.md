---
title: Plan directeur pour l’activation de profil et d’audience avec les applications Experience Cloud
description: Gérez les profils et les audiences dans Experience Platform et partagez-les avec les applications Experience Cloud.
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 3425495df36ff8da0f2fd737b35d294ccafe31bd
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 100%

---

# Plan directeur pour l’activation de profil et d’audience avec les applications Experience Cloud

Gérez les profils et les audiences dans Experience Platform et partagez-les avec les applications Experience Cloud. Créez et diffusez des segments et des informations riches sur les clients dans Experience Platform et partagez-les avec les applications Experience Cloud.

L’activation avec les applications Experience Cloud s’aligne étroitement sur le [plan directeur de client connu](known.md).

## Cas d’utilisation

* Personnalisez et ciblez sur différents canaux d’interaction client optimisés par Experience Cloud.
* Partagez les données d’audience et de profil entre les applications Experience Platform et Experience Cloud.

## Applications

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]
* Experience Platform Activation
* Applications Experience Cloud
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer

## Architecture

Consultez la [section Architecture d’Experience Platform et de ses applications](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=fr) pour obtenir des schémas d’architecture supplémentaires relatifs aux intégrations d’Experience Platform avec les applications Experience Cloud.

### Activation de profil et d’audience avec les applications Experience Cloud

<img src="../experience-platform/assets/aep+apps_horizontal.svg" alt="Architecture de référence pour l’activation d’audience et de profil avec les applications Experience Cloud" style="width:90%; border:1px solid #4a4a4a" />
<br>

## Garde-fous

Référez-vous aux [garde-fous décrits sur la page de présentation d’Audience et Profil Activation](overview.md)

## Considérations de mise en œuvre

* Le partage des données de profil avec les destinations nécessite que vous incluiez la valeur d’identité spécifique utilisée par la destination dans la payload de destination. Toute identité nécessaire pour une destination cible doit être ingérée dans Platform et configurée en tant qu’identité pour le [!UICONTROL profil client en temps réel].

### Partage d’audiences de Real-time Customer Data Platform vers Audience Manager

* Pour plus d’informations, consultez la documentation suivante. [Partage de segments Experience Platform avec Audience Manager et d’autres solutions Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=fr).

* L’abonnement à l’audience de la plateforme RT-CDP est partagé en flux continu vers Audience Manager dès que l’évaluation du segment est terminée et inscrite dans le profil Real-time Customer, que l’évaluation du segment ait eu lieu par lot ou en flux continu. Si le profil qualifié contient les informations de routage régional pour les appareils de profil associés, l’abonnement à l’audience de la plateforme RTCDP est qualifiée en continu dans le profil Audience Manager Edge associé. Si les informations de routage régional ont été appliquées à un profil avec un horodatage datant des 14 derniers jours, elles seront évaluées dans Audience Manager Edge en continu. Si les profils de la plateforme RTCDP ne contiennent pas d’informations de routage régional ou si les informations de routage régional ont plus de 14 jours, les abonnements au profil sont envoyés à l’emplacement central d’Audience Manager pour une évaluation et une activation basées par lots. Les profils éligibles à l’activation dans Edge seront activés dans les minutes suivant la qualification des segments à partie de la plateforme RTCDP, les profils qui ne remplissent pas les critères pour l’activation dans Edge seront qualifiés dans le centre Audience Manager et peuvent présenter un délai de traitement de 12 à 24 heures.

* Les informations de routage régional pour lesquelles Edge le profil d’Audience Manager est stocké peuvent être collectées vers Experience Platform à partir d’Audience Manager, du service d’identification des visiteurs, d’Analytics, de Launch ou directement à partir du SDK web en tant que jeu de données de classe d’enregistrement de profil distinct à l’aide du groupe de champs XDM « informations sur la région de capture de données ».

* Dans les scénarios d’activation où les audiences sont partagées depuis Experience Platform vers Audience Manager, les identités suivantes sont automatiquement partagées : ECID, IDFA, GAID, adresses e-mail hachées (EMAIL_LC_SHA256), AdCloud ID. Actuellement, les espaces de noms personnalisés ne sont pas partagés.

* Les audiences d’Experience Platform peuvent être partagées par le biais des destinations d’Audience Manager lorsque les identités de destination requises sont incluses dans le [!UICONTROL profil client en temps réel], ou lorsque les identités du [!UICONTROL profil client en temps réel] peuvent être reliées aux identités de destination requises qui sont liées dans Audience Manager.

### Partage d’audiences de Real-time Customer Data Platform vers Target

* Consultez [Personnalisation web/mobile avec le plan directeur des données en ligne et hors ligne](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/online-offline.html?lang=fr) pour obtenir plus d’informations sur le partage de profils et d’audiences de Real-time Customer Data Platform vers Target.

### Partage d’audiences de Real-time Customer Data Platform vers Campaign et Journey Optimizer

* Consultez [Plans directeurs des parcours client](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html?lang=fr) pour obtenir plus d’informations sur le partage de profils et d’audiences de Real-time Customer Data Platform vers Campaign et Journey Optimizer.

## Documentation connexe

* Description de [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=fr)

## Vidéos et tutoriels connexes

* Présentation de [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=fr)
* [Vidéo de démonstration de [!UICONTROL Real-time Customer Data Platform ]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=fr)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr)
