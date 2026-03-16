---
title: Analyses B2B
description: Découvrez comment inclure des informations au niveau du compte B2B dans l’analyse des parcours client cross-canal.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7528'
ht-degree: 1%

---


# Analyses B2B

Ce guide fournit une référence d’implémentation complète pour l’analyse au niveau du compte B2B à l’aide de [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition et [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition. Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui doivent intégrer des informations au niveau du compte B2B dans l’analyse cross-canal du parcours client.

Il couvre toutes les approches viables pour l’analyse centrée sur les comptes, des structures de compte plates aux hiérarchies de comptes globales complexes, avec des conseils sur le moment de choisir chaque option. Le plan traite des connexions de données B2B, de la configuration des vues de données de compte, de l’analyse de l’espace de travail et de la publication des tableaux de bord.

B2B Analytics étend les fonctionnalités [!DNL CJA] standard avec des connexions basées sur les comptes, des conteneurs spécifiques au B2B (compte, compte global, opportunité, groupe d’achat) et des rapports au niveau du compte. Cette fonctionnalité permet aux entreprises d’analyser l’engagement marketing et commercial au niveau du compte, de suivre la progression des opportunités, de mesurer l’exhaustivité du groupe d’achats et d’attribuer le chiffre d’affaires aux points de contact marketing sur l’ensemble des cycles de vente B2B étendus.

## Présentation du cas d’utilisation

Les organisations B2B sont confrontées à un défi analytique fondamental : leurs clients ne sont pas des personnes individuelles, mais des comptes composés de plusieurs parties prenantes, de groupes d’achat et d’opportunités. L’analyse standard basée sur la personne ne peut pas répondre à des questions du type « Quels comptes sont les plus engagés ? », « Dans quelle mesure nos groupes d’achats sont-ils complets ? » ou « Quels points de contact marketing génèrent la progression des opportunités ? »

L’analyse B2B résout ce problème en exploitant [!DNL CJA] B2B edition pour créer des vues analytiques centrées sur les comptes qui combinent des données comportementales au niveau de la personne avec des dimensions de compte, d’opportunité et de groupe d’achat. [!DNL RT-CDP] B2B edition fournit l’unification des profils de compte sous-jacente et la résolution d’identité B2B qui alimente la couche Analytics. Ensemble, ces solutions permettent aux entreprises de créer une analyse de parcours cross-canal au niveau du compte, de corréler l’engagement marketing à la progression du pipeline et de fournir des informations exploitables aux équipes marketing et commerciales.

L’audience cible comprend les équipes opérationnelles marketing B2B, les responsables de la génération de la demande, les analystes des opérations de chiffre d’affaires et le leadership commercial qui ont besoin de visibilité sur l’engagement au niveau du compte et l’intégrité des pipelines.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Amélioration des analyses et des rapports

Améliorez les fonctionnalités de création de rapports pour obtenir des informations marketing plus rapides et plus exploitables grâce à des tableaux de bord unifiés et des outils en libre-service. L’analyse B2B permet aux entreprises de consolider des données d’engagement au niveau du compte provenant de plusieurs sources dans un seul environnement analytique, offrant ainsi une visibilité cross-canal sur la manière dont les programmes marketing influencent le pipeline et le chiffre d’affaires.

**KPI : Efficacité** productivité

[En savoir plus sur l’amélioration des analyses et des rapports](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### Activer la prise de décision pilotée par les données

Donnez aux équipes les moyens d’utiliser des analyses en libre-service, des informations sur les clients en temps réel et des prédictions basées sur l’IA pour orienter la stratégie. L’analyse au niveau des comptes dote les équipes marketing et commerciales des données nécessaires pour hiérarchiser les comptes, optimiser les stratégies d’engagement et s’aligner sur les opportunités de pipeline.

**KPI : Efficacité** productivité

[En savoir plus sur comment activer la prise de décision pilotée par les données](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### Améliorer la qualification et la conversion des prospects

Augmentez la qualité des prospects et accélérez la progression du pipeline grâce à la notation, à l’entretien et au suivi personnalisé. CJA B2B edition offre des intervalles de recherche en amont de 13 mois étendus, spécialement conçus pour les cycles de vente B2B, ce qui permet une attribution multipoint précise sur l’ensemble du parcours des comptes.

**KPI : Efficacité** revenus incrémentiels

[En savoir plus sur l’amélioration de la qualification et de la conversion des prospects](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont ce modèle peut être appliqué dans la pratique.

- **Analyse de notation de l’engagement du compte** — Mesurez et classez les comptes par leur engagement agrégé sur le web, les e-mails, les événements et les interactions de contenu afin d’identifier les comptes à forte intention pour le suivi des ventes
- **Suivi de l&#39;exhaustivité du groupe d&#39;achats** — Analysez la composition du groupe d&#39;achats sur les comptes pour identifier les lacunes dans la couverture des rôles et hiérarchisez l&#39;acquisition de leads pour les groupes d&#39;achats incomplets
- **Corrélation des pipelines d’opportunités** — Corrélez les données d’engagement marketing avec la progression de la phase d’opportunité pour comprendre quelles campagnes et quels points de contact génèrent l’avancement du pipeline
- **Attribution B2B multipoint** : appliquez des modèles d’attribution avec des intervalles de recherche en amont de 13 mois pour créditer les points de contact marketing sur l’ensemble du parcours d’achat B2B, du premier contact à l’expérience confirmée
- **Mappage du parcours de compte** — Visualisez le parcours de compte cross-canal depuis la connaissance initiale jusqu’à la création et la fermeture de l’opportunité, en identifiant les chemins communs et les points de friction
- **L’influence de la campagne sur le pipeline** — Mesurez la manière dont des campagnes spécifiques influencent la création du pipeline de compte, l’avancement des opportunités et la génération de revenus
- **Progression de l’engagement du groupe d’achat** - Suivez l’évolution des scores d’engagement du groupe d’achat au fil du temps et corrélez les seuils d’engagement avec les résultats des opportunités
- **Performances du contenu basé sur les comptes** — Analysez quelles ressources et rubriques de contenu correspondent à des segments de compte, des secteurs d’activité ou des rôles de groupe d’achat spécifiques
- **Tableaux de bord d’alignement des ventes et du marketing** — Créez des tableaux de bord partagés qui offrent aux équipes marketing et commerciales une vue unifiée de l’engagement du compte, de l’intégrité du pipeline et de l’attribution des recettes
- **Segmentation de compte pour l’activation** — Créez des segments B2B basés sur l’analyse au niveau du compte (par exemple, « comptes à fort engagement sans opportunités ouvertes ») et publiez-les pour l’activation en aval

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Account Engagement Score | Mesure d’engagement agrégée pour tous les contacts d’un compte | Mesure calculée combinant les visites web, les interactions par e-mail, la participation à des événements et les téléchargements de contenu au niveau du compte |
| Exhaustivité du groupe d&#39;achat | Pourcentage de rôles requis remplis dans un groupe d&#39;achats | Ratio des rôles renseignés par rapport au total des rôles requis par groupe d&#39;achat, suivi au fil du temps |
| Pipeline influencé par le marketing | Chiffre d’affaires de pipeline ayant été touché par des activités marketing | Valeur de l’opportunité où les contacts de compte associés ont des points de contact marketing dans la fenêtre d’attribution |
| Taux de conversion compte à opportunité | Pourcentage de comptes engagés qui génèrent des opportunités qualifiées | Comptes avec opportunités divisés par le total des comptes engagés sur une période définie |
| Durée moyenne du cycle de l’affaire | Temps écoulé entre la première touche marketing et la conclusion de l’appel | Durée moyenne du premier point de contact attribué à la date de fermeture de l’opportunité |
| Chiffre d’affaires de l’attribution marketing | Chiffre d’affaires attribué aux points de contact marketing | Chiffre d’affaires d’opportunités closes avec des contacts marketing, distribué par modèle d’attribution |
| Portée et pénétration du compte | Nombre de contacts engagés par compte cible | Contacts uniques avec interactions marketing par compte, par rapport au nombre total de contacts connus |
| Engagement du contenu par rôle d’achat | Mesures d’engagement segmentées par rôle de groupe d’achat | Pages vues, téléchargements et temps passé ventilé par persona/rôle dans les groupes d’achats |

## Modèle de cas d’utilisation

**Analyse B2B**

Incluez des informations au niveau du compte B2B dans l’analyse des parcours client cross-canal.

**Chaîne de fonctions :** Connexion de données B2B > Configuration de la vue de données du compte > Analyse Workspace > Publication sur tableau de bord

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Customer Journey Analytics]B2B edition** — Fournit des connexions basées sur les comptes, des conteneurs de vues de données spécifiques au B2B, une analyse de l’espace de travail au niveau du compte, une analyse des groupes d’achats, une analyse des opportunités, une segmentation B2B et une attribution B2B avec des intervalles de recherche en amont étendus
- **[!DNL Real-Time CDP]B2B edition** — Fournit la base de données B2B, y compris l’unification des profils de compte, la résolution des identités B2B, les classes de schéma B2B (compte, opportunité, groupe d’achat) et l’intégration [!DNL Marketo Engage] pour l’ingestion de données d’engagement B2B

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Obligatoire | Sandbox configuré avec [!DNL CJA] droits B2B edition et [!DNL RT-CDP] B2B edition. Rôles configurés pour les ingénieurs de données, les analystes et les utilisateurs des opérations marketing ayant accès à [!DNL CJA] et au modèle de données B2B. | [Présentation des sandbox](https://experienceleague.adobe.com/fr/docs/experience-platform/sandbox/home) |
| Modélisation et préparation des données | Obligatoire | Schémas XDM B2B configurés à l’aide des classes B2B : compte professionnel XDM, opportunité commerciale XDM, relation de la personne avec le compte professionnel XDM, relation de la personne avec l’opportunité commerciale XDM et membres de la liste marketing professionnelle XDM. Les groupes de champs pour les attributs de compte, les étapes d&#39;opportunité et les rôles de groupe d&#39;achat doivent être définis. Jeux de données créés et activés pour le profil. | [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home), [Schémas B2B edition](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/schemas/b2b) |
| Sources et collecte de données | Obligatoire | Sources de données B2B connectées, généralement via le connecteur source [!DNL Marketo Engage] ou [!DNL Salesforce] connecteur source CRM. Les enregistrements de compte, les enregistrements d’opportunité, les relations personne-compte et les événements d’engagement comportemental doivent circuler dans les jeux de données AEP. [!DNL Web SDK] ou [!DNL Marketo] intégration doit capturer des événements comportementaux avec l’association de compte. | [Présentation des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home), [Connecteur Marketo Engage](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Configuration des identités et des profils | Obligatoire | Résolution d’identité B2B configurée pour résoudre les relations personne à compte. L’ID de compte, l’ID de personne (ID de lead [!DNL Marketo] ou ID de contact CRM) et les identités inter-appareils (ECID, adresse électronique) doivent être liés. Le graphique d’identité doit prendre en charge le mappage plusieurs-à-plusieurs entre une personne et un compte inhérent aux modèles de données B2B. | [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home), [résolution d’identité B2B](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/schemas/b2b) |
| Définition et segmentation de l’audience | Supposé en place | Les définitions d’audience au niveau du compte doivent être disponibles si les segments B2B seront publiés de [!DNL CJA] vers AEP pour activation. Pour les cas d’utilisation d’analyses uniquement, il ne s’agit pas d’un strict prérequis, mais cela est recommandé pour l’analyse basée sur les segments. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés sur les profils de compte (par exemple, score total de l’engagement, jours depuis la dernière activité, nombre d’opportunités) enrichissent les dimensions analytiques disponibles dans [!DNL CJA] pour l’analyse au niveau du compte. | [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | Les jeux de données B2B, en particulier les données d’événement comportemental issues de [!DNL Marketo Engage], peuvent croître rapidement. Les politiques d’expiration des jeux de données permettent de gérer le stockage et de garantir la conformité aux exigences de conservation des données. | [Gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les données B2B contiennent souvent des informations commerciales sensibles (valeurs contractuelles, veille concurrentielle). Les libellés d’utilisation des données et les politiques de gouvernance garantissent que ces données sont utilisées de manière appropriée dans les workflows d’analyse et d’activation. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home) |
| Surveillance et observabilité | Recommandé | Les connecteurs source B2B ([!DNL Marketo], [!DNL Salesforce]) nécessitent une surveillance de l’intégrité de l’ingestion. La surveillance de l’intégrité des connexions dans [!DNL CJA] garantit l’actualisation des données pour les analyses. Les règles d’alerte pour les échecs d’ingestion empêchent les tableaux de bord obsolètes. | [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Ce modèle est lui-même un modèle d’analyse. Cette fonction est incluse de manière inhérente, car la chaîne de fonctions principale fournit des fonctionnalités de création de rapports et d’analyse. | Présentation de [CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Customer Journey Analytics] B2B edition

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Connexion basée sur un compte | Phase 1 : Connexion aux données B2B | Configurez les connexions en utilisant Compte ou Compte global comme identifiant principal pour l’analyse au niveau de l’organisation |
| Configuration des vues de données B2B | Phase 2 : configuration de la vue de données du compte | Définissez des vues de données avec des conteneurs spécifiques au B2B (compte, compte global, opportunité, groupe d’achats) à côté des conteneurs standard Personne, Session et Événement |
| Analyse Workspace au niveau du compte | Phase 3 : analyse Workspace | Créer une analyse de structure libre à l’aide de dimensions, de mesures et de conteneurs B2B au niveau du compte pour les informations de parcours au niveau de l’organisation |
| Analyse du groupe d&#39;achat | Phase 3 : analyse Workspace | Analysez la composition, l&#39;engagement et la progression du groupe d&#39;achat tout au long du processus de décision d&#39;achat |
| Analyse des opportunités | Phase 3 : analyse Workspace | Suivre la progression des opportunités à travers les étapes de funnel des ventes et corréler les données d’engagement marketing |
| Segmentation B2B | Phase 3 : analyse Workspace | Créer des segments à l’aide de conteneurs B2B pour une analyse filtrée au niveau du compte |
| Attribution B2B | Phase 3 : analyse Workspace | Application de modèles d’attribution avec des intervalles de recherche en amont de 13 mois étendus pour l’analyse du cycle de vente B2B |
| Création de mesure calculée | Phase 3 : analyse Workspace | Définir des mesures calculées pour les indicateurs clés de performance B2B tels que le taux d’engagement du compte, l’exhaustivité du groupe d’achats et l’influence du pipeline |
| Publication sur tableau de bord et carte de score | Phase 4 : publication du tableau de bord | Créer et partager des tableaux de bord et des cartes de performance mobiles pour le leadership marketing et commercial |
| Publication d’audiences | Phase 4 : publication du tableau de bord | Publiez à nouveau des audiences basées sur un compte défini par [!DNL CJA] dans AEP pour l’activation en aval |

### [!DNL Customer Journey Analytics] — fonctions standard

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Connexion aux données | Phase 1 : Connexion aux données B2B | Liaison de jeux de données B2B AEP à des connexions [!DNL CJA] pour une analyse cross-canal |
| Configuration de la vue de données | Phase 2 : configuration de la vue de données du compte | Configurer des dimensions, des mesures, des paramètres d’attribution et de persistance standard dans la vue de données B2B |
| Analyse Workspace | Phase 3 : analyse Workspace | Créez une analyse de structure libre avec des visualisations de tableaux, d’abandons, de flux, de cohortes et d’attribution |
| Analyse guidée | Phase 3 : analyse Workspace | Utilisez des workflows guidés pour analyser les funnel, les tendances et la rétention au niveau du compte |

### [!DNL Real-Time CDP] B2B edition

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Unification du profil de compte | Prérequis (F2/F4) | Consolidez les données B2B inter-sources en profils de compte unifiés à l’aide de classes de schéma B2B XDM spécialisées |
| Résolution d’identités B2B | Prérequis (F4) | Résoudre les relations de personne à compte en prenant en charge les hiérarchies de comptes à plusieurs niveaux et les mappages multiples-à-multiples |
| Intégration [!DNL Marketo Engage] | Prérequis (F3) | Ingérez des données d’engagement comportemental et des enregistrements de compte/prospect à partir de [!DNL Marketo Engage] via des connecteurs source B2B natifs. |

## Conditions préalables

Les éléments suivants doivent être en place avant le début de l’implémentation.

- [!DNL CJA] licence B2B edition est active et configurée pour l’organisation
- [!DNL RT-CDP] licence B2B edition est active avec les schémas B2B et les profils de compte configurés
- Les schémas XDM B2B sont définis (compte, opportunité, relation compte-personne, relation opportunité-personne, membres de la liste marketing).
- Les connecteurs source [!DNL Marketo Engage] et/ou CRM sont configurés et ingèrent activement des données
- Les données comportementales d’événement au niveau du compte (visites web, interactions par e-mail, envois de formulaire) sont transmises à AEP avec l’association de compte
- Les relations personne à compte sont établies dans le graphique d’identité
- Au moins 30 jours de données historiques d’engagement B2B sont disponibles pour une analyse significative
- Les parties prenantes se sont mises d’accord sur les définitions des rôles des groupes d’achat et les correspondances des intérêts des solutions
- Les comptes utilisateur [!DNL CJA] sont dotés des profils de produit appropriés pour les fonctionnalités de B2B edition
- Les KPI cibles et les exigences en matière de rapports ont été définis par les responsables marketing et commerciaux

## Options de mise en œuvre

Les sections suivantes décrivent différentes approches pour mettre en œuvre ce modèle de cas d’utilisation.

### Option A : Analyse centrée sur le compte

**Idéal pour :** les organisations qui souhaitent analyser toutes les données d’engagement et de pipeline à travers le prisme du compte. Cette approche utilise le conteneur Compte en tant qu’unité d’analyse principale, offrant une vue de haut en bas de la progression des comptes sur le parcours d’achat.

**Fonctionnement :**

Configurez une connexion B2B [!DNL CJA] avec le compte comme identifiant principal. Toutes les données relatives aux événements comportementaux, aux opportunités et aux groupes d’achats sont cumulées au niveau du compte. La vue de données utilise le compte comme conteneur de plus haut niveau, avec la personne, la session et l’événement imbriqués. Cela permet d’effectuer une analyse du type « Combien de comptes ont visité la page de tarification, puis créé une opportunité dans les 30 jours ? »

L’analyse centrée sur les comptes offre la vue la plus naturelle pour les organisations B2B où le compte est l’unité d’achat. Des dimensions telles que le secteur d’activité, la taille de l’entreprise, le niveau de compte et le propriétaire du compte peuvent être utilisées pour ventiler les modèles d’engagement et les mesures de pipeline. L’attribution est appliquée au niveau du compte avec des intervalles de recherche en amont de 13 mois qui s’adaptent aux longs cycles de vente B2B.

**Considérations principales :**

- Nécessite un mappage compte à personne propre dans le graphique d’identités
- Tous les événements au niveau de la personne doivent être attribuables à un compte
- Le trafic web anonyme qui ne peut pas être associé à un compte n’apparaît pas dans l’analyse au niveau du compte

**Avantages :**

- Fournit une véritable vue au niveau du compte de l’ensemble du parcours d’achat
- Active l’attribution basée sur les comptes qui correspond à la manière dont le chiffre d’affaires B2B est généré
- Prend en charge l’analyse des groupes d’achats et des opportunités en tant que conteneurs imbriqués dans le compte
- Aligne les analyses sur la stratégie marketing basée sur les comptes (ABM)

**Limitations :**

- Nécessite une résolution d’identité robuste de personne à compte
- Les données d’engagement anonymes ou sans correspondance sont exclues de l’analyse.
- Plus complexe à configurer que l’analyse centrée sur la personne

**Experience League:**

- [Présentation de CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [Schémas B2B edition](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/schemas/b2b)

### Option B : Analyse globale centrée sur les comptes

**Idéal pour :** organisations d&#39;entreprise avec des hiérarchies de comptes complexes dans lesquelles une société parent possède plusieurs comptes filiales. Cette approche utilise le compte global comme identifiant principal, remontant toute l&#39;activité du compte filiale au niveau de l&#39;organisation parent.

**Fonctionnement :**

Configurez la connexion B2B [!DNL CJA] avec le compte global comme identifiant principal au lieu du compte . Cela agrège les données d&#39;engagement de tous les comptes filiales sous leur organisation parent. Par exemple, si « Acme Corp » a des filiales régionales « Acme EMEA » et « Acme APAC », une connexion au compte global regroupe tous les engagements des trois entités en une seule vue analytique.

La vue de données inclut le compte global comme conteneur de niveau supérieur, avec le compte, la personne, la session et l’événement comme conteneurs imbriqués. Cela permet une analyse au niveau du compte global et des comptes secondaires dans le même projet d’espace de travail. Les intervalles de recherche en amont d’attribution s’appliquent au niveau du compte global, capturant tous les points de contact de l’ensemble de la hiérarchie de l’entreprise.

**Considérations principales :**

- Nécessite des données de hiérarchie de compte avec des relations parent-enfant définies dans le modèle de données B2B
- L’identifiant de compte global doit être renseigné et précis dans tous les enregistrements de compte
- Les comptes secondaires doivent être correctement mappés à leur parent

**Avantages :**

- Offre une visibilité consolidée sur toutes les structures de compte d’entreprise complexes
- Empêche l’analyse fragmentée lorsqu’un seul client d’entreprise possède plusieurs enregistrements de compte
- Permet la comparaison entre des filiales régionales au sein d’un compte global unique
- Prise en charge des pipelines au niveau de l’entreprise et de la création de rapports sur les revenus

**Limitations :**

- Nécessite des données de hiérarchie de compte précises, que de nombreuses organisations ont du mal à gérer
- Peuvent obscurcir les modèles au niveau des filiales lorsqu’ils sont affichés uniquement au niveau mondial
- Effort supplémentaire de modélisation des données pour établir et maintenir les relations hiérarchiques

**Experience League:**

- [Présentation de CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Option C : personne hybride + analyse de compte

**Idéal pour :** les organisations qui passent d’analyses basées sur la personne à analyses basées sur le compte, ou celles qui ont besoin de vues au niveau de la personne et au niveau du compte. Cette approche crée deux vues de données à partir de la même connexion, une centrée sur la personne et une centrée sur le compte.

**Fonctionnement :**

Configurez une connexion B2B [!DNL CJA] unique qui inclut tous les jeux de données B2B (événement, compte, opportunité, groupe d’achats, relations personne-compte). Créez ensuite deux vues de données : l’une utilisant Personne comme conteneur principal (similaire au [!DNL CJA] standard) et l’autre utilisant Compte comme conteneur principal. Les analystes peuvent basculer entre les vues de données en fonction de la question posée.

La vue de données centrée sur la personne fournit une analyse de parcours traditionnelle au niveau individuel (par exemple, « Quel est le chemin de conversion pour les prospects qui deviennent des opportunités ? »), tandis que la vue de données centrée sur le compte fournit une analyse au niveau de l’organisation (par exemple, « Quels comptes ont le taux de conversion engagement-pipeline le plus élevé ? »). Les deux vues utilisent les mêmes données sous-jacentes, ce qui garantit la cohérence.

**Considérations principales :**

- Nécessite deux vues de données avec des configurations de dimension et de mesure potentiellement différentes
- Les analystes ont besoin d’une formation sur l’utilisation de chaque vue
- Les mesures calculées peuvent devoir être créées séparément pour chaque vue de données

**Avantages :**

- Permet d’analyser les données au niveau de la personne et du compte
- Chemin d’adoption plus facile pour les équipes habituées à l’analyse au niveau de la personne
- Permet la comparaison entre les mesures au niveau de la personne et au niveau du compte
- Prend en charge les stratégies marketing basées sur les prospects et les comptes

**Limitations :**

- Deux vues de données à gérer et à maintenir synchronisées
- Confusion potentielle pour les analystes concernant la vue à utiliser
- Les mesures et filtres calculés peuvent nécessiter une duplication entre les vues

**Experience League:**

- [Créer ou modifier une vue de données](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Présentation des vues de données](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/data-views)

### Comparaison des options

| Critères | Option A : centrée sur le compte | Option B : centrée sur les comptes globaux | Option C : personne hybride + compte |
| --- | --- | --- | --- |
| Idéal pour | B2B standard avec structure de compte plate | Entreprise avec hiérarchies parent-enfant | Organisations en transition ou besoins doubles |
| Complexité | Moyenne | Élevée | Medium-Grand |
| Exigences en matière de données | Mappage compte-personne | Hiérarchie des comptes + mappage | Mappage compte-personne |
| Portée de l’attribution | Niveau du compte (recherche en amont sur 13 mois) | Niveau de compte global (recherche en amont sur 13 mois) | Au niveau de la personne et du compte |
| Données anonymes | Exclu de la vue du compte | Exclu de la vue globale | Inclus dans la vue Personne, exclu de la vue Compte |
| Requiert | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition, données de hiérarchie | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition |
| Effort de maintenance | Vue de données unique | Vue de données unique | Deux vues de données |

### Choisir la bonne option

- **Choisissez l’option A** si votre organisation dispose d’une structure de comptes plate (aucune hiérarchie parent-enfant), votre stratégie ABM fonctionne au niveau du compte individuel et vous souhaitez obtenir le chemin d’accès le plus simple vers l’analyse au niveau du compte.
- **Choisissez l’option B** si vos comptes cibles sont de grandes entreprises ayant des comptes filiales dans plusieurs régions ou divisions et que vous avez besoin d’un reporting consolidé au niveau de la société mère. Cette option nécessite des données de hiérarchie de comptes de haute qualité.
- **Choisissez l’option C** si votre entreprise passe d’un marketing basé sur les prospects à un marketing basé sur les comptes, vos analystes ont besoin d’une analyse funnel au niveau de la personne et d’une analyse de l’engagement au niveau du compte, ou vous disposez d’une combinaison de lignes d’activité B2B et B2C.

## Phases de mise en œuvre

Les phases suivantes décrivent la séquence d’implémentation recommandée.

### Phase 1 : connexion aux données B2B

**Fonction d’application :** [!DNL CJA] B2B : connexion basée sur le compte, [!DNL CJA] : connexion aux données

Configurez la connexion [!DNL CJA] qui lie vos jeux de données B2B AEP aux [!DNL CJA] pour analyse. Cette connexion définit les jeux de données qui entrent dans [!DNL CJA], le type d’identifiant principal (compte ou compte global) et la manière dont les données historiques et de diffusion en continu sont ingérées. La connexion est la base de toute analyse ultérieure.

#### Décision : type d&#39;identifiant du Principal

Déterminez si la connexion doit utiliser l’identifiant de compte ou l’identifiant de compte global comme identifiant principal.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| ID de compte | Structure de compte plate, pas de hiérarchies parent-enfant | Configuration plus simple ; chaque compte est analysé indépendamment. Choix le plus courant pour le B2B axé sur les PME. |
| ID de compte global | Comptes d&#39;entreprise avec hiérarchies de filiales | Nécessite des données de hiérarchie ; agrège toutes les filiales sous le parent. Idéal pour les programmes ABM d’entreprise. |

#### Décision : sélection du jeu de données et désignation du type

Déterminez quels jeux de données B2B doivent être inclus et comment chacun doit être saisi.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Jeux de données d’événements (comportementaux) | Toujours inclure | Interactions web, événements e-mail, envois de formulaire, téléchargements de contenu. Doit avoir un champ d’horodatage. Ce sont les signaux d&#39;engagement. |
| Jeux de données d’enregistrement de compte (profil) | Toujours inclure | Attributs de compte tels que le secteur, la taille, le niveau et le propriétaire. Fournit le contexte dimensionnel pour l’analyse de compte. |
| Jeux de données d’opportunités (recherche/profil) | Inclure pour l’analyse du pipeline | Étape de l’opportunité, valeur, date de fermeture. Requis pour l’analyse d’attribution de pipeline et de chiffre d’affaires. |
| Jeux de données de groupe d’achat (recherche/profil) | Inclure pour l&#39;analyse du groupe d&#39;achat | Rôles de groupe d’achat, scores d’engagement, exhaustivité. Requis pour l&#39;analyse de composition du groupe d&#39;achat. |
| Jeux de données de relation personne-compte (recherche) | Toujours inclure | Mappe les personnes sur les comptes. Essentiel pour associer des événements au niveau de la personne à une analyse au niveau du compte. |
| Jeux de données de campagne/programme (recherche) | Inclure pour attribution | Métadonnées de campagne, types de programmes, canaux. Active l’analyse de l’influence de la campagne. |

#### Décision : plage de renvoi

Déterminez la quantité de données historiques à importer dans la connexion.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Toutes les données existantes | Les cycles de vente B2B sont longs (6 à 18 mois) et vous avez besoin d’un historique complet | Recommandé pour B2B. Le renvoi peut prendre plusieurs jours pour les jeux de données volumineux, mais fournit des données d’attribution complètes. |
| Période personnalisée (2-3 dernières années) | La qualité des données se dégrade au-delà d’un certain point | Équilibre exhaustivité et qualité des données. Fréquent lorsque les données CRM présentent des incohérences historiques. |
| Pas de renvoi | Test ou développement uniquement | Seules les nouvelles données affluent. Ne convient pas aux analyses B2B de production. |

#### Configurer la connexion aux données B2B

**Navigation dans l’interface utilisateur :** [!DNL Customer Journey Analytics] > Connexions > Créer une connexion

Détails de configuration clés :

- Sélectionner le sandbox AEP contenant les jeux de données B2B
- Définir le nombre moyen d’événements quotidiens pour la planification des capacités
- Ajoutez chaque jeu de données et désignez son type (événement, recherche ou profil)
- Configurez le champ ID de personne pour utiliser l’ID de compte ou l’ID de compte global pour les connexions B2B
- Activer la diffusion en continu pour les jeux de données qui nécessitent des mises à jour en temps quasi réel
- Activez l’option « Importer toutes les données existantes » pour le renvoi historique

**Là où les options divergent :**

**Pour L’Option A (Centrée Sur Les Comptes) :**
Définissez l’identifiant principal sur l’identifiant du compte. Ajoutez des jeux de données d’enregistrement de compte, d’opportunité, de groupe d’achats et de relation personne-compte. Configurez des jeux de données d’événement au niveau de la personne avec le champ ID de compte pour la jonction de jeux de données croisés.

**Pour L’Option B (Centrée Sur Les Comptes Globaux) :**
Définissez l’identifiant principal sur l’identifiant de compte global. Assurez-vous que les données de la hiérarchie des comptes incluent le champ Identifiant de compte global . Tous les jeux de données doivent inclure l’identifiant de compte global ou pouvoir y être associés pour un cumul correct.

**Pour L’Option C (Hybride) :**
Créez une connexion unique avec tous les jeux de données B2B. Utilisez l’identifiant de compte comme identifiant principal. La vue centrée sur la personne sera créée à la phase 2 à l’aide d’une configuration de vue de données différente sur la même connexion.

**Documentation Experience League :**

- [Présentation des connexions](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/overview)
- [Création ou modification d’une connexion](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/create-connection)
- [Gérer des connexions](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/manage-connections)
- [Présentation de CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Phase 2 : configuration de la vue de données du compte

**Fonction d’application :** [!DNL CJA] B2B : configuration des vues de données B2B, [!DNL CJA] : configuration des vues de données

Configurez la vue de données qui définit la manière dont les données de connexion apparaissent dans l’analyse. Pour les analyses B2B, cela inclut la configuration de conteneurs spécifiques au B2B (compte, opportunité, groupe d’achats), le mappage des champs de schéma B2B aux dimensions et aux mesures, la définition de modèles d’attribution avec des intervalles de recherche en amont appropriés au B2B et la création de champs dérivés pour la logique commerciale B2B.

#### Décision : configuration du conteneur

Déterminez quels conteneurs B2B doivent être activés et comment ils doivent être nommés.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Compte + Personne + Session + Événement | B2B standard sans analyse de groupe d’achat ou d’opportunité | Hiérarchie de conteneur B2B la plus simple. Le compte est le conteneur de niveau supérieur. |
| Compte + Opportunité + Personne + Session + Événement | Analyse du pipeline et du chiffre d’affaires requise | Ajoute l’opportunité au niveau du conteneur, ce qui permet une analyse de la portée de l’opportunité. |
| Compte + Groupe D’Achats + Opportunité + Personne + Session + Événement | Analyse B2B complète comprenant la composition du groupe d’achat | La plus complète. Permet l’analyse à chaque niveau du modèle de données B2B. |
| Compte global + Compte + Personne + Session + Événement | Analyse de la hiérarchie globale des comptes | Ajoute le compte global comme conteneur de plus haut niveau au-dessus du compte. |

#### Décision : modèle d’attribution pour les mesures B2B

Déterminez quel modèle d’attribution doit être la valeur par défaut pour les mesures de conversion.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Attribution linéaire (recherche en amont de 13 mois) | Accorder le même crédit à tous les points de contact du parcours B2B | Idéal pour comprendre l’ensemble des activités marketing. Point de départ recommandé pour le B2B. |
| Attribution en U (recherche en amont de 13 mois) | Accent mis sur le premier et le dernier contact avec le crédit aux contacts intermédiaires | Met en évidence les moments de création de leads et de conversion d’opportunités. Courant dans l&#39;analyse de génération de demande. |
| Atténuation temporelle (recherche en amont de 13 mois) | Les points de contact plus récents doivent être davantage reconnus | Idéal lorsque la récence de l’engagement est un signal important pour la préparation des ventes. |
| Dernière touche | Rapport simple du point de contact final avant la conversion | Facile à comprendre, mais sous-estime le marketing à un stade précoce. À utiliser uniquement pour les rapports opérationnels rapides. |

#### Décision : définition de session pour B2B

Déterminez comment les sessions doivent être définies pour l’engagement B2B.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Temporisation de 30 minutes (par défaut) | Comportement de session Web Analytics standard | Norme pour l’analyse de l’engagement web. Peuvent fragmenter les longues sessions de consommation de contenu. |
| Délai d’expiration étendu (60 à 120 minutes) | Les utilisateurs B2B participent à des sessions de recherche plus longues | Les acheteurs B2B passent souvent beaucoup de temps à examiner le contenu technique, les prix et la documentation. |
| Nouvelle session basée sur un événement | Des événements spécifiques doivent toujours démarrer une nouvelle session | À utiliser lorsque les clics publicitaires de campagne ou les demandes de démonstration doivent toujours commencer une nouvelle session analytique. |

#### Configuration de la vue de données du compte

**Navigation dans l’interface utilisateur :** [!DNL Customer Journey Analytics] > Vues de données > Créer une vue de données

Détails de configuration clés :

- Sélectionnez la connexion créée à la phase 1
- Configurer le fuseau horaire et le type de calendrier appropriés à l’organisation
- Renommez les conteneurs en termes pertinents pour le B2B (par exemple, Compte/Engagement/Point de contact).
- Mappez les champs de schéma B2B aux dimensions : nom du compte, ID de compte, secteur, taille de l’entreprise, niveau de compte, propriétaire du compte, étape de l’opportunité, valeur de l’opportunité, rôle du groupe d’achat, intérêt de la solution
- Mapper les mesures d’engagement : événements (occurrences), personnes, sessions, pages vues, envois de formulaires, ouvertures d’e-mails, clics sur les e-mails
- Configurez la persistance pour les dimensions clés (par exemple, le secteur du compte persiste au niveau du compte)
- Définissez l’attribution sur linéaire avec une recherche en amont de 13 mois par défaut pour les mesures de conversion
- Créez des champs dérivés pour la classification de canal marketing, les niveaux de notation de l’engagement et le regroupement des étapes d’opportunité

**Là où les options divergent :**

**Pour L’Option A (Centrée Sur Les Comptes) :**
Configurez une vue de données unique avec Compte comme conteneur de niveau supérieur. Incluez les conteneurs Opportunité et Groupe d&#39;achats si une analyse de pipeline et de groupe d&#39;achats est nécessaire.

**Pour L’Option B (Centrée Sur Les Comptes Globaux) :**
Configurez Compte global comme conteneur de niveau supérieur. Incluez le compte en tant que sous-conteneur pour permettre l’analyse globale et subsidiaire.

**Pour L’Option C (Hybride) :**
Créez deux vues de données à partir de la même connexion. La vue de données 1 utilise Personne comme conteneur principal (comportement [!DNL CJA] standard). La vue de données 2 utilise le compte comme conteneur principal avec les conteneurs B2B. Mappez des mesures identiques aux deux vues, le cas échéant.

**Documentation Experience League :**

- [Présentation des vues de données](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/data-views)
- [Créer ou modifier une vue de données](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Présentation des paramètres de composant](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Paramètres de persistance](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Paramètres d’attribution](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Champs dérivés](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Paramètres de session](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/session-settings)

### Phase 3 : analyse Workspace

**Fonction d’application :** [!DNL CJA] B2B : analyse Workspace au niveau du compte, analyse du groupe d’achats, analyse des opportunités, segmentation B2B, attribution B2B, [!DNL CJA] : analyse Workspace, création de mesures calculées, analyse guidée

Créer des projets d’espace de travail qui fournissent les informations analytiques définies dans les indicateurs clés de performance. Cette phase comprend la création de tableaux à structure libre avec des dimensions et des mesures B2B, la création de mesures calculées pour les indicateurs clés de performance B2B, la configuration de visualisations spécifiques au B2B (flux au niveau du compte, funnel d’opportunité, engagement du groupe d’achats), la création de filtres/segments à l’aide de conteneurs B2B et l’application de modèles d’attribution B2B.

#### Décision : structure Analysis Workspace

Déterminez comment le projet Workspace doit être organisé.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Projet complet unique avec plusieurs panneaux | Petite équipe, toutes les parties prenantes voient les mêmes rapports | Facile à gérer. Utilisez des panneaux pour séparer les rubriques (engagement, pipeline, attribution). Jusqu’à 40 panneaux par projet. |
| Plusieurs projets ciblés par audience | Différentes parties prenantes ont besoin de points de vue différents | Le marketing obtient l’engagement/attribution. Le service des ventes obtient l’intégrité du pipeline/compte. Les opérations obtiennent la qualité des données. Plus de maintenance mais mieux ciblée. |
| Projets basés sur des modèles avec analyse guidée | Analyses en libre-service pour les utilisateurs non experts | Utilisez l’analyse guidée pour les vues funnel et de tendance. Enregistrez-les en tant que modèles pour une analyse répétable. Idéal pour une adoption généralisée. |

#### Décision : mesures calculées B2B

Déterminer les mesures calculées nécessaires pour les indicateurs clés de performance B2B.

| Mesure | Formule | Quand créer |
| --- | --- | --- |
| Taux d’engagement du compte | (Total Des Événements De Compte / Total Des Comptes) | Toujours — Mesure B2B principale |
| % de complétion du groupe d&#39;achat | (Rôles renseignés / Rôles requis) * 100 | Lorsque l&#39;analyse du groupe d&#39;achat est dans la portée |
| Conversion compte à opportunité | Comptes avec opportunités / comptes engagés | Lorsqu’une analyse de pipeline est nécessaire |
| Pourcentage d’influence du pipeline | Valeur du pipeline influencé / Valeur totale du pipeline | Lorsque l’attribution marketing est requise |
| Engagement moyen par contact | Événements/personnes uniques par compte | Lorsqu’une analyse de pénétration de compte est nécessaire |
| Engagement du contenu par rôle | Evénements filtrés par rôle de groupe d&#39;achat | Lorsque l’optimisation du contenu pour le B2B est nécessaire |

#### Décision : filtre B2B/portée de segment

Déterminez à quel niveau de conteneur les filtres doivent être créés.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Filtres au niveau du compte | Analyse étendue aux comptes répondant aux critères (par exemple, comptes d’entreprise, secteurs d’activité spécifiques) | Inclut tous les événements provenant de comptes admissibles. Plus fréquent pour le B2B. |
| Filtres au niveau de l’opportunité | Analyse étendue à des types d’opportunités ou à des étapes spécifiques | Inclut tous les événements associés aux opportunités de qualification. |
| Achat de filtres au niveau du groupe | Analyse étendue à des états de groupes d&#39;achat spécifiques | Inclut les événements de personnes appartenant à des groupes d&#39;achats admissibles. |
| Filtres au niveau de la personne | Analyse étendue aux individus répondant aux critères (par exemple, rôles spécifiques, titres) | Comportement de filtre standard. À utiliser lors de l’analyse de l’engagement individuel dans le contexte B2B. |

#### Création de l’analyse de l’espace de travail

**Navigation dans l’interface utilisateur :** [!DNL Customer Journey Analytics] > Workspace > Projets > Créer un projet

Détails de configuration clés :

- Sélectionnez la vue de données B2B créée à la phase 2
- Créer des tableaux à structure libre avec des dimensions au niveau du compte (nom du compte, secteur, niveau) ventilées par mesures d’engagement
- Création de visualisations funnel des opportunités présentant la progression des opportunités à travers les étapes
- Créer des tableaux de composition de groupes d’achats indiquant les taux de remplissage des rôles et l’engagement par rôle
- Configurez les panneaux d’attribution B2B comparant les modèles d’attribution (linéaires, en forme de U, décroissance temporelle) à la recherche en amont de 13 mois
- Créez des visualisations de flux de compte présentant les chemins courants à travers le parcours d’achat
- Créer des tableaux de cohortes analysant la rétention des comptes et le réengagement au fil du temps
- Application de filtres B2B à l’analyse des segments par niveau de compte, secteur ou niveau d’engagement
- Créer des annotations pour les événements importants (lancements de campagne, mises à jour de produit, modifications de prix)

**Documentation Experience League :**

- [Présentation de Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)
- [Créer un projet](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tableau à structure libre](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Panneau d’attribution](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Visualisation de flux](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualisation des abandons](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Table de cohorte](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Présentation des filtres](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Création de mesures calculées](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Présentation des annotations](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/annotations/overview)
- [Aperçu des analyses guidées](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/guided-analysis/overview)
- [Répartition des dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

### Phase 4 : publication de tableaux de bord

**Fonction d’application :** [!DNL CJA] : publication de tableaux de bord et de cartes de performance, [!DNL CJA] : publication d’audiences

Créez des tableaux de bord partageables et des cartes de performance mobiles qui fournissent des informations d’analyse B2B aux parties prenantes. Cette phase couvre également la publication d’audiences B2B définies par [!DNL CJA] dans AEP pour activation dans des cas d’utilisation en aval, tels que l’activation des audiences B2B.

#### Décision : méthode de diffusion dans le tableau de bord

Déterminez comment les informations d’analyse B2B doivent être diffusées aux parties prenantes.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Projet Workspace (ordinateur de bureau) | Analystes et opérations marketing ayant besoin d’une exploration interactive | Interactivité complète, analyse en profondeur, basculement de filtre. Nécessite un accès [!DNL CJA]. |
| Carte de performance mobile | Cadres et responsables des ventes qui ont besoin de KPI en un coup d’œil | Synthèse des chiffres avec des lignes de tendance. Accessible par le biais de l’application de tableaux de bord [!DNL Adobe Analytics]. Interactivité limitée. |
| Exportation PDF/CSV planifiée | Parties prenantes sans accès [!DNL CJA] qui ont besoin de mises à jour régulières | Diffusion automatisée selon un planning. Aucune interactivité. Idéal pour les résumés exécutifs hebdomadaires/mensuels. |
| Tout ce qui précède | Grandes organisations avec des besoins divers des parties prenantes | Portée maximale. Effort de maintenance plus élevé. Recommandé pour les programmes d’analyse B2B matures. |

#### Décision : publication d’audiences à partir de [!DNL CJA]

Déterminez si les segments B2B doivent être republiés vers AEP pour activation.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Publication d’audiences basées sur un compte | Les informations d’Analytics doivent éclairer le ciblage et la suppression | Active l’activation de segments définis par l’[!DNL CJA] (par exemple, « comptes à fort engagement sans opportunités ouvertes ») via [!DNL RT-CDP]. Fréquence d’actualisation : 4 heures à toutes les semaines. |
| Ne pas publier | Analytics est destiné aux rapports uniquement, et non à l’activation | Configuration simplifiée. L’activation est gérée séparément dans [!DNL RT-CDP]. |

#### Publication de tableaux de bord et d’audiences

**Navigation dans l’interface utilisateur :** [!DNL Customer Journey Analytics] > Projets > Partager (pour Workspace), Projets > Créer > Carte de performance mobile (pour les cartes de performance), Composants > Audiences > Publier (pour la publication d’audience)

Détails de configuration clés :

- Créer des tableaux de bord exécutifs avec des chiffres récapitulatifs pour les indicateurs clés de performance B2B (total des comptes engagés, valeur du pipeline, exhaustivité du groupe d’achat)
- Configurer des périodes de comparaison (mois par mois, trimestre par trimestre) pour les indicateurs de tendance
- Créez des cartes de performance mobiles avec des vignettes pour l’engagement du compte, l’intégrité du pipeline et les mesures d’attribution
- Ajoutez des filtres pour les cadres afin d’activer/désactiver les vues par région, secteur ou niveau de compte
- Configurer la diffusion planifiée du projet pour les rapports exécutifs hebdomadaires
- Pour la publication d’audiences : sélectionnez le filtre B2B, configurez l’espace de noms d’identité (ID de compte) et définissez la cadence d’actualisation

**Documentation Experience League :**

- [Création d’une carte de performance mobile](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Partager des projets](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planification de projets](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Configuration et traitement des cartes de performance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Tableaux de bord Adobe Analytics - guide exécutif](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Présentation des audiences](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Création et publication d’audiences](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/audiences/publish)

## Considérations relatives à la mise en œuvre

Les sections suivantes couvrent les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage à garder à l’esprit lors de la mise en œuvre.

### Mécanismes de sécurisation et limites

- [!DNL CJA] connexions peuvent inclure des jeux de données provenant d’un seul sandbox AEP : [mécanismes de sécurisation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-admin/guardrails)
- Maximum de 5 000 dimensions et 5 000 mesures par vue de données
- Maximum de 100 champs dérivés par vue de données
- L’attribution B2B prend en charge des intervalles de recherche en amont allant jusqu’à 13 mois pour l’analyse au niveau du compte
- Maximum de 75 audiences publiées par client [!DNL CJA] dans tous les sandbox
- La fréquence minimale d’actualisation de la publication d’audience est toutes les 4 heures
- La latence de diffusion en continu d’AEP vers [!DNL CJA] est généralement inférieure à 90 minutes
- Les tableaux à structure libre prennent en charge jusqu’à 10 répartitions de dimension profondes
- Les cartes de performance mobiles prennent en charge jusqu’à 16 vignettes par carte de performance
- Les projets Workspace prennent en charge jusqu’à 40 panneaux par projet
- Le renvoi de jeux de données B2B volumineux (des milliards d’enregistrements) peut prendre plusieurs jours

### Pièges courants

- **Mappage personne-compte incomplet :** si des événements au niveau de la personne ne peuvent pas être associés à un compte, ils n’apparaîtront pas dans l’analyse au niveau du compte. Assurez-vous que tous les jeux de données d’événement incluent un champ qui peut être joint à l’identifiant de compte, directement ou par le biais d’un jeu de données de recherche de relation personne-compte. Contrôlez le pourcentage d’événements avec une association de compte manquante avant de créer l’analyse.
- **Désignation de type de jeu de données incorrecte :** les jeux de données de recherche B2B (opportunité, groupe d’achats, relations personne-compte) doivent être correctement désignés comme type de recherche ou de profil dans la connexion [!DNL CJA]. La saisie erronée d’un jeu de données de recherche en tant que jeu de données d’événement produira des résultats incorrects, car [!DNL CJA] tenterez de traiter chaque enregistrement comme un événement horodaté.
- **Fenêtre d’attribution trop courte pour le B2B :** l’utilisation de fenêtres d’attribution de 30 jours par défaut permet d’ignorer les premiers points de contact d’un parcours B2B qui s’étendent généralement sur 6 à 18 mois. Configurez toujours des intervalles de recherche en amont de 13 mois pour les mesures d’attribution B2B.
- **Mélange incorrect des mesures au niveau du compte et au niveau de la personne :** compter les « personnes » dans une analyse au niveau du compte peut être trompeur. Assurez-vous que les mesures calculées sont définies au niveau du conteneur approprié. Un « taux d’engagement de compte » doit utiliser des événements au niveau du compte divisés par comptes, et non par personnes.
- **Données de groupe d’achat obsolètes :** la composition du groupe d’achat et les affectations de rôles changent au fil du temps. Si les jeux de données du groupe d’achats ne sont pas actualisés régulièrement, les mesures d’exhaustivité seront inexactes. Assurez-vous que le système source ([!DNL Marketo Engage] ou [!DNL AJO] B2B edition) synchronise activement les données du groupe d&#39;achats.
- **Surcharger un seul projet Workspace :** l’analyse B2B couvre l’engagement, le pipeline, l’attribution et les groupes d’achat. Si vous tentez de tout regrouper dans un projet, le chargement est lent et la navigation devient confuse. Utilisez plusieurs projets ciblés ou des panneaux clairement étiquetés.

### Bonnes pratiques

- Commencez par l’option A (centrée sur le compte) même si vous prévoyez d’utiliser l’option B (compte global) ultérieurement. L’analyse centrée sur les comptes est plus simple et valide votre modèle de données avant d’ajouter de la complexité à la hiérarchie.
- Créez un projet d’espace de travail « Qualité des données B2B » dédié qui suit le pourcentage d’événements avec une association de compte, le nombre de comptes orphelins et les mesures d’exhaustivité du groupe d’achats. Exécutez cette semaine pour détecter les problèmes de données de manière précoce.
- Utilisez des champs dérivés pour créer des niveaux de score d’engagement (Élevé/Medium/Faible) en fonction du nombre d’événements au niveau du compte. Cela simplifie l’analyse et rend les tableaux de bord plus exploitables pour les parties prenantes non techniques.
- Lors de la configuration de l’attribution B2B, commencez par utiliser l’attribution linéaire comme ligne de base, puis comparez-la aux modèles en forme de U et de décroissance temporelle. Les différences entre les modèles indiquent souvent si votre mix marketing est pondéré en fonction des activités de sensibilisation ou de conversion.
- Publiez une carte de performance mobile « Résumé exécutif B2B » avec pas plus de 8 vignettes couvrant les indicateurs de performance clés qui comptent le plus pour le leadership. Restez concentrés : les fiches de performance des dirigeants doivent répondre « Comment allons-nous ? » pas « Pourquoi ? »
- Annotez les événements clés (lancements de produits, lancements de campagnes majeures, modifications de prix, modifications de processus de vente) pour fournir un contexte aux tendances des données. Les données B2B présentent souvent des pics et des creux inexplicables sans contexte d’événement.
- Lors de la publication d’audiences B2B à partir de [!DNL CJA], utilisez l’actualisation quotidienne pour les segments d’activation standard et l’actualisation toutes les 4 heures uniquement pour les segments sensibles au facteur temps. Des actualisations fréquentes consomment des ressources de traitement.

### Décisions de compromis

>[!NOTE]
>Les décisions de compromis suivantes doivent être évaluées en fonction des exigences et des contraintes spécifiques de votre organisation.

**Exhaustivité des données par rapport à la précision des analyses**

L’inclusion de tous les événements au niveau de la personne dans l’analyse du compte (même ceux qui ont une association de compte faible) améliore l’exhaustivité des données mais peut réduire la précision des analyses si le mappage des comptes n’est pas fiable.

- **Inclusion de tous les événements favorisés :** mesure complète de l’engagement, scores d’engagement de compte plus élevés, visibilité accrue
- **L’exclusion des événements non correspondants favorise :** des mesures précises au niveau du compte, une attribution de confiance, une corrélation de pipeline fiable.
- **Recommandation :** exclure les événements non correspondants de l’analyse au niveau du compte, mais les inclure dans une vue de données distincte au niveau de la personne (option C) pour comprendre l’ensemble. Privilégiez l’amélioration de la qualité des données d’association de compte en tant que flux de travail parallèle.

**Longueur de l’intervalle de recherche en amont d’attribution B2B**

Des intervalles de recherche en amont plus longs (13 mois) capturent davantage de points de contact, mais peuvent inclure des activités marketing qui ne sont plus pertinentes pour la décision d’achat actuelle.

- **Recherche en amont plus longue (13 mois) :** capturer l’intégralité du parcours B2B, créditer les activités de sensibilisation, prendre en compte les longs cycles de vente.
- **Recherche en amont plus courte (6 mois) :** vous concentrer sur les engagements récents, réduire le bruit des anciens points de contact, mieux refléter l’intention d’achat actuelle.
- **Recommandation :** utilisez une recherche en amont de 13 mois pour les comptes d’entreprise avec des cycles de vente longs (12 mois et plus). Utilisez une recherche en amont de 6 mois pour les comptes de taille moyenne avec des cycles plus courts. Créez des mesures calculées distinctes pour chaque fenêtre à comparer.

**Vue de données complète unique contre vues de données concentrées multiples**

La gestion d’une vue de données avec tous les conteneurs et dimensions B2B est plus simple, mais elle peut surcharger les analystes en raison de sa complexité. Les vues de données multi-focus (engagement, pipeline, attribution) sont plus faciles à utiliser, mais plus difficiles à gérer.

- **La vue unique favorise :** cohérence, maintenance plus facile, analyse interdomaines au sein d’un seul projet.
- **Plusieurs vues sont préférées :** simplicité pour les analystes, temps de chargement plus rapides, listes de composants personnalisées par cas d’utilisation
- **Recommandation :** commencez par une seule vue de données complète. Si les analystes signalent des difficultés à trouver les dimensions et mesures appropriées, créez des groupes de composants sélectionnés dans la même vue avant de les diviser en plusieurs vues. Utilisez des modèles d’espace de travail pour guider les analystes vers les composants appropriés.

## Documentation connexe

Les ressources suivantes apportent des informations supplémentaires sur l’implémentation de ce modèle de cas d’utilisation.

**[!DNL CJA]B2B edition**

- [Présentation de CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [Présentation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview)
- [Mécanismes de sécurisation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-admin/guardrails)

**Connexions**

- [Présentation des connexions](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/overview)
- [Création ou modification d’une connexion](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/create-connection)
- [Gérer des connexions](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/manage-connections)

**Vues de données**

- [Présentation des vues de données](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/data-views)
- [Créer ou modifier une vue de données](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Présentation des paramètres de composant](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Paramètres de persistance](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Paramètres d’attribution](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Paramètres de format](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Champs dérivés](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Paramètres de session](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace et analyse**

- [Présentation de Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)
- [Créer un projet](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Tableau à structure libre](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Visualisation de flux](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Visualisation des abandons](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Table de cohorte](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Panneau d’attribution](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Partager des projets](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planification de projets](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Répartition des dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**Composants**

- [Présentation des filtres](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Création de filtres](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Présentation des mesures calculées](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Création de mesures calculées](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Présentation des annotations](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/annotations/overview)
- [Périodes](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**Audiences**

- [Présentation des audiences](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Création et publication d’audiences](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/audiences/publish)
- [Gestion des audiences](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-components/audiences/manage)

**Tableaux de bord et cartes de performance**

- [Création d’une carte de performance mobile](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configuration et traitement des cartes de performance](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Tableaux de bord Adobe Analytics - guide exécutif](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**Analyse guidée**

- [Aperçu des analyses guidées](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/guided-analysis/overview)
- [Vue funnel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Vue Tendances](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Vue de rétention](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [Présentation de RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [Schémas B2B edition](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/schemas/b2b)
- [Présentation des sources B2B](https://experienceleague.adobe.com/fr/docs/experience-platform/rtcdp/sources/b2b)

**AEP data foundation**

- [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home)
- [Présentation des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home)
- [Connecteur Marketo Engage](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation des sandbox](https://experienceleague.adobe.com/fr/docs/experience-platform/sandbox/home)

**Gouvernance et cycle de vie des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home)
- [Gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/home)

**Tutoriels et guides**

- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/schema/composition)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home)
