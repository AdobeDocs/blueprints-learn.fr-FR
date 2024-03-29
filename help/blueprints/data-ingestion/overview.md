---
title: Collecte et préparation de données
description: Ce plan directeur décrit toutes les méthodes de préparation et d’ingestion des données dans Adobe Experience Platform.
solution: Data Collection
kt: 7204
thumbnail: null
exl-id: 5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
source-git-commit: 802507291f54dc3f253d469e7a64d78e34b75c6a
workflow-type: ht
source-wordcount: '214'
ht-degree: 100%

---

# Plans directeurs de collecte et de préparation de données

La collecte et la préparation des données englobe et décrit toutes les méthodes de préparation et d’ingestion des données dans Adobe Experience Platform. Elle inclut également la possibilité de collecter des données vers Adobe Experience Platform Edge Network et de les transférer ultérieurement via le transfert latéral vers des destinations d’entreprise.

La préparation des données inclut le mapping de données sources vers un schéma du Modèle de données d’expérience (XDM). Elle inclut également la réalisation de transformations sur les données, y compris le formatage de la date ; le fractionnement, la concaténation ou les conversions de champ ; et la jonction, la fusion ou la ressaisie d’informations. La préparation des données permet d’unifier les données clients pour fournir une analyse agrégée / filtrée, y compris la création de rapports ou la préparation de données pour l’assemblage d’un profil client, la data science, l’activation.

| Plan directeur | Description | Applications Experience Cloud |
|---|---|---|
| **[Préparation et ingestion des données](ingestion.md)** | <ul><li>Le plan directeur de la préparation et de l’ingestion de données englobe et décrit toutes les méthodes de préparation et d’ingestion des données dans Adobe Experience Platform.</ul></li> | <ul><li> Adobe Experience Platform </ul></li> |
| **[Collecte de données d’entreprise côté serveur](server-side-collection.md)** | <ul><li>Activez vers des destinations connues basées sur le profil telles que les fournisseurs de messagerie électronique, les réseaux sociaux et les destinations publicitaires. </li><li>Utilisez les attributs et les événements hors ligne tels que les commandes hors ligne, les transactions, la gestion de la relation client (CRM) ou les données sur la fidélité, combines avec le comportement en ligne pour le ciblage et la personnalisation en ligne.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-time Customer Data Platform]</li><li>Adobe Audience Manager (facultatif)</li></ul> |
