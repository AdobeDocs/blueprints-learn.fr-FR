---
title: Activation d’audience et de profil
description: Proposez des expériences client activées par l’audience et centrées sur les profils grâce à Real-time Customer Data Platform.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 5471d9c0f6fdef6fbac72d5d35f32353ea5a5ee8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Activation d’audience et de profil

L’activation d’audience et de profil est la clé du succès dans un monde du marketing axé sur les données. Cependant, de nombreuses marques concentrent toujours leurs efforts sur l’activation axée sur le canal en premier, qui offre souvent une portée et une personnalisation incohérentes.

Avec une approche axée sur le canal, chaque canal agit comme un silo dans lequel les efforts de personnalisation ne ciblent que les clients interagissant avec la marque sur ce canal. Cette approche ne reflète pas la réalité selon laquelle les clients interagissent avec les marques sur de nombreux points de contact différents. L’activation d’audience et de profil permet aux marques de connecter les interactions des clients sur plusieurs canaux, afin de fournir un profil et une audience centralisés qui peuvent être activés sur tous les canaux.

| Plan directeur | Description | Applications Experience Cloud |
|---|---|---|
| **[Activation d’audience anonyme](anonymous.md)** | <ul><li>Ciblez des audiences sur le web et les canaux publicitaires pour des données client anonymes et comportementales.</li><li>Intégrez des données d’audience tierces pour une personnalisation accrue.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Activation d’audience en ligne / hors ligne](online-offline.md)** | <ul><li>Activez vers des destinations connues basées sur le profil telles que les fournisseurs de messagerie électronique, les réseaux sociaux et les destinations publicitaires. </li><li>Utilisez les attributs et les événements hors ligne tels que les commandes hors ligne, les transactions, la gestion de la relation client (CRM) ou les données sur la fidélité, combinés avec le comportement en ligne pour le ciblage et la personnalisation en ligne.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-time Customer Data Platform]</li><li>Adobe Audience Manager (facultatif)</li></ul> |
| **[Activation d’audience et de profil vers des destinations d’entreprise](enterprise-destinations.md)** | <ul><li>Réplication et mise à jour des modifications de profil et d’audience dans les entrepôts de données des entreprises pour les cas d’utilisation d’activation et de compte rendu des performances. </li></ul><ul><li>Lancez une action de vente ou d’assistance au client en notifiant l’action du client à partir de [!UICONTROL Real-time Customer Data Platform] aux systèmes et applications d’entreprise.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Plate-forme de données client en temps réel]</li><li>Activation d’Experience Platform</li><li>Adobe Audience Manager (facultatif)</li></ul> |
| **[Audience et Activation Profil avec les applications Experience Cloud](platform-and-applications.md)** | </ul><li>Gérer les profils et les audiences dans l’Experience Platform et les partager avec les applications Experience Cloud</li><li>Créez et partagez des segments de clients riches et des informations sur les Experience Platform et partagez-les avec des applications Experience Cloud.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Plate-forme de données client en temps réel]</li><li>Activation d’Experience Platform</li><li>Applications Experience Cloud</li></ul> |
| **[Centre d’activité client](customer-activity.md)** | <ul><li>Fournissez un contexte client plus étoffé aux interactions prises en charge par l’agent, telles que les expériences vécues par le client en matière de service clientèle et de vente. À travers la recherche de profil dans Adobe Experience Platform, les agents peuvent recevoir plus de contexte sur le client, comme les achats récents, les interactions de campagne, les propensions, les abonnements et d’autres attributs et informations stockés dans le profil client en temps réel.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |



## Gardiens pour les plans d&#39;Activation des Audiences et des Profils

* [Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)


### Activation des attributs et des identités

* [!UICONTROL Real-time Customer Data Platform] peut activer les adhésions aux audiences, ainsi que les modifications d’attribut et d’identité survenant pour les profils membres de segments sélectionnés pour l’activation. Si votre objectif est d’activer des attributs ou des identités, vous devez définir un segment global qui inclut tous les profils auxquels des mises à jour d’attributs et d’identités sont envoyées. À ce stade, vous pouvez sélectionner le segment et les attributs souhaités à activer dans le cadre de la configuration de destination.
* Notez que les destinations par lots ne prennent pas en charge l’activation d’événements de modification d’attribut uniquement. Les adhésions complètes ou incrémentielles aux audiences peuvent être envoyées avec les attributs sélectionnés pour l’activation, mais vous ne pouvez pas activer les événements de modification d’attribut uniquement par lot.

### Activation de segments par lots vers des destinations de diffusion en continu

* L’activation de segment par lots vers des destinations de diffusion en continu est prise en charge. Les traitements de segment par lots placent des messages sur le pipeline une fois le traitement de segment terminé pour l’activation de flux continus.

### Activation de segments en flux continu vers des destinations par lots

* L’activation des segments en flux continu vers les destinations par lot est prise en charge. Le planning de destination du lot exporte les adhésions de segment de profil en fonction du planning de destination du lot. Cela inclut les adhésions aux segments déterminées par les méthodes de diffusion en continu et par lots.

### Activation des événements d’expérience

* L’activation d’événements d’expérience bruts n’est pas prise en charge. Pour être activé par rapport aux événements d’expérience, un segment doit être créé avec les règles nécessaires qui incluent ou excluent la logique de l’événement d’expérience. Cela crée un segment défini par rapport aux événements d’expérience et l’adhésion au segment peut être activée en tant que proxy pour activer les événements d’expérience bruts. Envisagez également d’utiliser [!UICONTROL Platform Launch côté serveur] pour activer les événements d’expérience bruts collectés via le SDK.


## Articles de blog connexes

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
