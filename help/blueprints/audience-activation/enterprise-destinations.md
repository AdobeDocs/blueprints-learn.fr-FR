---
title: Profil et Audience Activation vers les destinations d’entreprise
description: Profil et Audience Activation vers les destinations d’entreprise
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
translation-type: tm+mt
source-git-commit: f48f7e6d712db97e94d9b60309e15539f3ec4c9e
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Scénario profil et Audience Activation vers les destinations d&#39;entreprise

Réplication et mise à jour des modifications de profil apportées aux entrepôts de données d’entreprise pour les cas d’activation et d’utilisation de rapports.

Lancez une action de vente ou d’assistance au client en notifiant l’action du client à partir de la plate-forme de données client en temps réel aux systèmes et applications d’entreprise.

## Cas d’utilisation

* Activation d’profil et d’Audience vers les destinations d’enregistrement en mode cloud ou les destinations de diffusion en flux continu pour le suivi d’entreprise, l’enregistrement, l’analyse et l’activation des données et des statistiques client.

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
Une fois par jour ou à lancement manuel de ad hoc via l’API

* Environ 1 heure par emploi pour une capacité de stockage de profils pouvant atteindre 10 To
* Environ 2 heures par emploi pour 10 à 100 To de profil

## Etapes de mise en oeuvre

1. Créer des schémas pour l’assimilation des données
1. Créer des jeux de données pour les données à ingérer
1. Configurez les identités et les espaces de nommage d&#39;identité corrects sur le schéma pour vous assurer que les données saisies peuvent être associées dans un profil unifié.
1. Activez les schémas et les jeux de données pour le traitement des profils.
1. Configurer des sources pour l&#39;assimilation de données
1. Segments d’auteur dans l’Experience Platform, à évaluer par lot ou en flux continu. Le système détermine automatiquement si le segment est évalué en tant que lot ou flux continu.
1. Configurez les destinations pour le partage d&#39;attributs de profil et d&#39;adhésions d&#39;audience vers les destinations souhaitées.

## Considérations relatives à la mise en oeuvre

Activation des attributs et des identités

* La plate-forme de données client en temps réel peut activer les adhésions à l’audience ainsi que les modifications d’attribut et d’identité survenant pour les profils membres de segments sélectionnés pour activation. En tant que tel, si le cas d&#39;utilisation est d&#39;activer des attributs et/ou des identités, un segment global doit être défini qui inclura tous les profils pour lesquels des mises à jour d&#39;attribut/d&#39;identité seront envoyées doit être défini. Une fois cette configuration en place, le segment et les attributs souhaités à activer peuvent être sélectionnés dans le cadre de la configuration de destination.
* Notez que les destinations par lot ne prennent pas en charge l’activation des attributs uniquement en cas de événement de modification. L’appartenance à une Audience complète ou incrémentielle peut être envoyée avec les attributs sélectionnés pour l’activation, mais les événements de modification d’attribut uniquement ne peuvent pas être activés par lots.

Activation des segments par lots aux destinations de diffusion en continu

* L’Activation de segment par lot aux destinations de diffusion en continu est prise en charge. Les tâches de segment par lot placent des messages sur le canal une fois la tâche de segment terminée pour l’activation en flux continu.

Activation de segments en flux continu vers des destinations de lot

* L’activation des segments en flux continu vers la destination par lot est prise en charge. Le programme de destination du lot exporte les appartenances de segments des profils en fonction du programme de destination du lot. Cela inclut les adhésions aux segments déterminées par les méthodes de diffusion en continu et par lots.

Activation des Événements d’expérience

* L’Activation des événements d’expérience brute n’est actuellement pas prise en charge. Pour être activé par rapport aux événements d’expérience, un segment doit être créé avec les règles nécessaires qui incluent/excluent la logique du événement d’expérience pour laquelle être activé. Cela crée un segment défini par rapport aux événements d’expérience et l’adhésion au segment peut être activée en tant que proxy pour activer les événements d’expérience brute. Envisagez également de tirer parti de Launch Server Side pour l’activation des événements d’expérience bruts collectés via SDK.

## Documentation connexe

* [Description du produit de la plate-forme de données client en temps réel](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Instructions relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Vidéos et Tutorials connexes

* [Présentation de la plate-forme de données clientes en temps réel](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Démonstration de la plateforme de données client en temps réel](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)