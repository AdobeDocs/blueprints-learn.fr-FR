---
title: Schéma d’architecture d’Adobe Experience Platform et applications
description: Ce schéma d’architecture montre comment Adobe Experience Platform se rattache aux autres applications et services applicatifs Adobe Experience Cloud.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Offer Decisioning, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 6c4b72159d4ba2a171215678e4e4842956d82745
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 11%

---

# Adobe Experience Platform et Applications

## Schéma d’architecture d’Adobe Experience Platform et applications

Ce schéma d’architecture montre comment Adobe Experience Platform se rattache aux autres applications et services applicatifs Adobe Experience Cloud.

<img src="assets/aep+apps_vertical.svg" alt="Adobe Experience Platform et applications" style="border:1px solid #4a4a4a; width:80%;" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Schéma détaillé d’architecture pour Adobe Experience Platform et Applications

<img src="assets/aep+apps_horizontal.svg" alt="Adobe Experience Platform et applications" style="border:1px solid #4a4a4a; width:80%;" />

## Intégrations d’applications Adobe Experience Platform et Experience Cloud

<table class="relative-table wrapped" style="width: 100%;" >
   <colgroup>
    <col style="width: 16.0202%;"/>
    <col style="width: 29.3423%;"/>
    <col style="width: 33.5582%;"/>
    <col style="width: 21.0793%;"/>
  </colgroup>
  <tbody>
    <tr>
      <th>Application</th>
      <th>Experience Platform à l’application</th>
      <th>Application pour Experience Platform</th>
      <th>Plans directeurs associés</th>
    </tr>
    <tr>
      <td colspan="1">Ad Cloud</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans la plateforme de données clients en temps réel peuvent être partagées avec Ad Cloud à des fins de ciblage via l’Audience Manager.</li>
        </ul>
      </td>
      <td colspan="1">Aucune intégration actuelle</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Activation d’audience anonyme</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Activation d’audience en ligne / hors ligne</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation avec Experience Platform et applications</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Analytics</td>
      <td>Aucune intégration actuelle</td>
      <td>
        <ul>
          <li>Les données collectées par Analytics peuvent être envoyées au lac de données et à la banque de profils Experience Platform. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en">Connecteur de données Analytics</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=en">Flux de données Experience Platform</a>
          </li>
        </ul>
        <p>
          <br/>
        </p>
      </td>
    </tr>
    <tr>
      <td>Audience Manager</td>
      <td>
        <ul>
          <li>Les audiences définies dans la plateforme de données clients en temps réel peuvent être partagées dans Audience Manager pour activation vers des destinations de cookies tiers.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>Les données collectées et l’appartenance à l’audience évaluée peuvent être partagées avec le lac de données et la banque de profils Experience Platform. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en">Connecteur source d’Audience Manager</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Activation d’audience anonyme</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Activation d’audience en ligne / hors ligne</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation avec Experience Platform et applications</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Classic</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans la plateforme de données clients en temps réel peuvent être partagées avec Campaign Classic en tant qu’audience pour lancer des campagnes.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les données d’interaction et de campagne collectées par Campaign peuvent être ingérées par Experience Platform en tant que source de données pour une utilisation ultérieure dans la création d’audiences via la plateforme de données clients en temps réel et l’analyse via Customer Journey Analytics et Experience Platform Query Service et Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">Messagerie par lots</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Adobe Campaign Standard</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans la plateforme de données clients en temps réel peuvent être partagées avec Campaign Standard en tant qu’audience pour lancer des campagnes.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les données d’interaction et de campagne collectées par Campaign peuvent être ingérées par Experience Platform en tant que source de données pour une utilisation ultérieure dans la création d’audiences via la plateforme de données clients en temps réel et l’analyse via Customer Journey Analytics et Experience Platform Query Service et Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">Messagerie par lots</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Customer Journey Analytics</td>
      <td colspan="1">
        <ul>
          <li>Les données collectées et ingérées dans un lac de données Experience Platform sont disponibles pour traitement dans Customer Journey Analytics. </li>
        </ul>
      </td>
      <td colspan="1">Aucune intégration actuelle n’est disponible. La possibilité de partager les résultats de l’audience avec Experience Platform à partir de Customer Journey Analytics figure sur la feuille de route.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=en">Customer Journey Analytics</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Experience Manager</td>
      <td colspan="1">
        <ul>
          <li>Le profil Experience Platform est directement accessible côté serveur pour alimenter les expériences personnalisées diffusées via Experience Manager. Notez que les activités de personnalisation sont le plus souvent diffusées via Experience Manager via l’intégration de Target. </li>
        </ul>
      </td>
      <td colspan="1">Aucune intégration, comportement et interaction actuels effectués sur les sites des Experience Manager n’est collectée directement via le SDK Web et mobile des Experience Platform.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Activation d’audience en ligne / hors ligne</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Journey Optimizer</td>
      <td colspan="1">
        <ul>
          <li>Les événements de données et les profils ingérés dans Experience Platform sont mis à la disposition de Journey Optimizer pour lancer et alimenter les parcours dans Journey Optimizer.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les données d’interaction et de campagne générées par Journey Optimizer sont collectées dans Experience Platform pour une utilisation ultérieure dans la création d’audiences via la plateforme de données clients en temps réel et l’analyse via Customer Journey Analytics, Experience Platform Query Service et Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/triggered-messaging.html?lang=en">Messagerie déclenchée</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Magento</td>
      <td colspan="1">Aucune intégration actuelle</td>
      <td colspan="1">Aucune intégration actuelle</td>
      <td colspan="1">Aucune intégration actuelle</td>
    </tr>
    <tr>
      <td colspan="1">Marketo</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans la plateforme de données clients en temps réel peuvent être partagées avec Marketo en tant qu’audience pour lancer des campagnes Marketo et mettre à jour des objets Marketo.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les comptes Marketo, les contacts et les données d’opportunité, ainsi que les données d’interaction et de campagne produites par Marketo, sont ingérés dans Experience Platform pour une utilisation ultérieure dans la création d’audiences via la plateforme de données clients B2B et l’analyse via Customer Journey Analytics, Experience Platform Query Service et Data Science Workspace. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en">Connecteur Marketo Engage</a>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Activation B2B - dans le développement</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">CDP en temps réel</td>
      <td colspan="1">
        <ul>
          <li>Les données ingérées et collectées dans Experience Platform sont la source de données permettant d’assembler les profils clients en temps réel qui alimentent la plateforme de données clients en temps réel.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les mesures d’audience et de profil sont envoyées au lac de données Experience Platform pour alimenter les tableaux de bord de rapports des informations sur les profils.</li>
          <li>Les données Audience et Profile du lac de données peuvent être utilisées pour obtenir des informations supplémentaires via Query Service, Data Science Workspace et Customer Journey Analytics.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Activation d’audience en ligne / hors ligne</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation avec Experience Platform et applications</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Cible</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans la plateforme de données clients en temps réel peuvent être partagées avec Target et utilisées dans les expériences de personnalisation et de ciblage fournies par Target. </li>
          <li>L’intégration directe d’Experience Edge avec Target pour l’adhésion aux segments en temps réel et l’accès aux attributs de profil est sur la feuille de route.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les données collectées pour les expériences et interactions Target peuvent être collectées pour Experience Platform via le SDK Web Experience Platform. Ces données peuvent être utilisées dans la création d’audiences via la plateforme de données clients en temps réel et pour l’analyse via Customer Journey Analytics,  Experience Platform Query Service et Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Activation d’audience en ligne / hors ligne</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation avec Experience Platform et applications</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
