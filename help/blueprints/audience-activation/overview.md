---
title: Audience et Activation Profil
description: Proposez des expériences client activées par l’audience et centrées sur les profils grâce à Real-time Customer Data Platform.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 58368eb06b9bbd6c332424bdcfa2789dde7d4c2f
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 16%

---


# Audience et Activation Profil

L&#39;Audience et l&#39;activation des Profils sont la clé du succès dans un monde de marketing axé sur les données. Cependant, de nombreuses marques concentrent toujours leurs efforts sur l’activation axée sur le canal en premier, qui offre souvent une portée et une personnalisation incohérentes.

Avec une approche axée sur le canal, chaque canal agit comme un silo dans lequel les efforts de personnalisation ne ciblent que les clients interagissant avec la marque sur ce canal. Cette approche ne reflète pas la réalité selon laquelle les clients interagissent avec les marques sur de nombreux points de contact différents. L&#39;Audience et l&#39;activation des Profils permettent aux marques de connecter les interactions client sur plusieurs canaux, afin de fournir un profil et une audience centralisés qui peuvent être activés sur tous les canaux.

| Plan directeur | Description | Applications Experience Cloud |
|---|---|---|
| **[Audience Activation anonyme](anonymous.md)** | <ul><li>Ciblez des audiences sur le web et les canaux publicitaires pour des données client anonymes et comportementales.</li><li>Intégrez des données d’audience tierces pour une personnalisation accrue.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Audience Activation en ligne / hors ligne](online-offline.md)** | <ul><li>Activez les destinations profils connues, telles que les fournisseurs de messagerie, les réseaux sociaux et les destinations publicitaires. </li><li>Utilisez des attributs et des événements hors ligne, tels que des commandes hors ligne, des transactions, des données de gestion de la relation client ou de fidélité, ainsi que le comportement en ligne pour le ciblage et la personnalisation en ligne.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-time Customer Data Platform]</li><li>Adobe Audience Manager (facultatif)</li></ul> |
| **[Audience et Activation Profil vers les destinations d’entreprise](enterprise-destinations.md)** | <ul><li>Réplication et mise à jour des modifications d’profil et d’audience dans les entrepôts de données d’entreprise pour les cas d’activation et d’utilisation de rapports. </li></ul><ul><li>Lancez une action de vente ou d’assistance au client en notifiant l’action du client à partir de la [!UICONTROL plate-forme de données client en temps réel] aux systèmes et applications d’entreprise.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Plate-forme de données client en temps réel]</li><li>activation Experience Platform</li><li>Adobe Audience Manager (facultatif)</li></ul> |
| **[Centre d’activité client](customer-activity.md)** | <ul><li>Fournissez un contexte consommateur plus étoffé aux interactions prises en charge par l’agent, telles que les expériences vécues par le client en matière de service clientèle et de vente. En utilisant la recherche de profil dans l’Experience Platform, les agents peuvent recevoir plus de contexte sur le consommateur, comme les achats récents, les interactions de campagne, les propensions, les adhésions à l’audience et d’autres attributs et connaissances stockés dans le profil client en temps réel.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## Gardiens pour les plans d&#39;Activation des Audiences et des Profils

### Diagramme de garde

<img src="assets/activation_guardrails.svg" alt="Diagramme de référence pour les plans d'Activation des Audiences et des Profils" style="border:1px solid #4a4a4a" />

* [Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

### Gardiens pour l’évaluation et l’Activation des segments

| Type de segmentation | Cas d’utilisation | Fréquence | Débit | Latence (évaluation des segments) | Latence (Activation de segment) | Charge utile Activation |
|--------------------------|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Segmentation Edge | Personnalisation Web/Mobile (Même page/Page suivante) | La segmentation Edge est actuellement en version bêta et n’est pas encore disponible en général. | - | Environ 100 millisecondes | Cible et Journey Optimizer :<ul><li>Disponible immédiatement dans la même demande de personnalisation.</li></ul><br>Destinations basées sur les cookies :<ul><li>Disponible pour les décisions de page suivante.</li></ul> | Recherches de Profil Edge (Cible et Journey Optimizer) :<ul><li>Appartenances à l&#39;Audience</li><li>Attributs de profil</li></ul><br>Destinations basées sur les cookies :<ul><li>Appartenances à l&#39;Audience</li></ul> |
| Segmentation en streaming | Marketing basé sur les déclencheurs (diffusion en continu) | Chaque fois qu’un nouveau événement ou enregistrement de diffusion en continu est assimilé au profil client en temps réel et que la définition de segment est un segment de diffusion en continu valide. <br>Consultez la documentation sur la segmentation pour obtenir des instructions sur la documentation sur la  [segmentation des critères de segmentation en flux continu.](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr) | Jusqu’à 1 500 événements par seconde. | Environ 5 minutes, p95 | Destinations de diffusion en continu :<ul><li>Environ 1 minute pour l&#39;Audience Manager et la Cible</li><li>Environ 10 minutes vers des destinations externes ou micro-lots dépendant de la destination.</li></ul><br>Destinations planifiées :<ul><li>Activé vers des destinations externes par lot en fonction de l’heure de diffusion de destination planifiée.</li></ul> | Destinations de diffusion en continu : <ul><li>Modifications de l’adhésion à l’Audience</li><li>Valeurs d’identité</li><li>Attributs de profil</li></ul><br>Destinations planifiées :<ul><li>Modifications de l’adhésion à l’Audience</li><li>Valeurs d’identité</li><li>Attributs de profil</li></ul> |
| Segmentation incrémentielle | <li>Messagerie par lots<li>Ciblage des campagnes et des expériences | Une fois par heure pour les nouvelles données qui ont été ingérées dans le profil client en temps réel depuis la dernière évaluation incrémentielle ou par lot. | Sans objet | Dépend du nombre de profils, de la taille des profils et du nombre de segments évalués. | Destinations de diffusion en continu :<ul><li>Environ 1 minute pour l&#39;Audience Manager et la Cible</li><li>Environ 10 minutes vers des destinations externes ou micro-lots dépendant de la destination.</li></ul><br>Destinations planifiées :<ul><li>Activé vers des destinations externes par lot en fonction de l’heure de diffusion de destination planifiée.</li></ul> | Destinations de diffusion en continu : <ul><li>Modifications de l’adhésion à l’Audience</li><li>Valeurs d’identité</li></ul><br>Destinations planifiées :<ul><li>Modifications de l’adhésion à l’Audience</li><li>Valeurs d’identité</li><li>Attributs de profil</li></ul> |
| Segmentation par lots | <ul><li>Messagerie par lots</li><li>Ciblage des campagnes et des expériences</li></ul> | Une fois par jour, en fonction d’un calendrier prédéfini du système, ou d’un appel ad hoc lancé manuellement via l’API. | Sans objet | Dépend du nombre de profils, de la taille des profils et du nombre de segments évalués.<ul><li>Environ une heure par emploi pour une capacité de stockage de profils de 10 To</li><li>2 heures par travail pour 10 à 100 To de profil.</li></ul> | Destinations de diffusion en continu :<ul><li>Environ 1 minute pour l&#39;Audience Manager et la Cible</li><li>Environ 10 minutes vers des destinations externes ou micro-lots dépendant de la destination.</li></ul><br>Destinations planifiées :<ul><li>Activé vers des destinations externes par lot en fonction de l’heure de diffusion de destination planifiée.</li></ul> | Destinations de diffusion en continu : <ul><li>Modifications de l’adhésion à l’Audience</li><li>Valeurs d’identité</li></ul><br>Destinations planifiées :<ul><li>Modifications de l’adhésion à l’Audience</li><li>Valeurs d’identité</li><li>Attributs de profil</li></ul> |

### Gardiens pour le partage d’Audiences entre applications

| Intégrations des applications d&#39;Audience | Cas d’utilisation | Fréquence | Débit/volume | Latence (évaluation des segments) | Latence (Activation de segment) |
|-|-|-|-|-|-|-|-|-|
| Plate-forme de données client en temps réel vers l&#39;Audience Manager | Enrichir la publicité tierce avec les audiences de profil connues | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | <ul><li>Dans les minutes qui suivent l&#39;achèvement de l&#39;évaluation du segment.</li><li>La synchronisation initiale de la configuration des audiences entre RTCDP et AAM prend environ 4 heures.</li><li>Toute adhésion d&#39;audience réalisée au cours de la période de 4 heures sera écrite à l&#39;AAM sur la tâche de segmentation par lots suivante en tant qu&#39;adhésion d&#39;audience &quot;existante&quot;.</li></ul> |
| Adobe Analytics à l&#39;Audience Manager | Enrichir la publicité tierce avec des audiences basées sur le comportement granulaires |  | Par défaut, 75 audiences au maximum peuvent être partagées pour chaque suite de rapports Adobe Analytics. Si une licence d’Audience Manager est utilisée, il n’y a aucune limite. |  |  |
| Adobe Analytics à la plateforme de données client en temps réel | Non disponible actuellement. | Non disponible actuellement | Non disponible actuellement | Non disponible actuellement | Non disponible actuellement |


### Activation des attributs et des identités

* [!UICONTROL La ] plate-forme de données clientes en temps réel peut activer les adhésions aux audiences, ainsi que les modifications d’attribut et d’identité survenant pour les profils membres de segments sélectionnés pour l’activation. Si votre objectif est d’activer des attributs ou des identités, vous devez définir un segment global qui inclut tous les profils auxquels des mises à jour d’attributs et d’identités sont envoyées. A ce stade, vous pouvez sélectionner le segment et les attributs souhaités à activer dans le cadre de la configuration de destination.
* Notez que les destinations par lot ne prennent pas en charge l’activation de événements de modification d’attribut uniquement. Les adhésions complètes ou incrémentielles aux audiences peuvent être envoyées avec les attributs sélectionnés pour l&#39;activation, mais vous ne pouvez pas activer les événements de modification d&#39;attribut uniquement par lots.

### Activation de segments par lot vers des destinations de diffusion en continu

* L’Activation de segment par lot aux destinations de diffusion en continu est prise en charge. Les tâches de segment par lot placent des messages sur le canal une fois la tâche de segment terminée pour l’activation en flux continu.

### Activation de segments de diffusion en continu vers des destinations par lot

* L’activation des segments en flux continu vers les destinations par lot est prise en charge. La planification de destination du lot exporte les adhésions de segment de profil en fonction de la planification de destination du lot. Cela inclut les adhésions aux segments déterminées par les méthodes de diffusion en continu et par lots.

### Activation des événements d’expérience

* L’activation de événements d’expérience brute n’est pas prise en charge. Pour être activé par rapport aux événements d’expérience, un segment doit être créé avec les règles nécessaires qui incluent ou excluent la logique du événement d’expérience. Cela crée un segment défini par rapport aux événements d’expérience et l’adhésion au segment peut être activée en tant que proxy pour activer les événements d’expérience brute. Envisagez également d’utiliser [!UICONTROL Lancement côté serveur] pour activer les événements d’expérience bruts collectés via le SDK.


## Articles de blog connexes

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
