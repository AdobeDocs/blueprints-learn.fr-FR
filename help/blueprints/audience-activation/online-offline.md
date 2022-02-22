---
title: Activation avec le plan directeur de données en ligne et hors ligne
description: Activation d’audience en ligne / hors ligne
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
source-git-commit: 53ef83cbaa9dde0793e379c0044f449cfca078ab
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Activation avec le plan directeur de données en ligne et hors ligne

Utilisez les attributs et les événements hors ligne tels que les commandes hors ligne, les transactions, la gestion de la relation client (CRM) ou les données sur la fidélité, combinés avec le comportement en ligne pour le ciblage et la personnalisation en ligne.

Activez des audiences vers des destinations connues basées sur le profil telles que les fournisseurs de messagerie électronique, les réseaux sociaux et les destinations publicitaires

Plus de précisions sont fournies dans le [plan directeur pour l’activation de profil et d’audience avec les applications Experience Cloud](platform-and-applications.md) spécifiques aux intégrations entre les applications Experience Platform et Experience Cloud.

## Cas d’utilisation

* Ciblage d’audience pour des audiences connues sur les réseaux sociaux et les destinations publicitaires.
* Personnalisation en ligne avec des attributs en ligne et hors ligne.
* Activez des audiences vers des canaux connus, tels que la messagerie électronique et les SMS.

## Applications

* Adobe Experience Platform 
* [!UICONTROL Real-time Customer Data Platform]

## Architecture

### Activation avec des données en ligne et hors ligne liées à des destinations

<img src="assets/online_offline_activation.svg" alt="Architecture de référence pour le plan directeur d’activation d’audience en ligne / hors ligne" style="width:80%; border:1px solid #4a4a4a" />
<br>

## Garde-fous

[Référez-vous aux garde-fous tels que décrits sur la page de présentation d’Audience et Profil Activation](overview.md)

## Étapes d’implémentation

1. [Créez des schémas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) pour les données à ingérer.
1. [Créez des jeux de données](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=fr) pour les données à ingérer.
1. [Configurez les identités et les espaces de noms d’identité corrects](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=fr) sur le schéma pour vous assurer que les données ingérées peuvent s’intégrer dans un profil unifié.
1. [Activez les schémas et les jeux de données pour le profil](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=fr).
1. [Ingérez des données](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=fr) dans Experience Platform.
1. [Réalisez un partage de segments [!UICONTROL Real-time Customer Data Platform]](https://www.adobe.com/go/audiences) entre Experience Platform et Audience Manager pour les audiences définies dans Experience Platform à partager avec Audience Manager.
1. [Créez des segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=fr) dans Experience Platform. Le système détermine automatiquement si le segment est évalué en tant que lot ou en tant que flux continu.
1. [Configurez les destinations](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=fr) pour le partage des attributs de profil et des appartenances à une audience vers les destinations souhaitées.

## Considérations de mise en œuvre

* Le partage des données de profil avec les destinations nécessite que vous incluiez la valeur d’identité spécifique utilisée par la destination dans la payload de destination. Toute identité nécessaire pour une destination cible doit être ingérée dans Platform et configurée en tant qu’identité pour le [!UICONTROL profil client en temps réel].

### Partage d’audiences de Real-time Customer Data Platform vers Audience Manager

* L’abonnement à l’audience de la plateforme RT-CDP est partagé en flux continu vers Audience Manager dès que l’évaluation du segment est terminée et inscrite dans le profil Real-time Customer, que l’évaluation du segment ait eu lieu par lot ou en flux continu. Si le profil qualifié contient les informations de routage régional pour les appareils de profil associés, l’abonnement à l’audience de la plateforme RTCDP est qualifiée en continu dans le profil Audience Manager Edge associé. Si les informations de routage régional ont été appliquées à un profil avec un horodatage au cours des 14 derniers jours, elles seront évaluées sur l’Audience Manager Edge dans la diffusion en continu. Si les profils de la plateforme RTCDP ne contiennent pas d’informations de routage régional ou si les informations de routage régional ont plus de 14 jours, les adhésions au profil sont envoyées à l’emplacement central de l’Audience Manager pour l’évaluation et l’activation basées sur les lots. Les profils éligibles à l’activation d’Edge seront activés dans les minutes suivant la qualification des segments à partir de la plateforme RTCDP, les profils qui ne remplissent pas les critères pour l’activation d’Edge seront qualifiés dans le centre d’Audience Manager et peuvent avoir un délai de 12 à 24 heures pour le traitement.

* Les informations de routage régional pour lesquelles Edge le profil d’Audience Manager est stocké peuvent être collectées pour l’Experience Platform à partir d’Audience Manager, du service d’identification des visiteurs, d’Analytics, de Launch ou directement à partir du SDK Web en tant que jeu de données de classe d’enregistrement de profil distinct à l’aide du groupe de champs XDM &quot;informations sur la région de capture de données&quot;.

* Dans les scénarios d’activation où les audiences sont partagées depuis Experience Platform vers Audience Manager, les identités suivantes sont automatiquement partagées : IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Actuellement, les espaces de noms personnalisés ne sont pas partagés.

Les audiences d’Experience Platform peuvent être partagées via les destinations d’Audience Manager lorsque les identités de destination requises sont incluses dans le [!UICONTROL profil client en temps réel], ou lorsque les identités du [!UICONTROL profil client en temps réel] peuvent être reliées aux identités de destination requises qui sont liées dans Audience Manager.

## Documentation connexe

* Description de [[!UICONTROL Real-time Customer Data Platform]](https://helpx.adobe.com/fr/legal/product-descriptions/real-time-customer-data-platform.html)
* [Lignes directrices relatives au profil et à la segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
* [Documentation sur la segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=fr)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=fr)

## Vidéos et tutoriels connexes

* Présentation de [[!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=fr)
* [Vidéo de démonstration de [!UICONTROL Real-time Customer Data Platform ]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=fr)
* [Création de segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
