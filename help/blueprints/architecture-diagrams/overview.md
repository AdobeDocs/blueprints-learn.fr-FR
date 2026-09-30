---
title: Diagrammes d’architecture
description: Diagrammes de référence d’architecture visuelle et de flux de données pour Adobe Experience Platform et les applications, couvrant l’architecture de la plateforme, l’activation des audiences, le marketing B2B, les informations sur les clients et les parcours de clients.
solution: Experience Platform
doc-type: overview-page
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%
---
# Diagrammes d’architecture

Les diagrammes d’architecture sont des références visuelles et techniques qui montrent comment Adobe Experience Platform et les applications s’intègrent (points d’intégration du système, flux de données et de contenu et séquence d’opérations). Utilisez-les pour comprendre la conception de solution avant de passer aux conseils détaillés dans [modèles de cas d’utilisation](/help/blueprints/use-case-patterns/overview.md).

Les diagrammes sont organisés dans les catégories suivantes. Sélectionnez une carte pour accéder à la page de destination ou au diagramme de prospect de cette catégorie. Utilisez le volet de navigation de gauche pour parcourir tous les diagrammes d’une catégorie.

<table style="table-layout:fixed; width:100%;">
<tr>
  <td style="width:33%; vertical-align:top; padding:10px; box-sizing:border-box;">
    <a href="architecture-overviews/overview.md">
      <img alt="Aperçu de l’architecture" src="architecture-overviews/assets/aep_apps_overview.png" style="display:block; width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;" />
    </a>
    <div style="min-height:100px;">
      <a href="architecture-overviews/overview.md">
        <strong>Aperçu de l’architecture</strong>
      </a>
      <p>Comment les applications Experience Cloud, Experience Platform et les SDK de déploiement s’intègrent, ainsi que les mécanismes de sécurisation et les latences.</p>
    </div>
  </td>
  <td style="width:33%; vertical-align:top; padding:10px; box-sizing:border-box;">
    <a href="audience-profile-activation/overview.md">
      <img alt="Activation des audiences et des profils" src="audience-profile-activation/assets/real_time_cdp_activation.png" style="display:block; width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;" />
    </a>
    <div style="min-height:100px;">
      <a href="audience-profile-activation/overview.md">
        <strong>Activation des audiences et des profils</strong>
      </a>
      <p>comment les audiences et les profils sont créés dans Adobe Real-Time CDP et activés vers les destinations et les applications ;</p>
    </div>
  </td>
  <td style="width:33%; vertical-align:top; padding:10px; box-sizing:border-box;">
    <a href="b2b-activation-marketing/overview.md">
      <img alt="Activation et marketing B2B" src="b2b-activation-marketing/assets/b2b-audience-profile-activation.png" style="display:block; width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;" />
    </a>
    <div style="min-height:100px;">
      <a href="b2b-activation-marketing/overview.md">
        <strong>Activation et marketing B2B</strong>
      </a>
      <p>Activation des audiences basées sur des comptes et des personnes avec Real-Time Customer Data Platform B2B edition sur plusieurs canaux et destinations.</p>
    </div>
  </td>
</tr>
<tr>
  <td style="width:33%; vertical-align:top; padding:10px; box-sizing:border-box;">
    <a href="customer-insights/overview.md">
      <img alt="Informations sur le client" src="customer-insights/assets/cja.png" style="display:block; width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;" />
    </a>
    <div style="min-height:100px;">
      <a href="customer-insights/overview.md">
        <strong>Informations sur le client</strong>
      </a>
      <p>Comment Customer Journey Analytics unifie et analyse les données comportementales cross-canal et s’intègre à Real-Time CDP et Journey Optimizer.</p>
    </div>
  </td>
  <td style="width:33%; vertical-align:top; padding:10px; box-sizing:border-box;">
    <a href="customer-journeys/journey-optimizer/journey-optimizer-overview.md">
      <img alt="Parcours client" src="customer-journeys/journey-optimizer/images/ajo-architecture.png" style="display:block; width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;" />
    </a>
    <div style="min-height:100px;">
      <a href="customer-journeys/journey-optimizer/journey-optimizer-overview.md">
        parcours client</strong><strong>
      </a>
      <p>Orchestration des parcours basée sur les événements avec Journey Optimizer, prise de décision sur le serveur Edge et le hub, et orchestration par lots avec Adobe Campaign.</p>
    </div>
  </td>
  <td style="width:33%; vertical-align:top; padding:10px; box-sizing:border-box;"></td>
</tr>
</table>

## Contenu associé

* [Modèles de cas d’utilisation](/help/blueprints/use-case-patterns/overview.md) : approches d’implémentation répétables qui s’appuient sur ces architectures
* [Principaux objectifs commerciaux](/help/blueprints/business-objectives/overview.md) : les résultats commerciaux que ces architectures vous aident à atteindre
* [Cas d’utilisation du secteur](/help/blueprints/industry-use-cases/use-case-catalog.md) — applications verticales spécifiques de ces modèles
