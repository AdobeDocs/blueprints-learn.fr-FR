---
title: Schéma de l'architecture d’Experience Platform et des autres applications Adobe
description: Ce schéma d’architecture montre comment Adobe Experience Platform se rattache aux autres applications et services applicatifs Adobe Experience Cloud.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Offer Decisioning, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 0e981eba79a4a99c32598a8d018beff7cec1da0e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Experience Platform et autres applications Adobe

## Schéma de l&#39;architecture d’Experience Platform et des autres applications Adobe

Ce schéma d’architecture montre comment Adobe Experience Platform se rattache aux autres applications et services applicatifs Adobe Experience Cloud.

<img src="assets/aep+apps_vertical.svg" alt="Experience Platform et autres applications" style="border:1px solid #4a4a4a; width:80%;" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Schéma détaillé d’architecture d&#39;Experience Platform et des autres applications Adobe

<img src="assets/aep+apps_horizontal.svg" alt="Experience Platform et autres applications" style="border:1px solid #4a4a4a; width:80%;" />

## Intégrations d’applications Adobe Experience Platform et Experience Cloud

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
      <th>D'Experience Platform vers l’application</th>
      <th>De l’application vers Experience Platform</th>
      <th>Plans directeurs associés</th>
    </tr>
    <tr>
      <td colspan="1">Ad Cloud</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Ad Cloud à des fins de ciblage par le biais d'Audience Manager.</li>
        </ul>
      </td>
      <td colspan="1">Aucune intégration en cours</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=fr">Activation d’audience anonyme</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=fr">Activation d’audience en ligne / hors ligne</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=fr">Activation avec Experience Platform et les applications</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Analytics</td>
      <td>Aucune intégration en cours</td>
      <td>
        <ul>
          <li>Les données collectées par Analytics peuvent être envoyées au lac de données et à la banque de profils Experience Platform. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=fr">Connecteur de données Analytics</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=fr">Flux de données d’Experience Platform</a>
          </li>
        </ul>
        <p>
          <br/>
        </p>
      </td>
    </tr>
    <tr>
      <td>Audience Manager</td>
      <td>
        <ul>
          <li>Les audiences définies dans Real-time Customer Data Platform peuvent être partagées dans Audience Manager pour permettre leur activation vers des destinations de cookies tiers.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>Les données collectées et les résultats d'évaluation d’appartenance à une audience peuvent être partagées avec le lac de données et la banque de profils Experience Platform. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=fr">Connecteur source Audience Manager</a>
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
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation avec Experience Platform et les applications</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Classic</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Campaign Classic et permettront en tant qu’audience de lancer des campagnes.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les données d’interaction et de campagne collectées par Adobe Campaign peuvent être ingérées par Experience Platform et serviront en tant que source de données pour être ensuite utilisées pour créer des audiences par le biais de Real-time Customer Data Platform et pour les analyser à l'aide de Customer Journey Analytics et Experience Platform Query Service et Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/batch-messaging.html?lang=fr">Messagerie par lots</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Standard</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Campaign Standard et permettront en tant qu’audience de lancer des campagnes.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les données d’interaction et de campagne collectées par Adobe Campaign peuvent être ingérées par Experience Platform et serviront en tant que source de données pour être ensuite utilisées pour créer des audiences par le biais de Real-time Customer Data Platform et pour les analyser à l'aide de Customer Journey Analytics et Experience Platform Query Service et Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/batch-messaging.html?lang=en">Messagerie par lots</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Customer Journey Analytics</td>
      <td colspan="1">
        <ul>
          <li>Les données collectées et ingérées dans un lac de données Experience Platform sont disponibles pour être traitées dans Customer Journey Analytics. </li>
        </ul>
      </td>
      <td colspan="1">Aucune intégration n’est en cours. La possibilité de partager les résultats de l’audience avec Experience Platform à partir de Customer Journey Analytics est à l'étude.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=fr">Customer Journey Analytics</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Experience Manager</td>
      <td colspan="1">
        <ul>
          <li>Le profil Experience Platform est directement accessible côté serveur pour alimenter les expériences personnalisées diffusées par Experience Manager. Notez que les activités de personnalisation sont le plus souvent diffusées par Experience Manager à l'aide de l’intégration de Target. </li>
        </ul>
      </td>
      <td colspan="1">Les intégrations, les comportements et les interactions actuellement réalisés sur les sites d’Experience Manager ne sont jamais collectés directement par le biais des SDK web et mobile d’Experience Platform.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Activation d’audience en ligne / hors ligne</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Journey Optimizer</td>
      <td colspan="1">
        <ul>
          <li>Les événements de données et les profils ingérés dans Experience Platform sont mis à la disposition de Journey Optimizer pour lancer et alimenter les parcours dans celui-ci.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les données d’interaction et de campagne générées par Journey Optimizer sont collectées dans Experience Platform pour être ensuite utilisées pour créer des audiences par le biais de Real-time Customer Data Platform et les analyser à l'aide de Customer Journey Analytics, Experience Platform Query Service et Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=en">Journey Optimizer</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Magento</td>
      <td colspan="1">Aucune intégration en cours</td>
      <td colspan="1">Aucune intégration en cours</td>
      <td colspan="1">Aucune intégration en cours</td>
    </tr>
    <tr>
      <td colspan="1">Marketo</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Marketo et permettront en tant qu’audience de lancer des campagnes Marketo et de mettre à jour des objets Marketo.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les comptes, les contacts et les données d’opportunité Marketo, ainsi que les données d’interaction et de campagne produites par Marketo, sont ingérés dans Experience Platform pour être ensuite utilisées pour créer des audiences sur la plateforme de données clients B2B et les analyser à l'aide de Customer Journey Analytics, Experience Platform Query Service et Data Science Workspace. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=fr">Connecteur Marketo Engage</a>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Activation B2B - En développement</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Real-time CDP</td>
      <td colspan="1">
        <ul>
          <li>Les données ingérées et collectées dans Experience Platform servent de source de données permettant d’assembler les profils clients en temps réel qui alimentent Real-time Customer Data Platform.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les mesures d’audience et de profil sont envoyées au lac de données d’Experience Platform pour alimenter les tableaux de bord de rapports des informations sur les profils.</li>
          <li>Les données d’audience et de profil du lac de données peuvent être utilisées pour obtenir des informations supplémentaires par le biais de Query Service, Data Science Workspace et Customer Journey Analytics.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Activation d’audience en ligne / hors ligne</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation avec Experience Platform et les applications</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Target</td>
      <td colspan="1">
        <ul>
          <li>Les audiences définies dans Real-time Customer Data Platform peuvent être partagées avec Target et utilisées dans les expériences de personnalisation et de ciblage fournies par Target. </li>
          <li>L’intégration directe d’Experience Edge avec Target pour la détermination en temps réel de l’appartenance aux segments et de l’accès aux attributs de profil est à l'étude.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Les données collectées pour les expériences et interactions Target peuvent être collectées pour Experience Platform à l'aide du SDK web d’Experience Platform. Ces données peuvent être utilisées pour créer des audiences dans Real-time Customer Data Platform et pour les analyser à l'aide de Customer Journey Analytics, Experience Platform Query Service et Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Activation d’audience en ligne / hors ligne</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation avec Experience Platform et les applications</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
