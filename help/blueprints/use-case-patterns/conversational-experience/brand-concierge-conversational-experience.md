---
title: Expérience de conversation Brand Concierge
description: Découvrez comment transformer les propriétés numériques en expériences de conversation optimisées par l’IA et sécurisées par la marque qui guident la découverte des clients.
solution: Experience Platform, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7239'
ht-degree: 0%

---


# Expérience de conversation Brand Concierge

Ce guide fournit une référence d’implémentation complète pour les expériences de conversation optimisées par l’IA utilisant [!DNL Adobe Brand Concierge], intégré à [!DNL Adobe Experience Platform] (AEP) et [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]). Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin de déployer des agents de conversation sécurisés par la marque sur des propriétés numériques.

Il couvre toutes les approches viables pour déployer des expériences de conversation, des chatbots de conseil sur les produits aux assistants de navigation de site complets, avec des conseils sur le moment de choisir chaque option. Le plan traite de la configuration des agents, de la gouvernance de marque, de l’intégration de contenu, des stratégies de déploiement, de l’enrichissement des profils à partir des signaux de conversation et de l’optimisation des analyses.

[!DNL Brand Concierge] permet aux marques de déployer des agents conversationnels intelligents qui comprennent la voix de la marque, d&#39;accéder à des catalogues de produits et à du contenu approuvés, de fournir des recommandations personnalisées basées sur des données de profil en temps réel et de capturer des signaux d&#39;intention et de sentiment dans le profil client unifié. Le résultat est une expérience de conversation qui semble naturelle et sur la marque tout en enrichissant la compréhension de chaque client par l&#39;organisation.

## Présentation du cas d’utilisation

Les entreprises cherchent de plus en plus à transformer les expériences digitales statiques en conversations dynamiques basées sur l’IA qui guident les clients tout au long de la découverte, de la sélection de produits et des décisions d’achat. [!DNL Adobe Brand Concierge] Pour résoudre ce problème, fournit une couche d’IA conversationnelle orchestrée qui se trouve au-dessus des propriétés numériques existantes, optimisées par AEP Agent Orchestrator.

Ce modèle se distingue des implémentations de chatbot traditionnelles, car il est nativement intégré au profil unifié d’AEP, utilise des mécanismes de sécurisation de la gouvernance de marque pour s’assurer que chaque réponse s’aligne sur les normes de la marque et renvoie des signaux de conversation à la plateforme de données client pour la personnalisation et l’activation en aval.

Le public cible comprend des équipes d’expérience digitale, des gestionnaires d’e-commerce, des stratèges de contenu et des technologues marketing qui doivent déployer des expériences de conversation intelligentes qui stimulent l’engagement, la conversion et l’enrichissement des profils.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Offrir des expériences personnalisées aux clients

Adaptez le contenu, les offres et les messages aux préférences, aux comportements et à l’étape du cycle de vie des individus.

**KPI :** engagement, taux de conversion, satisfaction de la clientèle (CSAT)

[En savoir plus sur la diffusion d’expériences client personnalisées](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### Améliorer l’engagement client

Augmentez la fréquence et la profondeur des interactions sur tous les points de contact numériques et physiques.

**KPI :** Engagement, Temps passé sur la page (web), Taux d’ouverture

[En savoir plus sur l’amélioration de l’engagement client](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### Augmentation des taux de conversion

Améliorez le pourcentage de visiteurs et de prospects qui effectuent les actions souhaitées telles que les achats, les inscriptions ou les envois de formulaire.

**KPI :** taux de conversion, conversion de lead, coût par lead

[En savoir plus sur l’augmentation des taux de conversion](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### Acquérir de nouveaux clients

Étendez votre base de clients grâce à des campagnes d’acquisition ciblées, des audiences semblables et l’optimisation des médias achetés.

**KPI :** % de montée en gamme/ventes croisées, chiffre d’affaires incrémentiel, valeur durée de vie du client

[En savoir plus sur l’acquisition de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont ce modèle peut être appliqué dans la pratique.

- **Assistant de découverte de produits** — Déployez un agent conversationnel sur les pages de liste des produits qui pose des questions de qualification et limite les recommandations de produits en fonction des besoins, des préférences et du budget des clients
- **Conseiller en comparaison guidé** — Aidez les clients à comparer les produits côte à côte grâce à un dialogue naturel, en mettant en évidence les différences pertinentes par rapport à leurs priorités déclarées
- **Concierge taille et ajustement** — Guidez les acheteurs de vêtements ou de chaussures en sélectionnant leur taille à l&#39;aide de questions-réponses conversationnelles, en réduisant les retours et en augmentant la confiance d&#39;achat
- **Sélecteur d’abonnement ou de formule** : guide les clients à travers les options de niveau de service ou de formule d’abonnement avec des recommandations personnalisées basées sur les schémas d’utilisation et les besoins déclarés
- **Assistant de navigation de site** — Aidez les visiteurs à trouver du contenu, des ressources d’assistance ou des catégories de produits pertinents en fonction de l’intention déclarée, ce qui réduit les taux de rebond sur les sites complexes
- **Consultation avant l&#39;achat** — Fournissez des conseils d&#39;achat à haute considération (par exemple, produits électroniques, produits financiers, assurance) par le biais de conversations à plusieurs tours qui permettent d&#39;élaborer une recommandation
- **Concierge du programme de fidélité** — Aidez les membres du programme de fidélité à découvrir les récompenses, à comprendre les avantages de niveau et à trouver des opportunités de rachat grâce à une interaction conversationnelle
- **Conversation de réengagement** — Lancez une conversation proactive avec les visiteurs récurrents en fonction de l’historique de navigation précédent ou des éléments de panier abandonnés
- **Escalade de l’agent en direct avec contexte** - Transmettez facilement les demandes complexes aux agents commerciaux ou de support en direct tout en préservant le contexte de conversation complet et les données de profil client
- **Assistance après achat et montée en gamme** — Contactez les clients après achat avec une assistance à la configuration, des suggestions de produits complémentaires et des bilans de satisfaction par le biais de canaux de conversation

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Taux d’engagement des conversations | Pourcentage de visiteurs et visiteuses qui engagent et soutiennent une conversation | Conversations lancées / pages vues éligibles |
| Taux d’achèvement de la conversation | Pourcentage de conversations qui parviennent à une résolution significative | Conversations terminées / conversations démarrées |
| Taux de conversion de conversation | Pourcentage de conversations qui mènent à une action souhaitée (achat, inscription, formulaire de prospect) | Conversions de la conversation / total des conversations |
| Profondeur de conversation moyenne | Nombre de tours par conversation, indiquant la qualité de l’engagement | Nombre moyen de messages par session |
| Satisfaction du client (CSAT) | Score de satisfaction post-conversation à partir du retour d’expérience | Réponses à un questionnaire ou notes pouces vers le haut/bas |
| Taux d’acceptation des recommandations | Pourcentage de recommandations de produits acceptées ou ayant fait l’objet d’un clic | Recommandations suivies / recommandations diffusées |
| Taux de remise de l’agent actif | Pourcentage de conversations redirigées vers des agents en direct | Remises / total des conversations |
| Taux d’enrichissement du profil | Pourcentage de conversations qui génèrent de nouveaux signaux d’intention ou de préférence | Profils enrichis / total des conversations |
| Chiffre d’affaires influencé par la conversation | Chiffre d’affaires des achats pour lesquels une conversation [!DNL Brand Concierge] a précédé la conversion | Analyse de l’attribution sur les parcours de conversation-achat |
| Délai de résolution | Durée moyenne du début de la conversation à la résolution ou à la remise | Analyse de l’horodatage pour les événements de conversation |

## Modèle de cas d’utilisation

**Expérience de conversation Brand Concierge**

Transformez les propriétés numériques en expériences conversationnelles sécurisées, optimisées par l’IA, qui guident la découverte des clients par le biais d’un dialogue naturel, enrichissent les profils avec des signaux d’intention et de sentiment et fournissent des recommandations de produits personnalisées.

**Chaîne de fonctions :** Configuration de l’agent > Configuration de la gouvernance de marque > Intégration de contenu > Déploiement de l’expérience de conversation > Enrichissement du profil > Analyses et optimisation

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Brand Concierge]** : application d’expérience de conversation optimisée par l’IA fournissant l’agent orchestrator, Product Advisor Agent, l’agent de conseil sur le site, la gouvernance de marque et l’analyse de conversation
- **[!DNL Adobe Experience Platform] (AEP)** — Base de données unifiée fournissant des schémas XDM, la résolution d&#39;identité, des profils clients en temps réel et une infrastructure de collecte de données pour les signaux conversationnels
- **[!DNL Real-Time CDP] ([!DNL RT-CDP])** — Plateforme de données client permettant la recherche de profils en temps réel pour des conversations personnalisées, la segmentation d&#39;audience à partir de signaux conversationnels et l&#39;enrichissement de profils avec des données d&#39;intention et de sentiment

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Obligatoire | Sandbox avec droits d’accès [!DNL Brand Concierge] activés ; rôles configurés pour les administrateurs d’expérience de conversation, les gestionnaires de contenu et les utilisateurs d’analyses ; politiques ABAC en place pour les données de conversation contenant des informations d’identification personnelles ou des signaux clients sensibles | [Présentation du contrôle d’accès](https://experienceleague.adobe.com/fr/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Schémas XDM pour les événements conversationnels (classe ExperienceEvent avec groupes de champs spécifiques à la conversation capturant l’intention, le sentiment, les interactions de produit et les événements de transfert) ; schéma de profil étendu avec les attributs de préférence et d’intention de conversation ; schéma de recherche de catalogue de produits pour les recommandations de mise à la terre | [&#x200B; Présentation du système XDM &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home) |
| Sources et collecte de données | Obligatoire | [!DNL Web SDK] ou [!DNL Mobile SDK] configurés avec des flux de données acheminant des données d’événement conversationnel vers des jeux de données AEP ; intégration [!DNL Edge Network] pour la capture d’événements en temps réel lors de conversations ; données de catalogue de produits ingérées par le biais de connecteurs source ou par ingestion par lots | [Présentation du SDK web](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home) |
| Configuration des identités et des profils | Obligatoire | Espaces de noms d’identité configurés pour l’identification des visiteurs (ECID pour les utilisateurs anonymes, ID CRM ou e-mail pour les utilisateurs authentifiés) ; politique de fusion configurée avec l’activation Edge pour la recherche de profil en temps réel pendant les conversations ; règles de liaison d’identité pour la continuité de la conversation entre appareils | [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home) |
| Définition et segmentation de l’audience | Supposé en place | Les audiences ne sont pas requises pour le déploiement conversationnel de base, mais elles sont nécessaires pour les stratégies de conversation personnalisées (par exemple, les segments de clients à forte valeur ajoutée reçoivent différents flux de conversation). Une évaluation Edge ou en flux continu est recommandée pour la personnalisation de la conversation en temps réel | [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Agrégez les signaux de conversation en attributs au niveau du profil (par exemple, le nombre total de conversations, les intérêts dominants du produit, le score moyen du sentiment) à utiliser dans la segmentation et la personnalisation en aval | [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | Configurez des politiques de conservation des données d’événement de conversation, gérez le consentement pour l’enregistrement et le profilage des conversations et prenez en charge les demandes de suppression des informations personnelles pour les transcriptions des conversations | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Recommandé | Étiqueter les champs de données de conversation contenant des signaux d’informations d’identification personnelles, de sentiment ou d’intention ; appliquer des politiques de gouvernance empêchant les données de conversation sensibles d’atteindre des destinations non autorisées | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home) |
| Surveillance et observabilité | Recommandé | Surveillez les pipelines d’ingestion d’événements de conversation, suivez les taux de réussite de l’enrichissement des profils et alertez sur les échecs de flux de données qui peuvent affecter la qualité de la personnalisation des conversations | [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home) |
| Rapports et analyses | Inclus | Analysez les performances des conversations, les commentaires des clients, l’attribution des conversions et l’efficacité des agents à l’aide d’analyses et de [!DNL CJA] intégrées [!DNL Brand Concierge] pour l’analyse de l’impact des conversations cross-canal | Présentation de [CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Brand Concierge]

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Configuration de l’agent | Phase 1 : configuration de l’agent | Configurez l’orchestrateur d’agent [!DNL Brand Concierge] avec des spécialisations d’agent (Product Advisor, Site Advisory) et des paramètres de comportement de base |
| Configuration de la gouvernance des marques | Phase 2 : configuration de la gouvernance de marque | Définir la voix de la marque, le ton, les mécanismes de sécurisation de la messagerie, les limites du contenu approuvé et les sujets interdits qui façonnent toutes les interactions conversationnelles |
| Intégration de contenu | Phase 3 : intégration de contenu | Connectez des sources de contenu approuvées par la marque, notamment le contenu AEM, les catalogues de produits, les bases de connaissances et d’autres données fiables pour obtenir des réponses de base |
| Configuration de la grille de produits | Phase 3 : intégration de contenu | Configurez le Product Advisor Agent pour obtenir des recommandations de produits personnalisées, des comparaisons guidées et une diffusion de réponse alignée sur la marque |
| Configuration des conseils sur le site | Phase 3 : intégration de contenu | Configurez l’agent de conseil sur le site pour améliorer la navigation en adaptant les interactions en fonction du comportement du visiteur et des signaux d’intention |
| Déploiement de l’expérience de conversation | Phase 4 : déploiement de l’expérience de conversation | Déployez des expériences de conversation sur les canaux pris en charge (web, application mobile, SDK personnalisé) avec la prise en charge des interactions textuelles et vocales. |
| Gestion Des Flux À Faible Code | Phase 4 : déploiement de l’expérience de conversation | Permettre aux équipes marketing de mettre à jour la tonalité de conversation, les flux et le contenu à l’aide d’outils de configuration à code faible |
| Enrichissement du profil de conversation | Phase 5 : enrichissement du profil | Enrichissez les profils clients AEP avec des signaux d’intention, de sentiment, d’affinité de produit et de comportement capturés lors des conversations |
| Analytique de conversation | Phase 6 : Analyses et optimisation | Surveillez les mesures d’engagement, les commentaires des clients, les données de conversion et la qualité de la conversation via des tableaux de bord d’analyse intégrés. |
| Transfert de l’agent en direct | Phase 4 : déploiement de l’expérience de conversation | Configurez une remise transparente à des agents de vente ou de support en direct tout en préservant le contexte de conversation complet. |

### [!DNL Real-Time CDP]

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Recherche de profil en temps réel | Phase 4 : déploiement de l’expérience de conversation | Accédez aux attributs de profil client en temps réel et aux appartenances aux segments pour personnaliser les réponses conversationnelles en fonction des données client connues |
| Enrichissement de profil | Phase 5 : enrichissement du profil | Enrichir les profils avec des attributs calculés dérivés d’événements comportementaux conversationnels (scores d’intention, évolutions du sentiment, affinité du produit) |
| Évaluation d’audience | Phase 5 : enrichissement du profil | Évaluez l’appartenance à l’audience en fonction des signaux de conversation pour permettre le ciblage en aval des segments de conversation engagés |

## Conditions préalables

Les éléments suivants doivent être en place avant le début de l’implémentation.

- [!DNL Adobe Brand Concierge] droit est actif pour l’organisation
- Les licences AEP et [!DNL RT-CDP] sont configurées avec des droits suffisants sur les profils et les volumes d’événements
- Le document des directives sur la marque disponible définit la voix, le ton, les messages approuvés et les sujets interdits
- Préparation du catalogue de produits ou du référentiel de contenu pour l’intégration (ressources AEM, données PIM ou flux de produits structuré)
- Propriétés web identifiées pour le déploiement de l’expérience de conversation avec accès technique pour l’intégration de SDK
- Infrastructure d&#39;agent en ligne disponible si une remise est requise (plateforme de centre de contact, intégration CRM)
- Structure de gestion du consentement en place pour la capture et le profilage des données conversationnelles
- [!DNL Web SDK] ou [!DNL Mobile SDK] déjà déployés sur les propriétés cible (ou prévus pour un déploiement simultané)
- Alignement des parties prenantes sur la portée de la conversation (conseil sur le produit uniquement, navigation sur le site ou les deux)
- Confidentialité et examen juridique terminés pour la capture et l’utilisation des données conversationnelles optimisées par l’IA

## Options de mise en œuvre

Les sections suivantes décrivent différentes approches pour mettre en œuvre ce modèle de cas d’utilisation.

### Option A : déploiement de la grille de produits

**Idéal pour** les organisations de commerce électronique et de vente au détail se concentrent sur la découverte guidée de produits, la comparaison et les expériences de recommandation qui génèrent la conversion et la valeur moyenne des commandes.

**Fonctionnement :**

Le Product Advisor Agent est configuré comme principale spécialisation conversationnelle. Il se connecte au catalogue de produits, comprend les attributs et les relations des produits et guide les clients à travers un dialogue naturel pour aboutir à des recommandations personnalisées. L’agent utilise des mécanismes de sécurisation de la gouvernance de marque pour s’assurer que les recommandations s’alignent sur les priorités commerciales (par exemple, la promotion des articles en stock, la mise en évidence des produits favorables aux marges).

La fonction de conseil sur les produits s’intègre au profil client en temps réel pour accéder à l’historique des achats, au comportement de navigation et aux données de préférence, ce qui permet d’obtenir des recommandations qui tiennent compte de ce que le client possède déjà, a précédemment considéré ou aura probablement besoin en fonction de son profil. Les conversations sont capturées à mesure que les événements d’expérience et les signaux d’intention reviennent dans le profil pour une utilisation en aval.

**Considérations principales :**

- Nécessite un catalogue de produits bien structuré avec des données d’attributs riches pour des recommandations efficaces
- Les données sur les produits doivent être tenues à jour pour éviter de recommander des articles en rupture de stock ou abandonnés
- La gouvernance de marque doit définir la manière dont l’agent gère les mentions de produits concurrents et les comparaisons de prix

**Avantages :**

- Génère directement un impact mesurable sur le chiffre d’affaires grâce à la conversion guidée des achats
- Réduit les taux de retour des produits grâce à des décisions d’achat mieux informées
- Capture des signaux d’affinité et d’intention de produit à forte valeur ajoutée pour la personnalisation en aval
- Extension naturelle des expériences e-commerce existantes

**Limitations :**

- Nécessite une maintenance et une synchronisation continues du catalogue de produits
- Limité aux conversations axées sur le produit ; les questions relatives à la navigation sur le site peuvent ne pas être traitées
- L’efficacité dépend de la qualité et de l’exhaustivité des données du catalogue

**Experience League:**

- [Présentation de Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Conseiller de produit Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)

### Option B : Déploiement de la fonction de conseil sur le site

**Idéal pour :** les organisations disposant de propriétés numériques complexes (médias, services financiers, soins de santé, technologie) où les visiteurs ont besoin d’une aide à la navigation pour trouver du contenu, des ressources ou des outils en libre-service pertinents.

**Fonctionnement :**

L&#39;agent de conseil sur le site est configuré comme principale spécialisation conversationnelle. Il indexe la structure du contenu du site, comprend les relations entre les pages et les catégories de contenu, et adapte ses conseils en fonction des signaux de comportement du visiteur et de l’intention déclarée. Lorsqu’un visiteur interagit, l’agent interprète ses besoins et l’oriente vers le contenu, les outils ou les ressources les plus pertinents.

La fonction de conseil sur le site utilise des signaux comportementaux en temps réel (page actuelle, source de référence, chemin de navigation) combinés à des données de profil (visites précédentes, préférences de contenu, niveau client) pour fournir une aide à la navigation contextuelle pertinente. Cela s’avère particulièrement utile sur les sites dotés de hiérarchies de contenu profondes, de plusieurs lignes de produits ou de workflows en libre-service complexes.

**Considérations principales :**

- Nécessite une indexation complète du contenu et un réexploré régulier à mesure que le contenu du site change
- La plus efficace sur les sites présentant une largeur de contenu importante, où les visiteurs ont généralement du mal à trouver ce dont ils ont besoin
- La gouvernance de marque doit définir les limites de l’étendue (zones du site auxquelles l’agent peut accéder)

**Avantages :**

- Réduit les taux de rebond et améliore la visibilité du contenu sur les sites complexes
- Capture les signaux d’intention de navigation qui révèlent les lacunes de contenu et les problèmes d’expérience utilisateur
- Mise en œuvre moins complexe que la fonction de conseil sur les produits (aucune intégration de catalogue de produits requise)
- Fournit des informations d’analyse sur ce que les visiteurs recherchent mais ne trouvent pas

**Limitations :**

- Moins directement liées à la conversion des recettes que les conversations axées sur les produits
- Nécessite que le contenu soit bien structuré et régulièrement mis à jour pour des conseils précis
- Peut nécessiter un recyclage fréquent à mesure que la structure du site évolue

**Experience League:**

- [Présentation de Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)

### Option C : Déploiement combiné de la fonction de conseil en produits et de conseil sur le site

**Idéal pour :** les organisations qui souhaitent une expérience de conversation complète couvrant à la fois la découverte de produits et la navigation sur le site, généralement les grandes marques de vente au détail ou B2C avec des propriétés numériques étendues et des intentions de visiteur diverses.

**Fonctionnement :**

Product Advisor Agent et l’agent de conseil sur le site sont configurés dans l’orchestrateur [!DNL Brand Concierge]. L&#39;orchestrateur de l&#39;agent utilise la détection d&#39;intention pour acheminer les conversations vers la spécialisation appropriée : les requêtes relatives aux produits sont envoyées à la fonction de conseil sur les produits, tandis que les requêtes de navigation et de recherche de contenu sont envoyées à la fonction de conseil sur le site. L’orchestrateur gère des transitions transparentes entre les spécialisations au sein d’une conversation unique.

Cette approche offre l’expérience de conversation la plus complète possible, en répondant à l’ensemble des besoins des visiteurs, depuis « Aide-moi à trouver un produit » jusqu’à « Où puis-je vérifier l’état de ma commande ? » Les mécanismes de sécurisation de la gouvernance de marque s’appliquent uniformément aux deux spécialisations, assurant une voix de marque cohérente quel que soit le sujet de la conversation.

**Considérations principales :**

- Mise en œuvre plus complexe nécessitant à la fois l’intégration du catalogue de produits et du contenu
- Le routage de l’intention entre les spécialisations doit être bien adapté pour éviter les conversations mal orientées
- La configuration de la gouvernance des marques est plus étendue pour couvrir les contextes de produit et de navigation

**Avantages :**

- Offre aux visiteurs l’expérience de conversation la plus complète possible
- Un point d’entrée unique gère les différentes intentions des visiteurs sans nécessiter d’interfaces distinctes
- Les conversations sur les spécialisations croisées (par exemple, la question sur le produit qui mène à la navigation d’assistance) sont gérées naturellement
- Enrichissement de profil le plus riche à partir de divers signaux de conversation

**Limitations :**

- Effort de mise en œuvre et de maintenance continus les plus élevés
- Nécessite une coordination entre les équipes de contenu et de catalogue de produits
- Exigences plus complexes en matière de test et d’assurance qualité
- La configuration de la gouvernance de marque est plus impliquée.

**Experience League:**

- [Présentation de Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Comparaison des options

| Critères | Option A : Conseiller produit | Option B : Avis sur le site | Option C : Combinée |
| --- | --- | --- | --- |
| Idéal pour | E-commerce, conversion axée sur les produits | Sites riches en contenu, navigation en libre-service | Expérience digitale complète |
| Complexité | Moyenne | Low-Medium | Élevée |
| Délai de valorisation | 4-6 semaines | 3-5 semaines | 6-10 semaines |
| Impact sur le chiffre d’affaires | Élevée (influence directe de la conversion) | Medium (indirect via l’engagement) | La plus élevée (conversion et engagement) |
| Exigences de contenu | Catalogue de produits avec des attributs riches | Index de contenu du site | Catalogue de produits et index de contenu |
| Enrichissement de profil | Affinité du produit, intention d’achat | Mode de navigation, préférences de contenu | Spectre de signal complet |
| Effort de maintenance | Synchronisation du catalogue de produits | Réindexation de contenu | Les deux sont en cours |

### Choisir la bonne option

Commencez par évaluer votre objectif commercial principal et les caractéristiques de vos propriétés numériques :

1. **Si votre objectif principal est de générer la conversion d’un produit** et que votre propriété numérique est axée sur le commerce, choisissez **Option A (Product Advisor)**. Il s’agit du point de départ le plus courant pour les marques de vente au détail et de commerce électronique.

2. **Si votre objectif principal est d’améliorer la visibilité du contenu** et que votre site comporte des hiérarchies de contenu profondes ou des workflows en libre-service complexes, choisissez **Option B (conseil sur le site)**. Idéal pour les entreprises du secteur des médias, des services financiers, de la santé et des technologies.

3. **Si vous avez besoin d’une couverture complète** et avez des besoins à la fois en matière de commerce de produits et de navigation de contenu, choisissez **Option C (combinée)**. Envisagez de commencer par une spécialisation et d’ajouter la seconde après que la première est stable et optimisée.

Une approche progressive est recommandée pour la plupart des organisations : commencez par déployer une spécialisation, validez les performances et collectez les enseignements, puis développez pour atteindre le déploiement combiné.

## Phases de mise en œuvre

Les phases suivantes décrivent la séquence d’implémentation recommandée.

### Phase 1 : configuration de l’agent

**Fonction d’application :** [!DNL Brand Concierge] : configuration de l’agent

Configurez l’orchestrateur de l’agent de [!DNL Brand Concierge] de base, notamment en sélectionnant des spécialisations d’agent (Product Advisor, Site Advisory, ou les deux), en configurant le comportement de l’agent de base et en établissant la connexion entre [!DNL Brand Concierge] et AEP pour l’accès au profil et la capture d’événements.

#### Décision : sélection de la spécialisation de l’agent

Déterminez quelles spécialisations d’agent doivent être activées pour ce déploiement.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Conseiller produit uniquement | Déploiement axé sur Commerce ciblant la découverte et la conversion de produits | Nécessite une intégration au catalogue de produits ; chemin le plus rapide vers un impact sur le chiffre d’affaires |
| Site Advisory uniquement | Déploiement axé sur le contenu et la navigation | Complexité d’intégration réduite ; idéal pour les sites non commerciaux |
| Les deux spécialisations | Couverture conversationnelle complète sur l’ensemble des produits et contenus | Plus grande complexité ; envisagez un déploiement échelonné commençant par un |

#### Décision : modèle d’initiation de la conversation

Déterminez comment les conversations doivent commencer sur la propriété numérique.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Initié par le visiteur (passif) | Approche par défaut où le widget de conversation est disponible, mais n’engage pas de manière proactive | Réduction du risque d’interruption ; repose sur la sensibilisation des visiteurs à l’option de chat |
| Engagement proactif (déclenché) | L’agent entame la conversation en fonction de signaux comportementaux (par exemple, un temps d’attente prolongé, des visites de page répétées, une hésitation du panier). | Taux d’engagement plus élevés, mais risque d’irriter les visiteurs si les déclencheurs sont trop agressifs ; nécessite un ajustement comportemental des déclencheurs. |
| Hybride (passif avec invites contextuelles) | Le widget de conversation est passif, mais affiche des invites contextuelles basées sur le contenu de la page ou le comportement du visiteur | Approche équilibrée ; guide sans forcer l&#39;engagement |

#### Configuration de l’agent

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Assistant IA > [!DNL Brand Concierge] > Configuration de l’agent

Détails de configuration clés :

- Définissez le nom et la description de l’agent qui apparaîtront dans l’interface de conversation
- Sélectionnez le sandbox AEP qui contient le profil client et les données d’événement auxquelles l’agent doit accéder
- Configurez l’orchestrateur d’agent pour acheminer les requêtes entre les spécialisations en fonction de la détection d’intention
- Définition des paramètres de session de conversation (durée de temporisation, durée maximale de conversation, limites de sessions simultanées)
- Activer l’intégration de la recherche de profil en temps réel afin que l’agent puisse accéder aux données du profil du visiteur pendant les conversations

**Là où les options divergent :**

**Pour L’Option A (Grille De Produits) :**
Activez la spécialisation de la grille de produits et configurez sa connexion à la source de données du catalogue de produits. Définissez les paramètres de recommandation de produit, notamment le nombre maximal de recommandations par réponse, les préférences d’affichage des attributs de produit et les règles de gestion des comparaisons.

**Pour L’Option B (Avis Sur Le Site) :**
Activez la spécialisation Conseil sur le site et configurez sa connexion à l’index de contenu du site. Définissez les paramètres de navigation, notamment les limites de la portée du contenu, la gestion des catégories de page et les préférences de génération de liens profonds.

**Pour L’Option C (Combinée) :**
Activez les deux spécialisations et configurez la logique de routage d’intention de l’orchestrateur. Définissez des règles de routage qui déterminent à quel moment une conversation doit être gérée par le Conseiller produit plutôt que par Site Advisory, et comment les transitions entre spécialisations doivent être gérées au sein d&#39;une seule conversation.

**Documentation Experience League :**

- [Présentation de Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Présentation de l’assistant AI](https://experienceleague.adobe.com/fr/docs/experience-platform/ai-assistant/home)
- [AEP Agent Orchestrator](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Phase 2 : configuration de la gouvernance de marque

**Fonction d’application :** [!DNL Brand Concierge] : configuration de la gouvernance des marques

Configurez les mécanismes de sécurisation de la gouvernance de marque qui façonnent toutes les interactions conversationnelles. Cela inclut les définitions de voix et de tonalité de marque, les limites de contenu approuvées, les sujets interdits, les directives de style de réponse et les règles de réaffectation. La gouvernance de la marque garantit que chaque réponse générée par l’IA s’aligne sur les normes de la marque.

#### Décision : niveau de rigueur de la gouvernance

Déterminez dans quelle mesure les mécanismes de sécurisation de la gouvernance de marque doivent limiter les réponses conversationnelles.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Gouvernance stricte | Secteurs très réglementés (services financiers, santé, assurance) ou marques premium nécessitant un contrôle précis du ton | Limite la flexibilité de la conversation ; peut entraîner des réponses « Je ne peux pas m’en empêcher » plus fréquentes ; sécurité maximale de la marque. |
| Gouvernance modérée | Pour la plupart des marques grand public, la cohérence vocale de la marque est importante, mais une certaine flexibilité conversationnelle est acceptable | Bon équilibre entre la sécurité de la marque et le naturel conversationnel ; point de départ recommandé pour la plupart des implémentations |
| Gouvernance flexible | Marques occasionnelles ou de style de vie où la personnalité et l&#39;engagement conversationnels sont prioritaires | La plupart des conversations se déroulent naturellement de la même manière ; nécessite une surveillance plus continue des réponses hors marque. |

#### Décision : stratégie de gestion hors sujet.

Déterminez comment l’agent doit traiter les questions en dehors de sa portée configurée.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Rediriger vers la portée | L&#39;agent prend note de la question et le redirige vers les sujets qu&#39;il peut aider avec | maintient l’engagement, mais peut frustrer les visiteurs et visiteuses qui ont des besoins hors sujet légitimes. |
| Remise à l’agent en direct | L’agent offre de connecter le visiteur à un agent humain pour des questions hors sujet | Meilleure expérience client, mais nécessite une infrastructure et un personnel d’agents actifs |
| Déclin progressif avec les ressources | L’agent explique qu’il ne peut pas vous aider pour cette rubrique et fournit des liens vers des ressources ou des canaux d’assistance pertinents | Solution de secours à faible coefficient de frottement ; ne nécessite pas de disponibilité d’agent actif |

#### Configurer la gouvernance de marque

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Assistant IA > [!DNL Brand Concierge] > Gouvernance des marques

Détails de configuration clés :

- Définir les attributs de la marque : nom de la marque, slogan, mission, valeurs et traits de personnalité qui orientent le ton de la conversation
- Définissez les paramètres de ton : niveau de formalité, tolérance à l’humour, niveau d’empathie et assurance pour les recommandations de produits
- Configurer les limites de contenu approuvées : rubriques dont l’agent est autorisé à discuter et rubriques explicitement interdites
- Définissez les instructions de format de réponse : longueur de réponse maximale, utilisation de listes ou prose, politique d’émoticône et formatage des liens
- Définir des déclencheurs de réaffectation : conditions qui doivent automatiquement acheminer une conversation vers un agent en direct (par exemple, détection des plaintes, signaux d’insatisfaction répétés, identification des clients à forte valeur ajoutée).
- Configurer la gestion des mentions concurrentielles : comment l’agent doit-il répondre lorsque les visiteurs interrogent des produits concurrents ?
- Définir les exigences en matière de clause de non-responsabilité et d’avis juridique : informations obligatoires pour les secteurs réglementés

**Documentation Experience League :**

- [Gouvernance de marque de Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Informations opérationnelles sur l’assistant AI](https://experienceleague.adobe.com/fr/docs/experience-platform/ai-assistant/home)

### Phase 3 : intégration de contenu

**Fonction d’application :** [!DNL Brand Concierge] : intégration de contenu, configuration de la grille de produits, configuration des conseils sur le site.

Configurez les sources de contenu qui fondent les réponses conversationnelles dans des informations précises et approuvées par la marque. Cela inclut l’intégration du catalogue de produits, les connexions de contenu AEM, les importations de la base de connaissances et les plannings d’actualisation du contenu.

#### Décision : méthode d’intégration du catalogue de produits

Déterminez comment les données de produit doivent être fournies au Product Advisor Agent. (options A et C uniquement)

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Intégration du jeu de données AEP | Le catalogue de produits est déjà ingéré dans AEP en tant que jeu de données de recherche via les connecteurs source | tire parti des infrastructures de données existantes ; maintient les données de produit synchronisées avec les données de profil ; nécessite la modélisation et la collecte de données fondamentales pour inclure le catalogue de produits. |
| Intégration de flux direct | Le catalogue de produits existe dans une plateforme PIM ou commerciale qui peut fournir un flux structuré | Peut offrir plus de données d&#39;inventaire et de tarification en temps réel ; nécessite la configuration et la planification des flux |
| Intégration de contenu AEM | Le contenu du produit est géré dans AEM et doit servir de source de données de produit faisant autorité | Idéal pour les marques où AEM est le hub de contenu ; garantit la cohérence entre le contenu web et les réponses conversationnelles |

#### Décision : fréquence d’actualisation du contenu

Déterminez la fréquence de mise à jour de la base de connaissances du contenu de l’agent.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Temps réel / quasi temps réel | La disponibilité du produit, les prix ou le contenu changent fréquemment (par exemple, ventes flash, vente au détail sensible aux stocks). | Précision maximale, mais charge d’infrastructure plus élevée ; critique pour les recommandations sensibles au stock |
| Actualisation quotidienne | Les modifications de contenu sont planifiées et planifiées (par exemple, les calendriers éditoriaux, les promotions hebdomadaires) | Bon équilibre entre précision et performances ; adapté à la plupart des implémentations |
| Actualisation à la demande | Les modifications de contenu sont peu fréquentes et peuvent être déclenchées manuellement en cas de mises à jour | Frais généraux les plus bas ; adapté aux catalogues de produits statiques ou aux sites de contenu stables |

#### Configuration des sources de contenu

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Assistant IA > [!DNL Brand Concierge] > Sources de contenu

Détails de configuration clés :

- Connecter les sources de données du catalogue de produits au mappage de champs pour le nom, la description, les attributs, le prix, la disponibilité, les images et la hiérarchie des catégories du produit
- Configurez l’indexation du contenu pour les pages de site, les articles de la base de connaissances, le contenu des questions fréquentes et la documentation d’assistance
- Définir les limites de la portée du contenu en définissant le contenu auquel l’agent peut faire référence et celui qui est exclu
- Configurez le comportement de secours du contenu lorsque l’agent ne trouve pas de contenu approprié pour répondre à une question
- Configurer des règles de qualité du contenu : seuil de confiance minimal du contenu à inclure dans les réponses, exigences de citation et attribution de la source

**Là où les options divergent :**

**Pour L’Option A (Grille De Produits) :**
Insistez sur l’intégration du catalogue de produits avec le mappage d’attributs de produit riches. Configurez la logique de recommandation de Product Advisor Agent, notamment le nombre de produits à suggérer, la manière de gérer les articles en rupture de stock, de présenter des comparaisons de produits et d’incorporer des données de profil client (historique d’achat, comportement de navigation) dans le classement de recommandation.

**Pour L’Option B (Avis Sur Le Site) :**
Concentrez-vous sur l’indexation du contenu du site avec le mappage de hiérarchie de page. Configurez la logique de navigation de l’agent de conseil sur le site, notamment la manière d’interpréter l’intention du visiteur, les catégories de contenu à prioriser, la manière de gérer les requêtes de navigation ambiguës et d’adapter les suggestions en fonction du contexte de page et du comportement de session actuels du visiteur.

**Pour L’Option C (Combinée) :**
Configurez le catalogue de produits et les sources de contenu du site. Assurez-vous que la logique de routage du contenu affecte correctement le contenu à la spécialisation appropriée et que les références croisées entre le contenu du produit et le contenu de navigation du site sont correctement mappées.

**Documentation Experience League :**

- [Configuration du contenu Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Conseiller de produit Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Présentation des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home)

### Phase 4 : déploiement de l’expérience de conversation

**Fonction d’application :** [!DNL Brand Concierge] : déploiement de l’expérience de conversation, gestion des flux à faible code, remise de l’agent en direct ; [!DNL RT-CDP] : recherche de profil en temps réel

Déployez l’expérience de conversation sur les propriétés numériques cibles, notamment la configuration des canaux, la personnalisation des widgets, l’intégration de la recherche de profil pour la personnalisation, les règles de remise d’agent en direct et les outils low-code pour la gestion de contenu en continu.

#### Décision : canal de déploiement

Déterminez le ou les canaux sur lesquels l’expérience de conversation doit être déployée.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Web (widget incorporé) | La propriété web du Principal est le principal point de contact du client | Point de départ le plus courant : nécessite une intégration [!DNL Web SDK] ; prend en charge les visiteurs anonymes et authentifiés |
| Application mobile (intégration de SDK) | L’application mobile est un canal d’engagement client important | Nécessite une intégration [!DNL Mobile SDK] ; prend en compte les contraintes de l’écran pour l’interface utilisateur de conversation |
| Déploiement SDK personnalisé | L’expérience de conversation doit être intégrée à une application personnalisée, un kiosque ou une propriété numérique non standard | Flexibilité maximale ; nécessite davantage d’efforts de développement ; convient aux kiosques en magasin ou aux plateformes propriétaires. |
| Déploiement multicanal | Expérience de conversation nécessaire sur le web, les appareils mobiles et d’autres canaux simultanément | Portée maximale. Nécessite une gouvernance de marque cohérente sur l’ensemble des canaux. Le contexte de conversation doit persister sur l’ensemble des canaux lorsque cela est possible. |

#### Décision : profondeur de Personalization pour les conversations

Déterminez la quantité de données de profil client que l’agent doit utiliser pour personnaliser les conversations.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Anonyme uniquement (contexte de session) | Approche privilégiant la confidentialité ou lorsque la plupart des visiteurs et visiteuses ne sont pas identifiés | Utilise uniquement des signaux comportementaux en session ; aucune recherche de profil requise ; adapté à la découverte anonyme de produits |
| Compatible avec les profils (visiteurs authentifiés) | Les visiteurs sont généralement connectés et reçoivent des recommandations personnalisées en fonction de la valeur ajoutée de l’historique | Nécessite une recherche de profil en temps réel via [!DNL RT-CDP] ; qualité de recommandation considérablement améliorée pour les clients connus |
| Personnalisation progressive | Combinaison d’anonyme et d’authentifié avec création de profil progressive lors de la conversation | Commence par le contexte de la session ; s’enrichit lorsque le visiteur fournit des informations ou s’authentifie ; équilibre confidentialité et personnalisation |

#### Décision : configuration de la remise de l’agent dynamique

Déterminez si les conversations doivent être escalables pour des agents humains vivants.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Pas de remise (libre-service uniquement) | L’agent AI peut gérer tous les types de conversation attendus ou les agents actifs ne sont pas disponibles | Déploiement le plus simple ; peut frustrer les visiteurs avec des besoins complexes ; adapté aux scénarios de navigation de produits à faible risque. |
| Transfert basé sur des règles | Les déclencheurs spécifiques doivent être transmis aux agents en direct (par exemple, la détection des plaintes, les clients à forte valeur ajoutée, les demandes complexes) | Comportement de réaffectation prévisible ; nécessite la définition de règles et de déclencheurs de réaffectation ; nécessite l’intégration de la plateforme de l’agent en direct |
| Remise à la demande du visiteur | Les visiteurs peuvent demander un agent en direct à tout moment dans la conversation | Meilleure expérience client ; nécessite une dotation en personnel d’agent toujours disponible ou la gestion des files d’attente ; le contexte de conversation doit être transféré. |

#### Déploiement de l’expérience de conversation

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Assistant IA > [!DNL Brand Concierge] > Déploiement

Détails de configuration clés :

- Configurer l’aspect du widget de conversation : position, modèle de couleurs, avatar, message de bienvenue et style d’interaction (texte, voix ou les deux)
- Intégration à [!DNL Web SDK] ou [!DNL Mobile SDK] pour la capture d’événements et la résolution de profil
- Configurez la recherche de profil en temps réel pour accéder aux attributs du client, aux appartenances aux segments et à l’activité récente pendant les conversations
- Configurez l&#39;intégration de remise d&#39;agent en direct avec la plateforme du centre de contact, y compris le protocole de transfert de contexte, le routage de file d&#39;attente et la notification d&#39;agent
- Activez les outils de gestion de flux à code faible pour que les équipes marketing mettent à jour les démarreurs de conversation, les messages promotionnels, le contenu saisonnier et les variations de flux sans implication du développeur
- Configurez les règles de persistance de la session de conversation : durée pendant laquelle l’historique des conversations est conservé, si les conversations peuvent reprendre entre les sessions et continuité des conversations entre les appareils

**Documentation Experience League :**

- [Déploiement de Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Présentation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/fr/docs/experience-platform/edge-network-server-api/overview)
- [Point d’entrée des entités d’API de profil](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/api/entities)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/home)

### Phase 5 : enrichissement du profil

**Fonction d’application :** [!DNL Brand Concierge] : enrichissement de profil de conversation ; [!DNL RT-CDP] : enrichissement de profil, évaluation d’audience

Configurez le pipeline de capture et d’enrichissement qui renvoie des signaux de conversation au profil client unifié d’AEP. Cela inclut le mappage des événements de conversation à XDM, l’extraction des signaux d’intention et de sentiment, la création d’attributs calculés à partir de données de conversation et la création d’audiences en fonction des comportements de conversation.

#### Décision : portée de la capture du signal de conversation

Déterminez les signaux de conversation à capturer et à écrire dans le profil client.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Signaux d’engagement principaux uniquement | Enrichissement minimal du profil ; capture le début, la fin, la durée et l’état d’achèvement de la conversation. | Volume de données le plus faible ; suffisant pour les analyses de base ; valeur de personnalisation limitée |
| Signaux d’intention et de préférence | Capturer les intérêts de produit déduits, les préférences déclarées et les catégories de sujets abordées | Valeur de personnalisation élevée ; volume de données modéré ; recommandé le plus souvent |
| Capture complète du signal | Capturez l’intention, le sentiment, les interactions de produit, les réponses de recommandation, les événements de remise et les scores de retour | Enrichissement de profil le plus élevé ; volume de données le plus élevé ; permet des analyses avancées et une personnalisation pilotée par ML |

#### Décision : création d’une audience à partir de données conversationnelles

Déterminez si les audiences doivent être créées en fonction des comportements de conversation pour l’activation en aval.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Aucune audience conversationnelle | Données de conversation utilisées uniquement pour l’analyse, et non pour l’activation de l’audience | Approche la plus simple ; adaptée si les conversations sont complémentaires aux canaux d’engagement existants |
| Audiences basées sur l’intention | Créer des audiences en fonction des intérêts de produit ou des intentions de navigation déclarés des conversations | Permet de recibler les visiteurs et visiteuses qui ont exprimé un intérêt mais n’ont pas effectué de conversion ; valeur élevée pour Commerce |
| Audiences comportementales | Créez des audiences en fonction des modèles d’engagement de la conversation (par exemple, engagement élevé, conversation abandonnée, visites répétées) | Permet l’orchestration de parcours en fonction des conversations et le suivi cross-canal |

#### Configurer l’enrichissement du profil

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Client > Profils > Attributs calculés (pour les signaux dérivés) ; Client > Audiences > Créer une audience (pour les audiences de conversation)

Détails de configuration clés :

- Mappez les événements conversationnels aux champs de schéma XDM ExperienceEvent afin de capturer l’identifiant de conversation, le nombre de messages, les sujets abordés, les produits référencés, les scores de sentiment et le statut de résolution
- Configurez l’enrichissement du profil [!DNL Brand Concierge] pour écrire les signaux d’intention et de préférence dans le profil unifié
- Créer des attributs calculés à partir des données d’événement conversationnel : nombre total de conversations (durée de vie), intérêt de la catégorie de produits dominante (30 jours), score moyen du sentiment (90 jours), taux de conversion conversation-achat
- Définissez les segments d’audience par lots ou en flux continu en fonction des signaux de conversation pour l’activation en aval (par exemple, « Visiteurs et visiteuses qui ont discuté de la catégorie de produits X au cours des 7 derniers jours, mais n’ont pas effectué d’achat »).
- Validez l’enrichissement du profil en recherchant des profils types pour confirmer que les attributs de conversation sont renseignés

**Documentation Experience League :**

- [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/ui)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/home)

### Phase 6 : analyse et optimisation

**Fonction d’application :** [!DNL Brand Concierge] : Conversational Analytics

Configurez des tableaux de bord et des rapports d’analyse pour mesurer les performances de l’expérience de conversation, identifier les opportunités d’optimisation et suivre les KPI. Cela inclut des analyses intégrées [!DNL Brand Concierge], une intégration [!DNL CJA] facultative pour l’analyse de l’impact des conversations cross-canal et des workflows d’optimisation continus.

#### Décision : profondeur d’Analytics

Déterminez le niveau d’analyse conversationnelle nécessaire.

| Option | Quand choisir | Considérations |
| --- | --- | --- |
| Analyses [!DNL Brand Concierge] intégrées | Les rapports standard sur le volume de conversations, l’engagement, la satisfaction et la conversion sont suffisants | Activation la plus rapide ; couvre les indicateurs clés de performance principaux ; corrélation cross-canal limitée |
| Intégration [!DNL Brand Concierge] + [!DNL CJA] | Analyse cross-canal nécessaire pour comprendre comment les conversations influencent les parcours client au sens large | Nécessite une connexion [!DNL CJA] et une configuration des vues de données ; permet l’analyse d’attribution entre les conversations et autres canaux |
| Pile d’analyses complète ([!DNL Brand Concierge] + [!DNL CJA] + tableaux de bord personnalisés) | Création de rapports au niveau de l’exécutif, modélisation d’attribution avancée et création d’audiences personnalisées à partir d’insights Analytics | Des capacités analytiques très élevées ; nécessite une expertise [!DNL CJA] ; permet une optimisation des conversations pilotée par les données |

#### Configuration des analyses et de l’optimisation

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Assistant IA > [!DNL Brand Concierge] > Analytics; [!DNL Analytics Platform] > Workspace (pour [!DNL CJA])

Détails de configuration clés :

- Consultez [!DNL Brand Concierge] tableaux de bord d’analyse intégrés : tendances du volume de conversation, taux d’engagement, taux d’achèvement, scores CSAT, taux d’acceptation des recommandations et fréquence de remise
- Configurez [!DNL CJA] connexion pour inclure des jeux de données d’événements conversationnels pour l’analyse cross-canal (si vous choisissez l’intégration [!DNL CJA]).
- Créez [!DNL CJA] analyse de l’espace de travail pour l’attribution de conversation à conversion, en identifiant les sujets de conversation en corrélation avec le comportement d’achat
- Configurez la surveillance de la qualité des conversations : suivez les sujets sur lesquels l’agent se débat, les questions courantes sans réponse et les évolutions du sentiment au fil du temps
- Définir des workflows d’optimisation : fréquence de révision régulière pour les mises à jour de la gouvernance de marque, les déclencheurs d’actualisation de contenu et les améliorations du flux de conversation en fonction des informations d’analyse

**Documentation Experience League :**

- [Brand Concierge analytics](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Présentation de CJA Analysis Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)
- [Création ou modification d’une connexion CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/create-connection)
- [Création ou modification d’une vue de données CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/create-dataview)

## Considérations relatives à la mise en œuvre

Les sections suivantes couvrent les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage à garder à l’esprit lors de la mise en œuvre.

### Mécanismes de sécurisation et limites

- [!DNL Brand Concierge] expériences de conversation sont soumises à des limites de taux de génération de réponse de l’IA ; la capacité de conversation simultanée dépend du niveau de droits
- La recherche de profil en temps réel au cours des conversations est soumise aux limites de débit de l’API Profile par sandbox [mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)
- L’ingestion des données d’événement de conversation suit les limites standard d’ingestion en flux continu d’AEP — [&#x200B; Mécanismes de sécurisation d’ingestion](https://experienceleague.adobe.com/fr/docs/experience-platform/ingestion/guardrails)
- La taille du catalogue de produits et le volume de l’index de contenu sont soumis à des limites d’intégration de contenu [!DNL Brand Concierge]
- Un maximum de 25 attributs calculés par sandbox s’applique aux agrégations de signaux conversationnels — [&#x200B; Mécanismes de sécurisation des attributs calculés &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)
- Un maximum de 4 000 définitions de segment par sandbox s’applique aux audiences conversationnelles — [Mécanismes de sécurisation de segmentation](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)

### Pièges courants

- **Définition de la gouvernance de marque insuffisante :** le déploiement sans configuration complète de la gouvernance de marque entraîne des réponses hors marque qui sapent la confiance des clients. Investissez beaucoup de temps dans la phase 2 pour définir le ton, les limites et les règles d’escalade avant le déploiement.
- **Données de catalogue de produits obsolètes :** les recommandations de la conseillère produit basées sur des données d’inventaire, de prix ou de disponibilité obsolètes frustrent les clients et sapent la confiance. Établissez des pipelines d’actualisation de contenu automatisés avec des contrôles de validation.
- **Déclencheurs d’engagement proactif trop agressifs :** la définition de déclencheurs comportementaux trop agressifs (par exemple, le déclenchement d’une conversation après 3 secondes sur la page) ennuie les visiteurs et augmente le taux de rebond. Commencez par des déclencheurs conservateurs et ajustez-les en fonction des données d’engagement.
- **Négliger l’expérience des visiteurs anonymes :** en concentrant la personnalisation uniquement sur les visiteurs authentifiés, vous ignorez la majorité du trafic. Concevez des flux de conversation qui offrent de la valeur aux visiteurs anonymes en utilisant des signaux comportementaux en session.
- **Ignorer la configuration d’enrichissement du profil :** le déploiement de conversations sans capturer de signaux en retour vers le profil gaspille des données précieuses d’intention et de préférence. Configurez l’enrichissement du profil en parallèle au déploiement, et non comme une réflexion après coup.
- **Ignorer l’expérience de remise d’agent en direct :** de mauvaises expériences de remise (contexte perdu, questions répétées, longs temps d’attente) nuisent davantage à l’expérience de conversation globale qu’une remise impossible. Testez le flux de transfert complet de bout en bout avant le lancement.

### Bonnes pratiques

- Commencez par une spécialisation d&#39;agent unique (Product Advisor ou Site Advisory) et développez-la après avoir établi des performances de base.
- Organisez des ateliers sur la gouvernance de la marque avec les parties prenantes du marketing, du droit et de l’expérience client avant de configurer les mécanismes de sécurisation.
- Utiliser la personnalisation progressive : démarrez les conversations avec des réponses basées sur le contexte de session et approfondissez la personnalisation lorsque le visiteur fournit des informations ou s’authentifie.
- Implémentez des tests A/B sur les démarreurs de conversation, les invites et les formats de présentation des recommandations à l&#39;aide des outils de gestion de flux à faible code.
- Planifiez une révision régulière (hebdomadaire ou bihebdomadaire) de l’analyse des conversations afin d’identifier les lacunes de contenu, les points d’échec courants et les opportunités d’optimisation.
- Créez une boucle de commentaires entre les mises à jour de l’analyse conversationnelle et de la gouvernance de marque — utilisez les données de la conversation pour affiner le ton, ajouter de nouvelles rubriques approuvées et ajuster les règles de réaffectation.
- Surveillez les évolutions du sentiment de conversation comme système d’alerte précoce pour les problèmes de produit, les problèmes de site ou les changements de perception de la marque.
- Concevez des flux de conversation qui capturent naturellement des signaux qui enrichissent le profil sans donner à l&#39;interaction l&#39;impression d&#39;être une interrogation.

### Décisions de compromis

>[!NOTE]
>Les décisions de compromis suivantes doivent être évaluées en fonction des exigences et des contraintes spécifiques de votre organisation.

**Profondeur de la personnalisation de la conversation ou simplicité de la confidentialité**

Une intégration de profil plus approfondie permet des conversations plus personnalisées et plus efficaces, mais augmente la complexité de la collecte de données, les exigences de consentement et la charge de conformité en matière de confidentialité.

- **Favoris de la personnalisation profonde :** taux de conversion plus élevés, meilleure qualité de recommandation, enrichissement du profil plus riche et conversations plus engageantes pour les clients récurrents
- **La simplicité de la confidentialité favorise :** déploiement plus rapide, une gestion plus simple du consentement, un risque réglementaire moindre et un positionnement de la marque axé sur la confidentialité
- **Recommandation :** commencez par une personnalisation progressive qui fonctionne bien pour les visiteurs anonymes et ajoute une personnalisation basée sur les profils pour les sessions authentifiées. Cela offre une valeur ajoutée à tous les niveaux d’identification tout en maintenant la conformité en matière de confidentialité gérable. Implémentez la capture du consentement pour le profilage conversationnel en conformité avec les frameworks de consentement existants.

**La rigueur en matière de gouvernance de marque par rapport au naturel conversationnel**

Des mécanismes de sécurisation stricts de la gouvernance de la marque garantissent que chaque réponse correspond aux normes de la marque, mais des contraintes trop rigides donnent aux conversations l’impression d’être robotisées et réduisent l’engagement.

- **Favoris stricts en matière de gouvernance :** sécurité de la marque, conformité aux réglementations, messagerie cohérente et comportement prévisible des agents
- **La flexibilité de la gouvernance favorise** flux de conversation naturel, un engagement accru, une meilleure satisfaction des clients et la capacité à gérer un large éventail de requêtes.
- **Recommandation** commencez par une gouvernance modérée et resserrez ou relâchez-vous en fonction de l’analyse des conversations. Surveillez le taux de réponses « Je ne peux pas m’en empêcher » comme indicateur de restriction excessive. Utilisez les outils de gestion des flux à code faible pour itérer rapidement sur les paramètres de gouvernance sans l’implication des développeurs.

**Actualisation du contenu en temps réel et performances du système**

La synchronisation du contenu en temps réel garantit que l’agent dispose toujours des données actuelles sur les produits et le contenu, mais l’actualisation continue consomme davantage de ressources d’infrastructure et peut introduire de la latence.

- **Favoris de l’actualisation en temps réel :** précision des recommandations tenant compte des stocks, des promotions sensibles au facteur temps et du contenu qui change rapidement.
- **L’actualisation planifiée favorise :** stabilité du système, une consommation prévisible des ressources et des coûts d’infrastructure inférieurs.
- **Recommandation** utilisez l’actualisation quotidienne du contenu par défaut, avec l’actualisation en temps quasi réel uniquement pour les données de disponibilité des stocks et de tarification qui affectent considérablement l’expérience client. Surveillez les mesures de précision du contenu pour déterminer si la fréquence d’actualisation est adéquate.

**Capture de signal complète par rapport à la surcharge de gestion des données**

La capture de chaque signal conversationnel fournit l’enrichissement et l’analyse de profil les plus riches, mais augmente le volume de données, les coûts de stockage et la complexité de la gouvernance.

- **Avantages de la capture complète des signaux :** analyses avancées, formation des modèles ML, enrichissement complet des profils et valeur maximale de personnalisation en aval
- **La capture sélective favorise :** coûts de stockage réduits, gouvernance des données simplifiée, performances de recherche de profil accélérées et conformité plus facile aux principes de minimisation des données
- **Recommandation :** Commencez par la capture du signal d’intention et de préférence (terrain intermédiaire) et passez à la capture complète du signal uniquement après avoir validé que les données supplémentaires créent une valeur mesurable en aval. Appliquez des politiques d’expiration de jeu de données aux données d’événement conversationnelles pour gérer la croissance du stockage.

## Documentation connexe

Les ressources suivantes apportent des informations supplémentaires sur l’implémentation de ce modèle de cas d’utilisation.

**[!DNL Brand Concierge]**

- [Présentation de Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Conseiller de produit Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Présentation de l’assistant AI](https://experienceleague.adobe.com/fr/docs/experience-platform/ai-assistant/home)

**[!DNL Adobe Experience Platform]**

- [Présentation d’AEP](https://experienceleague.adobe.com/fr/docs/experience-platform/landing/home)
- [Présentation du système XDM](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/schema/composition)
- [Présentation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/home)

**Collecte de données et intégration**

- [Présentation de Web SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/web-sdk/home)
- [Présentation de Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configurer les flux de données](https://experienceleague.adobe.com/fr/docs/experience-platform/datastreams/configure)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/fr/docs/experience-platform/edge-network-server-api/overview)
- [Présentation des sources](https://experienceleague.adobe.com/fr/docs/experience-platform/sources/home)

**Identité et profil**

- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/merge-policies/overview)
- [Présentation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview)

**Audiences et segmentation**

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Segmentation par flux](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/methods/streaming-segmentation)

**Gouvernance et confidentialité des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/home)
- [Groupe de champs Consentement et préférences](https://experienceleague.adobe.com/fr/docs/experience-platform/xdm/field-groups/profile/consents)
- [Présentation de Privacy Service](https://experienceleague.adobe.com/fr/docs/experience-platform/privacy/home)
- [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/home)

**Surveillance et observabilité**

- [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home)
- [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview)

**Analyses et rapports**

- [Présentation de CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation de CJA Connections](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-connections/overview)
- [Présentation des vues de données CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-dataviews/data-views)
- [Présentation d’Analysis Workspace](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-workspace/home)

**Mécanismes de sécurisation**

- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/fr/docs/experience-platform/ingestion/guardrails)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/guardrails)
