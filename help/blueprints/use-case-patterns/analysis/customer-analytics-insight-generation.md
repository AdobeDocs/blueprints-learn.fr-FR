---
title: Génération de Customer Analytics et d’Insight
description: Découvrez comment créer des espaces de travail d’analyse cross-canal, des mesures calculées et des tableaux de bord pour l’analyse du comportement et des performances.
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8947'
ht-degree: 1%

---

# Génération de Customer Analytics et d’insight

Ce guide fournit une référence complète d’implémentation pour la génération de Customer Analytics et d’insight. Il explique comment connecter des jeux de données [!DNL Adobe Experience Platform] à des [!DNL Customer Journey Analytics], configurer des vues de données, créer des espaces de travail d’analyse de structure libre, créer des mesures calculées, publier des tableaux de bord et des cartes de performance mobiles et, éventuellement, republier des audiences définies par CJA sur [!DNL Adobe Experience Platform] pour activation.

Il est conçu pour les architectes de solutions, les techniciens marketing et les ingénieurs en implémentation qui ont besoin de comprendre tous les chemins d’implémentation viables, les compromis entre eux et les décisions de configuration requises à chaque phase.

Contrairement aux autres modèles de la taxonomie qui se concentrent sur l’activation et l’engagement (envoi de messages, personnalisation du contenu, activation des audiences), ce modèle se concentre sur la compréhension : l’analyse du comportement des clients, la mesure des performances de la campagne, l’identification des tendances et la génération d’informations qui éclairent les décisions de stratégie et d’optimisation. Il s’agit du modèle le plus souvent composé et associé à presque chaque modèle d’activation ou de personnalisation.

## Présentation du cas d’utilisation

Les entreprises doivent comprendre le comportement des clients sur l’ensemble des canaux, les performances des campagnes, l’endroit où les clients chutent dans leurs parcours, le contenu qui résonne et la manière dont les différents segments sont conservés au fil du temps. La génération de Customer Analytics et d’insight répond à ce besoin en connectant les données cross-canal riches en [!DNL Adobe Experience Platform] à [!DNL Customer Journey Analytics], où les analystes peuvent créer des espaces de travail à structure libre, créer des mesures personnalisées, configurer des modèles d’attribution et publier des tableaux de bord à l’intention des parties prenantes.

Ce modèle s’adresse à plusieurs audiences : les analystes marketing qui ont besoin d’une analyse exploratoire approfondie, les responsables de campagne qui ont besoin de tableaux de bord des performances, les chefs de produit qui ont besoin d’informations sur l’engagement et la rétention et les cadres qui ont besoin de cartes de performance d’un coup d’œil. L’approche de mise en œuvre varie en fonction de l’objectif analytique principal : mesure des performances de la campagne, analyse de parcours cross-canal, activation d’audience basée sur une analyse ou informations guidées sur les produits.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

**Amélioration des analyses et des rapports**

Améliorez les fonctionnalités de création de rapports pour obtenir des informations marketing plus rapides et plus exploitables grâce à des tableaux de bord unifiés et des outils en libre-service.

- **KPI : Efficacité** productivité

Consultez [Amélioration des analyses et des rapports](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md) pour plus d’informations sur cet objectif commercial.

**Activer la prise de décision pilotée par les données**

Donnez aux équipes les moyens d’utiliser des analyses en libre-service, des informations sur les clients en temps réel et des prédictions basées sur l’IA pour orienter la stratégie.

- **KPI : Efficacité** productivité

Consultez [Activer la prise de décision pilotée par les données](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md) pour plus d’informations sur cet objectif commercial.

**Amélioration de l’attribution marketing**

Mesurez avec précision l’impact des points de contact, des canaux et des campagnes marketing sur les résultats de conversion et de chiffre d’affaires.

- **KPI : Efficacité** revenus incrémentiels

Consultez [Amélioration de l’attribution marketing](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md) pour plus d’informations sur cet objectif commercial.

**Optimiser les dépenses marketing et le retour sur investissement**

Optimisez l’allocation du budget marketing en identifiant les canaux et les campagnes qui offrent le meilleur retour.

- **KPI : Efficacité** revenus incrémentiels

Consultez [ Optimiser les dépenses marketing et le retour sur investissement ](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md) pour plus d’informations sur cet objectif commercial.

## Exemples de cas d’utilisation tactiques

Vous trouverez ci-dessous des exemples de cas d’utilisation tactiques pouvant être mis en œuvre avec ce modèle.

- Tableau de bord des performances de la campagne : mesures de diffusion, taux d’engagement, conversion et attribution des recettes dans les campagnes par e-mail, SMS, notification push et médias achetés
- Analyse des abandons du parcours client : identifier où les clients quittent les tunnels d’achat, d’enregistrement ou d’intégration
- Analyse de rétention des cohortes : mesure de la rétention des différentes cohortes d’acquisition sur plusieurs semaines, mois et trimestres
- Modélisation de l’attribution des canaux : comparez l’attribution première touche, dernière touche, linéaire et décroissance temporelle pour comprendre quels canaux génèrent des conversions
- Analyse des performances du contenu : identifiez le contenu qui résonne le plus par segment, canal et étape du cycle de vie
- Analyse de l’utilisation et de l’adoption des produits : suivez l’adoption des fonctionnalités, la fréquence d’engagement et les tendances de croissance des utilisateurs
- Analyse des étapes du cycle de vie des clients : segmentez et analysez les clients par étape du cycle de vie (nouvelle, active, à risque, périmée).
- Tableau de bord d’optimisation du marketing mix - Comparer l’investissement dans les canaux à la contribution au chiffre d’affaires
- Score et reporting d&#39;engagement cross-canal : créez des scores d&#39;engagement composites à partir d&#39;interactions web, d&#39;applications, de courriers électroniques et de campagnes

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Efficacité | Réduction du temps nécessaire à insight et des efforts de création de rapports manuels | Effectuer le suivi du temps passé par les analystes à créer des rapports avant et après l’implémentation de CJA |
| Productivité | Nombre d’analyses en libre-service créées par les utilisateurs professionnels | Surveillance de la création de projets Workspace et de l’utilisation des tableaux de bord |
| Revenu incrémentiel | Chiffre d’affaires attribué aux décisions d’optimisation basées sur les informations | Mesurer l’effet élévateur de revenu des campagnes optimisées en fonction de l’analyse CJA |
| Taux de conversion | Taux d’achèvement de funnel dans les principaux parcours clients | Suivre les taux d’abandons à chaque étape du parcours à l’aide de la visualisation des abandons CJA |
| Engagement | Profondeur et fréquence des interactions des clients sur l’ensemble des canaux | Création de mesures calculées pour le score de l’engagement dans CJA |
| Rétention | Taux de retour client sur des périodes définies | Utilisation de l’analyse des cohortes CJA pour mesurer les courbes de rétention |

## Modèle de cas d’utilisation

**Customer Analytics et génération d’insight**

Créez des espaces de travail d’analyse cross-canal, des mesures calculées et des tableaux de bord pour comprendre le comportement des clients et clientes et les performances des campagnes.

**Chaîne de fonctions :** Connexion de données > Configuration des vues de données > Analyse Workspace > Création des mesures calculées > Publication sur le tableau de bord

Voir la section [Options d’implémentation](#implementation-options) pour obtenir des conseils sur la composition.

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Customer Journey Analytics](CJA)** : connexions, vues de données, analyse de l’espace de travail, analyse guidée, mesures calculées, tableaux de bord, publication d’audiences et analyse de contenu
- **[!DNL Adobe Experience Platform](AEP)** : lac de données, jeux de données, schémas XDM, données de profil et d’événement qui alimentent les connexions CJA

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | Profil de produit CJA configuré avec les autorisations de création d’espace de travail et d’accès aux vues de données. Jeux de données AEP accessibles à la connexion CJA. Utilisateurs affectés aux rôles CJA appropriés. | [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Les schémas et les jeux de données XDM qui seront connectés à CJA doivent exister dans AEP. La conception de schémas a un impact direct sur les dimensions et mesures disponibles dans les vues de données CJA. Les schémas d’événement nécessitent des champs d’horodatage ; les schémas de recherche nécessitent des champs clés. | [ Présentation du système XDM ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Sources et collecte de données | Obligatoire | Les données doivent circuler dans les jeux de données AEP : événements web via Web SDK, événements d’application via Mobile SDK, événements de campagne AJO, données CRM via des connecteurs source. La richesse des analyses dépend de l’ampleur des données collectées. | [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Configuration des identités et des profils | Obligatoire | La configuration de l’ID de personne dans la connexion CJA détermine la manière dont les événements sont regroupés dans les jeux de données. La combinaison d’identités entre appareils dans AEP améliore la capacité de CJA à créer des parcours client complets. L’espace de noms d’identité doit être configuré pour le champ ID de personne . | [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Définition et segmentation de l’audience | Sans objet | CJA crée ses propres filtres et audiences dans le contexte d’analyse. Les audiences RT-CDP ne sont pas une condition préalable, bien que CJA puisse republier des audiences dans AEP via la publication d’audience (option C). | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés d’AEP peuvent enrichir les jeux de données connectés à CJA, fournissant des dimensions et des mesures supplémentaires pour l’analyse (par exemple, nombre d’achats sur la durée de vie, jours depuis la dernière activité). Ces agrégations au niveau du profil sont disponibles en tant que dimensions dans les vues de données CJA. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | Les politiques de conservation des jeux de données affectent les données historiques disponibles dans CJA. La rétention à long terme est généralement souhaitée pour Analytics afin d’activer les comparaisons d’une année sur l’autre et l’analyse des tendances à long terme. Configurez les TTL de jeux de données pour garantir une profondeur historique adéquate. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les libellés de gouvernance sur les champs sensibles peuvent restreindre ce qui apparaît dans les vues de données CJA. Si des informations d’identification personnelles ou des données sensibles sont incluses dans la connexion CJA, les étiquettes de gouvernance des données garantissent un accès conforme et empêchent toute exposition non autorisée dans les tableaux de bord partagés. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Surveillance et observabilité | Recommandé | L’intégrité de la connexion CJA et l’actualisation des données doivent être surveillées. Configurez des alertes pour les échecs de flux de données source et les problèmes d’ingestion afin de vous assurer que le CJA d’alimentation des données est fiable et à jour. | [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Il s’agit de la mise en œuvre des rapports et des analyses. Lorsqu’un plan de référence pour un autre modèle inclut S5, utilisez ce plan de génération Customer Analytics et insight pour l’implémentation d’Analytics. | Présentation de [](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Customer Journey Analytics] (CJA)

Le tableau suivant répertorie les fonctions d’application CJA utilisées dans ce modèle.

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Connexion aux données | Phase 1 : Connexion Des Données | Lier des jeux de données AEP à une connexion CJA pour une analyse cross-canal, en configurant les types de jeux de données et l’ID de personne pour le groupement entre jeux de données |
| Configuration de la vue de données | Phase 2 : configuration des vues de données | Définissez les dimensions, mesures, modèles d’attribution, paramètres de persistance, paramètres de session et champs dérivés qui façonnent la perspective analytique |
| Analyse Workspace | Phase 3 : Création d’analyses et de mesures | Créez des projets d’analyse de structure libre avec des tableaux, des visualisations, des filtres, des annotations et des répartitions de dimensions (options A, B et C). |
| Analyse guidée | Phase 3 : Création d’analyses et de mesures | Utiliser des workflows guidés structurés pour l’analyse de funnel, des tendances, de la fidélisation, de la croissance des utilisateurs et utilisatrices et de la fréquence d’engagement (option D) |
| Création de mesure calculée | Phase 3 : Création d’analyses et de mesures | Définir des mesures calculées à l’aide de formules, de filtres et de fonctions pour les KPI réutilisables tels que le taux de conversion, le score d’engagement et le chiffre d’affaires par visite |
| Publication sur tableau de bord et carte de score | Phase 4 : publication du tableau de bord | Créer et partager des tableaux de bord interactifs et des cartes de performance mobiles pour le reporting des parties prenantes |
| Publication d’audiences | Phase 5 : publication auprès d’une audience (option C uniquement) | Publiez à nouveau des audiences définies par CJA dans le profil client en temps réel d’AEP pour l’activation en aval |
| Content Analytics | Phase 3 : Création d’analyses et de mesures | Analysez les tendances, les anomalies et la fatigue des performances du contenu sur les propriétés numériques (lorsque l’analyse du contenu est le point central). |

### [!DNL Adobe Experience Platform] (AEP)

Le tableau suivant répertorie les fonctions d’application AEP utilisées dans ce modèle.

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Lac de données et jeux de données | Prérequis (F2, F3) | Fournissez les jeux de données d’événement source, de profil et de recherche qui alimentent la connexion CJA |
| Service d’identité | Prérequis (F4) | Fournir une configuration d’espace de noms d’identité pour l’assemblage des ID de personne entre les jeux de données dans la connexion CJA |

## Conditions préalables

Les conditions préalables suivantes doivent être remplies avant d’implémenter ce modèle de cas d’utilisation.

- [ ] droits de produit CJA est configuré pour l’organisation
- [ ] profils de produit CJA sont configurés avec un accès utilisateur approprié (création d’espace de travail, accès aux vues de données)
- [ ] sandbox AEP contient les jeux de données cibles avec des flux de données (événements web, événements d’application, données de campagne, enregistrements CRM)
- [ ] schémas XDM sont définis pour tous les jeux de données sources avec les groupes de champs appropriés
- [ ] champ ID de personne est identifié et systématiquement disponible pour tous les jeux de données qui seront connectés
- [ ] Les espaces de noms d’identité sont configurés dans AEP pour l’ID de personne utilisé dans l’assemblage des connexions CJA
- [ ] Les exigences des parties prenantes sont documentées : quels indicateurs clés de performance, quelles audiences utiliseront les tableaux de bord, quel niveau de détail
- [ ] Pour les cartes de performance mobiles : l’application mobile des tableaux de bord [!DNL Adobe Analytics] est installée pour les parties prenantes
- [ ] pour l’option C (publication d’audiences) : le profil client en temps réel d’AEP est activé dans le sandbox cible
- [ ] pour l’option D (analyse guidée) : le SKU CJA comprend des fonctionnalités d’analyse guidée

## Options de mise en œuvre

Cette section décrit les options d’implémentation disponibles pour ce modèle de cas d’utilisation.

### Option A : analyse des performances de Campaign

**Idéal pour :** mesurer et optimiser l’efficacité des campagnes et des parcours : tableaux de bord des campagnes par e-mail, analyse des funnel de parcours, comparaison des performances des canaux et rapports sur le retour sur investissement marketing.

**Fonctionnement :**

Cette option connecte les jeux de données de campagne et de parcours d’AJO à CJA, configure les vues de données avec les mesures de diffusion et d’engagement (envois, diffusions, ouvertures, clics, bounces, désabonnements), crée des tableaux de bord de performances de campagne et publie des cartes de performance pour les parties prenantes marketing. L’objectif est de comprendre les performances des campagnes marketing sur l’ensemble des canaux et au fil du temps.

La vue de données est configurée avec des dimensions spécifiques à la campagne (nom de la campagne, nom du parcours, type de canal, variante du message) et des mesures de diffusion. Les mesures calculées sont créées pour les mesures dérivées telles que le taux d’ouverture, le taux de clic publicitaire, le taux de conversion et le chiffre d’affaires par message. Les tableaux de bord présentent ces indicateurs de performance clés avec des périodes de comparaison pour l’analyse des tendances.

**Considérations principales :**

- Nécessite des jeux de données de campagne et d’événement de parcours AJO dans AEP
- Les modèles d’attribution doivent s’aligner sur la philosophie de mesure des campagnes de l’organisation
- Pensez à inclure les rapports natifs AJO (pour les mesures de diffusion opérationnelles) et CJA (pour l’impact commercial cross-canal)

**Avantages :**

- Conçu spécifiquement pour la mesure et l’optimisation des campagnes
- Permet la comparaison entre campagnes et l’analyse de la combinaison de canaux
- Les mesures calculées fournissent des définitions de KPI normalisées pour toutes les campagnes
- Les cartes de performance mobiles offrent des performances instantanées aux responsables marketing

**Limitations :**

- Limité aux données de campagne et de parcours ; ne fournit pas un contexte de parcours client complet.
- N’inclut pas le cheminement du parcours, les abandons ou l’analyse des cohortes
- L’attribution est étendue aux points de contact de la campagne plutôt qu’au parcours client complet

**Experience League:**

- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Présentation de Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Option B : Analyse du parcours client

**Idéal pour :** comprendre les parcours client cross-canal : analyse des abandons, analyse des chemins, rétention des cohortes, modélisation d’attribution et analyse des étapes du cycle de vie sur le web, les applications, les e-mails, le CRM et les points de contact hors ligne.

**Fonctionnement :**

Cette option connecte plusieurs jeux de données AEP (événements web, événements d’application, données CRM, interactions de campagne, enregistrements transactionnels) pour créer une vue cross-canal unifiée du parcours client. La vue de données est configurée avec des dimensions et des mesures couvrant tous les canaux. Les visualisations de flux, d’abandons, de cohortes et d’attribution de CJA sont utilisées pour analyser la manière dont les clients se déplacent dans les parcours, où ils chutent, comment différents segments sont conservés et quels canaux méritent du crédit pour les conversions.

Il s’agit de l’option analytique la plus complète, offrant une connaissance approfondie d’insight dans l’expérience client de bout en bout. Il s’agit également de la plus complexe à implémenter, nécessitant une configuration minutieuse de l’ID de personne pour l’assemblage entre jeux de données et une conception de vue de données réfléchie pour exposer les dimensions et mesures appropriées.

**Considérations principales :**

- Nécessite un ID de personne cohérent sur tous les jeux de données connectés pour une analyse cross-canal précise
- La conception de schémas dans AEP a un impact direct sur la qualité et la profondeur de l’analyse CJA
- Plus de jeux de données dans la connexion signifie une analyse plus riche, mais des temps de renvoi plus longs
- La modélisation d’attribution nécessite des définitions d’événement de conversion claires

**Avantages :**

- Visibilité complète du parcours client cross-canal
- Suite complète de visualisations CJA : flux, abandon, cohorte, attribution, tableaux à structure libre
- Permet de découvrir les informations invisibles dans le compte rendu des performances à canal unique
- Prend en charge des questions analytiques complexes sur le comportement et le cycle de vie des clients

**Limitations :**

- Plus grande complexité d’implémentation en raison des connexions à plusieurs jeux de données et de l’assemblage cross-canal
- Nécessite une planification plus précoce de la configuration des vues de données et des champs dérivés
- Le renvoi pour des connexions multi-jeux de données volumineuses peut prendre plusieurs jours
- La qualité de l&#39;analyse dépend de l&#39;exhaustivité et de la cohérence des données sous-jacentes

**Experience League:**

- [Présentation des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Visualisation de flux](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualisation des abandons](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Table de cohorte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Panneau d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)

### Option C : Analytics avec publication d’audiences

**Idéal pour** activation basée sur l’analyse : découvrez des segments intéressants par le biais de l’analyse CJA, puis publiez-les de nouveau dans AEP pour activation via les destinations RT-CDP, les campagnes AJO ou les parcours AJO.

**Fonctionnement :**

Cette option étend l’option A ou l’option B avec la publication d’audience à partir de CJA. Les analystes créent des segments dans CJA à l’aide de données comportementales cross-canal et de la pleine puissance d’analyse des filtres CJA, puis publient ces audiences dans le profil client en temps réel d’AEP pour l’activation en aval. Cela permet de combler le fossé entre insight et l’action : les segments découverts lors de l’analyse exploratoire deviennent des audiences exploitables sans avoir à les recréer manuellement dans le créateur de segments d’AEP.

Les audiences publiées apparaissent dans AEP Audience Portal avec l’origine « CJA » et peuvent être activées vers n’importe quelle destination RT-CDP, utilisées comme cibles de campagne dans AJO ou comme conditions d’entrée de parcours.

**Considérations principales :**

- Nécessite que le profil client en temps réel AEP soit activé dans le sandbox cible
- La connexion CJA doit comporter un ID de personne valide qui est résolu sur un espace de noms d’identité AEP
- Les audiences publiées sont comptabilisées dans les droits d’audience AEP de l’organisation
- La fréquence d’actualisation doit être configurée en fonction des exigences d’activation (une fois, toutes les 4 heures, quotidiennement, toutes les semaines).

**Avantages :**

- Ferme la boucle entre l’analyse et l’activation
- Permet de découvrir des segments à forte valeur ajoutée à l’aide des données comportementales cross-canal de CJA
- Les audiences définies dans CJA peuvent utiliser des dimensions et des filtres qui ne sont pas disponibles dans le créateur de segments d’AEP
- Prend en charge l’affinement itératif des critères d’audience en fonction d’informations analytiques

**Limitations :**

- Maximum de 75 audiences publiées par client CJA
- L’évaluation initiale de l’audience peut prendre jusqu’à 24 heures pour les jeux de données volumineux
- Les audiences publiées par CJA ne peuvent pas être modifiées dans AEP. des modifications doivent être apportées dans CJA.
- Nécessite un espace de noms d’identité et une configuration de profil supplémentaires au-delà des analyses de base

**Experience League:**

- [Présentation des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Création et publication d’audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

### Option D : analyse guidée pour les équipes produit

**Idéal pour** informations sur l’expérience produit : adoption des fonctionnalités, tendances d’interaction client, analyse de la rétention, conversion de funnel et analyse de l’impact des versions à l’aide de workflows d’analyse guidée par CJA sans nécessiter de configuration de projet Workspace à structure libre complexe.

**Fonctionnement :**

Cette option utilise l’analyse guidée par CJA pour la génération structurée et modélisée d’insight. L’analyse guidée fournit des types d’analyse préconfigurés (funnel, tendances, fidélisation, croissance des utilisateurs, fréquence d’engagement, impact des versions, première utilisation et chronologie) qui guident les analystes dans un workflow structuré afin de répondre à des questions spécifiques sur le produit et l’expérience. Il est idéal pour les chefs de produit et les analystes qui ont besoin d’informations rapides et ciblées sans avoir à créer des projets à structure libre à partir de zéro.

La mise en œuvre connecte les jeux de données AEP à CJA, configure une vue de données avec des dimensions et des mesures au niveau de l’événement, puis utilise des workflows d’analyse guidée pour générer des informations. Les résultats peuvent être enregistrés en tant que panneaux dans les projets Workspace pour une personnalisation plus poussée.

**Considérations principales :**

- L’analyse guidée nécessite des droits de produit CJA qui incluent des fonctionnalités d’analyse guidée
- Idéal pour l’analyse des produits et des expériences plutôt que pour la mesure des performances des campagnes
- Fournit des workflows structurés plus accessibles aux utilisateurs non-analystes
- Peut être associé à une analyse Workspace à structure libre pour une exploration plus approfondie

**Avantages :**

- Barrière d’entrée plus faible : les workflows structurés guident les utilisateurs tout au long de l’analyse
- Conçu spécifiquement pour les questions relatives à l’expérience produit (funnel, rétention, croissance, impact)
- Un délai de mise sur le marché d’insight plus rapide pour les questions analytiques courantes
- Les analyses enregistrées peuvent être incorporées dans des projets Workspace parallèlement à l’analyse de structure libre

**Limitations :**

- Moins flexible que l’analyse Workspace à structure libre
- Limité aux types d’analyse préconfigurés (funnel, tendances, rétention, croissance, fréquence, impact, chronologie)
- Les comparaisons de segments prennent en charge jusqu’à 3 segments simultanément
- L’analyse funnel prend en charge un maximum de 15 étapes

**Experience League:**

- [Aperçu des analyses guidées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Vue funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Vue de rétention](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

### Comparaison des options

Le tableau suivant compare les options d’implémentation disponibles.

| Critères | Option A : Performances de la campagne | Option B : parcours client | Option C : Analytics + activation | Option D : Analyse guidée |
| --- | --- | --- | --- | --- |
| Idéal pour | Mesure et optimisation des campagnes | Compréhension du parcours cross-canal | Activation d’audience pilotée par Insight | Informations sur l’expérience du produit |
| Complexité | Low-Medium | Élevée | Élevée | Faible |
| Jeux de données requis | Campagne AJO/événements de parcours | Jeux de données cross-canal multiples | Identique à A ou B, plus l’identité du profil | Jeux de données d’événements avec interactions de produits |
| Visualisations clés | Tableaux à structure libre, synthèses des chiffres, lignes de tendance | Flux, abandon, cohorte, attribution | Identique à A ou B, plus publication d’audience | Funnel, tendances, rétention, croissance |
| Fonction d&#39;activation | Non (rapports uniquement) | Non (rapports uniquement) | Oui (publie des audiences dans AEP) | Non (rapports uniquement) |
| Audience requise | Analystes marketing, responsables de campagne | Analystes de données, architectes de parcours | Analystes + équipes d’activation | Chefs de produit, analystes de croissance |
| Fonctions CJA utilisées | Connexion, Vue De Données, Workspace, Mesures Calculées, Tableau De Bord | Connexion, Vue De Données, Workspace, Mesures Calculées, Tableau De Bord | Identique à A ou B, plus Publication d’audiences | Connexion, Vue De Données, Analyse Guidée, Tableau De Bord |
| Temps jusqu’à la première insight | Jours | Semaines | Semaines | Heures-Jours |

### Choisir la bonne option

Suivez les conseils ci-dessous pour sélectionner l’option d’implémentation qui correspond le mieux à vos besoins.

- **Si votre objectif principal est de mesurer l’efficacité de la campagne** et que vous disposez de données de campagne AJO qui circulent dans AEP, commencez par **Option A**. Il offre le délai de rentabilisation le plus rapide pour le compte rendu des performances marketing.

- **Si vous devez comprendre le parcours client complet** sur le web, l’application, les e-mails et les points de contact hors ligne, et que vous disposez de plusieurs jeux de données avec un ID de personne cohérent, choisissez **Option B**. Il offre les fonctionnalités d’analyse les plus approfondies, mais nécessite davantage d’investissement initial dans la configuration des vues de données.

- **Si vous souhaitez agir sur les informations** en publiant à nouveau les segments découverts par CJA dans AEP pour activation dans RT-CDP ou AJO, choisissez **Option C**. Cela étend les options A ou B avec la publication d’audience et nécessite la configuration du profil client en temps réel d’AEP.

- **Si votre équipe a besoin d’informations rapides et structurées sur les produits** sans la complexité des projets de Workspace à structure libre et que votre SKU CJA comprend une analyse guidée, choisissez **Option D**. Il s’agit du chemin le plus rapide pour répondre à des questions spécifiques sur l’expérience produit.

- **De nombreuses entreprises mettent en œuvre plusieurs options** : option A pour les tableaux de bord de campagne de l’équipe marketing, option B pour l’analyse cross-canal de l’équipe analytics et option D pour les informations en libre-service de l’équipe produit. Ces options partagent la même connexion CJA et la même infrastructure de vue de données.

## Phases de mise en œuvre

Cette section décrit les phases d’implémentation étape par étape de ce modèle de cas d’utilisation.

### Phase 1 : Connexion aux données

**Fonction d’application :** CJA : Connexion aux données

Cette phase configure une connexion CJA qui lie un ou plusieurs jeux de données AEP à CJA pour analyse. La connexion définit les jeux de données qui se déplacent dans CJA, la manière dont les événements sont regroupés entre les jeux de données via l’ID de personne et la manière dont les données historiques et de diffusion en continu sont ingérées. Il s’agit du lien fondamental entre le lac de données d’AEP et CJA.

#### Points de décision

Les décisions suivantes doivent être prises au cours de cette phase.

>[!NOTE]
>**Décision : sélection du sandbox AEP**
>
>Quel sandbox AEP contient les jeux de données sources ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Sandbox de production | Données clients en direct pour le compte rendu des performances de production | Utiliser pour les tableaux de bord de production et les rapports des parties prenantes |
>| Sandbox de développement | Tests et itération avant le déploiement en production | À utiliser pour la configuration et la validation initiales avant la promotion en production |

>[!NOTE]
>**Décision : sélection du jeu de données et désignation du type**
>
>Quels jeux de données AEP doivent être inclus dans la connexion et quel type doit être attribué à chacun d’eux ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Jeux de données d’événements | Données comportementales horodatées (interactions web, événements d’application, interactions de campagne, transactions) | Nécessite un champ de date et heure ; constitue le cœur de la plupart des analyses |
>| Jeux de données de recherche | Données de référence clé-valeur (catalogue de produits, métadonnées de campagne, emplacements de magasin) | Joint aux données d’événement via une clé partagée ; seul le dernier état est utilisé |
>| Jeux de données de profil | Attributs au niveau de la personne (niveau de fidélité, valeur de durée de vie, attributs CRM) | Fournir un enrichissement au niveau de la personne ; seul le dernier état est utilisé. |

>[!NOTE]
>**Décision : configuration de l’ID de personne**
>
>Quel champ sert d’ID de personne pour le groupement entre jeux de données ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| ID CRM | L’organisation dispose d’un identifiant CRM cohérent sur tous les canaux | Fournit l’assemblage cross-canal le plus précis pour les clients connus |
>| ECID (Experience Cloud ID) | Analyse principalement du comportement web/d’application anonyme | Étendue de l’appareil ; ne se connecte pas aux appareils sans résolution d’identité |
>| E-mail (haché) | L’e-mail est l’identifiant commun aux jeux de données | Fonctionne bien lorsque les e-mails sont capturés de manière cohérente entre les points de contact |
>| Espace de noms personnalisé | L’entreprise utilise un identifiant propriétaire. | Doit correspondre à un espace de noms d’identité AEP pour la publication d’audience (option C) |

>[!NOTE]
>**Décision : plage de renvoi**
>
>Quelle quantité de données historiques doit être importée dans la connexion ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Toutes les données existantes | Profondeur historique maximale nécessaire pour les comparaisons d’une année sur l’autre et les tendances à long terme | Le renvoi de jeux de données volumineux (milliards d’enregistrements) peut prendre plusieurs jours |
>| Période personnalisée | Seul un historique récent est pertinent ou l’optimisation du stockage pose problème | Limite la profondeur historique disponible pour l’analyse |
>| Pas de renvoi | Seule une analyse prospective est nécessaire | Configuration de la connexion la plus rapide ; aucune donnée historique disponible jusqu’à ce que de nouvelles données soient introduites |

>[!NOTE]
>**Décision : activation de la diffusion en continu**
>
>Les nouvelles données doivent-elles circuler dans CJA en temps quasi réel ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Activer la diffusion en continu | Des rapports en temps quasi réel sont nécessaires (données disponibles dans les 90 minutes suivant l’ingestion d’AEP) | La plus courante pour les connexions de production ; permet une analyse en temps voulu |
>| Lot uniquement | Une actualisation périodique est suffisante et le streaming n’est pas nécessaire | Configuration plus simple ; données disponibles après le traitement par lots |

#### Configurer la connexion aux données

**Navigation dans l’interface utilisateur :** CJA > Connexions > Créer une connexion

Détails de configuration clés :

- Le nom et la description de la connexion doivent respecter les conventions de dénomination de l’organisation
- Le nombre moyen d’événements quotidiens est utilisé pour la planification de la capacité de CJA
- Tous les jeux de données d’une seule connexion doivent provenir du même sandbox AEP
- Les champs d’ID de personne doivent être cohérents entre tous les jeux de données pour un regroupement précis entre les jeux de données
- Vérifiez que le champ ID de personne existe et est renseigné dans chaque jeu de données avant de l’ajouter à la connexion

**Documentation Experience League :**

- [Présentation des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Création ou modification d’une connexion](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Gérer des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [Mécanismes de sécurisation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Phase 2 : configuration des vues de données

**Fonction d’application :** CJA : configuration des vues de données

Cette phase configure une vue de données qui définit la manière dont les données de connexion apparaissent dans l’analyse. La vue de données détermine les champs de schéma exposés en tant que dimensions et mesures, la manière dont les valeurs sont attribuées et conservées, la manière dont les sessions sont définies et les champs dérivés qui transforment les données brutes en composants prêts à l’analyse. Plusieurs vues de données peuvent être créées à partir d’une seule connexion pour différentes perspectives analytiques.

#### Points de décision

Les décisions suivantes doivent être prises au cours de cette phase.

>[!NOTE]
>**Décision : dénomination du conteneur**
>
>Quelle terminologie les conteneurs doivent-ils utiliser pour correspondre au domaine d’activité ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Par Défaut (Personne / Session / Événement) | L’équipe comprend la terminologie analytique standard | Fonctionne pour la plupart des implémentations |
>| Noms personnalisés (par exemple, acheteur/visite/interaction) | La terminologie spécifique au domaine d’activité améliore l’adoption par les utilisateurs et utilisatrices | Aide les parties prenantes non techniques à comprendre la portée de l’analyse |
>| Noms B2B (par exemple, compte / engagement / point de contact) | Analyses B2B où l’analyse au niveau du compte est l’élément central | Aligne la portée du conteneur sur les concepts commerciaux B2B |

>[!NOTE]
>**Décision : expiration de la session**
>
>Quelle est la durée d’inactivité définissant une limite de session ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| 30 minutes (par défaut) | Définition de session Web Analytics standard | Norme du secteur ; s’aligne sur la plupart des références d’analyse |
>| 15 minutes | Contenu de forme courte ou sites transactionnels où les utilisateurs effectuent des tâches rapidement | Crée plus de sessions ; peut mieux capturer des intentions d’utilisateur distinctes |
>| 60 minutes ou plus | Contenu de forme longue, interactions B2B complexes ou parcours nécessitant de nombreuses recherches | Moins de sessions ; capture la recherche étendue en tant que sessions uniques |
>| Personnalisé avec les nouveaux événements de session | Certains événements (par exemple, lancement d’application, clic publicitaire dans une campagne) doivent toujours démarrer une nouvelle session | Détermine les limites de session en fonction de la logique métier |

>[!NOTE]
>**Décision : valeurs par défaut du modèle d’attribution**
>
>Quel modèle d’attribution par défaut doit être appliqué aux mesures de conversion ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Dernière touche (par défaut) | Le crédit doit être attribué au point de contact le plus récent avant la conversion | Simple et intuitif ; peut sous-estimer les canaux de sensibilisation |
>| Première touche | Comprendre quels canaux génèrent la prise de conscience et l’acquisition initiales | Utile pour l’analyse d’acquisition ; ignore les points de contact de culture |
>| Linéaire | Tous les points de contact doivent partager le même crédit | Répartition équitable ; peut diluer l’impact des points de contact clés |
>| Atténuation temporelle | Les points de contact récents doivent être mieux reconnus que les points distants | Équilibre la récence avec la contribution historique |
>| en U | Le premier et le dernier points de contact méritent le plus de reconnaissance | Bon pour comprendre les canaux d’acquisition et de fermeture |
>| Algorithmique | Attribution pilotée par les données à l’aide de modèles d’IA CJA | Les plus précis, mais nécessite un volume de données de conversion suffisant |

>[!NOTE]
>**Décision : logique de champ dérivé**
>
>Des règles métier personnalisées sont-elles nécessaires pour transformer les données brutes en dimensions prêtes pour l’analyse ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Classification de canal marketing (cas si) | Les codes de suivi bruts doivent être classés en groupes de canaux | Cas d’utilisation de champ dérivé le plus courant ; critique pour l’analyse de canal |
>| Regroupement des valeurs | Les valeurs continues doivent être regroupées en plages (par exemple, niveaux de valeur d’ordre) | Simplifie l’analyse des mesures continues |
>| Fusion de champs | Plusieurs champs sources doivent être combinés en une seule dimension | Utile lorsque le même concept existe dans différents chemins de schéma entre les jeux de données |
>| Extraction basée sur une expression régulière | Les valeurs structurées doivent être analysées (par exemple, extraction du type de campagne du code de campagne) | Puissant, mais nécessite une conception de modèle RegEx soignée |

#### Configurer la vue de données

**Navigation dans l’interface utilisateur :** CJA > Vues de données > Créer une vue de données

Détails de configuration clés :

- Sélectionnez la connexion parente créée à la phase 1
- Configuration du fuseau horaire et du type de calendrier pour répondre aux exigences de création de rapports
- Mappez les champs de schéma XDM aux dimensions avec les paramètres de persistance appropriés (attribution et expiration).
- Mappez les champs de schéma XDM aux mesures avec les paramètres de format (décimal, entier, devise, pourcentage, temps) et d’attribution.
- Configurez les règles d’inclusion/exclusion sur les dimensions pour filtrer les valeurs non pertinentes
- Activer la déduplication des mesures si nécessaire pour éviter le double comptage
- Créer des champs dérivés pour la classification de canal marketing, le regroupement de valeurs ou la fusion de champs
- Maximum de 5 000 dimensions et 5 000 mesures par vue de données
- Maximum de 100 champs dérivés par vue de données

#### Là où les options divergent

**Pour l’option A (Analyse des performances de Campaign) :**

Mapper des dimensions spécifiques à une campagne : nom de la campagne, nom du parcours, type de canal, variante du message, objet. Mapper les mesures de diffusion : envois, diffusions, ouvertures, clics, bounces, désabonnements. Configurez l’attribution sur les mesures de conversion en fonction de la philosophie de mesure de campagne.

**Pour l’option B (Analyse des parcours client) :**

Mapper des dimensions cross-canal : nom de page, écran d’application, canal, campagne, produit, type de contenu. Mappez les mesures d’engagement et de conversion sur tous les canaux. Configurez plusieurs modèles d’attribution pour l’analyse de comparaison. Créez des champs dérivés pour la classification de canal et l’identification de l’étape de parcours.

**Pour l’option D (analyse guidée) :**

Mappez des dimensions et des mesures au niveau de l’événement pertinentes pour l’analyse de l’expérience du produit : nom de la fonctionnalité, action de l’utilisateur, type d’engagement. Concentrez-vous sur les événements qui définissent les étapes de funnel, les critères de rétention et les signaux de croissance.

**Documentation Experience League :**

- [Présentation des vues de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Créer ou modifier une vue de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Présentation des paramètres de composant](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Paramètres de persistance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Paramètres d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Paramètres de format](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Déduplication des mesures](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Valeurs d’inclusion/exclusion](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Paramètres de session](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Champs dérivés](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Phase 3 : création d’analyses et de mesures

**Fonction d’application :** CJA : Analyse Workspace, CJA : Analyse guidée, CJA : Création de mesure calculée

Cette phase crée les espaces de travail d’analyse (projets à structure libre ou analyse guidée), les mesures calculées pour les indicateurs clés de performance dérivés, les filtres pour l’analyse segmentée et les annotations pour les événements clés. C’est là que se produit la valeur analytique : en créant les tableaux, les visualisations et les mesures qui répondent aux questions commerciales.

#### Points de décision

Les décisions suivantes doivent être prises au cours de cette phase.

>[!NOTE]
>**Décision : approche d’analyse**
>
>Cette analyse doit-elle utiliser des projets Workspace à structure libre ou des workflows d’analyse guidée ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Workspace à structure libre (options A, B et C) | Analyse exploratoire approfondie, dispositions personnalisées, répartitions complexes, visualisations avancées | Flexibilité maximale ; nécessite des compétences d’analyste ; prend en charge tous les types de visualisation |
>| Analyse Guidée (Option D) | Informations structurées sur les produits, réponses rapides à des questions spécifiques, utilisateurs moins techniques. | Délai d’exécution d’insight plus rapide ; limité à des types d’analyse préconfigurés ; enregistre dans Workspace pour une personnalisation plus poussée. |
>| Les deux | L’organisation a besoin d’une analyse approfondie et d’informations structurées rapides | Utiliser l’analyse guidée pour les questions courantes ; Workspace pour l’exploration en profondeur |

>[!NOTE]
>**Décision : types de visualisation**
>
>Quelles visualisations communiquent le mieux les informations pour ce cas d’utilisation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Tableau à structure libre | Exploration détaillée des données avec les répartitions des dimensions | Base de la plupart des analyses ; prend en charge jusqu’à 10 niveaux de répartition |
>| Visualisation de flux | Comprendre le comportement du cheminement (flux de page, transitions de canal) | Excellent pour la découverte de chemins parcours ; peut être complexe avec une cardinalité élevée |
>| Visualisation des abandons | Mesure de la conversion par le biais d’une séquence définie de points de contact | Idéal pour l’analyse funnel ; indique clairement une baisse à chaque étape. |
>| Table de cohorte | Analyse de la rétention dans le temps par cohorte d’acquisition | Indique l’efficacité de rétention des différents groupes ; essentiel pour l’analyse du cycle de vie |
>| Panneau d’attribution | Comparaison des modèles d’attribution pour les mesures de conversion | Comparaison de modèles côte à côte ; nécessite une définition claire de l’événement de conversion. |
>| Synthèse des chiffres/modification | Affichage des indicateurs de performance clés exécutifs avec comparaison période par période | Affichage des mesures clair en un coup d’œil ; idéal pour les en-têtes de tableau de bord |

>[!NOTE]
>**Décision : formules de mesures calculées**
>
>Quels indicateurs de performance clés métier nécessitent des mesures calculées au-delà des mesures de vue de données de base ?
>
>| Modèle de mesure | Exemple de formule | Quand l’utiliser |
>| --- | --- | --- |
>| Rapport / Taux | Commandes/Visites | Taux de conversion, taux de clics publicitaires, taux de rebonds |
>| Mesure filtrée | Revenu (où canal = « e-mail ») | Mesures spécifiques au canal ou au segment |
>| Moyenne par article | Chiffre d’affaires/commandes | Valeur de commande moyenne, chiffre d’affaires par visite |
>| Formule composée | (Chiffre d’affaires - Coût) / Chiffre d’affaires | Pourcentage de marge, calculs du retour sur investissement |
>| Score d’engagement | Somme pondérée des interactions | Score d’engagement composite sur plusieurs canaux |

#### Configuration des analyses et des mesures

**Navigation dans l’interface utilisateur :**

- Workspace : CJA > Workspace > Projets > Créer un projet > Projet vierge
- Analyse guidée : CJA > Accueil > Analyse guidée (ou Workspace > Créer > Analyse guidée)
- Mesures calculées : CJA > Composants > Mesures calculées > Créer
- Filtres : CJA > Composants > Filtres > Créer un filtre

Détails de configuration clés :

- Sélectionnez la vue de données créée à la phase 2 comme vue de données du projet
- Définir des périodes et des périodes de comparaison appropriées pour l’analyse
- Créer des tableaux à structure libre en faisant glisser les dimensions vers les lignes et les mesures vers les colonnes
- Ajoutez des répartitions de dimension pour explorer les données à des niveaux plus profonds (par exemple, canal par campagne, page par produit).
- Créez des filtres réutilisables (segments) pour une analyse spécifique à l’audience (portée au niveau de la personne, de la session ou de l’événement)
- Ajoutez des annotations pour marquer les événements métier clés (lancements de produit, campagnes, incidents).
- Définissez le format des mesures calculées (décimale, pourcentage, devise, heure) et la polarité (une hausse est bonne ou une mauvaise).
- Partager des projets Workspace avec des utilisateurs de CJA disposant d’autorisations d’affichage ou de modification

#### Là où les options divergent

**Pour l’option A (Analyse des performances de Campaign) :**

Créer des tableaux à structure libre avec des dimensions de campagne réparties par mesures de diffusion et d’engagement. Créez des mesures calculées pour le taux d’ouverture, le taux de clic publicitaire, le taux de conversion, le chiffre d’affaires par message et le retour sur investissement de la campagne. Ajoutez des visualisations des tendances pour suivre les performances des campagnes au fil du temps. Comparez des variantes de campagne avec la comparaison de segments.

**Pour l’option B (Analyse des parcours client) :**

Créez des visualisations des abandons pour identifier les points de dépôt de parcours. Créez des visualisations de flux pour découvrir des modèles de navigation sur les canaux. Créez des tableaux de cohortes pour mesurer la rétention par cohorte d’acquisition. Configurez le panneau d’attribution pour comparer les modèles d’attribution pour les mesures de conversion. Créez des mesures calculées pour le taux d’achèvement du parcours, le score d’engagement cross-canal et la conversion des étapes du cycle de vie.

**Pour l’option C (Analytics avec publication d’audience) :**

Créez les espaces de travail d’analyse à partir des options A ou B, puis identifiez les segments à forte valeur ou peu performants lors de l’analyse. Créez des filtres CJA qui capturent ces segments pour publication au cours de la phase 5.

**Pour l’option D (analyse guidée) :**

Sélectionnez le type d’analyse guidée approprié en fonction de la question métier. Configurez les événements clés, les périodes, les méthodes de comptage et les comparaisons de segments. Enregistrez les analyses terminées en tant que panneaux dans les projets Workspace pour les personnaliser davantage.

**Documentation Experience League :**

- [Présentation de Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Créer un projet](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tableau à structure libre](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualisation de flux](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualisation des abandons](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Table de cohorte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Panneau d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Répartition des dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Présentation des filtres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Création de filtres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Présentation des annotations](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Création de mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Fonctions de mesure calculée](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Aperçu des analyses guidées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Vue funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Vue Tendances](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Vue de rétention](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Vue de croissance active](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Vue de la fréquence d’engagement](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Vue de l’impact de la version](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Content Analytics](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/content-analytics/content-analytics)

### Phase 4 : publication de tableaux de bord

**Fonction d’application :** CJA : publication de tableaux de bord et de cartes de performance

Cette phase permet de créer des tableaux de bord interactifs (projets Workspace) et des cartes de performance mobiles qui offrent une visibilité sur les indicateurs de performance clés aux parties prenantes. Les tableaux de bord offrent une visibilité opérationnelle et opérationnelle par le biais de synthèses numérotées, de lignes de tendance, de répartitions et d’annotations. Les cartes de performance mobiles fournissent des données de performances en un coup d’œil grâce à l’application mobile des tableaux de bord [!DNL Adobe Analytics].

#### Points de décision

Les décisions suivantes doivent être prises au cours de cette phase.

>[!NOTE]
>**Décision : type de tableau de bord**
>
>S’agit-il d’un tableau de bord Workspace de bureau, d’une carte de performance mobile ou des deux ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Projet Workspace (ordinateur de bureau) | Tableaux de bord interactifs détaillés pour les analystes et les spécialistes du marketing | Fonctionnalités de visualisation complètes ; prend en charge les panneaux, les tableaux et les mises en page complexes |
>| Carte de performance mobile | KPI en un coup d’œil pour les dirigeants et les parties prenantes sur les appareils mobiles | Limité à 16 mosaïques ; chiffres de synthèse avec graphiques sparkline de tendance ; nécessite une application mobile |
>| Les deux | L’entreprise a besoin d’une analyse détaillée et de rapports mobiles au niveau exécutif | Artefacts distincts mais pouvant partager la même vue de données et les mêmes mesures calculées |

>[!NOTE]
>**Décision : modèle de partage**
>
>Qui doit recevoir le tableau de bord et comment ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Partager avec des utilisateurs et utilisatrices spécifiques | Audience limitée avec des besoins d’accès spécifiques | Contrôle le plus granulaire ; nécessite une gestion individuelle des utilisateurs |
>| Partager avec le groupe de profils de produit | Accès au niveau de l’équipe aligné avec les rôles organisationnels | Efficacité pour la distribution à l’échelle de l’équipe ; gestion via les profils de produits CJA |
>| Planifier la diffusion par e-mail | Rapports PDF/CSV périodiques pour les parties prenantes qui ne se connectent pas à CJA | Diffusion automatisée : fréquence maximale par heure ; formats PDF et CSV |

>[!NOTE]
>**Décision : visibilité des annotations**
>
>Les événements clés doivent-ils être annotés sur les lignes de tendance du tableau de bord ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Oui — créer des annotations | Les campagnes majeures, les lancements de produits, les incidents de site ou les événements saisonniers peuvent expliquer les tendances des données | Les annotations apparaissent en tant que marqueurs sur les graphiques linéaires et les tendances des cartes de performance ; elles fournissent un contexte pour les pics ou les creux de données |
>| Non | L’audience du tableau de bord connaît le contexte commercial et les annotations encombreraient l’espace | Présentation visuelle plus simple |

#### Configuration des tableaux de bord

**Navigation dans l’interface utilisateur :**

- Tableaux de bord Workspace : CJA > Workspace > Créer un projet
- Cartes de performance mobiles : CJA > Projets > Créer > Carte de performance mobile
- Partage : CJA > Workspace > Partager > Partager avec les utilisateurs Workspace
- Diffusion planifiée : CJA > Workspace > Partager > Planifier le projet

Détails de configuration clés :

- Pour les cartes de performance mobiles, créez des mosaïques qui affichent une mesure unique avec un chiffre récapitulatif et une tendance de graphique sparkline
- Configurez les périodes par défaut et les périodes de comparaison (par exemple, les 30 derniers jours par rapport à la période précédente ou mois par mois).
- Ajoutez des filtres d’audience que les cadres peuvent activer/désactiver sur les cartes de performance mobiles
- Configurer la diffusion e-mail planifiée pour les rapports PDF ou CSV récurrents
- 16 vignettes maximum par carte de performance mobile ; 15 panneaux maximum par projet Workspace
- Les annotations sont limitées à 100 par vue de données

**Documentation Experience League :**

- [Création d’une carte de performance mobile](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configuration et traitement des cartes de performance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Tableaux de bord Adobe Analytics - guide exécutif](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Partager des projets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planification de projets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Visualisation Synthèse des chiffres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)
- [Périodes](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

### Phase 5 : publication d’audiences (option C uniquement)

**Fonction d’application :** CJA : Publication d’audiences

Cette phase configure la publication d’audiences CJA pour renvoyer les segments découverts par l’analyse vers le profil client en temps réel d’AEP pour une activation en aval dans les destinations RT-CDP, les campagnes AJO ou les parcours AJO.

#### Points de décision

Les décisions suivantes doivent être prises au cours de cette phase.

>[!NOTE]
>**Décision : fréquence d’actualisation**
>
>À quelle fréquence l’abonnement à l’audience doit-il être actualisé ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Ponctuel (instantané) | Audience spécifique à la campagne qui n’a pas besoin d’être actualisée en continu | Aucun traitement en cours ; republication obligatoire pour les mises à jour |
>| Toutes les 4 heures | Exigences d’activation en temps quasi réel | Coût de traitement plus élevé ; idéal pour les audiences sensibles au temps |
>| Quotidienne | Cadence d’activation marketing standard | Fraîcheur et coût équilibrés ; choix le plus courant |
>| Hebdomadaire | Audiences stables et à évolution lente | Traitement minimal ; adapté aux segments à long terme |

>[!NOTE]
>**Décision : espace de noms d’identité**
>
>Quel espace de noms d’identité CJA doit-il utiliser pour la résolution des membres d’audience ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| ID CRM | Identifiant client principal de l’organisation | Meilleure précision pour la correspondance client connue |
>| ECID | Principalement des audiences web/basées sur des applications | Périphérique défini ; peut ne pas se résoudre à tous les enregistrements de profil |
>| E-mail (haché) | L’e-mail est l’identifiant commun pour l’activation | Doit correspondre à l’espace de noms utilisé dans la configuration d’identité AEP |
>| Espace de noms personnalisé | Identifiant propriétaire utilisé dans l&#39;ensemble de l&#39;organisation | Doit être configuré dans AEP Identity Service |

#### Configuration de la publication d’audiences

**Navigation dans l’interface utilisateur** CJA > Composants > Audiences > Publier l’audience

Détails de configuration clés :

- Définissez des critères d’audience à l’aide des filtres CJA (portée du conteneur de personnes, de sessions ou d’événements)
- Sélectionnez la vue de données et le filtre à publier
- Configuration de l’espace de noms d’identité pour la résolution de profil AEP
- Définir la cadence d’actualisation en fonction des besoins d’activation
- Surveiller le statut de publication dans la liste des audiences CJA (composants > audiences > statut)
- Vérifiez que l’audience apparaît dans AEP Audience Portal (Audiences > Parcourir > Filtrer par origine « CJA »)
- Maximum de 75 audiences publiées par client CJA (sur tous les sandbox)
- L’évaluation initiale de l’audience peut prendre jusqu’à 24 heures pour les jeux de données volumineux

**Documentation Experience League :**

- [Présentation des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Création et publication d’audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestion des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)
- [Présentation d’Audience Portal](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

## Considérations relatives à la mise en œuvre

Cette section couvre les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage pour ce modèle de cas d’utilisation.

### Mécanismes de sécurisation et limites

Les mécanismes de sécurisation et limites suivants s’appliquent à cette implémentation.

- **Limites de connexion :** le nombre maximal de connexions par organisation est limité par les droits de SKU CJA. Une seule connexion peut inclure des jeux de données provenant d’un seul sandbox AEP. — [Mécanismes de sécurisation de ](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- **Limites des vues de données :** 5 000 dimensions et 5 000 mesures au maximum par vue de données. Maximum de 100 champs dérivés par vue de données avec jusqu’à 5 niveaux de fonctions imbriquées.
- **Limites de Workspace :** maximum de 40 panneaux par projet. Les tableaux à structure libre prennent en charge jusqu’à 10 répartitions de dimension profondes. 50 000 lignes maximum par demande de rapport.
- **Limites des cartes de performance :** 16 vignettes au maximum par carte de performance mobile.
- **Latence de diffusion en continu :** les données de diffusion en continu sont généralement disponibles dans CJA dans les 90 minutes suivant l’ingestion d’AEP.
- **Limites de publication d’audience :** maximum de 75 audiences publiées par client CJA. La cadence minimale d’actualisation est toutes les 4 heures.
- **Limites d’analyse guidée :** l’analyse Funnel prend en charge un maximum de 15 étapes. Les comparaisons de segments prennent en charge jusqu’à 3 segments simultanément.

### Pièges courants

Tenez compte des problèmes courants suivants lors de l’implémentation de ce modèle.

- **Incompatibilité des ID de personne entre les jeux de données :** tous les jeux de données d’une connexion doivent utiliser un champ ID de personne cohérent pour l’analyse entre les jeux de données. Les ID de personne non concordants entraînent des affichages client fragmentés où la même personne apparaît comme plusieurs personnes. Vérifiez la cohérence de l’ID de personne avant de créer la connexion.

- **Le renvoi prend une durée inattendue :** le renvoi de jeux de données volumineux contenant des milliards d’enregistrements peut prendre plusieurs jours. Planifiez cette opération pendant les délais d’implémentation et commencez le renvoi tôt. Surveillez la progression dans la vue des détails de la connexion.

- **Vue de données indiquant « Non spécifié » pour la plupart des valeurs de dimension :** le champ de schéma mappé peut être peu renseigné dans les données source. Vérifiez la qualité des données du jeu de données source avant d’assumer une erreur de configuration. Envisagez d’utiliser un champ dérivé pour gérer les valeurs nulles.

- **Le nombre de sessions semble incorrect :** les paramètres de délai d’expiration de session affectent considérablement les mesures de la portée de la session. Une temporisation très courte crée plus de sessions, une temporisation très longue en crée moins. Les nouveaux événements de début de session peuvent également fragmenter les sessions de manière inattendue. Examinez et testez les paramètres de session par rapport aux modèles de comportement utilisateur connus.

- **Le modèle d’attribution ne s’applique pas comme prévu :** les modèles d’attribution s’appliquent uniquement aux mesures, et non aux dimensions. Vérifiez que l’intervalle de recherche en amont est défini correctement pour le cycle économique. Les intervalles de recherche en amont courts peuvent ignorer les points de contact de funnel précoce.

- **Mesures calculées renvoyant des zéros ou des valeurs inattendues :** vérifiez que les mesures de base référencées dans la formule contiennent des données dans la vue de données cible pour la période sélectionnée. Recherchez la division par zéro dans les mesures de ratio. Récupérez la définition de la mesure et vérifiez la structure de la formule.

- **Échec de la publication de l’audience (option C) :** la connexion CJA doit comporter un ID de personne valide qui est résolu sur un espace de noms d’identité AEP. Vérifiez la configuration de l’espace de noms d’identité et que le profil client en temps réel AEP est activé dans le sandbox cible.

### Bonnes pratiques

Suivez ces bonnes pratiques pour une implémentation réussie.

- **Commencez avec une seule connexion complète :** créez une connexion qui comprend tous les jeux de données pertinents, puis créez plusieurs vues de données pour différentes perspectives analytiques. Cela évite la prolifération des connexions et simplifie la gestion.

- **Utiliser des champs dérivés pour la classification de canal marketing :** plutôt que de vous fier aux codes de suivi bruts, créez des champs dérivés avec la logique Case When pour classer le trafic dans les canaux marketing. Cela garantit la cohérence des rapports sur les canaux pour toutes les analyses.

- **Créer un dictionnaire de mesures :** documenter toutes les mesures calculées avec leurs formules, leur utilisation prévue et leurs plages de valeurs attendues. Partagez ce dictionnaire avec l’équipe d’analyse afin de garantir une utilisation cohérente des mesures entre les projets.

- **Concevoir des vues de données pour votre audience :** créez des vues de données distinctes pour différents groupes de parties prenantes : une vue de données marketing avec des dimensions et des mesures axées sur la campagne, et une vue de données de produit avec des dimensions de fonctionnalité et d’engagement. Cela simplifie les listes de composants pour chaque groupe d’utilisateurs.

- **Tout annoter :** créez des annotations pour les lancements de campagne, les modifications du site, les incidents techniques, le caractère saisonnier et tout événement susceptible d’expliquer les tendances des données. Les annotations fournissent un contexte essentiel lors de la révision des tableaux de bord des mois plus tard.

- **Tester les mesures calculées par rapport aux calculs manuels :** avant de vous fier à une mesure calculée pour les tableaux de bord, exécutez un rapport avec la mesure calculée et ses composants de base côte à côte. Vérifiez que les valeurs calculées correspondent à un calcul manuel.

- **Utilisez les filtres de manière stratégique :** créez des filtres réutilisables pour les modèles de segmentation courants (nouveaux ou récurrents, mobiles ou ordinateurs de bureau, par zone géographique). Appliquez-les sous la forme de filtres au niveau du panneau plutôt que de les incorporer dans chaque tableau à structure libre.

- **Surveiller régulièrement l’intégrité de la connexion :** vérifiez la vue des détails de connexion pour connaître les enregistrements ignorés, les lots ayant échoué et les retards de diffusion en continu. Les problèmes de qualité des données au niveau de la connexion affectent toutes les analyses en aval.

### Décisions de compromis

Tenez compte des compromis suivants lors de la planification de votre implémentation.

>[!NOTE]
>**Compromis : profondeur de l’analyse par rapport au délai d’insight**
>
>L’option B (Customer parcours Analytics) fournit les informations cross-canal les plus approfondies, mais nécessite un investissement initial important dans la configuration de la connexion, la conception de la vue de données et la création de champs dérivés. L’option D (analyse guidée) offre un délai de mise sur le marché d’insight plus rapide avec des workflows structurés, mais offre moins de flexibilité analytique.
>
>- **L’option B privilégie** compréhension complète, analyse multicanal complexe, modélisation de l’attribution, développement d’indicateurs de performance clés personnalisés.
>- **L’option D privilégie :** la vitesse, l’accessibilité pour les utilisateurs non analystes et les questions sur l’expérience structurée du produit.
>- **Recommandation :** commencez par l’option D pour obtenir des informations immédiates sur les produits tout en créant l’infrastructure de l’option B en parallèle. De nombreuses organisations exécutent les deux simultanément pour différentes équipes.

>[!NOTE]
>**Compromis : complétion du renvoi ou préparation de la connexion**
>
>L’importation de toutes les données historiques fournit une profondeur d’analyse maximale pour les comparaisons d’une année sur l’autre et l’analyse des tendances à long terme, mais le renvoi de jeux de données volumineux peut prendre des jours. La limitation du renvoi à une période récente permet à la connexion de se préparer plus rapidement, mais limite l’analyse historique.
>
>- **Toutes les données sont en faveur :** analyse des tendances à long terme, comparaisons d’une année sur l’autre, analyse des cohortes avec un historique étendu
>- **Favoris de renvoi limités :** préparation plus rapide de la connexion, délai plus court pour le premier tableau de bord, optimisation du stockage
>- **Recommandation :** renvoyer toutes les données pour les connexions de production qui prennent en charge l’analyse stratégique. Utilisez un renvoi limité pour les connexions de développement et les implémentations de preuve de concept.

>[!NOTE]
>**Compromis : vue de données complète unique par rapport à plusieurs vues de données ciblées**
>
>Une vue de données unique avec toutes les dimensions et mesures fournit un espace de travail analytique unifié, mais peut surcharger les utilisateurs avec des listes de composants. Plusieurs vues de données ciblées (une par équipe ou cas d’utilisation) simplifient l’expérience des composants, mais nécessitent plusieurs configurations.
>
>- **La vue de données unique est privilégiée :** analyse unifiée, répartitions entre domaines, gestion simplifiée
>- **Plusieurs vues de données sont préférées :** listes de composants plus claires, terminologie spécifique à l’équipe, différentes définitions de session par cas d’utilisation
>- **Recommandation :** commencez par une vue de données principale, puis créez des vues de données ciblées supplémentaires si la complexité de la liste des composants devient un obstacle à l’adoption. Toutes les vues de données peuvent référencer la même connexion.

>[!NOTE]
>**Compromis : diffusion en continu en temps réel et ingestion par lots uniquement**
>
>L’activation du streaming sur la connexion CJA fournit des données en temps quasi réel (dans les 90 minutes suivant l’ingestion d’AEP), mais traite davantage de données en continu. L’ingestion par lots uniquement traite les données de manière périodique et peut entraîner des retards.
>
>- **Favoris de streaming :** rapports en temps opportun, surveillance des campagnes actives, tableaux de bord en temps quasi réel
>- **Avantages du traitement par lots uniquement :** configuration simplifiée, fenêtres de traitement prévisibles, suffisantes pour les rapports hebdomadaires ou mensuels
>- **Recommandation :** activer la diffusion en continu pour les connexions de production. Le coût de traitement incrémentiel est minime par rapport à la valeur des données opportunes pour la surveillance active des campagnes et les tableaux de bord opérationnels.

## Documentation connexe

Les ressources suivantes apportent des informations supplémentaires sur ce modèle de cas d’utilisation.

### [!DNL Customer Journey Analytics] — Prise en main

- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Mécanismes de sécurisation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Connexions

- [Présentation des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Création ou modification d’une connexion](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Gérer des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

### Vues des données

- [Présentation des vues de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Créer ou modifier une vue de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Présentation des paramètres de composant](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Paramètres de persistance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Paramètres d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Paramètres de format](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Déduplication des mesures](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Valeurs d’inclusion/exclusion](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Paramètres de session](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Champs dérivés](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace et analyse

- [Présentation de Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Créer un projet](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tableau à structure libre](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualisation de flux](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualisation des abandons](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Table de cohorte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Panneau d’attribution](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Répartition des dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Partager des projets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planification de projets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Présentation de l’exportation](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### Analyse guidée

- [Aperçu des analyses guidées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Vue funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Vue Tendances](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Vue de la fréquence d’engagement](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Vue de rétention](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Vue de croissance active](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Vue de l’impact de la version](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Première utilisation de la vue d’impact](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [Mode Chronologie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/streams/timeline)

### Composants

- [Présentation des filtres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Création de filtres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Création de mesures calculées](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Fonctions de mesure calculée](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Présentation des annotations](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Périodes](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [Composant Mesures](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/apply-create-metrics)

### Publication d’audiences

- [Présentation des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Création et publication d’audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestion des audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

### Analyse de contenu

- [Content Analytics](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/content-analytics/content-analytics)
- [Configuration de Content Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### Tableaux de bord et cartes de performance

- [Création d’une carte de performance mobile](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configuration et traitement des cartes de performance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Tableaux de bord Adobe Analytics - guide exécutif](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Visualisation Synthèse des chiffres](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### Principes de base d’AEP

- [Présentation des jeux de données](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview)
- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation d’Audience Portal](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

### Intégration de la création de rapports AJO

- [Guide d’intégration d’AJO + CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Rapport sur les e-mails de campagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [Parcours du rapport sur les e-mails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### Tutoriels et guides

- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
