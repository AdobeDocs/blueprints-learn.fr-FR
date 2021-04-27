---
title: Modèle d'Activation des Audiences et des Profils aux destinations d'entreprise
description: Audience et Activation Profil vers les destinations d’entreprise
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 2f35195b875d85033993f31c8cef0f85a7f6cccc
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 15%

---

# Modèle d&#39;Activation des Audiences et des Profils aux destinations d&#39;entreprise

Partagez les modifications et les événements d’profil et d’audience en flux continu ou par lot de [!UICONTROL Plate-forme de données client en temps réel] vers les entrepôts de données et les applications d’entreprise. Ces événements d&#39;profil et d&#39;audience peuvent être utilisés pour lancer une action de vente ou d&#39;assistance au client, telle que le suivi d&#39;un processus de demande abandonné ou d&#39;un enregistrement de webinaire, ou pour mettre à jour les applications d&#39;entreprise avec les derniers attributs du client et les dernières informations de [!UICONTROL plate-forme de données client en temps réel].

## Cas d’utilisation

* Activation de profil et d’audience vers les destinations d’enregistrement en mode cloud ou les destinations de diffusion en flux continu pour le suivi d’entreprise, l’enregistrement, l’analyse et l’activation des données et des statistiques client.

## Applications

* Adobe Experience Platform Activation

## Architecture

<img src="assets/enterprise_destination.svg" alt="Architecture de référence pour le scénario d'Activation d'entreprise" style="border:1px solid #4a4a4a" />

## Garde-fous

[Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)

### Gardiens pour l’évaluation et l’Activation des segments

| Type de segmentation | Fréquence | Débit | Latence (évaluation des segments) | Latence (Activation de segment) | Charge utile Activation |
|-|-|-|-|-|-|-|-|-|
| Segmentation Edge | La segmentation Edge est actuellement en version bêta et permet une segmentation en temps réel valide à évaluer sur le réseau Edge Experience Platform pour une prise de décision en temps réel sur la même page via Adobe Target et Adobe Journey Optimizer. |  | ~100 ms | Disponible immédiatement pour la personnalisation en Adobe Target, pour les recherches de profil dans le Profil Edge et pour l&#39;activation via des destinations basées sur des cookies. | Appartenances aux Audiences disponibles sur le bord pour les recherches de profil et les destinations basées sur les cookies.<br>Audience Les adhésions et les attributs de Profil sont disponibles pour Adobe Target et Journey Optimizer.  |
| Segmentation en flux continu | Chaque fois qu’un nouveau événement ou enregistrement de diffusion en continu est assimilé au profil client en temps réel et que la définition de segment est un segment de diffusion en continu valide. <br>Voir la  [documentation sur la ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr) segmentation pour obtenir des instructions sur les critères de segmentation en flux continu. | Jusqu&#39;à 1500 événements par seconde.  | ~ p95 &lt;5min | Destinations de diffusion en continu : Les adhésions aux audiences en flux continu sont activées en moins de 10 minutes environ ou micro-par lot selon les exigences de la destination.<br>Destinations planifiées : Les abonnements aux audiences en flux continu sont activés par lots en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |
| Segmentation incrémentielle | Une fois par heure pour les nouvelles données qui ont été ingérées dans le profil client en temps réel depuis la dernière évaluation incrémentielle ou par lot. |  |  | Destinations de diffusion en continu : Les adhésions à des audiences incrémentielles sont activées dans un délai d&#39;environ 10 minutes ou par micro-lot en fonction des exigences de la destination.<br>Destinations planifiées : Les adhésions aux audiences incrémentielles sont activées par lot en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience et valeurs d’identité uniquement.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |
| Segmentation par lots | Une fois par jour, en fonction d&#39;un calendrier prédéfini du système, ou d&#39;un appel ad hoc lancé manuellement via l&#39;API. |  | Environ une heure par emploi pour un magasin de profils de 10 To, 2 heures par emploi pour un magasin de profils de 10 à 100 To. Les performances de la tâche de segment par lot dépendent du nombre de profils, de la taille des profils et du nombre de segments évalués. | Destinations de diffusion en continu : Les adhésions à l&#39;audience par lot sont activées dans les 10 heures suivant la fin de l&#39;évaluation de la segmentation ou par micro-lot selon les exigences de la destination.<br>Destinations planifiées : Les adhésions à l’audience par lot sont activées en fonction de l’heure de diffusion de destination planifiée. | Destinations de diffusion en continu : Modifications de l’appartenance à l’Audience et valeurs d’identité uniquement.<br>Destinations planifiées : Modifications de l’appartenance à l’Audience, valeurs d’identité et attributs de profil. |



## Étapes d’implémentation

1. Créez des schémas pour que les données soient assimilées.
1. Créez des jeux de données pour les données à ingérer.
1. Configurez les identités et les espaces de noms d’identité corrects sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.
1. Activez les schémas et les jeux de données pour le traitement des profils.
1. Configurez toutes les sources pour l&#39;assimilation des données.
1. Segments d’auteur dans l’Experience Platform, à évaluer par lot ou en flux continu. Le système détermine automatiquement si le segment est évalué en tant que lot ou en tant que flux continu.
1. Configurez les destinations pour le partage des attributs de profil et des appartenances à une audience vers les destinations souhaitées.

## Considérations de mise en œuvre

Activation des attributs et des identités

* [!UICONTROL La ] plate-forme de données clientes en temps réel peut activer les adhésions aux audiences, ainsi que les modifications d’attribut et d’identité survenant pour les profils membres de segments sélectionnés pour l’activation. Si votre objectif est d’activer des attributs ou des identités, vous devez définir un segment global qui inclut tous les profils auxquels des mises à jour d’attributs et d’identités sont envoyées. A ce stade, vous pouvez sélectionner le segment et les attributs souhaités à activer dans le cadre de la configuration de destination.
* Notez que les destinations par lot ne prennent pas en charge l’activation de événements de modification d’attribut uniquement. Les adhésions complètes ou incrémentielles aux audiences peuvent être envoyées avec les attributs sélectionnés pour l&#39;activation, mais vous ne pouvez pas activer les événements de modification d&#39;attribut uniquement par lots.

Activation de segments par lot vers des destinations de diffusion en continu

* L’Activation de segment par lot aux destinations de diffusion en continu est prise en charge. Les tâches de segment par lot placent des messages sur le canal une fois la tâche de segment terminée pour l’activation en flux continu.

Activation de segments de diffusion en continu vers des destinations par lot

* L’activation des segments en flux continu vers la destination par lot est prise en charge. La planification de destination du lot exporte les adhésions de segment de profil en fonction de la planification de destination du lot. Cela inclut les adhésions aux segments déterminées par les méthodes de diffusion en continu et par lots.

Activation des événements d’expérience

* L’activation de événements d’expérience brute n’est pas prise en charge. Pour être activé par rapport aux événements d’expérience, un segment doit être créé avec les règles nécessaires qui incluent ou excluent la logique du événement d’expérience. Cela crée un segment défini par rapport aux événements d’expérience et l’adhésion au segment peut être activée en tant que proxy pour activer les événements d’expérience brute. Envisagez également d’utiliser [!UICONTROL Lancement côté serveur] pour activer les événements d’expérience bruts collectés via le SDK.

## Documentation connexe

* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=fr)
* [Présentation des destinations d’enregistrement dans le cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [Destination HTTP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [Description de Real-time Customer Data Platform](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Directives sur le profil et la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Vidéos et tutoriels connexes

* [Présentation de Real-time Customer Data Platform ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=fr)
* [[!UICONTROL Vidéo de démonstration de Real-time Customer Data Platform ]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=fr)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr)
