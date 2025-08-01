---
title: Plan directeur de marketing et de gestion des Parcours basé sur les groupes d’achats
description: Découvrez comment idéaliser, concevoir et créer un parcours qui qualifie les prospects pour un groupe d’achats dans Adobe Journey Optimizer B2B edition.
solution: Journey Optimizer B2B Edition
exl-id: 0a9da49c-f13a-4f2a-8407-277def2db591
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# Plan directeur de marketing et de gestion des Parcours basé sur les achats de groupe

Les équipes marketing sont actuellement confrontées à de nombreux défis pour fournir aux ventes des prospects qualifiés. L’un de ces défis est de travailler avec les bonnes personnes au sein de l’organisation, et il est généralement évident que les efforts et l’exactitude sont suffisants. Avec la _notation des prospects_, le groupe est trop étroit et les équipes peuvent ne pas trouver les bonnes personnes. Avec la _notation des comptes_, un effort plus important est nécessaire pour identifier la bonne personne ayant une vue aussi large d’un compte.

C&#39;est là que le concept de **_groupe d&#39;achat_** est introduit. Un groupe d’achat permet aux spécialistes du marketing de trouver le bon groupe de personnes dans le compte et de travailler avec ces personnes en qualifiant les prospects et en identifiant leur rôle dans le groupe.

## Utilisation des groupes d&#39;achats pour qualifier les leads et les comptes

La création d&#39;un groupe d&#39;achat et les efforts déployés pour le mener à bien augmentent l&#39;efficacité de l&#39;activité de marketing pour qualifier les prospects et les occasions de vente. Les groupes d’achat dépendent de la correspondance entre les prospects et les modèles de rôle liés à l’intention de la solution.

Un exemple de groupe d’achat pourrait être _Groupe d’achat de semences Acme Corp_, qui a un intérêt pour la solution _Semences pilotées par l’IA_.

Les groupes d’achat représentent un groupe de personnes au sein de l’entreprise qui sont intéressées par une solution basée sur une intention de solution. Et un groupe d&#39;achat pourrait être identifié pour plus d&#39;un intérêt de solution et les individus apparaissent dans plus d&#39;un groupe d&#39;achat.

Grâce aux fonctionnalités B2B améliorées fournies par Journey Optimizer B2B edition, vous pouvez désormais relever les défis suivants :

* Absence de campagnes marketing _le client d’abord_.
* Conversion incohérente du prospect qualifié marketing (MQL) en prospect qualifié ventes (SQL), nécessitant l’alignement des initiatives avec les ventes pour favoriser MQL
* Absence de mécanisme vendable pour identifier et cibler les comptes _concurrentiels_.
* Risque de concentration dans les revenus et les pipelines.

Les KPI suivants s’alignent bien sur la mesure du succès des cas d’utilisation :

* **Sensibilisation** : les clients cibles voient-ils vos publicités et les dirigent-ils vers votre site web à un rythme plus élevé qu’auparavant ?
* **Engagement** : les clients cibles visitent-ils votre site web et interagissent-ils avec le contenu ?
* **Temps** : combien de temps faut-il à l’équipe commerciale pour trouver et ajouter des contacts à l’opportunité à partir de divers outils ?
* **Coût** : combien d&#39;argent coûte chaque lead sur chaque plateforme ?

## Marketing basé sur les comptes

Un cas d’utilisation courant, et l’accent de ce plan directeur, est une initiative marketing basée sur les comptes. Ce cas d&#39;utilisation explore le point où votre groupe d&#39;achats créé est renseigné avec un prospect lorsqu&#39;ils sont associés à un rôle et à un intérêt pour la solution.

Lorsque vous accompagnez une personne dans le parcours, vous collectez plus d’informations sur le prospect (processus de groupe d’achats) par le biais de formulaires, de la synchronisation CRM et de l’activation LinkedIn.

Lorsqu’un prospect montre clairement l’intérêt de la solution, il indique un événement métier défini par une optique commerciale. À ce stade, l&#39;entreprise est convaincue que ce prospect s&#39;intéresse vraiment à un produit. Dans Journey Optimizer B2B edition, le prospect est associé à un groupe d’achat pour cette solution dans un modèle de rôles (influenceurs, décideurs, champions et sponsors, par exemple).

Comme l’illustre le diagramme suivant, vous pouvez collecter des détails dans des formulaires ou par le biais de l’activation LinkedIn et qualifier une intention de solution lorsqu’une interaction avec un chat-robot s’est produite.

![parcours du groupe d&#39;achat](./assets/buying-group-journey-diagram.svg){zoomable="yes"}

Lorsque le pourcentage d&#39;achèvement du groupe d&#39;achats est suffisamment élevé, vous partagez le groupe avec l&#39;équipe des ventes via SQL ou un SOL pour convertir les leads du compte en une vente terminée.

## Solution axée sur les comptes

La gestion des prospects B2B se concentre sur les comptes et leurs prospects. La couche technique est configurée pour prendre en charge les données qui représentent ces caractéristiques, ce qui est une exigence pour la réussite de la segmentation des comptes et de la gestion des parcours.

### Conditions requises

La solution axée sur les comptes nécessite les applications et services suivants :

* Adobe Journey Optimizer B2B edition
* B2B edition d’Adobe Real-time Customer Data Platform (RTCDP)
* Adobe Marketo Engage

>[!NOTE]
>
>L’obtention d’une licence pour Journey Optimizer B2B edition doit inclure les éléments suivants :
><ul><li>Instance Journey Optimizer B2B edition connectée à Experience Platform B2B</li><li>Instance de Marketo Engage synchronisée avec RTCDP</li></ul>
>&gt;<br/>
>&gt;Pour les clients Marketo Engage existants, une connexion à l’instance existante est l’approche recommandée.
>&gt;<br/><br/>
>&gt;D’autres extensions sont disponibles pour la solution afin d’améliorer la richesse du profil :
>&gt;<ul><li>Sources supplémentaires à RTCDP pour enrichir le profil</li><li>Destination RTCDP vers Marketo Engage</li></ul>

La mise en œuvre de cette solution nécessite également une compréhension claire du concept de _Compte_ et _Groupe d&#39;achat_, ainsi que de la manière dont ils amplifient et accélèrent votre qualification de prospect commercial. Cela étant, vous devez également déterminer le score d&#39;exhaustivité du groupe d&#39;achats souhaité.

### Architecture

![Architecture de solution pour le marketing et la gestion de parcours basés sur le groupe d’achats](./assets/ajo-b2b-architecture.png){zoomable="yes"}

### Schéma de données

Dans toute mise en œuvre de l’automatisation du marketing pilotée par les données, la conception de schémas est essentielle à la réussite de l’implémentation. Avant de concevoir votre schéma, passez en revue les espaces de noms et schémas [B2B](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces) et assurez-vous de comprendre l’utilitaire de génération automatique disponible pour générer un nouveau schéma dans un nouveau scénario d’implémentation.

Les schémas sont spécifiquement enrichis d’éléments de données B2B pour prendre en charge la relation riche en profils et inclure la perspective de compte à travers le `sourceKey` pour lier les événements et les profils au schéma de compte. Les schémas sont une représentation des exigences de votre organisation et des données collectées et profilées. Pour répondre à ces besoins, les schémas B2B sont flexibles et constituent une extension des éléments B2B requis.

Lors de la conception du schéma de données pour votre organisation, il est recommandé de représenter et d’étiqueter les principales entités de votre ERD avec les entités de haut niveau. (Reportez-vous au premier diagramme de la documentation sur le schéma B2B RTCDP [&#128279;](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/tutorials/relationship-b2b)). Ce processus est très utile pour comprendre les éléments de données requis que vous devez définir dans chaque schéma.

À ce stade, les événements d’expérience ne sont pas encore en mesure d’influencer les parcours. Outre les schémas Événement d’expérience , il est recommandé d’ajouter des propriétés au compte qui représentent des décisions majeures basées sur les activités de l’utilisateur. Ces propriétés sont utilisées pour les éléments de chemin de division dans le concepteur de parcours.

>[!NOTE]
>
>Actuellement, la seule relation prise en charge par Journey Optimizer B2B edition est les relations directes via l’attribut `personComponents[0].sourceAccountKey.sourceKey` sur l’entité `Person`. Une extension future est prévue pour prendre en charge l’objet de relation compte-personne dans le schéma B2b.

### Connecteur source Marketo Engage

Pour enrichir les éléments de données de compte, vous pouvez utiliser Marketo Engage et ses données B2B afin d’enrichir la vue de compte RTCDP et Journey Optimizer B2B edition. La configuration du connecteur Source Marketo Engage et le mappage des données Marketo Engage aux attributs de schéma RTCDP permettent aux données de circuler de Marketo Engage vers RTCDP et, si cela est désigné, vers le profil.

Pour plus d’informations sur la configuration du connecteur et le mappage des champs obligatoire au schéma, consultez la documentation du connecteur Marketo Engage [&#128279;](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

### Garde-fous

Les mécanismes de sécurisation de Journey Optimizer B2B edition sont détaillés dans la [page de description du produit](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-journey-optimizer-b2b.html).

Mécanismes de sécurisation liés à la mise en œuvre

* Tous les mécanismes de sécurisation des audiences B2B sont décrits dans le [plan directeur de l’activation des audiences et des profils B2B](https://experienceleague.adobe.com/fr/docs/blueprints-learn/architecture/b2b-activation/b2bactivation) sont directement transposés au succès du B2B edition Journey Optimizer.
* Si l’activation est requise via les canaux Marketo Engage du parcours de compte ou si la synchronisation CRM est utilisée pour enrichir le compte, les [mécanismes de sécurisation liés à Marketo Engage](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails) sont pertinents.

Consultez la documentation sur les [mécanismes de sécurisation de Real-Time CDP](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/guardrails/overview) pour plus d’informations sur les mécanismes de sécurisation de RTCDP.

### Attribution des privilèges d’accès

* Toutes les instances doivent se trouver sur la même organisation IMS.
* Une seule instance Journey Optimizer B2B edition peut être liée à un sandbox Experience Platform.
* Nous vous recommandons vivement de mettre en œuvre le connecteur Marketo Source [vers Real-time Customer Data Platform](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

## Implémentation

Les étapes suivantes fournissent des conseils pour activer les groupes d’achats dans votre instance Journey Optimizer B2B edition, y compris l’activation des audiences pour prendre en charge l’expansion de votre base de compte avec un accent sur les modèles de rôle de groupe d’achats manquants.

### Étapes prérequises

1. Définissez le schéma XDM qui va représenter votre vue commerciale des comptes et des prospects.

   Dans un premier temps, vous définissez et créez un schéma d’expérience conçu pour répondre aux besoins du cas d’utilisation B2B et couvrant les sources de données, par lots et en temps réel. Cette conception doit représenter la manière dont l’entreprise conçoit les entités de compte et de personne, ainsi que les cas d’utilisation que vous souhaitez prendre en charge. Pour que le schéma soit un schéma B2B, il doit suivre les structures disponibles dans la documentation [Schéma B2B RTCDP ](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/tutorials/relationship-b2b).

   Une pratique utile consiste à prendre les noms d’entités du diagramme et à identifier ces entités dans votre schéma en les étiquetant de la même manière. Notez que certains schémas nécessitent des clés spécifiques, telles que `sourceKey`, pour fonctionner dans RTCDP B2B. À court terme, la relation _plusieurs à plusieurs_ entre le compte et la personne par le biais de la relation compte-personne n’est pas prise en charge dans Journey Optimizer B2B. Utilisez les scripts d’accélérateur pour obtenir le meilleur point de départ :

   * Utilisez le script de création de schéma B2B [RTCDP](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility) pour générer le schéma initial
   * Ajoutez des champs spécifiques aux cas d’utilisation aux schémas générés afin de compléter le schéma en fonction des besoins de l’organisation.

   À ce stade, vous disposez de la connexion entre Marketo Engage et RTCDP et la structure du schéma pour accepter les données du compte et de la personne afin de renseigner les jeux de données pour que les segments de compte soient définis. L’étape suivante consiste à connecter RTCDP à Marketo Engage et Journey Optimizer B2B edition.

1. Configurez le connecteur Marketo Engage, y compris le mappage de Marketo Engage à la structure XDM.

   Une fois la structure et les champs XDM en place, connectez Marketo Engage à RTCDP à l’aide du connecteur , qui alimente les jeux de données avec des données provenant de Marketo Engage et de Journey Optimizer B2B. Commencez par organiser le mappage des champs des classes Marketo Engage aux classes RTCDP. Utilisez les informations de la [documentation du connecteur](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo#field-mapping-from-marketo-engage-to-xdm) pour identifier les champs que vous souhaitez inclure à partir de votre implémentation Marketo Engage.

### Configuration du groupe d&#39;achat

1. Créez des audiences de compte dans Journey Optimizer B2B edition ou RTCDP.

   Activez l’option Planification de toutes les audiences de la page de navigation → Audiences → du client pour activer les audiences du compte. (Dans les cas où cela ne fonctionne pas, vous devez créer un segment de profil client pour pouvoir activer la création d’audiences de compte.)

   Pour créer un segment, suivez les étapes décrites dans la documentation [audiences de compte](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/account-audiences/account-audience-overview). L’utilisation du créateur de segments avec les champs de données que vous avez identifiés comme clés pour l’audience de votre compte serait l’activité clé pour définir l’audience.

   À ce stade, vous savez que le compte permet de se concentrer sur via RTCDP et d’utiliser pour les blocs de création du groupe d’achat.

1. Définissez le modèle de rôles.

   Dans chaque groupe d&#39;achat, identifiez les rôles qui représentent le rôle que les individus jouent dans le groupe que vous souhaitez traiter. Par exemple, vous pouvez utiliser _décideur_, _influenceur_ et _champion_. Définissez également le poids et les conditions de ce rôle dans le groupe d&#39;achat.

   La [documentation sur les modèles de rôles](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates) décrit ce processus et comment définir des conditions spéciales.

1. Définissez l’intérêt de la solution.

   Un intérêt pour une solution est un moyen d’indiquer l’objectif des groupes d’achat pour vos activités et votre stratégie marketing.

   Pour définir un intérêt de solution, suivez les étapes de la documentation [intérêts de solution](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/buying-groups/solution-interests). Gardez à l&#39;esprit que vous l&#39;utilisez pour faire correspondre le groupe d&#39;achat à une initiative de vente dans l&#39;organisation.

1. Configurez le groupe d&#39;achat.

   Une fois les blocs de création du groupe d’achat prêts, configurez le groupe d’achat pour l’audience de compte et d’intérêt de la solution avec une cible pour compléter le modèle de rôles avec les membres appropriés du compte. Avec cette configuration, affectez un intérêt pour la solution au modèle de rôles que vous avez identifié et donnez à chaque rôle un poids dans le succès commercial pour ce produit spécifique.

   Pour créer le groupe d&#39;achat, suivez les étapes décrites dans la [documentation sur les groupes d&#39;achat](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create).

   À ce stade, vous êtes prêt à [créer un parcours ](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/account-journeys/journey-overview#get-started-with-a-journey) et à commencer à travailler avec l’audience du compte pour constituer le groupe d’achats et le qualifier pour l’intérêt pour la solution.

### Activation de l’audience

Augmentez l’exhaustivité du groupe d’achat par l’activation de l’audience.

1. Définissez une audience de compte apparié d’annonce publicitaire LinkedIn.

   En plus des activités de courrier électronique et de remplissage de formulaire, Journey Optimizer B2B edition offre une fonctionnalité d’annonce LinkedIn pour élargir votre compte et soutenir l’effort de finalisation d’un groupe d’achat par l’extension de l’étendue des prospects du compte et l’augmentation de la portée de vos activités marketing.

   Pour utiliser les médias payants LinkedIn afin de communiquer avec les comptes lorsque les groupes d&#39;achats ne sont pas suffisamment renseignés ou engagés, développez ou engagez l&#39;audience du compte, utilisez la fonctionnalité [Audiences appariées aux comptes LinkedIn](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/account-audiences/linkedin-account-matched-audiences) pour générer des audiences d&#39;annonces LinkedIn par l&#39;intermédiaire des audiences appariées aux comptes.

1. Activez l&#39;audience pour les groupes d&#39;achats.

>[!TIP]
>
>Quelques conseils pour réussir vos campagnes :
>
>* Une campagne doit avoir des filtres de rôle pour s&#39;adapter aux groupes d&#39;achat avec des rôles manquants afin d&#39;augmenter le retour sur investissement.
>* Pour capturer des prospects, demandez aux prospects de remplir des formulaires (formulaires LinkedIn ou Marketo Engage) et de recibler les pertes de formulaire.
