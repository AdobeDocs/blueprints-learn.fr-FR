---
title: Accès aux données et plan directeur d’exportation
description: Ce plan directeur fournit et présente toutes les méthodes par lesquelles les données peuvent être consultées et exportées à partir de Adobe Experience Platform et d’applications.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-time Customer Data Platform, Tags
source-git-commit: 67e66068bb8a2106dd8aa9784b5a39377225c045
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 4%

---

# Accès aux données et plan directeur d’exportation

Le plan directeur Accès aux données et Exportation décrit toutes les méthodes possibles pour accéder ou exporter des données à partir de Adobe Experience Platform et d’applications.

Le plan directeur est divisé en deux catégories pour l’accès aux données à partir d’Experience Platform et d’applications. tout d&#39;abord, les approches pour récupérer les données des Experience Platform et des applications ; il serait considéré comme une méthode de type push de sortie de données. Deuxièmement, les méthodes d’accès aux données des Experience Platform et des applications ; cela serait considéré comme une méthode de type pull d’accès aux données.

Méthodes d’accès aux données

* [API Real-time Customer Profile Access](#rtcp-profile-access-api)
* [API Data Access](#data-access-api)
* [Service de requête](#query-service)

Approches de l’exportation des données

* [Balises côté client](#client-side-tags-extensions)
* [Transfert d’événement](#event-forwarding)
* [Destinations Real-time Customer Data Platform](#RTCDP-destinations)
* [Actions personnalisées Journey Optimizer](#jo-custom-actions)

## Architecture de présentation de l’accès aux données et de l’exportation

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Architecture de référence pour le plan directeur de la préparation et de l’ingestion de données" style="width:90%; border:1px solid #4a4a4a" />

## Approches de l’accès aux données

### API Real-time Customer Profile Access {#rtcp-profile-access-api}

Les clients peuvent accéder à des profils unifiés uniques à partir de la banque de profils client en temps réel, y compris toutes les identités de profil, les appartenances à l’audience, les attributs et les événements d’expérience à l’aide de l’API Real-time Customer Profile Access.

Reportez-vous à la section [API Real-time Customer Profile Access](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en) pour plus d’informations.

#### Cas d’utilisation

* Recherchez un seul profil pour ajouter du contexte à l’interaction client de l’agent, comme des interactions d’assistance par le biais d’un chat et d’un centre d’appel, ou une interaction commerciale au point de vente.
* Ajout d’un contexte à une description de personnalisation effectuée par un système externe, par exemple un système de personnalisation web ou un système de décision d’offre.

#### Considérations

* Real-time Customer Profile [barrières de sécurité](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) appliquez.
* Conçu pour une recherche de profil unique à la fois. Non utilisé pour l’accès en masse aux profils ou le téléchargement de l’ensemble de la population de profils à des fins d’analyse ou de science des données.
* Le temps de réponse de la recherche de profil s’écoule aux barrières de sécurité du profil. Exigences de faible latence : par exemple, pour les mêmes exigences de personnalisation de page, doit utiliser le profil Edge ou les destinations de personnalisation client pour un accès à faible latence du profil. [Documentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en).

### API Data Access {#data-access-api}

Les clients de l’API d’accès aux données peuvent accéder directement aux fichiers de jeu de données bruts stockés dans le lac de données Experience Platform.

* Pour plus d’informations sur l’utilisation de l’API d’accès aux données, reportez-vous à la section [documentation](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=en).

#### Cas d’utilisation

* Extrayez les fichiers de données bruts et traités de l’Experience Platform à des fins de stockage et d’évaluation dans les environnements d’entreprise.

#### Considérations

* Comme l’accès aux données est effectué de manière asynchrone par lots, l’accès aux données sera par nature latent par rapport aux approches de sortie de données en flux continu telles que l’utilisation des balises, le transfert d’événements ou les destinations RTCDP.
* Les fichiers de données lorsqu’ils sont traités dans Experience Platform sont stockés sous la forme de collections de fichiers par lots et sont compressés et stockés au format parquet. Ainsi, lors de l’accès et du téléchargement des fichiers dans un environnement différent, ils doivent être systématiquement accessibles par leur lot et leur fichier, contrairement à un jeu de données entier. Toute opération sur les données doit donc tenir compte du fait que les fichiers sont compressés au format parquet.

### Service de requête {#query-service}

Les clients Query Service d’Experience Platform peuvent interroger des jeux de données dans Experience Platform et conserver les résultats de la requête. Un client SQL peut être utilisé pour interroger et conserver la réponse de requête dans la destination de stockage souhaitée que le client SQL peut prendre en charge. L’interface utilisateur de Query Service peut être utilisée pour stocker le résultat SQL dans un jeu de données cible dans l’Experience Platform ou les résultats peuvent être enregistrés sur l’ordinateur local.

* Pour plus d’informations sur la connexion aux clients SQL pour conserver les résultats SQL depuis Experience Platform Query Service, voir ce qui suit : [documentation](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=en).

#### Cas d’utilisation

* Interrogez les données brutes des jeux de données Experience Platform et conservez les résultats de la requête.
* Interrogez le jeu de données d’instantané de profil pour extraire des informations sur Real-time Customer Profile. [Documentation](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=en#profile-attribute-datasets).
* Stocker les résultats de requête dans un jeu de données distinct pour l’accès ou dans un jeu de données activé pour les profils qui peut ensuite être généré via la plateforme de données clients (RTCDP) et d’autres applications Experience Cloud qui accèdent à Real-time Customer Profile.

#### Considérations

* Comme les données sont interrogées de manière asynchrone par lots, l’accès aux données sera par nature latent par rapport aux approches de sortie de données en flux continu, telles que l’utilisation des balises, le transfert d’événements ou les destinations RTCDP.
* Seules les données disponibles dans le lac de données Experience Platform peuvent être interrogées à l’aide de Query Service. La banque de profils client en temps réel, le graphique d’identités et le Customer Journey Analytics ne peuvent pas être directement interrogés à l’aide de Query Service. Ce n’est que lorsque des jeux de données sont exportés vers le lac de données que ces jeux de données peuvent être interrogés, comme dans l’exemple du jeu de données d’instantané de profil.
* Notez que les barrières de sécurité pour le nombre de résultats de la requête et le délai d’expiration de la requête s’appliquent comme indiqué dans la section [Barrières de sécurité de Query Services](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en) documentation.

## Approches de l’exportation des données

### Extensions de balises côté client {#client-side-tags-extensions}

Les extensions peuvent être déployées à l’aide de la solution Balises d’Adobe. Une fois qu’une extension est déployée, les requêtes de données sont déployées directement sur un navigateur client ou une application et une requête peut être appelée pour envoyer des données et des requêtes vers la destination souhaitée.

Reportez-vous à la section [Présentation des balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) pour plus d’informations.

#### Cas d’utilisation

* Collectez des informations brutes en continu directement à partir des environnements côté client à l’aide du balisage.

#### Considérations

* Aucun accès direct aux informations côté serveur telles que le profil client en temps réel Experience Platform et les appartenances à l’audience.
* L’ajout de balises de collecte de données supplémentaires à la page peut augmenter le temps de chargement de la page.
* Possibilité de configurer des règles pour demander des données uniquement lorsque certains critères sont satisfaits.
* Les données sont collectées directement auprès du client, ce qui limite les types de transformations et d’enrichissement qui peuvent être effectués avant la collecte des données.

### Transfert d’événement {#event-forwarding}

Les demandes de collecte de données sont collectées directement auprès du réseau Edge d’Adobe. Les requêtes réseau Edge vers des points d’entrée RESTful externes peuvent être configurées pour transférer ces requêtes vers la destination externe.

Reportez-vous aux [Transfert d’événement](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en) pour plus d’informations.

#### Utilisation des castes

* Collectez des informations brutes en continu directement depuis les environnements côté client vers un point de terminaison d’entreprise à l’aide du transfert d’événement côté serveur d’Adobe.

#### Considérations

* Pour utiliser le transfert d’événement, les données doivent être envoyées au réseau Edge à l’aide du SDK Web ou du SDK Mobile.
* L’approche de transfert d’événement réduit le temps et le poids de chargement de la page en raison de balises supplémentaires ajoutées sur la page.
* Aucun enrichissement du profil Edge ou d’autres sources de données n’est actuellement pris en charge.
* Le filtrage des données limité et les transformations de mappage simples sont pris en charge.

### Destinations Real-time Customer Data Platform {#RTCDP-destinations}

Les données d’attribut de profil et les données d’appartenance à l’audience peuvent être activées vers les destinations d’entreprise et de publicité. Cela signifie que les données collectées doivent être ingérées dans le profil client en temps réel de l’Experience Platform.

Reportez-vous à la section [Destinations Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en) pour plus d’informations.

#### Cas d’utilisation

* Activez les informations sur les attributs de profil, y compris l’appartenance de l’audience à un entrepôt de données d’entreprise interne, un outil d’analyse, un système de messagerie ou un système d’assistance.
* Activez l’appartenance de l’audience de profil à un fournisseur de publicité externe pour cibler et personnaliser le contenu du profil.

#### Considérations

* Les attributs de profil et les appartenances à l’audience peuvent être activés. Actuellement, les événements d’expérience brute ne peuvent pas être activés dans le cadre des destinations RTCDP.
* Les activations se produisent par flux ou par lots selon la nature de l’évaluation du segment et la nature du protocole d’ingestion que la destination accepte.

### Actions personnalisées Journey Optimizer {#jo-custom-actions}

Les clients Journey Optimizer peuvent appeler une action personnalisée à partir du canevas de parcours pour envoyer un payload ou un message à un point de terminaison API externe configuré. Une action peut être configurée pour n’importe quel service de n’importe quel fournisseur pouvant être appelé via une API REST avec une payload au format JSON. Cette payload peut inclure des informations d’événement, des attributs de profil et des données d’événement précédent, des transformations et des enrichissements configurés dans le parcours.

Reportez-vous à la section [Actions personnalisées Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en) pour plus d’informations.

#### Cas d’utilisation

* Événements d’activation d’Experience Platform et de Journey Optimizer qui incluent des informations supplémentaires de Real-time Customer Profile.
* Notifier les systèmes externes lorsqu’un client a atteint un point spécifique d’un parcours.

#### Considérations

* Barrières de sécurité sur le débit pris en charge par [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=en) et les enrichissements pris en charge par la variable [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) appliquez.
* Les actions personnalisées peuvent être exécutées en continu une par une pour chaque événement ou profil dans un parcours. Il n’est pas possible d’effectuer des opérations en bloc ou des sorties de données en masse sous la forme de fichiers ou de requêtes agrégées sur les parcours client.
* Accès en continu aux attributs de profil client en temps réel et aux événements d’expérience qui peuvent être inclus dans la payload d’activation.
* Les données d’événement peuvent être filtrées et de simples transformations de mappage appliquées avant d’envoyer des événements vers des destinations externes.










