---
title: Audience et Activation Profil
description: Proposez des expériences client activées par l’audience et centrées sur les profils grâce à Real-time Customer Data Platform.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 9e0954334e8b8a8c5bf52651611e7afa165f6d21
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 15%

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

* [Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

### Gardiens pour l’évaluation et l’Activation des segments

| Type de segmentation | Fréquence | Débit | Latence (évaluation des segments) | Latence (Activation de segment) | Charge utile Activation |
|-|-|-|-|-|-|-|-|-|
| Segmentation Edge | La segmentation Edge est actuellement en version bêta et permet une segmentation en temps réel valide à évaluer sur le réseau Edge Experience Platform pour une prise de décision en temps réel sur la même page via Adobe Target et Adobe Journey Optimizer. |  | ~100 millisecondes | Disponible immédiatement pour la personnalisation en Adobe Target, pour les recherches de profil dans le Profil Edge et pour l&#39;activation via des destinations basées sur des cookies. | Appartenances aux Audiences disponibles sur le bord pour les recherches de profil et les destinations basées sur les cookies.<br>Audience Les adhésions et les attributs de Profil sont disponibles pour Adobe Target et Journey Optimizer.  |
| Segmentation en flux continu | Chaque fois qu’un nouveau événement ou enregistrement de diffusion en continu est assimilé au Profil Client en temps réel et que la définition de segment est un segment de diffusion en continu valide. <br>Voir la  [documentation sur la ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr) segmentation pour obtenir des instructions sur les critères de segmentation en flux continu. | Jusqu&#39;à 1500 événements par seconde.  | ~ p95 &lt; 5 minutes | Destinations de diffusion en continu : Les adhésions aux audiences en flux continu sont activées en moins de 10 minutes environ ou micro-par lot selon les exigences de la destination.<br>Destinations planifiées : Les abonnements aux audiences en flux continu sont activés par lots en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |
| Segmentation incrémentielle | Une fois par heure pour les nouvelles données qui ont été ingérées dans le Profil client en temps réel depuis la dernière évaluation incrémentielle ou par lot. |  |  | Destinations de diffusion en continu : Les adhésions à des audiences incrémentielles sont activées dans un délai d&#39;environ 10 minutes ou par micro-lot en fonction des exigences de la destination.<br>Destinations planifiées : Les adhésions aux audiences incrémentielles sont activées par lot, en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience et valeurs d’identité uniquement.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |
| Segmentation par lots | Une fois par jour, en fonction d&#39;un calendrier prédéfini du système, ou d&#39;un appel ad hoc lancé manuellement via l&#39;API. |  | Environ une heure par emploi pour une taille de magasin de profils de 10 téraoctets, 2 heures par emploi pour une taille de magasin de profils de 10 téraoctets à 100 téraoctets. Les performances de la tâche de segment par lot dépendent du nombre de profils, de la taille des profils et du nombre de segments évalués. | Destinations de diffusion en continu : Les adhésions à l&#39;audience par lot sont activées dans les 10 heures suivant la fin de l&#39;évaluation de la segmentation ou par micro-lot selon les exigences de la destination.<br>Destinations planifiées : Les adhésions à l’audience par lot sont activées en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience et valeurs d’identité uniquement.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |

### Gardiens pour le partage d’Audiences entre applications

| Intégrations des applications d&#39;Audience | Fréquence | Débit/volume | Latence (évaluation des segments) | Latence (Activation de segment) |
|-|-|-|-|-|-||
| Plate-forme de données client en temps réel vers l&#39;Audience Manager | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | Dépendant du type de segmentation - voir le tableau des garde-fous de segmentation ci-dessus. | Dans les minutes qui suivent l&#39;achèvement de l&#39;évaluation du segment.<br>La synchronisation initiale de la configuration des audiences entre la plateforme de données client en temps réel et l’Audience Manager prend environ 4 heures.<br>Les adhésions d’audience réalisées au cours de la période de 4 heures sont consignées à l’Audience Manager sur la tâche de segmentation par lots suivante en tant qu’adhésions d’audience &quot;existantes&quot;. |
| Plate-forme de données client en temps réel vers Ad Cloud | Notez que le partage d’audiences de la plateforme de données clientes en temps réel vers Adobe Advertising Cloud nécessite une Audience Manager. Les mêmes garde-fous qui s’appliquent au partage des plateformes de données clientes en temps réel avec Audience Manager s’appliquent à l’intégration des audiences de plateformes de données clientes en temps réel à Advertising Cloud. | - |-  | - |
| Adobe Analytics à la plateforme de données client en temps réel | Non disponible actuellement | Non disponible actuellement | Non disponible actuellement | Non disponible actuellement |
| Adobe Analytics à l&#39;Audience Manager |-  | Par défaut, 75 audiences au maximum peuvent être partagées pour chaque suite de rapports Adobe Analytics. Si une licence d’Audience Manager est utilisée, il n’y a aucune limite au nombre d’audiences pouvant être partagées entre Adobe Analytics et Adobe Target ou Adobe Audience Manager et Adobe Target. | - |-  |


### Des garde-fous pour activer les attributs et les identités

* [!UICONTROL La ] plate-forme de données clientes en temps réel peut activer les adhésions aux audiences, ainsi que les modifications d’attribut et d’identité survenant pour les profils membres de segments sélectionnés pour l’activation. Si votre objectif est d’activer des attributs ou des identités, vous devez définir un segment global qui inclut tous les profils auxquels des mises à jour d’attributs et d’identités sont envoyées. A ce stade, vous pouvez sélectionner le segment et les attributs souhaités à activer dans le cadre de la configuration de destination.
* Notez que les destinations par lot ne prennent pas en charge l’activation de événements de modification d’attribut uniquement. Les adhésions complètes ou incrémentielles aux audiences peuvent être envoyées avec les attributs sélectionnés pour l&#39;activation, mais vous ne pouvez pas activer les événements de modification d&#39;attribut uniquement par lots.

Activation de segments par lot vers des destinations de diffusion en continu

* L’Activation de segment par lot aux destinations de diffusion en continu est prise en charge. Les tâches de segment par lot placent des messages sur le canal une fois la tâche de segment terminée pour l’activation en flux continu.

Activation de segments de diffusion en continu vers des destinations par lot

* L’activation des segments en flux continu vers les destinations par lot est prise en charge. La planification de destination du lot exporte les adhésions de segment de profil en fonction de la planification de destination du lot. Cela inclut les adhésions aux segments déterminées par les méthodes de diffusion en continu et par lots.

Activation des événements d’expérience

* L’activation de événements d’expérience brute n’est pas prise en charge. Pour être activé par rapport aux événements d’expérience, un segment doit être créé avec les règles nécessaires qui incluent ou excluent la logique du événement d’expérience. Cela crée un segment défini par rapport aux événements d’expérience et l’adhésion au segment peut être activée en tant que proxy pour activer les événements d’expérience brute. Envisagez également d’utiliser [!UICONTROL Lancement côté serveur] pour activer les événements d’expérience bruts collectés via le SDK.


## Articles de blog connexes

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
