---
description: Réception et création - Optimisation de la chaîne d’approvisionnement Campaign avec Marketo et Workfront
title: Inprise et création
exl-id: 09679521-727c-4676-8e91-23d0b7fd54a2
source-git-commit: c33790d001c98628fcaa57f0ef8ebf449adb8af2
workflow-type: tm+mt
source-wordcount: '1325'
ht-degree: 0%

---

# Inprise et création {#intake-and-create}

Le nombre de demandes marketing qui entrent dans une équipe d’opérations marketing pour lancer de nouvelles campagnes peut transformer une équipe opérationnelle élevée en une porte d’arrêt de tâches répétitives, ce qui provoque un épuisement et une innovation stagnante.

En établissant un processus d’envoi de requêtes de campagne et en automatisant la création de campagnes marketing fréquemment demandées, vous pouvez : augmenter la vitesse de vos campagnes, réduire les erreurs, acheminer les requêtes vers le bon membre des opérations marketing, équilibrer et améliorer l’utilisation des ressources et concentrer davantage vos opérations marketing sur des tâches plus stratégiques ;

Avec Workfront et Marketo Engage, une connexion système à système permet de consulter les détails d’une [Formulaire de demande Workfront](https://experienceleague.adobe.com/docs/workfront/using/administration-and-setup/customize/custom-forms/create-or-edit-a-custom-form.html){target=&quot;_blank&quot;} pour créer un programme de Marketo Engage, puis renseignez les variables clés telles que : lignes d’objet, copie électronique, images, dates, heures, informations sur les événements, etc.

Pour réaliser cette intégration, vous utiliserez Workfront Fusion, une couche d’automatisation de travail qui vous permet d’automatiser les workflows entre Workfront et d’autres systèmes.

Le workflow ci-dessous présente une demande de webinaire envoyée par un responsable de campagne à l’aide d’un formulaire de demande Workfront. Les détails envoyés dans la requête déclenchent ensuite la création d’un programme et d’un email en Marketo Engage pour le webinaire. De plus, des détails sont fournis à partir du formulaire de demande pour renseigner le contenu de l’email.

![](assets/intake-and-create-1.png)

>[!TIP]
>
>Pour en savoir plus sur les différents types d’objets dans Workfront utilisés pour organiser le travail d’une campagne marketing et sur la façon dont ils sont mappés à un programme de Marketo Engage, consultez la section [Présentation de Marketo et Workfront](/help/blueprints/b2b/campaign-supply-chain/overview.md){target=&quot;_blank&quot;}.

## Préparation de votre processus de développement de campagne pour l’automatisation {#prepare-your-campaign-development-process-for-automation}

Derrière chaque grande automatisation des workflows se trouve un processus défini qui garantit que les équipes et les parties prenantes tirent le meilleur parti de l’automatisation.

**Quels types de requêtes marketing allez-vous recevoir ?**

Pensez aux types de tactiques marketing que vous exécuterez tels que les e-mails, les vidéos, les webinaires propriétaires et les événements. Exécutez-vous également des webinaires tiers ou des publicités affichées ? Chacune de ces demandes doit être prise en compte, car elles peuvent nécessiter des champs de saisie spécifiques dans le formulaire de demande et sera mappée à différents modèles de programme en Marketo Engage qui seront clonés.

Vous souhaitez également savoir si vous exécutez des campagnes dans plusieurs régions. Si tel est le cas, vous souhaiterez tenir compte d’un projet dans Workfront en créant plusieurs programmes en Marketo Engage, chaque programme représentant une prise en charge linguistique différente.

Il est important de savoir à l’avance quels types de requêtes marketing vous prévoyez de recevoir pour vous assurer que les requêtes peuvent être facilitées de manière automatisée.

**Quelles informations doivent être capturées dans la requête de campagne ?**

Pensez aux informations clés qui devront être capturées dans votre formulaire de demande pour chacune des différentes tactiques que vous exécutez. Vous trouverez ci-dessous quelques exemples d’informations que vous pouvez capturer dans un formulaire Workfront pour automatiser le développement de vos campagnes.

<table> 
  <tr> 
   <td><b>Tactique marketing</b></td>
   <td><b>Informations à capturer</b></td>
  </tr>
  <tr> 
   <td>Email Blast</td>
   <td>・ Objet du message électronique<br />
・ Date planifiée<br />
・ Copie d’email<br />
・ Appel à l'action<br />
・ Image(s) : les URL AEM Assets peuvent être directement référencées pour une utilisation dans Marketo<br />
・ Critères de qualification de l’audience</td>
  </tr>
  <tr>
   <td>Webinaire/événement</td>
   <td>・ Nom de l’événement<br />
・ Date de l’événement<br />
・ Heure de l’événement<br />
・ Ville de l’événement<br />
・ Description de l’événement<br />
・ Page d’enregistrement du webinaire - PageURL OnDemand<br />
・ Noms des présentateurs<br />
・ Titre du présentateur<br />
・ Images du présentateur<br />
・ Emails nécessaires (invitation, confirmation, rappel, suivi)<br />
・ Image(s) d’en-tête de message électronique<br />
・ Critères de qualification de l’audience</td>
  </tr>
  <tr>
   <td>Infirmière</td>
   <td>・ Nombre d’emails<br />
・ Copie d’email<br />
・ En-têtes d’email<br />
・ Appel à l'action<br />
・ Critères de qualification de l’audience</td>
  </tr>
  </tbody>
</table>

>[!NOTE]
>
>Aujourd’hui, la création d’audiences par programmation grâce à l’automatisation est limitée en Marketo Engage, car les jetons ne sont pas pris en charge dans les listes dynamiques. Cela signifie que les audiences devront être créées en Marketo Engage par un utilisateur ou que si vous disposez d’une audience prédéterminée à laquelle vous communiquez en permanence, vous pouvez inclure une liste dynamique configurée dans votre modèle de programme qui est clonée pendant le processus d’automatisation.

### Créer votre centre d’excellence {#establish-your-center-of-excellence}

Si vous voulez automatiser la création de programmes, vous aurez besoin d&#39;un centre d&#39;excellence en Marketo Engage. Un centre d’excellence comprend des programmes et des ressources modélisés pour accélérer et normaliser le processus de développement des campagnes. Par exemple, vous pouvez disposer d’un modèle de programme pour vos différents besoins de campagne : e-mail, support, événement personnel et webinaire. En outre, vous pouvez avoir plusieurs modèles de programme de messagerie que vous utilisez pour différentes régions ou différents types d’annonces par courrier électronique.

Construire votre centre d&#39;excellence avec des modèles de programme en Marketo Engage est l&#39;une des premières étapes pour avoir une approche plus programmée de l&#39;exécution des campagnes et servira de base à l&#39;automatisation des requêtes de campagne.

Une fois que vous disposez d’un ensemble de modèles de programme réutilisables, vous pouvez augmenter davantage vos efforts à l’aide de l’automatisation décrite dans ce plan directeur afin d’accélérer davantage le développement de vos campagnes.

Pour en savoir plus sur la création de votre propre centre d’excellence, consultez la [Communauté Marketo](https://nation.marketo.com/t5/product-blogs/marketo-master-class-center-of-excellence-with-chelsea-kiko/ba-p/243221){target=&quot;_blank&quot;} pour connaître les bonnes pratiques.

### Utilisation de jetons pour renseigner du contenu {#use-tokens-to-populate-content}

Avec Marketo Engage, les jetons peuvent être utilisés pour renseigner le contenu dans les ressources de votre campagne. Par exemple, après avoir cloné un modèle d’email provenant de votre centre d’excellence, Workfront Fusion peut prendre les détails de la requête de campagne dans Workfront et les transmettre à Mes jetons dans le programme de Marketo Engage. Les valeurs de jeton peuvent ensuite être héritées directement dans l’email pour générer l’email.

![](assets/intake-and-create-2.png)

### Renseignement des images à partir d’AEM Assets {#populate-images-from-aem-assets}

Vous pouvez automatiser davantage le développement de vos emails et de vos landing pages en utilisant des jetons de Marketo Engage, ainsi que des liens vers des ressources dans AEM Assets. Les demandeurs de campagne peuvent envoyer des liens d’image publiés à partir d’AEM Assets dans le cadre du processus de demande. Workfront Fusion peut ensuite prendre ces liens et les incorporer dans le HTML d’un email à l’aide de jetons de Marketo Engage.

N’oubliez pas que vous devrez créer vos programmes et modèles de programme en Marketo Engage pour utiliser Mes jetons afin que Fusion puisse mettre à jour les valeurs de jeton avec les informations envoyées dans Workfront.

>[!NOTE]
>
>AEM Assets n’est pas nécessaire pour prendre en charge ce workflow, mais peut permettre un processus plus rationnel de gestion des ressources de campagne dans la chaîne d’approvisionnement de développement de campagne.

### Assemblage d’une bibliothèque Lookup pour tous les types de requêtes de programme {#assemble-a-lookup-library-for-all-program-request-types}

Lors de l’automatisation de la création de nouveaux programmes de Marketo Engage à partir de requêtes Workfront, il est important d’inclure une étape dans votre automatisation de la fusion Workfront qui peut prendre des informations de la requête Workfront et rechercher les modèles de programme appropriés qui doivent être clonés en Marketo Engage.

Pour ce faire, vous pouvez importer un jeu de données dans Workfront Fusion qui comprend la liste de tous les différents modèles de programme de votre centre d’excellence de Marketo Engage.

Voici quelques informations de base à inclure dans votre bibliothèque de recherche de modèle de programme :

<table> 
  <tr> 
   <td><b>Colonne</b></td>
   <td><b>Description</b></td>
  </tr>
  <tr> 
   <td>Type de campagne</td>
   <td>Il peut s’agir d’un email, d’un webinaire, d’un support, d’un événement, d’un webinaire tiers, d’un import de liste, etc. Le type de campagne servira de description lisible de ce qui est demandé.</td>
  </tr>
  <tr> 
   <td>Type de requête Workfront</td>
   <td>Il s’agit du type de requête sélectionné dans le formulaire Workfront. Il peut s’agir du même type que le type de campagne, tel que le courrier électronique, le webinaire, la préparation ou l’événement. Elle permet de mapper l’entrée sélectionnée dans le formulaire Workfront à un modèle de programme dans Marketo.</td>
  </tr>
  <tr> 
   <td>Workfront Form ID</td>
   <td>L’identifiant unique du formulaire de demande Workfront utilisé pour valider la demande d’écriture est mappé au modèle de programme du Marketo Engage.</td>
  </tr>
  <tr> 
   <td>Identifiant de programme Marketo</td>
   <td>Il s’agit de l’identifiant du modèle de programme en Marketo Engage qui correspond à la demande en cours. Le fait d’avoir ces informations facilement disponibles dans Workfront Fusion permettra à Fusion d’adresser sa demande à Marketo Engage et de savoir exactement quel programme cloner.</td>
  </tr>
  </tbody>
</table>

## Flux d’ingestion et de création d’automatisation {#intake-and-create-automation-flow}

Voici un exemple de la manière dont la logique de workflow peut être assemblée dans Fusion à l’aide d’une préconception. [Workfront](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/workfront-modules.html){target=&quot;_blank&quot;} et [Marketo Engage](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/marketo-modules.html)Modules {target=&quot;_blank&quot;} qui vous permettent de fournir l’automatisation plus rapidement.

![](assets/intake-and-create-3.png)

## Ressources {#resources}

* [Modules Adobe Marketo Engage](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/marketo-modules.html){target=&quot;_blank&quot;}

* [Modules Adobe Workfront](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/workfront-modules.html){target=&quot;_blank&quot;}

* [Présentation de Marketo et Workfront](/help/blueprints/b2b/campaign-supply-chain/overview.md){target=&quot;_blank&quot;}
