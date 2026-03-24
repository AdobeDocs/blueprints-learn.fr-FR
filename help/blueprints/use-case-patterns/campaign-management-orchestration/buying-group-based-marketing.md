---
title: Marketing et gestion de Parcours par groupe d'achats
description: Découvrez comment développer des parcours au niveau du compte qui qualifient les prospects en groupes d’achats afin d’améliorer l’efficacité du marketing B2B.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 2bf57f67-80c8-4368-98d2-05706427772d
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7932'
ht-degree: 0%

---

# Gestion des parcours et marketing par groupe d&#39;achat

Ce guide fournit une référence d’implémentation complète pour le marketing de groupe d’achats et la gestion de parcours. Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui doivent mettre en œuvre une orchestration de parcours au niveau du compte avec une gestion de groupe d’achats utilisant [!DNL Adobe Journey Optimizer B2B Edition] et [!DNL Real-Time CDP B2B Edition].

Utilisez ce document pour comprendre ce qu’il faut configurer, où se trouvent les choix d’implémentation et quels compromis motivent chaque décision.

Contrairement aux modèles de parcours au niveau de la personne, ce modèle fonctionne au niveau du compte, qualifiant les prospects individuels dans les groupes d’achat associés aux intérêts de la solution, notant l’engagement au niveau du groupe d’achat et orchestrant des parcours de compte à plusieurs étapes qui font progresser les comptes à travers les étapes du pipeline vers la préparation aux ventes.

## Présentation du cas d’utilisation

Les organisations B2B sont confrontées à un défi fondamental : les décisions d’achat sont rarement prises par une seule personne. Les achats B2B complexes impliquent plusieurs parties prenantes (décideurs, influenceurs, champions, détenteurs de budget et évaluateurs techniques) qui forment collectivement un « groupe d’achat ». Le marketing traditionnel basé sur les leads traite chaque personne indépendamment, ce qui néglige le signal essentiel de savoir si la bonne combinaison de rôles au sein d’un compte est engagée et prête à acheter.

Le marketing de groupe et la gestion de parcours permettent d&#39;y remédier en déplaçant l&#39;unité d&#39;orchestration des prospects individuels vers les comptes et les groupes d&#39;achats. Le modèle permet aux spécialistes du marketing B2B de définir les intérêts de la solution (les produits ou services vendus), de créer des modèles de groupe d’achat qui spécifient les rôles nécessaires à une décision d’achat, de qualifier les prospects entrants par rapport à ces rôles, de noter l’engagement au niveau du groupe d’achat et d’orchestrer des parcours de compte qui répondent aux signaux d’exhaustivité et de préparation du groupe d’achat.

Le résultat escompté est l’amélioration de la qualité et de la vitesse du pipeline : le marketing ne livre les comptes aux ventes que lorsque les bonnes personnes au sein du compte sont engagées et que le groupe d’achat est suffisamment complet, ce qui réduit les efforts de vente gaspillés et accélère la progression de l’affaire.

## Objectifs commerciaux clés

Ce modèle de cas d’utilisation prend en charge les objectifs commerciaux suivants.

### Améliorer la qualification et la conversion des prospects

Augmentez la qualité des prospects et accélérez la progression du pipeline grâce à la notation, à l’entretien et au suivi personnalisé.

**KPI :** conversion de lead, conversion de prospect/lead, efficacité

[En savoir plus sur l’amélioration de la qualification et de la conversion des prospects](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Augmenter la génération de leads

Générer davantage de leads qualifiés pour le pipeline de vente par le biais de formulaires, d’événements, de contenu et d’engagements multicanaux.

**KPI :** prospects, coût par lead, conversion de lead

[En savoir plus sur l’augmentation de la génération de pistes](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Augmenter le chiffre d’affaires et les ventes

Stimuler la croissance du chiffre d’affaires de premier plan grâce à des canaux numériques, des campagnes et des parcours client optimisés.

**KPI :** croissance du chiffre d’affaires, vitesse du pipeline, taux de conclusion des affaires

[En savoir plus sur l’augmentation des recettes et des ventes](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## Exemples de cas d’utilisation tactiques

Vous trouverez ci-dessous des scénarios spécifiques où ce modèle peut être appliqué.

- **Qualification de groupe d’achats spécifique à une solution** — Définissez des groupes d’achats pour chaque ligne de produits (par exemple, « Enterprise CRM », « Data Platform », « Security Suite ») avec des modèles de rôle spécifiant les rôles requis (acheteur économique, évaluateur technique, champion, utilisateur final) et qualifiez les prospects provenant du système de gestion de la relation client et d’automatisation du marketing par rapport à ces rôles.
- parcours de compte pour l’accélération du pipeline **— Orchestrez un parcours de compte à plusieurs étapes qui envoie des e-mails de suivi ciblés aux rôles sous-engagés au sein d’un groupe d’achats, déclenche des alertes de ventes lorsque les seuils d’engagement sont atteints et fait passer le compte à une étape prête pour les ventes.**
- **Campagnes d&#39;exhaustivité du groupe d&#39;achat** — Identifiez les comptes où les groupes d&#39;achat ont des rôles manquants (par exemple, aucun acheteur économique identifié) et lancez des campagnes d&#39;acquisition ciblées pour engager les bonnes personnes au sein de ces comptes.
- parcours de comptes de ventes croisées **— Une fois la transaction initiale conclue, créez de nouveaux groupes d&#39;achat pour des intérêts de solution complémentaires et orchestrez des parcours de comptes qui favorisent l&#39;expansion du comité d&#39;achat.**
- **Réengagement pour les affaires bloquées** — Détectez les comptes où les scores d’engagement du groupe d’achat ont diminué et déclenchez des parcours de réengagement avec du contenu récent, des activités de sensibilisation des dirigeants ou des invitations à des événements.
- **Alignement des ventes et du marketing grâce à des informations CRM** — Affichez le statut du groupe d’achats, les données d’engagement et la progression du parcours de compte directement dans [!DNL Salesforce] ou [!DNL Dynamics 365] afin que les représentants commerciaux aient une visibilité en temps réel sur les comptes qualifiés pour le marketing.
- **Mises à jour des groupes d’achats pilotés par les événements** — Mettez automatiquement à jour les scores d’appartenance et d’engagement des groupes d’achats lorsque les prospects assistent à des webinaires, téléchargent des livres blancs, consultent des pages de tarification ou demandent des démonstrations.
- **Coordination de comptes multi-régions** — Gérez les groupes d&#39;achats sur les comptes mondiaux où différents contacts régionaux ont des rôles différents, unifiant la notation de l&#39;engagement entre les zones géographiques.

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer l’efficacité de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux de complétion du groupe d&#39;achat | Pourcentage de groupes d&#39;achats dont tous les rôles requis sont remplis | Tableaux de bord [!DNL AJO B2B] Analytics : suivre la couverture des rôles par groupe d’achats |
| Score d&#39;engagement du groupe d&#39;achat | Score d’engagement agrégé de tous les membres d’un groupe d’achat | Score de l’engagement [!DNL AJO B2B] : scores au niveau de la personne cumulés dans le groupe d’achat |
| Taux de compte qualifié marketing (MQA) | Pourcentage de comptes qui atteignent le seuil qualifié marketing | Critères de sortie du parcours de comptes : comptes passant à l’étape Prêt pour la vente |
| Vitesse du pipeline | Temps moyen entre la création du groupe d&#39;achat et l&#39;opportunité qualifiée pour la vente | Intégration CRM : suivi des transitions d’étape du pipeline [!DNL AJO B2B] vers CRM |
| Taux de qualification du groupe lead-acheteur | Pourcentage de leads qualifiés pour des rôles de groupe d&#39;achat | [!DNL AJO B2B] Gestion de groupe d&#39;achat : ratio de leads qualifiés par rapport aux leads non qualifiés |
| Taux de réponse aux alertes de ventes | Pourcentage d’alertes de ventes qui entraînent une activité de suivi des ventes | CRM Sales Insights : suivi de la conversion alerte-activité |
| Taux d’achèvement du Parcours de compte | Pourcentage de comptes qui terminent le chemin de parcours prévu | Tableaux de bord [!DNL AJO B2B] Analytics : mesures d’achèvement du parcours |
| Taux D’Engagement Des E-Mails (B2B) | Taux d’ouverture et de clic publicitaire pour les e-mails d’éducation B2B | Création de rapports [!DNL AJO B2B] : diffusion d’e-mails et mesures d’engagement |

## Modèle de cas d’utilisation

**Marketing et gestion de parcours par groupe d&#39;achat**

Développez des parcours au niveau du compte qui qualifient les prospects en groupes d’achat afin d’améliorer l’efficacité du marketing B2B.

**Chaîne de fonctions : Identification de compte** > Définition du groupe d’achat > Qualification du lead > Exécution du Parcours de compte > Notation de l’engagement > Rapports

## Applications

Les applications Adobe suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** — Orchestre les parcours au niveau du compte, gère les groupes d&#39;achats avec des modèles de rôle et des centres d&#39;intérêt pour les solutions, note l&#39;engagement au niveau de la personne et du groupe d&#39;achats, crée du contenu d&#39;e-mail B2B, envoie des SMS, configure des alertes de ventes et fournit des tableaux de bord d&#39;analyse B2B.
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** : unifie les profils de compte à partir de données B2B inter-sources, résout les relations personne à compte, évalue les audiences au niveau du compte, configure les destinations spécifiques au B2B ([!DNL Marketo Engage], [!DNL LinkedIn], CRM) et applique la gouvernance des données sur les données B2B.

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Obligatoire | Sandbox configuré avec droits [!DNL AJO B2B Edition] et [!DNL RT-CDP B2B Edition] activés. Rôles configurés pour les spécialistes du marketing B2B, les opérations de vente et les administrateurs disposant des autorisations appropriées pour la gestion des groupes d’achats, les parcours de compte et les paramètres d’intégration CRM. | [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Schémas XDM B2B configurés à l’aide de classes spécifiques au B2B : compte professionnel XDM, opportunité commerciale XDM, professionnel XDM (prospect/contact), campagne commerciale XDM et liste marketing professionnelle XDM. Les groupes de champs pour les attributs de compte, les attributs de personne et les données d’activité/engagement doivent être en place. Jeux de données créés et activés pour le profil pour chaque schéma. | [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [classes de schéma B2B](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Sources et collecte de données | Obligatoire | Pipelines d’ingestion de données B2B établis, généralement via le connecteur source [!DNL Marketo Engage] ou les connecteurs source CRM [!DNL Salesforce]/[!DNL Dynamics]. Les données relatives au compte, à la personne, à l’opportunité, à la campagne et aux membres de la campagne doivent être transmises aux jeux de données AEP. Les données comportementales d’engagement (visites web, interactions par e-mail, téléchargements de contenu) doivent également être ingérées pour le score d’engagement. | [Présentation des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home), [Connecteur Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Configuration des identités et des profils | Obligatoire | Résolution d’identité B2B configurée pour résoudre les relations personne à compte. Les espaces de noms d’identité pour les identifiants B2B (ID de personne [!DNL Marketo], ID de lead/contact [!DNL Salesforce], ID de compte) doivent exister. Politiques de fusion configurées pour l’unification des profils B2B. Les profils de compte doivent être unifiés à partir des données inter-sources. | [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Résolution d’identités B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) |
| Définition et segmentation de l’audience | Obligatoire | Définitions d’audience au niveau du compte créées à l’aide des attributs de compte, des attributs de personne et des données d’activité. Les audiences de compte identifient les comptes qui entrent dans les parcours du groupe d&#39;achat. L’évaluation par lots est généralement suffisante pour les parcours de compte B2B, bien que l’évaluation par flux puisse être utilisée pour les déclencheurs de qualification de compte en temps réel. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés peuvent agréger les événements d’engagement au niveau de la personne (ouvertures d’e-mails, téléchargements de contenu, participation à des webinaires) en mesures d’engagement au niveau du compte qui alimentent la logique de notation du groupe d’achats et de qualification du compte. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | La gestion du consentement est essentielle pour les communications B2B par e-mail et SMS. Les politiques d’expiration des jeux de données permettent de gérer le cycle de vie des données d’engagement transitoires et de garantir la conformité aux exigences de conservation des données. | [Gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les données B2B contiennent souvent des informations sensibles sur l’entreprise et des données personnelles de contacts professionnels. Les politiques de gouvernance des données garantissent une utilisation conforme des données B2B entre les destinations, en particulier lors de l’activation sur des plateformes publicitaires ou des systèmes tiers. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Surveillance et observabilité | Recommandé | La surveillance permet de s’assurer que les pipelines de données B2B (synchronisations CRM/[!DNL Marketo]) sont sains, que les profils de compte sont mis à jour et que les exécutions de parcours de compte se déroulent sans échec. Les alertes sur les échecs de flux de données source sont essentielles pour maintenir la devise des données. | [Présentation d’Observability Insights](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Les tableaux de bord d’analyse B2B d’[!DNL AJO B2B Edition] fournissent l’engagement du groupe d’achats, les performances du parcours de compte et les mesures de pipeline. [!DNL CJA B2B Edition] étend l’analyse avec l’analyse de l’espace de travail au niveau du compte, l’analyse des groupes d’achats et la corrélation des opportunités. | Présentation de [&#128279;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Configuration de l’intérêt de la solution | Phase 1 : Intérêt pour la solution et configuration du groupe d&#39;achat | Définir les intérêts de la solution qui font correspondre les produits ou les services aux critères de qualification du groupe d&#39;achat |
| Gestion des groupes d&#39;achat | Phase 1 : Intérêt pour la solution et configuration du groupe d&#39;achat | Créez et gérez des groupes d&#39;achats avec des modèles de rôle, des mappages de personnalités et des définitions des intérêts des solutions |
| Journey Orchestration du compte | Phase 3 : conception et exécution du Parcours de compte | Concevez et gérez des parcours de compte à plusieurs étapes avec des conditions, des actions et un embranchement basé sur l’engagement |
| Score de l’engagement | Phase 2 : qualification du lead et score de l’engagement | Noter l’engagement au niveau de la personne au sein des groupes d’achats pour mesurer l’exhaustivité et la préparation des groupes d’achats |
| Qualification du compte | Phase 2 : qualification du lead et score de l’engagement | Utilisez des agents de qualification de compte optimisés par IA pour évaluer la préparation du compte et la qualité du pipeline |
| Création d’e-mails B2B | Phase 3 : conception et exécution du Parcours de compte | Créer du contenu d’e-mail B2B avec des modèles, des fragments visuels, des thèmes de marque et la génération de contenu assistée par IA |
| Gestion des canaux SMS | Phase 3 : conception et exécution du Parcours de compte | Configurer et gérer des communications SMS dans les parcours de compte B2B |
| Configuration de l’alerte de ventes | Phase 4 : alignement des ventes et intégration CRM | Configurez les e-mails d’alerte commerciale pour informer les équipes commerciales des jalons d’engagement du compte et des signaux d’achat |
| Informations sur les ventes CRM | Phase 4 : alignement des ventes et intégration CRM | Fournissez une visibilité interne au CRM ([!DNL Salesforce], [!DNL Dynamics]) pour le statut du groupe d’achats, les données d’engagement et la progression du parcours de compte |
| Tableaux de bord B2B Analytics | Phase 5 : Rapports et optimisation | Surveillez les performances du parcours de compte, l’engagement du groupe d’achats et les mesures du pipeline via des tableaux de bord intelligents et d’engagement |

### [!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Unification du profil de compte | Phase 0 : Fondation de données B2B | Consolidez les données B2B inter-sources en profils de compte unifiés à l’aide de classes de schémas et de groupes de champs XDM B2B spécialisés |
| Résolution d’identités B2B | Phase 0 : Fondation de données B2B | Résolvez les relations personne à compte à l’aide d’identifiants principaux, en prenant en charge les hiérarchies de comptes à plusieurs niveaux et les mappages personne à compte multiples |
| Évaluation de l’audience du compte | Phase 0 : Fondation de données B2B | Évaluer l’appartenance à un segment au niveau du compte en combinant des attributs de compte, des attributs de personne et des données d’activité |
| Configuration de la destination du compte | Phase 4 : alignement des ventes et intégration CRM | Configurez des connexions à des destinations spécifiques au B2B (systèmes [!DNL Marketo Engage], [!DNL LinkedIn] et CRM) avec le mappage des champs au niveau du compte |
| Audience Activation du compte | Phase 4 : alignement des ventes et intégration CRM | Publier des audiences basées sur un compte vers des destinations pour le ciblage et la suppression basés sur un compte |
| Intégration [!DNL Marketo Engage] | Phase 0 : Fondation de données B2B | Ingérer et activer des données de manière bidirectionnelle avec [!DNL Marketo Engage] à l’aide de connecteurs source et de destination B2B natifs |
| Gouvernance des données B2B | Phase 0 : Fondation de données B2B | Application des politiques d’utilisation des données et du consentement dans les processus d’activation et de centralisation des données de compte B2B |

## Conditions préalables

Procédez comme suit avant de commencer l’implémentation.

- [ ] licence [!DNL AJO B2B Edition] configurée et activée sur le sandbox cible
- [ ] licence [!DNL RT-CDP B2B Edition] configurée et activée sur le sandbox cible
- [ ] système CRM ([!DNL Salesforce] ou [!DNL Microsoft Dynamics 365]) accessible avec les informations d’identification d’API appropriées pour la synchronisation bidirectionnelle des données
- [ ] instance [!DNL Marketo Engage] connectée (si [!DNL Marketo] est utilisée comme plateforme d’automatisation marketing) avec le connecteur source configuré
- [ ] schémas XDM B2B déployés : classes Compte, Personne, Opportunité, Campagne et Membre de la campagne avec les groupes de champs obligatoires
- [ ] les données de compte et de personne ingérées dans AEP avec des relations de personne à compte résolues
- [ ] canal e-mail configuré : sous-domaine délégué, groupe d’adresses IP préchauffé et surface de canal créée pour l’envoi d’e-mails B2B
- [ ] fournisseur SMS configuré (si le canal SMS est utilisé dans les parcours de compte) : [!DNL Sinch], [!DNL Twilio] ou informations d’identification [!DNL Infobip] configurées
- [ ] équipe commerciale a intégré le composant Informations sur les ventes de CRM (package [!DNL Salesforce] AppExchange ou solution [!DNL Dynamics] installée).
- [ ] Préparation des ressources de contenu : modèles d’e-mail B2B, thèmes de marque et fragments visuels pour les e-mails d’alerte relatifs aux cultures et aux ventes
- [ ] taxonomie des centres d’intérêt de la solution définie : liste des produits/services auxquels des groupes d’achat seront associés
- [ ] Modèles de rôle de groupe d’achat conçus : rôles et rôles requis pour chaque intérêt de solution (par exemple, acheteur économique, évaluateur technique, champion).

## Options de mise en œuvre

Cette section décrit les approches de mise en œuvre disponibles, chacune adaptée aux différents besoins et niveaux de maturité de l’entreprise.

### Option A : Intérêt pour une solution unique avec parcours de compte linéaire

**Idéal pour :** les organisations qui débutent dans la gestion des groupes d’achats et qui souhaitent commencer par une seule gamme de produits ou offre de solution, valider l’approche et effectuer une itération avant de passer à la solution répondant à plusieurs intérêts.

**Fonctionnement :**

Cette approche se concentre sur un seul intérêt de solution (un produit ou service) avec un modèle de groupe d’achat. Un parcours de compte linéaire est conçu avec des étapes séquentielles : identification du compte, formation du groupe d’achat, engagement de l’élève, seuil de score de l’engagement et transfert des ventes. Le parcours suit un chemin simple sans embranchement complexe ni pistes parallèles.

Les prospects sont qualifiés pour les rôles de groupe d’achat lorsqu’ils sont ingérés à partir du CRM ou de l’[!DNL Marketo Engage]. Le parcours de compte envoie des e-mails d’éducation aux rôles sous-engagés, surveille les scores d’engagement et déclenche une alerte commerciale lorsque le groupe d’achat atteint un seuil d’exhaustivité et d’engagement défini. Cette approche fournit une preuve de concept claire et mesurable avant d’introduire de la complexité.

**Considérations principales :**

- Implémentation et validation plus simples, ce qui le rend adapté à un premier déploiement
- Limité à un mouvement d’achat de produit/service à la fois
- La structure linéaire du parcours peut ne pas s&#39;adapter à des cycles d&#39;achat complexes à plusieurs étapes

**Avantages :**

- Retour sur investissement le plus rapide avec une complexité de configuration minimale
- Effacer les mesures de succès liées à un seul intérêt de solution
- Plus facile à expliquer et à obtenir l’adhésion de l’entreprise
- Rapports simples et mesure des KPI

**Limitations :**

- Ne traite pas des ventes croisées ou des scénarios multiproduits
- Les comptes intéressés par plusieurs solutions nécessitent des parcours distincts et non coordonnés
- Peut ne pas exploiter pleinement les capacités de gestion du groupe d&#39;achat

**Experience League:**

- [Présentation d’AJO B2B edition](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/guide-overview)
- [Créer des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)

### Option B : intérêts multiples de la solution avec des parcours de compte de branchement

**Idéal pour :** les organisations qui disposent de plusieurs gammes de produits ou offres de services et qui doivent gérer des groupes d’achat distincts par intérêt de solution, avec des parcours de compte qui se fondent sur les intérêts de solution actifs et sur l’avancement du processus de qualification de chaque groupe d’achat.

**Fonctionnement :**

Plusieurs intérêts de solution sont définis, chacun ayant son propre modèle de rôle de groupe d&#39;achat. Un parcours de compte commence par l’identification du compte et évalue les intérêts de la solution à appliquer à chaque compte en fonction des signaux comportementaux, des données micrographiques ou de l’intention explicite. Les branches de parcours pour répondre à chaque intérêt de solution actif, exécutant des suivis parallèles pour différents groupes d&#39;achat au sein du même compte.

La notation de l’engagement fonctionne indépendamment par groupe d’achats, ce qui permet à un groupe d’achats d’atteindre la préparation aux ventes tandis qu’un autre est toujours en cours de développement. Les alertes de ventes sont configurées en fonction des intérêts de la solution. L’équipe de vente ou le spécialiste concerné est donc averti lorsqu’un groupe d’achat spécifique se qualifie. Les informations CRM font apparaître tous les groupes d’achats actifs pour un compte, ce qui donne aux ventes une vue holistique.

**Considérations principales :**

- Nécessite une taxonomie des intérêts de la solution bien définie et des modèles de groupe d&#39;achat distincts
- La complexité du parcours augmente avec chaque intérêt supplémentaire pour la solution
- La coordination entre les groupes d&#39;achat (par exemple, les contacts partagés qui détiennent des rôles dans plusieurs groupes d&#39;achat) doit être planifiée

**Avantages :**

- Prend en charge les stratégies de compte multiproduit et de vente croisée
- Une notation indépendante par groupe d&#39;acheteurs offre une visibilité granulaire sur le pipeline
- Les équipes commerciales reçoivent des alertes ciblées par intérêt de solution
- Optimise les fonctionnalités de gestion des groupes d&#39;achat [!DNL AJO B2B Edition]

**Limitations :**

- Une implémentation plus complexe et un déploiement plus long
- Ressources de contenu supplémentaires requises (pistes d’e-mail distinctes par intérêt de solution)
- La création de rapports est plus complexe avec plusieurs groupes d’achats par compte
- Risque de messages excessifs envoyés à des contacts appartenant à plusieurs groupes d&#39;achat (nécessite une gestion des fréquences)

**Experience League:**

- [Centres d’intérêt des solutions](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Parcours de compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)

### Option C : qualification de compte assistée par IA avec progression automatisée du parcours

**Idéal pour :** les entreprises B2B matures disposant de données historiques importantes qui souhaitent utiliser des agents de qualification de compte optimisés par l’IA pour automatiser l’évaluation du niveau de préparation du compte, réduire l’effort de qualification manuel et ajuster dynamiquement les chemins de parcours en fonction des scores de préparation générés par l’IA.

**Fonctionnement :**

Cette approche s’appuie sur les intérêts multi-solutions de l’option B, mais ajoute la qualification de compte optimisée par l’IA pour automatiser la transition entre les étapes de parcours. Au lieu de se fier uniquement à des seuils de score d’engagement basés sur des règles, l’agent de qualification de l’IA évalue le niveau de préparation du compte à l’aide d’un ensemble plus large de signaux : exhaustivité du groupe d’achat, vitesse d’engagement, adéquation thermographique, modèles de conversion historiques et données d’intention.

Les parcours de compte utilisent la sortie de qualification de l’IA pour déterminer les étapes suivantes : les comptes présentant un degré de préparation élevé font l’objet d’un suivi rapide vers des alertes de ventes, les comptes de niveau intermédiaire bénéficient d’une attention accrue et les comptes à faible niveau de préparation sont placés dans des suivis de sensibilisation à long terme. L’agent d’IA réévalue continuellement à mesure que de nouvelles données d’engagement arrivent, permettant une progression dynamique du parcours sans intervention manuelle.

**Considérations principales :**

- Nécessite suffisamment de données historiques pour entraîner des modèles de qualification efficaces
- Les sorties de l’IA doivent être validées par rapport aux résultats réels du pipeline avant le déploiement complet.
- Se combine bien avec [!DNL CJA B2B Edition] pour analyser la précision de qualification et la corrélation de pipeline

**Avantages :**

- Réduit les efforts de qualification manuels et élimine les transferts arbitraires basés sur des seuils
- S’adapte de manière dynamique aux changements de comportement des comptes et de schémas d’engagement
- Une qualité de pipeline plus élevée en incorporant plusieurs signaux au-delà des simples scores d’engagement
- Une réévaluation continue empêche le blocage des comptes à des étapes de parcours incorrectes

**Limitations :**

- Nécessite des données de conversion historiques pour une formation IA significative
- Les décisions de qualification « boîte noire » peuvent être plus difficiles à comprendre et à faire confiance aux équipes commerciales au début
- Plus complexe à résoudre lorsque les comptes sont qualifiés de manière inattendue ou pas du tout
- Dépendance de la qualité et de l&#39;exhaustivité des données sur tous les signaux d&#39;entrée

**Experience League:**

- [Qualification du compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Assistant AI dans AJO B2B](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/guide-overview)

### Comparaison des options

| Critères | Option A : intérêt unique pour une solution | Option B : Intérêts multiples de la solution | Option C : qualification assistée par l’IA |
| --- | --- | --- | --- |
| Idéal pour | Premier déploiement, une seule gamme de produits | Organisations multiproduits | Organisations matures avec des données historiques |
| Complexité | Faible | Medium-Grand | Élevée |
| Délai de valorisation | 2-4 semaines | 4-8 semaines | 6-12 semaines |
| Centres d’intérêt des solutions | 1 | Multiple | Multiple |
| structure du parcours | Linéaire | Branchement, pistes parallèles | Progression dynamique pilotée par l’IA |
| Approche de notation | Seuils basés sur des règles | Basé sur des règles par groupe d&#39;achat | Qualification et règles optimisées par l’IA |
| Exigences de contenu | Minimale (une piste de maturation) | Élevé (par intérêt de solution) | Sélection de contenu dynamique + élevée |
| Alignement des ventes | Workflow d’alerte unique | Alertes par solution-intérêts | Alertes hiérarchisées et notées par l’IA |
| Requiert | Base des données B2B de base | Une taxonomie de solution bien définie | Données de conversion historiques + taxonomie |

### Choisir la bonne option

Commencez par répondre aux questions suivantes pour déterminer la meilleure approche d’implémentation :

1. **Combien de produits ou de services distincts ont des comités d&#39;achat indépendants ?** Si la réponse est une (ou si l’organisation souhaite d’abord prouver le concept), commencez par l’option A. S’il y en a plusieurs, passez à la question 2.

2. **Existe-t-il suffisamment de données historiques sur les affaires gagnées/perdues, la composition du comité d’achat et les schémas d’engagement ?** Si oui, et que l&#39;entreprise souhaite minimiser la qualification manuelle, l&#39;option C offre l&#39;approche la plus automatisée. Si ce n’est pas le cas, l’option B fournit une prise en charge multi-solution avec une notation basée sur des règles.

3. **Quelle est la capacité de l&#39;organisation en matière de gestion du changement ?** Les options B et C nécessitent une plus grande harmonisation organisationnelle (production de contenu, activation des ventes, coordination transversale). Si la capacité est limitée, commencez par l’option A et développez.

Un chemin de progression commun consiste à commencer par l’option A pour prouver le concept avec un intérêt pour la solution, à passer à l’option B en ajoutant les intérêts de la solution à mesure que la confiance augmente, puis à ajouter une couche dans la qualification IA de l’option C une fois que suffisamment de données historiques sont disponibles pour entraîner efficacement les modèles.

## Phases de mise en œuvre

Les phases suivantes décrivent le processus d’implémentation étape par étape pour ce modèle de cas d’utilisation.

### Phase 0 : base de données B2B

**Fonctions d’application :** [!DNL RT-CDP B2B] : unification des profils de compte, résolution d’identité B2B, intégration [!DNL Marketo Engage], gouvernance des données B2B, évaluation de l’audience du compte

Cette phase établit l’infrastructure de données B2B en [!DNL RT-CDP B2B Edition]. Vous unifierez les données de compte du CRM, de l’automatisation du marketing et d’autres sources en un seul profil de compte, résoudrez les relations personne-compte, configurerez la gouvernance des données B2B et créerez des audiences au niveau du compte qui alimenteront la gestion des groupes d’achats [!DNL AJO B2B Edition].

#### Décision : stratégie de source de données B2B

Quels systèmes servent de sources principales pour les données de compte, de personne et d’engagement ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| [!DNL Marketo Engage] comme source principale | [!DNL Marketo] est la plateforme d’automatisation du marketing de l’entreprise avec un riche historique d’engagement | Le connecteur bidirectionnel natif simplifie la configuration ; les flux de données d’engagement sont automatiques ; les relations personne à compte sont héritées de [!DNL Marketo] |
| CRM ([!DNL Salesforce]/[!DNL Dynamics]) comme source principale | Le CRM est le système d’enregistrement des comptes et des contacts ; [!DNL Marketo] n’est pas utilisé | Nécessite une configuration du connecteur source CRM ; les données d’engagement peuvent nécessiter des sources supplémentaires ; les relations personne à compte des associations compte-contact CRM |
| Hybride : CRM pour les comptes et [!DNL Marketo] pour l’engagement | Le CRM possède les données principales du compte/contact tandis que [!DNL Marketo] capture l’engagement comportemental | Modèle le plus courant pour les organisations qui utilisent les deux. Nécessite une résolution d’identité minutieuse pour lier les personnes [!DNL Marketo] aux contacts CRM |

#### Décision : stratégie de l’audience du compte

Comment les audiences de compte doivent-elles être définies pour l’entrée de parcours ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Audiences de compte basées sur des graphiques | Comptes cibles basés sur le secteur, la taille de l’entreprise, le niveau de chiffre d’affaires ou la zone géographique | Idéal pour les listes de cibles ABM ; ne nécessite pas de données d’engagement ; peut être étendu |
| Audiences de compte basées sur l’engagement | Comptes cibles sur lesquels les utilisateurs ont indiqué des signaux d’intention comportementale | Nécessite le flux des données d’engagement ; un ciblage plus précis ; peut ne pas tenir compte des comptes avec un intérêt latent |
| Combinaison de données démographiques + engagement | Comptes cibles correspondant au profil client idéal ET affichant l’engagement | La plus précise : nécessite les deux types de données. Recommandé pour la génération de pipeline qualifiée. |

**Navigation dans l’interface utilisateur :** Platform > Sources > Catalogue > Sélectionner la source ([!DNL Marketo Engage], [!DNL Salesforce], etc.) > Configurer le flux de données

**Détails de configuration clés :**

- Configurez des schémas XDM B2B pour chaque entité B2B (compte, personne, opportunité, campagne, membre de la campagne) avec les groupes de champs obligatoires
- Configurez les connecteurs source pour CRM et/ou [!DNL Marketo Engage] avec une planification appropriée (généralement des intervalles d’1 à 4 heures pour les données B2B).
- Configurer des espaces de noms d’identité pour les identifiants B2B (ID de personne [!DNL Marketo], ID de lead SFDC, ID de contact SFDC, ID de compte)
- Activer la résolution d’identité B2B pour lier des personnes à des comptes
- Créez des audiences au niveau du compte à l’aide de la fonctionnalité Audiences du compte dans [!DNL RT-CDP]

**Documentation Experience League :**

- [Présentation de RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Schémas B2B dans Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Connecteur source Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Résolution des identités B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)

### Phase 1 : intérêt pour la solution et configuration du groupe d&#39;achat

**Fonctions d&#39;application :** [!DNL AJO B2B] : Configuration de l&#39;intérêt de la solution, Gestion des groupes d&#39;achat

Cette phase définit les centres d&#39;intérêt de la solution (produits/services) et les modèles de groupe d&#39;achat qui constituent le cœur du modèle de gestion du groupe d&#39;achat. Vous allez créer des centres d&#39;intérêt pour la solution, définir des modèles de rôle avec des exigences personnelles et configurer la manière dont les prospects sont qualifiés en rôles de groupe d&#39;achat.

#### Décision : granularité des intérêts de la solution

À quel niveau les intérêts de la solution doivent-ils être définis ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Centres d’intérêt des solutions au niveau des produits | Chaque produit a son propre groupe d&#39;achat | Plus granulaire ; active des modèles de groupes d&#39;achats spécifiques à un produit ; peut entraîner de nombreux groupes d&#39;achats par compte |
| Centres d’intérêt au niveau de la catégorie de solution | Regroupez les produits associés dans des catégories de solutions (par exemple, « Marketing Cloud » au lieu de produits individuels). | Gestion simplifiée ; moins de groupes d’achats ; les rôles peuvent être plus génériques ; recommandé pour les déploiements initiaux. |
| Centres d’intérêt au niveau du cas d’utilisation | Définissez les intérêts autour des résultats commerciaux plutôt que des produits (par exemple, la « transformation numérique »). | S&#39;aligne sur la vente consultative ; les rôles des groupes d&#39;achat peuvent couvrir plusieurs produits ; il est plus difficile de mapper les étapes du pipeline CRM |

#### Décision : conception de modèle de rôle de groupe d&#39;achat

Comment les rôles devraient-ils être définis au sein de chaque groupe d&#39;achat ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Modèle de rôle standard | Utiliser un ensemble commun de rôles pour tous les intérêts de solution (par exemple, acheteur économique, évaluateur technique, champion, utilisateur final) | Notation et qualification cohérentes ; gestion plus facile ; possibilité de ne pas capturer les rôles spécifiques à la solution |
| Modèles de rôle spécifiques à une solution | Définir des rôles uniques par intérêt de solution en fonction du comité d’achat réel pour ce produit | Qualification plus précise ; nécessite une connaissance plus approfondie de chaque processus d&#39;achat ; une maintenance plus élevée |
| Modèles de rôle hiérarchisé | Définir les rôles requis (obligatoires pour la qualification) et les rôles facultatifs (améliorer l’exhaustivité, mais pas obligatoires) | Équilibre précision et flexibilité ; empêche les critères de qualification trop stricts de bloquer le pipeline. |

**Navigation dans l’interface utilisateur :** [!DNL AJO B2B Edition] > Groupes d’achat > Centres d’intérêt des solutions > Créer un centre d’intérêt des solutions

**Navigation dans l’interface utilisateur :** [!DNL AJO B2B Edition] > Groupes d’achat > Modèles de rôle > Créer un modèle de rôle

**Détails de configuration clés :**

- Définissez le centre d’intérêt de chaque solution avec un nom, une description et le résultat commercial auquel elle s’adresse
- Créez des modèles de rôle spécifiant les rôles requis pour chaque groupe d’achat (par exemple, « Décideur », « Influenceur », « Praticien », « Partenaire exécutif »).
- Configurez les critères de qualification de prospect à rôle : comment le système détermine à quelle persona un prospect correspond (en fonction du titre de la fonction, du service, de l’ancienneté ou des attributs personnalisés)
- Définir des seuils d&#39;exhaustivité : définir le pourcentage de rôles à remplir pour qu&#39;un groupe d&#39;achats soit considéré comme « terminé »
- Lier les intérêts de la solution aux audiences du compte ou aux attributs du compte qui indiquent un intérêt potentiel

**Là où les options divergent :**

**Pour L’Option A (Intérêt Pour Une Solution Unique) :**
Créez un centre d’intérêt pour la solution et un modèle de rôle. Insistez sur un mouvement d&#39;achat clair et bien compris pour le produit ou le service principal de l&#39;organisation.

**Pour L’Option B (Intérêts Multiples De La Solution) :**
Créez plusieurs centres d’intérêt de solution, chacun ayant son propre modèle de rôle. Mappez chaque intérêt de solution au type de produit/opportunité CRM approprié pour le suivi du pipeline en aval.

**Pour l’option C (qualification assistée par l’IA) :**
Configurez les intérêts de la solution et les modèles de rôle comme dans l’option B, mais configurez également l’agent de qualification de l’IA avec des données historiques sur les compositions de groupes d’achats réussies et les résultats des affaires pour entraîner le modèle de qualification.

**Documentation Experience League :**

- [Présentation des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Centres d’intérêt des solutions](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Modèles de rôle](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Créer des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)

### Phase 2 : qualification du lead et score de l’engagement

**Fonctions de l’application :** [!DNL AJO B2B] : score de l’engagement, qualification du compte

Cette phase configure le modèle de notation de l&#39;engagement qui mesure l&#39;engagement au niveau de la personne au sein des groupes d&#39;achats et le cumule avec les scores de préparation au niveau du groupe d&#39;achats et du compte. Vous configurerez les règles de notation, définissez les seuils d’engagement pour la qualification et activez éventuellement la qualification de compte optimisée par l’IA.

#### Décision : modèle de notation de l’engagement

Comment l’engagement doit-il être noté au niveau de la personne et du groupe d’achat ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Score basé sur les activités | Attribuez des valeurs de point à des actions spécifiques (ouverture d’e-mail = 5 pts, téléchargement de contenu = 15 pts, requête de démonstration = 50 pts). | Transparent et facile à régler ; nécessite une maintenance continue à mesure que le contenu et les canaux changent ; plus familier aux utilisateurs [!DNL Marketo] |
| Score pondéré par la récence | Pondération des activités récentes plus élevées que les activités plus anciennes (modèle de score décroissant) | Reflète mieux l’intention actuelle ; empêche les scores élevés obsolètes de gonfler la qualification ; est plus complexe à configurer. |
| Score optimisé par l’IA | Utilisez l’agent de qualification [!DNL AJO B2B] AI pour générer des scores de préparation en fonction de la reconnaissance des motifs | Plus sophistiqué ; s&#39;adapte automatiquement ; nécessite des données historiques ; peut être opaque au départ pour les équipes commerciales |

#### Décision : approche du seuil de qualification

Quand un groupe d&#39;achat doit-il être considéré comme prêt pour la remise des ventes ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Seuil de score uniquement | Qualification du groupe d&#39;achat lorsque le score d&#39;engagement total dépasse une valeur définie | Mise en œuvre simple : le seuil de score peut nécessiter un ajustement au fil du temps ; ne prend pas en compte la composition des rôles |
| Exhaustivité + seuil de score | Le groupe d&#39;achat se qualifie lorsque la couverture de rôle minimale ET le seuil de score sont tous deux atteints | Qualification plus robuste ; empêche le transfert de groupes d&#39;achat avec des scores élevés mais des rôles clés manquants |
| Préparation déterminée par l’IA | L’agent de qualification AI détermine le niveau de préparation en utilisant plusieurs signaux au-delà du score et de l’exhaustivité | Plus sophistiqué ; tient compte de la vitesse d&#39;achat, des signaux concurrentiels et des tendances historiques ; Option C uniquement |

**Navigation dans l’interface utilisateur :** [!DNL AJO B2B Edition] > Groupes d’achat > Score de l’engagement > Configurer les règles de score

**Détails de configuration clés :**

- Définir des règles de score d’engagement : attribuez des valeurs de point aux événements comportementaux (ouvertures d’e-mails, clics, visites de pages web, téléchargements de contenu, envois de formulaires, participation à des webinaires, demandes de démonstration).
- Configurez l’atténuation de score ou la pondération de récence si vous utilisez la notation sensible à l’heure
- Définir l’agrégation des scores au niveau du groupe d’achat : méthode d’agrégation des scores des personnes en un score de groupe d’achat (somme, moyenne pondérée ou seuil minimum par rôle)
- Définir des seuils de qualification : les niveaux de score et d&#39;exhaustivité qui déclenchent la transition vers l&#39;étape d&#39;achat suivante
- Configurez l’agent de qualification de l’IA (option C) : entraînez-vous avec les données historiques de l’offre, définissez les signaux que l’agent doit prendre en compte et définissez des seuils de confiance

**Documentation Experience League :**

- [Score de l’engagement](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Étapes du groupe d’achat](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Qualification du compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)

### Phase 3 : conception et exécution du parcours de compte

**Fonctions d’application :** [!DNL AJO B2B] : Journey Orchestration de compte, création d’e-mails B2B, gestion des canaux SMS

Cette phase conçoit et déploie le parcours de compte qui orchestre l&#39;engagement avec les membres du groupe d&#39;achat. Vous allez créer des parcours de compte avec des conditions d’entrée, des nœuds d’action (e-mail, SMS), des branches de condition (en fonction de la phase de groupe d’achat, du score d’engagement, de la couverture des rôles), des étapes d’attente et des critères de sortie.

#### Décision : déclencheur d’entrée de Parcours

Quel événement ou condition provoque l’entrée d’un compte dans le parcours ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Qualification de l’audience du compte | Le compte entre lorsqu’il rejoint une audience de compte cible | Orienté lot ; adapté à l’entrée basée sur une liste ABM ; l’audience doit être prédéfinie |
| Événement de création de groupe d&#39;achat | Le compte entre lorsqu&#39;un groupe d&#39;achats est créé pour la première fois pour le compte | Piloté par les événements ; déclenché par la qualification du prospect dans un rôle de groupe d’achat ; plus en temps réel |
| Modification de l’attribut de compte | Le compte entre lorsqu’un attribut spécifique change (par exemple, la note d’intention, le niveau de compte) | Nécessite que l’attribut de déclenchement soit mis à jour en temps réel ou quasi réel |

#### Décision : mix de canaux pour la maturation B2B

Quels canaux le parcours de compte doit-il utiliser pour impliquer les membres du groupe d’achat ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| E-mail uniquement | La plupart des interactions B2B se produisent par e-mail ; il n’existe aucune infrastructure d’accord préalable SMS | Configuration la plus simple ; modèle B2B le plus courant ; contacts mobiles-first risquent de ne pas être présents |
| E-mail + SMS | L’entreprise dispose de l’accord préalable des contacts professionnels pour les SMS ; notifications de haute urgence garanties | SMS effectif pour les alertes urgentes (rappels d’événement, confirmations de réunion) ; nécessite la configuration du fournisseur de SMS. |
| E-mail + SMS + Alertes de ventes | Gamme complète : sensibilisation au marketing par e-mail/SMS plus notifications de l’équipe des ventes | La plus complète ; nécessite l’adoption par l’équipe commerciale du workflow d’alerte ; coordonne les points de contact marketing et commercial |

#### Décision : stratégie d’embranchement du Parcours

Comment la branche de parcours doit-elle se baser sur le statut du compte et du groupe d&#39;achat ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Branchement basé sur l’étape | Branche basée sur l’étape du groupe d’achat (par exemple, sensibilisation, considération, décision) | S’aligne sur les étapes funnel traditionnelles ; contenu mappé aux étapes ; effacer le chemin de progression |
| Embranchement basé sur les rôles | Branche pour envoyer un contenu différent à différents rôles de groupes d’achat (contenu technique aux évaluateurs, contenu de retour sur investissement aux acheteurs économiques) | Plus personnalisé ; nécessite des ressources de contenu spécifiques au rôle ; un effort de production de contenu plus élevé |
| Embranchement basé sur l’engagement | Branche basée sur les seuils de score d’engagement (faible engagement = réengagement, élevé = accélération) | Dynamique et réactif ; s’adapte au comportement réel et peut créer des arborescences ramifiées complexes |

**Navigation dans l’interface utilisateur** [!DNL AJO B2B Edition] > Parcours de compte > Créer un Parcours

**Détails de configuration clés :**

- Créer le canevas du parcours de compte avec la condition d’entrée sélectionnée
- Ajouter des nœuds de parcours de compte : actions e-mail, actions SMS, étapes d’attente, divisions de conditions et embranchement des chemins
- Créez du contenu d’e-mail B2B à l’aide du Designer d’e-mail B2B avec des thèmes de marque, des fragments visuels et la génération de contenu assistée par IA
- Configurez des jetons de personnalisation faisant référence aux attributs de compte, aux attributs de personne et aux données de groupe d’achat
- Définir des durées d’attente entre les points de contact (les parcours B2B utilisent généralement des attentes plus longues : 3 à 7 jours entre les e-mails)
- Définir les critères de sortie : conditions dans lesquelles les comptes quittent le parcours (le groupe d&#39;achat atteint le seuil de qualification, l&#39;opportunité créée dans CRM, l&#39;opt-out du compte)
- Configurer des actions SMS si vous utilisez le canal SMS (nécessite la configuration du fournisseur SMS et l’accord préalable du contact)
- Tester le parcours avec des comptes de test avant la publication

**Là où les options divergent :**

**Pour L’Option A (Intérêt Pour Une Solution Unique) :**
Concevez un parcours linéaire avec des étapes séquentielles. L&#39;entrée est basée sur une audience de compte unique ou un événement de création de groupe d&#39;achats. Un seul suivi de l’alimentation des e-mails avec une urgence et une profondeur de contenu croissantes.

**Pour L’Option B (Intérêts Multiples De La Solution) :**
Concevez un parcours avec des branches parallèles par intérêt de solution. Utilisez les nœuds de condition pour acheminer les comptes vers la piste d&#39;acquisition appropriée en fonction des groupes d&#39;achat existants. Chaque branche possède son propre contenu et ses propres seuils de notation.

**Pour l’option C (qualification assistée par l’IA) :**
Concevez un parcours dans lequel les nœuds de condition évaluent le score de qualification de l’IA plutôt que (ou en plus) des seuils basés sur des règles. Incluez la sélection dynamique de chemins d’accès où l’IA détermine s’il faut accélérer, maintenir ou modifier la priorité d’un compte.

**Documentation Experience League :**

- [Présentation des parcours de compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Nœuds de parcours de compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [Création d’e-mails B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [Canal SMS dans AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [Assistant AI pour la création d’e-mails](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Phase 4 : alignement des ventes et intégration CRM

**Fonctions d’application :** [!DNL AJO B2B] : configuration des alertes de ventes, informations commerciales CRM ; [!DNL RT-CDP B2B] : configuration de la destination du compte, Audience Activation du compte

Cette phase établit une passerelle entre le marketing et les ventes en configurant les e-mails d’alerte commerciale, en déployant CRM Sales Insights pour une visibilité in-CRM et en activant éventuellement les audiences de compte vers des destinations B2B ([!DNL LinkedIn], [!DNL Marketo], systèmes CRM).

#### Décision : stratégie de déclenchement d’alerte des ventes

Quand les ventes doivent-elles être informées du statut du groupe d&#39;achats d&#39;un compte ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Alertes basées sur des jalons | Informer les ventes lorsque le groupe d&#39;achat atteint des jalons spécifiques (qualifié, complet, engagement élevé) | Notifications claires et discrètes ; empêche la fatigue des alertes ; peut ne pas correspondre aux tendances d’engagement progressives |
| Alertes basées sur un seuil | Notifier les ventes lorsque le score d&#39;engagement dépasse un seuil défini | Surveillance continue ; peut déclencher plusieurs alertes lorsque les scores fluctuent près du seuil. |
| Alertes de transition d’étape | Notifier les ventes lors du passage d&#39;un groupe d&#39;achat à une nouvelle étape (par exemple, de la prise en compte à la décision) | S’aligne sur les étapes du pipeline ; signale le plus clairement pour les ventes ; nécessite des définitions d’étape bien définies. |

#### Décision : profondeur d’intégration du CRM

À quel niveau les données du groupe d’achat doivent-elles être affichées dans le CRM ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Alertes de ventes uniquement (pas de composant CRM) | L’entreprise n’utilise pas [!DNL Salesforce] ni [!DNL Dynamics], ou l’intégration CRM n’est pas possible | Effort d’intégration le plus faible ; les ventes reçoivent des notifications par e-mail, mais pas de tableau de bord CRM ; visibilité limitée |
| Tableau de bord CRM Sales Insights | L&#39;entreprise utilise [!DNL Salesforce] ou [!DNL Dynamics] et souhaite que le statut du groupe d&#39;achats soit visible dans le CRM | Nécessite d’installer le package Informations sur les ventes CRM ; fournit des informations complètes au niveau du compte ; recommandé pour la plupart des mises en œuvre. |
| Synchronisation CRM bidirectionnelle complète | Les étapes du groupe d&#39;achat et les scores réécrivent sur les objets CRM, ce qui influence le workflow et le reporting CRM | Complexité d’intégration maximale ; permet la création de rapports de pipeline native CRM ; nécessite une configuration CRM personnalisée. |

**Navigation dans l’interface utilisateur :** [!DNL AJO B2B Edition] > Administration > Configuration des alertes de ventes

**Navigation dans l’interface utilisateur :** [!DNL AJO B2B Edition] > Administration > Informations sur les ventes CRM > Configurer

**Détails de configuration clés :**

- Configurez les modèles d’e-mail d’alerte commerciale : inclure le statut du groupe d’achats, les personnes engagées, le score d’engagement et les actions suivantes recommandées
- Définissez les règles de routage des alertes : les représentants commerciaux ou les équipes qui reçoivent des alertes en fonction de la propriété du compte, du territoire ou de l’intérêt de la solution
- Installer et configurer CRM Sales Insights pour [!DNL Salesforce] ou [!DNL Dynamics 365]
- Mappez les données du groupe d&#39;achats aux objets CRM afin que les ventes puissent afficher la composition, l&#39;engagement et la progression du parcours du groupe d&#39;achats dans leur workflow CRM.
- Configurez éventuellement les connexions de destination de compte pour activer les audiences de compte vers [!DNL LinkedIn] (pour la publicité ABM), [!DNL Marketo Engage] (pour le suivi au niveau du prospect) ou d’autres destinations B2B

**Documentation Experience League :**

- [E-mails d’alerte commerciale](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [Informations sur les ventes CRM](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)
- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destination des audiences correspondantes LinkedIn](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/social/linkedin)

### Phase 5 : Création de rapports et optimisation

**Fonctions d’application :** [!DNL AJO B2B] : tableaux de bord B2B Analytics

Cette phase établit le cadre de reporting et d&#39;analyse pour mesurer le rendement des groupes d&#39;achats, l&#39;efficacité des parcours de comptes et l&#39;impact des pipelines. [!DNL AJO B2B Edition] fournit des tableaux de bord analytics intégrés ; [!DNL CJA B2B Edition] (sous licence) étend l’analyse avec des informations cross-canal plus précises au niveau du compte.

#### Décision : approche en matière de rapports

Quels outils d’analyse doivent être configurés pour le suivi continu des performances ?

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Tableaux de bord [!DNL AJO B2B] uniquement | Les tableaux de bord intégrés de [!DNL AJO B2B Edition] sont suffisants pour les mesures de groupe d’achats et de parcours | Configuration la plus rapide ; couvre les mesures B2B principales ; fonctionnalité d’analyse personnalisée limitée |
| [!DNL AJO B2B] des tableaux de bord + [!DNL CJA B2B Edition] | L’organisation a besoin d’une analyse cross-canal plus approfondie, d’une analyse de groupe d’achats, d’une corrélation des opportunités et d’une attribution personnalisée | Nécessite une licence [!DNL CJA B2B Edition] ; est le plus complet ; prend en charge l’analyse de structure libre au niveau du compte |
| Tableaux de bord [!DNL AJO B2B] et création de rapports CRM | L’entreprise préfère centraliser les rapports de pipeline dans le CRM parallèlement aux mesures de groupe d’achats | Nécessite le développement d’un tableau de bord CRM ; combine les mesures de marketing et de vente au même endroit ; limité aux fonctionnalités de reporting CRM |

**Navigation dans l’interface utilisateur :** [!DNL AJO B2B Edition] > Tableaux de bord > Présentation de l’engagement / Tableau de bord intelligent

**Détails de configuration clés :**

- Accédez au tableau de bord d’engagement [!DNL AJO B2B] pour surveiller les scores d’engagement du groupe d’achats, les taux d’exhaustivité et la répartition par étapes
- Accédez au tableau de bord intelligent pour obtenir des informations basées sur l’IA sur la préparation du compte et la qualité du pipeline
- Si vous utilisez [!DNL CJA B2B Edition] : configurez une connexion CJA basée sur un compte comprenant des jeux de données [!DNL AJO B2B], configurez une vue de données B2B avec des conteneurs Groupe d’achats et Compte et créez une analyse de l’espace de travail pour la progression du groupe d’achats, la corrélation des opportunités et l’attribution
- Définir la cadence de création de rapports : examens hebdomadaires des performances des groupes d’achats, analyse mensuelle de l’impact des pipelines, optimisation trimestrielle des programmes
- Créez des annotations pour les événements importants (lancements de campagne, actualisations de contenu, modifications du modèle de notation) afin de les corréler aux tendances de performances

**Documentation Experience League :**

- [Tableaux de bord B2B Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Tableau de bord de l’engagement](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Tableau de bord intelligent](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [Présentation de CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

## Considérations relatives à la mise en œuvre

Les sections suivantes couvrent les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage à garder à l’esprit lors de la mise en œuvre.

### Mécanismes de sécurisation et limites

- [!DNL AJO B2B Edition] limites de parcours de compte, y compris le nombre maximal de parcours simultanés et le nombre maximal de comptes par parcours, suivez les mécanismes de sécurisation de produit [!DNL AJO B2B Edition] : [mécanismes de sécurisation B2B d’AJO](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/guide-overview)
- [!DNL RT-CDP B2B Edition] prend en charge jusqu’à 50 classes de schéma B2B et suit les mécanismes de sécurisation standard des profils et de la segmentation, [mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- L’évaluation de l’audience du compte fonctionne sur des plannings par lots ; les mises à jour de l’audience du compte en temps réel ne sont pas prises en charge pour tous les types de segment [Mécanismes de sécurisation de segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- L’ingestion du connecteur source B2B a des intervalles de planification minimaux (généralement 15 minutes pour les [!DNL Marketo], ce qui varie pour les sources CRM) — [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- Les surfaces de canal e-mail sont limitées à 10 par type de canal par sandbox : [mécanismes de sécurisation &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Pièges courants

- **Définir un trop grand nombre de rôles par groupe d&#39;achat :** en spécifiant de manière excessive des rôles (par exemple en exigeant de 8 à 10 rôles distincts), il est presque impossible pour les groupes d&#39;achat d&#39;atteindre les seuils d&#39;exhaustivité. Commencez par 3 à 5 rôles essentiels et développez-les à mesure que le modèle mûrit.
- **Définir des seuils de score d’engagement trop élevés ou trop bas :** si les seuils sont trop élevés, aucun groupe d’achat n’est qualifié, ce qui affame le pipeline. Si elles sont trop basses, les comptes non qualifiés inondent les ventes. Commencez par l’analyse des données historiques (le cas échéant) et effectuez une itération en fonction des commentaires des ventes.
- **Ignorer la qualité de la résolution de compte à compte :** si les personnes ne sont pas correctement liées aux comptes, les groupes d’achats auront des membres manquants même lorsque les bonnes personnes sont engagées. Investissez dans la qualité de résolution d’identité avant de lancer les parcours de groupe d’achat.
- **Contacts qui envoient trop de messages dans plusieurs groupes d’achat :** un seul contact peut détenir des rôles dans plusieurs groupes d’achat (par exemple, un CTO qui est un évaluateur technique pour les achats de CRM et de Data Platform). Sans gestion des fréquences, cette personne reçoit des e-mails de chaque parcours actif. Implémentez des règles de fréquence sur plusieurs parcours.
- **Négliger l’activation des ventes :** les équipes commerciales doivent comprendre comment interpréter les données des groupes d’achats, les scores d’engagement et les alertes de ventes. Sans formation ni adoption, le transfert du marketing vers les ventes échoue, quelle que soit la qualité des données.
- **Traiter les parcours de compte comme les parcours de personne :** les parcours de compte fonctionnent au niveau du compte, envoyant des e-mails aux personnes appartenant aux groupes d’achat du compte. La conception du parcours doit tenir compte du fait que plusieurs personnes reçoivent des messages par exécution de nœud de compte, ce qui est fondamentalement différent des parcours de [!DNL AJO] au niveau de la personne.

### Bonnes pratiques

- **Commencez avec un intérêt de solution et développez** — Démontrez que le modèle fonctionne pour un mouvement d&#39;achat avant de passer à plusieurs intérêts de solution. Cela permet à l’équipe d’affiner les modèles de rôle, les modèles de notation et le contenu avant d’ajouter de la complexité.
- **Aligner les rôles des groupes d&#39;achats sur le processus de vente CRM** — Mappez les rôles des groupes d&#39;achats aux personnes déjà reconnues par l&#39;équipe des ventes. Utiliser la même langue (acheteur économique, champion, etc.) la remise est donc intuitive.
- **Mettre en œuvre une boucle de commentaires sur les ventes** — Recueillez régulièrement des commentaires sur la qualité des comptes qualifiés pour le marketing. Utilisez ces commentaires pour ajuster les seuils de notation de l’engagement et les critères de qualification des rôles.
- **Concevoir du contenu pour les rôles, pas seulement pour les étapes** — Les différents rôles des groupes d&#39;achats ont besoin de contenu différent : les cadres veulent un retour sur investissement et un impact stratégique, les évaluateurs techniques veulent des détails sur l&#39;architecture et l&#39;intégration, les utilisateurs finaux veulent des démonstrations faciles à utiliser. Mappez les ressources de contenu aux rôles pour une conservation plus efficace.
- **Configurer CRM Sales Insights à l’avance** — N’attendez pas que le parcours complet soit en ligne pour déployer la visibilité CRM. Les équipes commerciales ont besoin de voir les données des groupes d’achats se former rapidement pour fournir des commentaires sur la précision des rôles et le ciblage des comptes.
- **Utiliser les étapes d’attente de manière stratégique** — Les cycles d’achat B2B sont longs. Les étapes d’attente du parcours de compte doivent refléter cette réalité (intervalles de 5 à 14 jours entre les contacts) plutôt qu’une urgence de type client (1 à 3 jours).
- **Surveillez la vitesse d’engagement, pas seulement le score d’engagement** — Un groupe d’achats qui passe d’un score de 20 à 80 en deux semaines signale une intention plus forte qu’un groupe qui atteint un score de 80 sur six mois. Configurez la notation et la qualification pour tenir compte de la vitesse.

### Décisions de compromis

Les compromis suivants doivent être évalués en fonction des besoins spécifiques de votre entreprise.

#### Exhaustivité du groupe d’achat par rapport au volume du pipeline

Le fait d&#39;exiger que tous les rôles soient remplis avant de qualifier un groupe d&#39;achat maximise la qualité du pipeline, mais peut fortement limiter le volume de comptes qualifiés, en particulier pour les nouveaux produits ou marchés où la base de données de l&#39;organisation a une couverture limitée.

- **Un seuil d’exhaustivité plus élevé favorise :** qualité du pipeline ; les ventes reçoivent des groupes d’achat entièrement formés ; taux de gain plus élevés par compte
- **Seuil d’exhaustivité inférieur favorisé :** volume de pipeline ; plus de comptes atteignent les ventes ; couverture plus large ; volume plus élevé, mais qualité potentiellement inférieure.
- **Recommandation :** commencez par un seuil modéré (60 à 70 % de couverture des rôles) et ajustez-le en fonction des données réelles sur le taux de gain. Pour les marchés établis avec une bonne couverture de données, augmentez votre taux vers plus de 80 %. Pour les nouveaux marchés, acceptez 50 à 60 % au départ et utilisez les campagnes d&#39;exhaustivité du groupe d&#39;achat pour combler les lacunes.

#### Granularité du score par rapport à la simplicité opérationnelle

Les modèles de notation très granulaires (avec des dizaines de types d’activité, une pondération de récence et une notation spécifique au rôle) fournissent des signaux de qualification plus précis, mais sont plus difficiles à gérer, à expliquer et à résoudre.

- **Une granularité plus élevée favorise :** précision de qualification ; différenciation nuancée entre les comptes ; meilleur alignement avec les processus d’achat complexes
- **Une granularité plus faible favorise :** simplicité opérationnelle ; gestion et explication plus faciles des ventes ; implémentation plus rapide ; moins de cas de figure
- **Recommandation :** commencez avec un modèle de notation simple (10 à 15 types d’activités, valeurs de point uniformes) et ajoutez de la complexité uniquement lorsque le modèle simple ne parvient pas à différencier la qualité du compte. Documentez minutieusement le modèle de notation pour l’alignement des ventes.

#### Parcours unique vs parcours spécialisés multiples

Un parcours de compte unique et complet qui gère toutes les étapes et les intérêts des solutions dans une zone de travail offre un contrôle unifié, mais peut devenir difficile à manier. Plusieurs parcours spécialisés (un par étape ou intérêt de solution) sont plus simples individuellement, mais plus difficiles à coordonner.

- **Le parcours unique favorise :** une vision holistique ; un timing et un message plus cohérents ; un suivi plus simple ; un emplacement pour toute logique
- **Les parcours multiples favorisent :** la modularité ; plus facile de mettre à jour une étape sans affecter les autres ; différentes équipes peuvent posséder différents parcours ; conception de la zone de travail plus propre
- **Recommandation** pour l’option A, un parcours unique est approprié. Pour les options B et C, utilisez un parcours principal d’« orchestration » qui achemine les comptes vers des sous-parcours spécialisés par intérêt de solution ou étape d’achat.

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les applications et fonctionnalités référencées dans ce guide.

### [!DNL AJO B2B Edition]

- [Accueil de la documentation d’AJO B2B edition](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/guide-overview)
- [Présentation des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Centres d’intérêt des solutions](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Modèles de rôle](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Créer des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [Étapes du groupe d’achat](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Présentation des parcours de compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Nœuds de parcours de compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [E-mails d’alerte commerciale](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [Informations sur les ventes CRM](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### E-mail et contenu B2B

- [Création d’e-mails B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [Création de SMS dans AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [Assistant AI pour la création d’e-mails](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Analyses et tableaux de bord B2B

- [Tableau de bord des groupes d&#39;achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Tableau de bord de l’engagement](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Tableau de bord intelligent](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [Présentation de CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [Présentation de RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Schémas B2B dans Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Connecteur source Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### Base des données

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home)
- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Configuration des canaux

- [Prise en main de la configuration du canal e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configurer le canal SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Gouvernance et confidentialité des données

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Destinations

- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Destination des audiences correspondantes LinkedIn](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/social/linkedin)

### Garde-fous

- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Mécanismes de sécurisation de Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Tutoriels et prise en main

- [Prise en main d’AJO B2B edition](https://experienceleague.adobe.com/fr/docs/journey-optimizer-b2b/user/guide-overview)
- [Tutoriel sur RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
