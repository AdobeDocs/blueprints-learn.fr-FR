---
title: Modèle d'Activation des Audiences et des Profils aux destinations d'entreprise
description: Audience et Activation Profil vers les destinations d’entreprise
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: a63da7d5da3038cf66b5f2c99e117d4aa5b21cc1
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Modèle d&#39;Activation des Audiences et des Profils aux destinations d&#39;entreprise

Réplication et mise à jour des modifications d’profil et d’audience dans les entrepôts de données d’entreprise pour les cas d’activation et d’utilisation de rapports. <!-- This sentence is difficult to mentally process because there's no verb. Describe what the customer can do with this feature. The first paragraph on a page should not be an abstract description.-->

Lancez une action de vente ou d’assistance au client en notifiant l’action du client à partir de la [!UICONTROL plate-forme de données client en temps réel] aux systèmes et applications d’entreprise. <!-- What kinds of sales or support actions? You might add a "For example...." The content in these blueprints should be more simple and friendly.-->

## Cas d’utilisation

* Activation de profil et d’audience vers les destinations d’enregistrement en mode cloud ou les destinations de diffusion en flux continu pour le suivi d’entreprise, l’enregistrement, l’analyse et l’activation des données et des statistiques client.

## Applications

* activation Adobe Experience Platform

## Architecture

<img src="assets/enterprise_destination.svg" alt="Architecture de référence pour le scénario d'Activation d'entreprise" style="border:1px solid #4a4a4a" />

## Gardiens

[Instructions relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

Seuils de latence et de débit :

Segmentation en flux continu :

* Jusqu’à 5 minutes pour la segmentation en flux continu, jusqu’à 1 500 événements par seconde
* Jusqu’à 11 minutes pour l’activation en flux continu

Segmentation par lots :
Une fois par jour, ou à l’aide de l’API, les données ad hoc sont lancées manuellement.

* Environ 1 heure par emploi pour une capacité de stockage de profils pouvant atteindre 10 To
* Environ 2 heures par emploi pour 10 à 100 To de profil

## Etapes de mise en oeuvre

1. Créez des schémas pour que les données soient assimilées. <!-- Cross-references to these topics would be helpful -->
1. Créez des jeux de données pour les données à ingérer.
1. Configurez les identités et les espaces de nommage d&#39;identité corrects sur le schéma pour vous assurer que les données saisies peuvent être associées dans un profil unifié.
1. Activez les schémas et les jeux de données pour le traitement des profils.
1. Configurez toutes les sources pour l&#39;assimilation des données.
1. Segments d’auteur dans l’Experience Platform, à évaluer par lot ou en flux continu. Le système détermine automatiquement si le segment est évalué en tant que lot ou flux continu.
1. Configurez les destinations pour le partage d&#39;attributs de profil et d&#39;adhésions d&#39;audience vers les destinations souhaitées.

## Considérations relatives à la mise en oeuvre

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

* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [Présentation des destinations d’enregistrement dans le cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [Destination HTTP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [[!UICONTROL Plate-forme de données client en temps réelDescription du produit ] ](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Directives sur le profil et la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Vidéos et Tutorials connexes

* [[!UICONTROL Présentation en temps réel de la ] plate-forme de données clientes](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Démonstration de la plateforme de données client en temps  [!UICONTROL réel]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
