---
title: Plan directeur d’export et d’accès aux données
description: Ce plan directeur présente un aperçu de toutes les méthodes qui peuvent être mises en œuvre pour accéder à des données et les exporter à partir d’Adobe Experience Platform et des applications.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-Time Customer Data Platform, Tags
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
source-git-commit: 8355a36a235d847a6faf2398f3fadbed28ccac37
workflow-type: tm+mt
source-wordcount: '1513'
ht-degree: 98%

---

# Plan directeur d’export et d’accès aux données

Le plan directeur d’export et d’accès aux données décrit toutes les méthodes qui peuvent être mises en œuvre pour accéder à des données et les exporter à partir d’Adobe Experience Platform et des applications.

Le plan directeur est divisé en deux catégories pour l’accès aux données à partir d’Experience Platform et d’applications. Il y a, tout d’abord, les méthodes de sortie de données depuis Experience Platform et les applications ; cela serait considéré comme une méthode de sortie de données de type « push ». Viennent ensuite les méthodes d’accès aux données à partir d’Experience Platform et des applications ; cela serait considéré comme une méthode d’accès aux données de type « pull ».

Méthodes d’accès aux données

* [API Real-time Customer Profile Access](#rtcp-profile-access-api)
* [API Data Access](#data-access-api)
* [Query Service](#query-service)

Méthodes d’export des données :

* [Balises côté client](#client-side-tags-extensions)
* [Transfert d’événement](#event-forwarding)
* [Destinations Real-time Customer Data Platform](#RTCDP-destinations)
* [Actions personnalisées de Journey Optimizer](#jo-custom-actions)

## Architecture de présentation de l’export et de l’accès aux données

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Architecture de référence pour le plan directeur de préparation et d’ingestion des données" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" />

## Méthodes d’accès aux données

### API Real-time Customer Profile Access {#rtcp-profile-access-api}

La clientèle peut accéder à des profils unifiés uniques à partir du magasin de profils clients en temps réel, y compris l’ensemble des identités de profil, des appartenances à l’audience, des attributs et des événements d’expérience à l’aide de l’API Real-time Customer Profile Access.

Pour plus d’informations, consultez la documentation [API Real-time Customer Profile Access](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=fr).

#### Cas d’utilisation

* Rechercher un seul profil pour ajouter du contexte à l’interaction client de l’agent, comme des interactions d’assistance par le biais de la messagerie instantanée (chat) et d’un centre d’appel, ou une interaction commerciale au niveau du point de vente.
* Autoriser l’ajout de contexte à une décision de personnalisation prise par un système externe ; par exemple, un système de personnalisation web ou un système de décision d’offre.

#### Considérations

* Les [garde-fous](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr) du profil client en temps réel sont d’application.
* Conçu pour rechercher un seul profil à la fois. Non utilisé pour l’accès à plusieurs profils ni pour le téléchargement de l’ensemble d’une population de profils à des fins d’analyse ou de science des données.
* Le temps de réponse de la recherche de profil respecte les garde-fous de profil. Exigences de faible latence en temps réel : par exemple, pour les exigences de personnalisation de la même page, le profil Edge de la [connexion Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=fr) ou de la [connexion Personnalisation sur mesure](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=fr) doit être utilisé pour un accès au profil en temps réel en vue d’une personnalisation dans l’application ou dans le navigateur.

### API Data Access {#data-access-api}

L’utilisation de l’API Data Access permet d’accéder directement aux fichiers de jeu de données bruts stockés dans le lac de données Experience Platform.

* Pour plus d’informations sur l’utilisation de l’API Data Access, consultez la [documentation](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=fr).

#### Cas d’utilisation

* Extraire des fichiers de données bruts et traités d’Experience Platform à des fins de stockage et d’évaluation dans les environnements d’entreprise.

#### Considérations

* Comme l’accès aux données s’effectue de manière asynchrone par lots, il s’agira, par nature, d’un accès latent par rapport aux méthodes de sortie de données en streaming telles que l’utilisation des balises, du transfert d’événement ou des destinations RTCDP.
* Lorsqu’ils sont traités dans Experience Platform, les fichiers de données sont stockés sous la forme de collections de fichiers par lots, et compressés et stockés au format Parquet. Ainsi, lorsque vous accédez aux fichiers et les téléchargez dans un autre environnement, l’accès doit s’effectuer systématiquement par lot et par fichier, contrairement à un jeu de données entier. De plus, toute opération sur les données doit tenir compte du fait que les fichiers sont compressés au format Parquet.

### Query Service {#query-service}

L’utilisation d’Experience Platform Query Service permet d’interroger des jeux de données dans Experience Platform et de conserver les résultats de la requête. Un client SQL peut être utilisé pour interroger et conserver la réponse de requête dans la destination de stockage souhaitée qu’il peut prendre en charge. L’interface utilisateur de Query Service peut être utilisée pour stocker le résultat SQL dans un jeu de données cible dans Experience Platform. Les résultats peuvent également être enregistrés sur l’ordinateur local.

* Pour plus d’informations sur la connexion aux clients SQL afin de conserver les résultats SQL d’Experience Platform Query Service, consultez la [documentation](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=fr) suivante.

#### Cas d’utilisation

* Interroger les données brutes provenant des jeux de données Experience Platform et conserver les résultats de la requête.
* Interroger le jeu de données d’instantané de profil pour extraire des informations sur le profil client en temps réel. [Documentation](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=fr#profile-attribute-datasets).
* Stocker les résultats de requête dans un jeu de données distinct en vue d’y accéder ou dans un jeu de données compatible avec le profil qui peut ensuite être extrait via RTCDP et d’autres applications Experience Cloud qui accèdent au profil client en temps réel.

#### Considérations

* Comme l’interrogation des données s’effectue de manière asynchrone par lots, il s’agira, par nature, d’un accès latent par rapport aux méthodes de sortie de données en streaming telles que l’utilisation des balises, du transfert d’événement ou des destinations RTCDP.
* Seules les données disponibles dans le lac de données Experience Platform peuvent être interrogées à l’aide de Query Service. Le magasin de profils clients en temps réel, le graphique d’identité et Customer Journey Analytics ne peuvent pas être directement interrogés à l’aide de Query Service. Ce n’est que lorsque les jeux de données sont exportés vers le lac de données qu’ils peuvent être interrogés, comme dans l’exemple du jeu de données d’instantané de profil.
* Notez que les garde-fous pour le nombre de résultats de requête et le délai d’expiration de la requête s’appliquent comme indiqué dans la section [Garde-fous de Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=fr).

## Méthodes d’export des données

### Extensions des balises côté client {#client-side-tags-extensions}

Les extensions peuvent être déployées à l’aide de la solution Balises d’Adobe. Une fois qu’une extension a été déployée, les demandes de données sont déployées directement sur une application ou un navigateur client et une demande peut être appelée pour envoyer des données et des demandes vers la destination souhaitée.

Pour plus d’informations, consultez la documentation [Présentation des balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr).

#### Cas d’utilisation

* Collecter des informations de streaming brutes directement à partir des environnements côté client à l’aide du balisage.

#### Considérations

* Aucun accès direct aux informations côté serveur telles que le profil client en temps réel d’Experience Platform et les appartenances à une audience.
* L’ajout de balises de collecte de données supplémentaires à la page peut augmenter le temps de chargement de la page.
* Possibilité de configurer des règles pour ne demander des données que lorsque certains critères sont satisfaits.
* Les données sont collectées directement auprès du client, ce qui limite les types de transformations et d’enrichissement qui peuvent être effectués avant la collecte des données.

### Transfert d’événement {#event-forwarding}

Les demandes de collecte de données sont collectées directement auprès du réseau Edge d’Adobe. À partir du réseau Edge, les demandes adressées à des points d’entrée RESTful externes peuvent être configurées pour être transférées vers la destination externe.

Pour plus d’informations, consultez la documentation [Transfert d’événement](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=fr).

#### Cas d’utilisation

* Collecter des informations de streaming brutes directement auprès d’environnements côté client vers un point d’entrée d’entreprise à l’aide du transfert d’événement côté serveur d’Adobe.

#### Considérations

* Pour utiliser le transfert d’événement, les données doivent être envoyées au réseau Edge à l’aide du SDK web ou de MobileSDK.
* La méthode de transfert d’événement réduit le poids et le temps de chargement de la page en raison des balises qui y sont ajoutées.
* Aucun enrichissement du profil Edge ou d’autres sources de données n’est actuellement pris en charge.
* Le filtrage limité des données et les transformations de mappage simples sont pris en charge.

### Destinations Real-time Customer Data Platform {#RTCDP-destinations}

Les données d’attribut de profil et d’appartenance à une audience peuvent être activées vers les destinations d’entreprise et de publicité. Cela signifie que les données extraites doivent être ingérées dans le profil client en temps réel d’Experience Platform.

Reportez-vous à la section [Destinations Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=fr) pour plus d’informations.

#### Cas d’utilisation

* Activer les informations sur les attributs de profil, y compris l’appartenance d’audience à des magasins de données d’entreprise internes, des outils d’analyse, des systèmes de messagerie ou des systèmes d’assistance.
* Activer l’appartenance de l’audience de profil à un fournisseur de publicité externe pour cibler et personnaliser le contenu pour le profil.

#### Considérations

* Les attributs de profil et les appartenances à une audience peuvent être activés. Actuellement, les événements d’expérience bruts ne peuvent pas être activés dans le cadre des destinations RTCDP.
* Les activations s’effectuent en streaming ou par lots selon la nature de l’évaluation du segment et celle du protocole d’ingestion accepté par la destination.

### Actions personnalisées de Journey Optimizer {#jo-custom-actions}

L’utilisation de Journey Optimizer permet d’appeler une action personnalisée à partir de la zone de travail du parcours afin d’envoyer une payload ou un message à un point d’entrée d’API externe configuré. Une action peut être configurée sur n’importe quel service à partir de tout fournisseur pouvant être appelé via une API REST avec une payload au format JSON. Cette payload peut inclure des informations d’événement, des attributs de profil et des données sur un événement antérieur, ainsi que des transformations et des enrichissements configurés dans le parcours.

Pour plus d’informations, consultez la documentation [Actions personnalisées de Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=fr).

#### Cas d’utilisation

* Événements d’activation d’Experience Platform et de Journey Optimizer qui comprennent des informations supplémentaires du profil client en temps réel.
* Informer les systèmes externes lorsqu’un client a atteint un point spécifique dans un parcours.

#### Considérations

* Les garde-fous sur le débit pris en charge par [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=fr) et les enrichissements pris en charge par le [profil client en temps réel](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr) sont d’application.
* Les actions personnalisées peuvent être effectuées une par une en mode streaming pour chaque événement ou profil d’un parcours. Il n’est pas possible d’effectuer des opérations en bloc ou des sorties de données en masse sous la forme de fichiers ou de demandes agrégées sur les parcours clients.
* Accès en streaming aux attributs de profil client en temps réel et aux événements d’expérience pouvant être inclus dans la payload d’activation.
* Les données d’événement peuvent être filtrées et des transformations de mappage simples peuvent être appliquées avant d’envoyer des événements vers des destinations externes.
