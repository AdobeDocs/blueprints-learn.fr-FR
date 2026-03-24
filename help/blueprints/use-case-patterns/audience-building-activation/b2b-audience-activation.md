---
title: Audience Activation B2B
description: Découvrez comment activer les audiences B2B basées sur un compte sur les canaux web, e-mail et publicitaires.
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7611'
ht-degree: 0%

---

# Activation des audiences B2B

Ce guide fournit une référence d’implémentation complète pour l’activation des audiences B2B basées sur un compte à l’aide de [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition. Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin de créer, d’évaluer et d’activer des audiences au niveau du compte sur les canaux web, e-mail, publicitaires et CRM.

Il couvre le cycle de vie complet, de l’unification du profil de compte à l’évaluation et l’activation des audiences, en passant par les destinations spécifiques au B2B telles que les systèmes [!DNL Marketo Engage], [!DNL LinkedIn] et CRM. Toutes les approches de mise en œuvre viables sont présentées avec des compromis et des conseils de décision pour vous aider à choisir la bonne voie pour votre organisation.

## Présentation du cas d’utilisation

Les équipes de marketing B2B doivent cibler et activer les audiences au niveau du compte plutôt qu’au niveau de la personne individuelle. Contrairement à l’activation d’audience B2C où l’unité de ciblage est un profil de consommateur unique, l’activation d’audience B2B nécessite de comprendre la relation entre les personnes et les comptes auxquels elles appartiennent, d’évaluer l’appartenance à l’audience en fonction des attributs au niveau du compte combinés à des signaux d’engagement au niveau de la personne, et de diffuser ces audiences vers des destinations qui prennent en charge le ciblage basé sur les comptes.

[!DNL RT-CDP] B2B edition étend la [!DNL Real-Time Customer Data Platform] standard avec des classes XDM spécialisées pour les comptes, les opportunités et les campagnes, ainsi que la résolution d’identité B2B qui mappe les relations personne-compte. Cela permet aux professionnels du marketing de créer des audiences de compte qui combinent des données thermographiques (secteur, chiffre d’affaires, nombre d’employés), des données technographiques (pile technologique, utilisation du produit) et des données comportementales (visites web, engagement par e-mail, présence à un événement) provenant des personnes associées à ces comptes.

Les audiences de compte activées alimentent les cas d’utilisation dans toute la funnel de génération de la demande : campagnes de sensibilisation en haut de funnel sur la publicité [!DNL LinkedIn] et display, programmes de culture mid-funnel en [!DNL Marketo Engage] et activation des ventes en bas de la funnel grâce à l’intégration de la gestion de la relation client (CRM). Les audiences de suppression de compte empêchent les dépenses inutiles en excluant les clients existants, les comptes fermés et perdus ou les comptes figurant déjà dans des cycles de vente actifs.

>[!NOTE]
>Si votre cas d’utilisation implique l’activation des audiences au niveau de la personne (B2C) plutôt qu’au niveau du compte, consultez la section [Activation des audiences vers les destinations](audience-activation-to-destinations.md). Ce modèle utilise le modèle de données RT-CDP standard et ne nécessite pas B2B edition.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Augmenter la génération de leads

Générer davantage de leads qualifiés pour le pipeline de vente par le biais de formulaires, d’événements, de contenu et d’engagements multicanaux.

**KPI :** prospects, coût par lead, conversion de lead

[En savoir plus sur l’augmentation de la génération de pistes](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Améliorer la qualification et la conversion des prospects

Augmentez la qualité des prospects et accélérez la progression du pipeline grâce à la notation, à l’entretien et au suivi personnalisé.

**KPI :** conversion de lead, conversion de prospect/lead, efficacité

[En savoir plus sur l’amélioration de la qualification et de la conversion des prospects](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Acquérir de nouveaux clients

Étendez votre base de clients grâce à des campagnes d’acquisition ciblées, des audiences semblables et l’optimisation des médias achetés.

**KPI : nouveaux clients** coût d’acquisition client, conversion des prospects et des leads

[En savoir plus sur l’acquisition de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Optimiser les dépenses marketing et le retour sur investissement

Améliorez le retour sur investissement marketing grâce à un meilleur ciblage, une meilleure attribution, la suppression de l’audience et une affectation budgétaire plus efficace.

**KPI :** économies de coûts, coût d’acquisition client, revenus incrémentiels

[En savoir plus sur l’optimisation des dépenses marketing et du retour sur investissement](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Exemples de cas d’utilisation tactiques

Les scénarios suivants illustrent la manière dont ce modèle peut être appliqué dans la pratique.

- **Publicité basée sur un compte sur[!DNL LinkedIn]** — Ciblez les comptes correspondant à votre profil client idéal (ICP) avec du contenu sponsorisé et des campagnes InMail sur [!DNL LinkedIn], à l’aide des listes de comptes activées depuis [!DNL RT-CDP] B2B edition
- **[!DNL Marketo Engage]le ciblage du programme d’éducation** — Activez les audiences de compte pour [!DNL Marketo Engage] à inscrire les prospects et les contacts associés aux flux d’éducation ciblés en fonction des critères de qualification au niveau du compte
- **Synchronisation des listes de comptes CRM** — Intégrez les listes de comptes qualifiés à [!DNL Salesforce] ou à [!DNL Microsoft Dynamics] pour la visibilité de l&#39;équipe des ventes, l&#39;affectation des territoires et les workflows de prospection sortante
- **Suppression de compte pour les médias achetés** — Supprimez les clients existants, les comptes clôturés ou les comptes des cycles de vente actifs des campagnes d’acquisition payantes afin de réduire les dépenses inutiles
- **Ciblage de compte basé sur l’intention** — Combinez les signaux d’intention tiers aux données d’engagement propriétaires au niveau du compte pour identifier et activer les audiences des comptes du marché
- **Vente croisée de produits à des comptes existants** — Créez des audiences de comptes en utilisant une ligne de produits, mais pas une autre, puis activez les canaux e-mail et publicitaires pour les campagnes de vente croisée
- **Ciblage des événements et des webinaires** — Activez les audiences de compte pour les canaux publicité et e-mail afin de générer l’enregistrement d’événements à partir des comptes cibles
- **Campagnes de déplacement compétitif** — Ciblez les comptes à l’aide de produits concurrents avec des messages personnalisés activés par le biais de canaux publicitaires et de messagerie électronique
- **Engagement de compte à plusieurs niveaux** : segmentez les comptes en niveaux d’engagement (élevé, moyen, faible) en fonction de l’activité agrégée au niveau de la personne et activez des campagnes différenciées pour chaque niveau
- **Audiences de co-marketing partenaires** — Partagez des segments d’audience de compte avec des partenaires de canal ou des programmes de co-marketing via des destinations de stockage dans le cloud

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

| KPI | Description | Approche de mesure |
| --- | --- | --- |
| Account Reach | Nombre de comptes cibles atteints sur les canaux d’activation | Suivi des comptes uniques activés par destination |
| Taux d’engagement du compte | Pourcentage de comptes activés affichant des signaux d’engagement | Mesurer l’engagement au niveau de la personne agrégé au compte |
| Influence sur le pipeline | Pipeline de revenus attribué aux campagnes d’activation basées sur les comptes | Suivre les opportunités créées à partir des audiences de compte activées |
| Coût par compte engagé | Dépenses marketing divisées par le nombre de comptes montrant l’engagement | Calculer les coûts sur l’ensemble des canaux publicitaires et de messagerie |
| Taux de conversion des leads | Pourcentage de leads provenant de comptes activés qui sont convertis en opportunités | Suivre la conversion de lead à opportunité pour les audiences activées |
| Économies réalisées lors de la suppression de l’audience | Coût évité en supprimant les comptes inéligibles des campagnes payantes | Mesurer la réduction des dépenses à partir des audiences de suppression |
| Couverture du compte | Pourcentage du marché adressable total (TAM) couvert par les audiences activées | Comparer les comptes activés à l&#39;univers ICP total |

## Modèle de cas d’utilisation

**Activation de l’audience B2B**

Activez les audiences B2B basées sur les comptes sur les canaux web, e-mail et publicitaires.

**Chaîne de fonctions :** Enrichissement du profil de compte > Évaluation de l’audience du compte > Configuration de la destination > Audience Activation > Surveillance

## Applications

Les applications suivantes sont utilisées pour implémenter ce modèle de cas d’utilisation.

- **[!DNL Real-Time CDP]B2B edition** : plateforme principale pour l’unification des profils de compte, la résolution des identités B2B, l’évaluation des audiences de compte, la configuration de destination spécifique au B2B et l’activation des audiences de compte
- **[!DNL Adobe Experience Platform](AEP)** : infrastructure de base pour la modélisation des données XDM B2B, l’ingestion des données à partir de sources d’automatisation CRM et marketing, le service d’identités et la gouvernance
- **[!DNL Marketo Engage]** : destination d’automatisation du marketing B2B Principal pour les programmes de formation des prospects, la notation et l’exécution de campagnes alimentés par des audiences de compte activées

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Obligatoire | Sandbox configuré avec [!DNL RT-CDP] B2B edition activé. Rôles configurés pour la gestion des données B2B, la création d’audiences et l’activation de destination. Politiques ABAC en place si les données de compte contiennent des champs restreints. | [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Schémas XDM B2B configurés à l’aide des classes XDM Business Account, XDM Business Opportunity, XDM Business Campaign et XDM Individual Profile. Groupes de champs B2B appliqués pour les attributs de compte, les relations personne-compte et les données d’opportunité. Jeux de données créés et activés pour le profil pour chaque entité B2B. Relations de schéma définies entre le compte, la personne, l’opportunité et les entités de campagne. | [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schémas B2B dans Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Sources et collecte de données | Obligatoire | Connecteurs Source configurés pour le CRM ([!DNL Salesforce], [!DNL Microsoft Dynamics]) et l’automatisation du marketing ([!DNL Marketo Engage]) afin d’ingérer les données de compte, de personne, d’opportunité et de campagne. Pipelines d’ingestion par lots ou par flux actifs. Mappages de la préparation des données configurés pour transformer les données sources en schémas XDM B2B. | [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Connecteur Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Configuration des identités et des profils | Obligatoire | Espaces de noms d’identité B2B configurés pour les identifiants de compte (ID de compte, ID de compte CRM) et les identifiants de personne (e-mail, ID de contact CRM, ID de lead Marketo). Relations de personne à compte résolues par la résolution d’identité B2B. Politiques de fusion configurées pour l’unification des profils de compte. | [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [B2B edition de Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b) |
| Définition et segmentation de l’audience | Obligatoire | Définitions d’audience au niveau du compte créées à l’aide des attributs de compte, des attributs de personne et des données d’activité. Plannings d’évaluation configurés pour les audiences de compte. Audiences de suppression définies pour exclure les comptes inéligibles. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les scores d’engagement agrégés, la valeur de durée de vie et les mesures d’activité au niveau du compte améliorent la précision de l’audience. Les attributs calculés peuvent cumuler des événements au niveau de la personne (ouvertures d’e-mail, visites web, téléchargements de contenu) au niveau du compte pour les utiliser dans la segmentation. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | Les politiques de conservation des données B2B garantissent le nettoyage des données obsolètes des comptes et des opportunités. La gestion du consentement pour les contacts B2B garantit la conformité aux réglementations de marketing par e-mail. Les politiques d’expiration des jeux de données empêchent l’accumulation de données de synchronisation CRM obsolètes. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Inclus | Les données de compte B2B contiennent souvent des restrictions contractuelles (chiffres d’affaires, nombre d’employés provenant de fournisseurs tiers). Les libellés d’utilisation des données empêchent l’activation d’attributs de compte restreints vers des destinations non autorisées. Les politiques de gouvernance garantissent que les champs PII des enregistrements de contact sont gérés correctement lors de l’activation. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Surveillance et observabilité | Inclus | La surveillance des flux de données du connecteur source [!DNL Marketo Engage] et CRM garantit que les données du compte restent à jour. La surveillance de l’activation des destinations confirme que les audiences sont correctement diffusées aux cibles [!DNL LinkedIn], [!DNL Marketo] et CRM. Les règles d’alerte détectent les échecs d’ingestion qui provoqueraient des données de compte obsolètes. | [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Surveillance des flux de données de destination](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations) |
| Rapports et analyses | Recommandé | [!DNL CJA] B2B edition fournit des analyses au niveau du compte, notamment la portée de l’audience, l’engagement et l’influence du pipeline. L’attribution basée sur les comptes permet de mesurer l’impact des campagnes d’activation sur la progression des opportunités et le chiffre d’affaires. | Présentation de [](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Real-Time CDP] B2B edition ([!DNL RT-CDP] B2B)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Unification du profil de compte | Phase 1 : enrichissement du profil de compte | Consolidez les données de compte du CRM, de l’automatisation marketing et de sources tierces en profils de compte unifiés à l’aide des classes de schéma XDM B2B . |
| Résolution d’identités B2B | Phase 1 : enrichissement du profil de compte | Résolvez les relations personne à compte à l’aide des identifiants principaux, en mappant les contacts et les prospects à leurs comptes associés. |
| Évaluation de l’audience du compte | Phase 2 : évaluation de l’audience du compte | Évaluez l’appartenance à un segment au niveau du compte en combinant des attributs de compte, des attributs de personne et des données d’activité de personne |
| Configuration de la destination du compte | Phase 3 : configuration de la destination | Configurez des connexions à des destinations spécifiques au B2B ([!DNL Marketo Engage], [!DNL LinkedIn], CRM, stockage dans le cloud) avec le mappage des champs au niveau du compte |
| Audience Activation du compte | Phase 4 : Audience Activation | Publiez des audiences basées sur un compte vers des destinations configurées pour le ciblage, la suppression ou la synchronisation CRM |
| Intégration [!DNL Marketo Engage] | Phase 3 : configuration de la destination | Configurer le flux de données bidirectionnel avec [!DNL Marketo Engage] à l’aide des connecteurs source et de destination B2B natifs |
| Gouvernance des données B2B | Phase 5 : gouvernance et surveillance | Application des politiques d’utilisation des données et du consentement sur l’activation des données de compte B2B pour empêcher l’exposition des données non autorisée |

### [!DNL Real-Time CDP] ([!DNL RT-CDP]) — fonctions standard

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Phase 2 : évaluation de l’audience du compte | Moteur d’évaluation sous-jacent pour les audiences de compte, prenant en charge l’évaluation par lots des définitions de segment au niveau du compte |
| Configuration de la destination | Phase 3 : configuration de la destination | Infrastructure de connexion de destination principale utilisée par la configuration de destination spécifique au B2B |
| Activation d’audience | Phase 4 : Audience Activation | Infrastructure de flux de données d’activation principale utilisée par l’activation de l’audience du compte |
| Application du consentement et de la gouvernance | Phase 5 : gouvernance et surveillance | Application des préférences de consentement et des politiques d’utilisation des données au moment de l’activation |

## Conditions préalables

Procédez comme suit avant de commencer l’implémentation.

- [ ] [!DNL RT-CDP] licence B2B edition configurée et activée sur l’organisation
- [ ] système CRM ([!DNL Salesforce] ou [!DNL Microsoft Dynamics]) accessible avec les informations d’identification d’API pour la configuration du connecteur source
- [ ] instance [!DNL Marketo Engage] dotée d’un accès API (Munchkin ID, ID client, secret client) si vous utilisez [!DNL Marketo] comme destination
- [ ] [!DNL LinkedIn] compte Campaign Manager avec la fonctionnalité d’audiences correspondantes si vous utilisez [!DNL LinkedIn] comme destination
- [ ] schémas XDM B2B créés avec des classes de compte, de personne, d’opportunité et de campagne (F2)
- [ Connecteurs ] Source configurés et ingérant activement des données d’automatisation du marketing et du CRM (F3)
- [ ] relations d’identité de personne à compte résolues et profils de compte unifiés (F4)
- [ ] Conventions de dénomination de compte et taxonomie convenues pour les définitions d’audience
- [ ] Règles de gouvernance des données définies pour les classifications de sensibilité des données au niveau du compte

## Options de mise en œuvre

Les options suivantes décrivent différentes approches pour mettre en œuvre ce modèle de cas d’utilisation. Examinez chaque option et sélectionnez celle qui correspond le mieux à vos besoins.

### Option A : activation de l’audience de diffusion en continu vers [!DNL Marketo Engage]

**Idéal pour :** les organisations qui utilisent [!DNL Marketo Engage] comme principale plateforme d’automatisation du marketing B2B et qui ont besoin de mises à jour de l’appartenance aux audiences en temps quasi réel pour déclencher des programmes de formation, mettre à jour les scores des prospects ou modifier l’appartenance à la campagne lorsque des comptes sont qualifiés ou disqualifiés.

**Fonctionnement :**

Cette option utilise le connecteur de destination [!DNL Marketo Engage] natif dans [!DNL RT-CDP] pour diffuser directement vers [!DNL Marketo Engage] les modifications d’appartenance à une audience de compte. Lorsqu’un compte est éligible ou quitte un segment d’audience, les prospects et contacts associés dans [!DNL Marketo] sont mis à jour avec les attributs d’appartenance au segment. [!DNL Marketo] les campagnes intelligentes peuvent ensuite se déclencher en fonction de ces modifications d’abonnement.

La destination [!DNL Marketo Engage] est une destination de diffusion en continu, ce qui signifie que les modifications d’appartenance à une audience sont envoyées de manière incrémentielle au fur et à mesure qu’elles se produisent plutôt que par lots planifiés. Les campagnes qui doivent répondre aux modifications de qualification des comptes bénéficient ainsi d’un délai d’action plus rapide. Les mappages de champs connectent [!DNL RT-CDP] attributs de profil aux champs de lead/contact [!DNL Marketo], ce qui permet d’enrichir les enregistrements [!DNL Marketo] avec les données au niveau du compte provenant de [!DNL RT-CDP].

**Considérations principales :**

- Nécessite un abonnement [!DNL Marketo Engage] actif avec accès API
- L’activation par flux envoie des mises à jour incrémentielles, et non des instantanés d’audience complets
- Les enregistrements au niveau de la personne dans [!DNL Marketo] sont mis à jour, et non les enregistrements au niveau du compte directement
- [!DNL Marketo] campagnes intelligentes doivent être configurées pour agir sur les mises à jour des champs d’appartenance aux segments

**Avantages :**

- Mises à jour de l’appartenance à une audience en temps quasi réel dans [!DNL Marketo]
- Le connecteur bidirectionnel natif simplifie l’intégration
- Les mises à jour incrémentielles réduisent le volume de transfert de données
- [!DNL Marketo] pouvez déclencher immédiatement des programmes nourriciers en fonction des modifications de l’audience

**Limitations :**

- Limité à [!DNL Marketo Engage] comme cible de l’activation
- Les contraintes d’éligibilité de l’évaluation en flux continu s’appliquent aux définitions d’audience sous-jacentes
- Nécessite un mappage entre les audiences de compte [!DNL RT-CDP] et les enregistrements de lead/contact [!DNL Marketo]
- Une logique de programme [!DNL Marketo] complexe peut être nécessaire pour traduire les mises à jour au niveau de la personne en actions au niveau du compte

**Experience League:**

- [Destination Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Activer des audiences vers la destination Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage#activate)

### Option B : Activation de l’audience par lots vers les plateformes publicitaires

**Idéal pour** campagnes publicitaires basées sur des comptes sur des [!DNL LinkedIn], des réseaux d’affichage ou d’autres plateformes publicitaires pour lesquelles les actualisations quotidiennes de l’audience sont suffisantes et dont l’objectif principal est la portée et la sensibilisation au niveau du compte plutôt que la réponse en temps réel.

**Fonctionnement :**

Cette option active les audiences de compte vers des destinations de plateforme publicitaire ([!DNL LinkedIn] audiences correspondantes, [!DNL Google] correspondance client, [!DNL Facebook] audiences personnalisées ou [!DNL The Trade Desk]) à une cadence par lots planifiée. Le flux de données d’activation exporte les membres de l’audience du compte avec des champs d’identité mappés (généralement des adresses e-mail hachées des contacts associés) que la plateforme publicitaire utilise pour comparer à sa base d’utilisateurs.

Pour [!DNL LinkedIn] d’informations en particulier, la destination Audiences [!DNL LinkedIn] avec correspondance accepte la correspondance de nom de société et de domaine en plus de la correspondance par e-mail, ce qui permet un véritable ciblage au niveau du compte. D’autres plateformes publicitaires nécessitent généralement des identifiants au niveau de la personne (e-mail, téléphone) de la part des contacts associés aux comptes admissibles.

L’activation par lots s’exécute selon un planning configurable (quotidien, toutes les 6 heures, etc.) et exporte des instantanés d’audience complets ou des modifications incrémentielles en fonction du type de destination. Cette approche est bien adaptée aux campagnes de sensibilisation soutenues où les exigences de fraîcheur de l’audience sont mesurées en heures plutôt qu’en minutes.

**Considérations principales :**

- L’actualisation de l’audience dépend du planning par lots (généralement quotidien)
- Les plateformes Advertising ont leurs propres limites de taux de correspondance
- [!DNL LinkedIn] prend en charge la correspondance au niveau du compte ; d’autres plateformes nécessitent des identifiants au niveau de la personne
- Les formats de fichiers d’exportation et les exigences en matière d’identité varient selon la destination

**Avantages :**

- Prend en charge plusieurs plateformes publicitaires simultanément
- Le traitement par lots gère efficacement d’importants volumes d’audiences
- Les audiences de suppression de compte réduisent le gaspillage et les dépenses
- [!DNL LinkedIn] audiences correspondantes permet le ciblage natif au niveau du compte

**Limitations :**

- Les mises à jour d’audience ne sont pas effectuées en temps réel ; la latence dépend du planning par lots
- Les taux de correspondance varient selon la plateforme et les champs d’identité disponibles
- Certaines plateformes ne prennent pas en charge la véritable correspondance au niveau du compte, mais uniquement au niveau de la personne
- Nécessite une configuration de destination distincte pour chaque plateforme publicitaire

**Experience League:**

- [Destination des audiences correspondantes LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Destination Google Customer Match](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/advertising/google-customer-match)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)

### Option C : activation basée sur les fichiers vers le stockage dans le cloud

**Idéal pour :** les organisations ayant besoin d’une flexibilité maximale dans la manière dont les audiences de compte sont utilisées en aval, y compris les importations CRM, l’enrichissement de l’entrepôt de données, le partage des données des partenaires ou les intégrations personnalisées où une remise basée sur des fichiers est préférée.

**Fonctionnement :**

Cette option exporte les audiences de compte au format CSV, JSON ou Parquet vers des destinations d’espace de stockage ([!DNL Amazon S3], [!DNL Azure Blob Storage], [!DNL Google Cloud Storage], SFTP) à une cadence planifiée. L’exportation comprend des attributs de compte, des champs au niveau de la personne des contacts associés et des métadonnées d’appartenance à l’audience. Les systèmes en aval utilisent ces fichiers par le biais de leurs propres processus d’importation.

L’activation basée sur des fichiers offre un meilleur contrôle sur le format d’exportation, la sélection de champs et la planification. Elle prend en charge l’exportation complète (instantané d’audience complet à chaque exécution) et l’exportation incrémentielle (modifications uniquement depuis la dernière exécution). Cette approche est généralement utilisée lorsque le système cible ne dispose pas d’un connecteur de destination [!DNL RT-CDP] natif, ou lorsque l’organisation doit prétraiter ou transformer les données avant de les charger dans le système cible.

**Considérations principales :**

- Nécessite une infrastructure de stockage cloud ([!DNL S3], [!DNL Azure Blob], [!DNL GCS] ou SFTP)
- Les processus d’importation en aval doivent être créés et gérés
- Le format de fichier (CSV, JSON, Parquet) doit correspondre à la configuration système requise en aval
- La planification des exportations doit s’aligner sur les fenêtres de traitement en aval

**Avantages :**

- Flexibilité maximale dans la façon dont les données d’audience sont utilisées
- Prend en charge tout système en aval pouvant lire les fichiers
- Contrôle total du format d’exportation, des champs et de la planification
- Peut servir plusieurs consommateurs en aval à partir d’une seule exportation
- Prend en charge les modes d’exportation complets et incrémentiels

**Limitations :**

- Latence la plus élevée de toutes les options (lot uniquement)
- Nécessite la création et la maintenance de workflows d’importation en aval
- Aucune intégration native : un effort de développement supplémentaire est nécessaire.
- La gestion des fichiers (nettoyage, archivage) doit être traitée séparément

**Experience League:**

- [Destination Amazon S3](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Destination de stockage des objets blob Azure](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/azure-blob)
- [Activer les audiences vers des destinations par lots](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/connect-activate-batch-destinations)

### Option D : activation par flux vers les systèmes CRM

**Idéal pour :** cas d’utilisation d’alignement vente-marketing où les modifications de qualification du compte doivent être reflétées dans le CRM ([!DNL Salesforce] ou [!DNL Dynamics]) en temps quasi réel pour la visibilité de l’équipe commerciale, les mises à jour d’affectation de territoire ou les workflows de vente automatisés.

**Fonctionnement :**

Cette option utilise des connecteurs de destination de diffusion en continu ([!DNL Salesforce] CRM, [!DNL Microsoft Dynamics]) pour pousser directement les modifications d’audience de compte vers les enregistrements de compte ou de contact CRM. Lorsqu’un compte est éligible ou quitte une audience, l’enregistrement CRM est mis à jour avec un champ personnalisé indiquant l’appartenance à un segment. Les équipes commerciales peuvent ensuite créer des rapports, des vues et des alertes CRM en fonction de ces champs.

Le connecteur de diffusion en continu envoie des mises à jour incrémentielles lorsque des modifications d’appartenance à une audience se produisent. Les mappages de champs connectent [!DNL RT-CDP] attributs de compte et de personne aux champs CRM, ce qui permet d’enrichir les enregistrements CRM avec des données unifiées provenant de [!DNL RT-CDP]. Cette approche ferme la boucle entre l’intelligence marketing (qualification de compte) et l’exécution des ventes (workflows CRM).

**Considérations principales :**

- Nécessite un accès à l’API CRM avec les autorisations d’écriture appropriées
- Des champs personnalisés CRM doivent être créés pour recevoir les données d’appartenance à une audience
- Le volume de diffusion en continu doit être compris dans les limites de débit de l’API CRM
- L’automatisation du workflow CRM doit être configurée pour agir sur les mises à jour des champs

**Avantages :**

- Mises à jour de la gestion de la relation client en temps quasi réel pour la visibilité des équipes commerciales
- Active les workflows CRM automatisés déclenchés par les modifications d&#39;audience
- Enrichit les enregistrements CRM avec des données de compte unifiées issues de [!DNL RT-CDP]
- Prend en charge les mises à jour des champs au niveau du compte et au niveau du contact

**Limitations :**

- Les limites de débit de l’API CRM peuvent ralentir les mises à jour volumineuses.
- Nécessite une personnalisation du CRM (champs personnalisés, workflows)
- Limité à [!DNL Salesforce] et [!DNL Microsoft Dynamics] comme connecteurs natifs
- Les contraintes d’évaluation par flux s’appliquent aux audiences sous-jacentes

**Experience League:**

- [Destination Salesforce CRM](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Destination Microsoft Dynamics 365](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)

### Comparaison des options

Le tableau suivant compare les caractéristiques clés de chaque option d’implémentation.

| Critères | Option A : Diffusion En Continu [!DNL Marketo] | Option B : lot Advertising | Option C : Stockage Dans Le Cloud | Option D : diffusion en continu CRM |
| --- | --- | --- | --- | --- |
| Idéal pour | Activation du programme de fidélisation | Publicité basée sur les comptes | Intégration flexible en aval | Alignement ventes/marketing |
| Complexité | Faible | Moyenne | Medium-Grand | Moyenne |
| Latence | Temps quasi réel (minutes) | Lot (heures) | Lot (heures) | Temps quasi réel (minutes) |
| Flexibilité | Faible ([!DNL Marketo] uniquement) | Medium (plateformes publicitaires) | Élevée (tout système en aval) | Faible (CRM uniquement) |
| Requiert | licence [!DNL Marketo Engage] | Comptes Advertising Platform | Infrastructure de stockage dans le cloud | Accès à l’API CRM |
| Ciblage au niveau du compte | Via les enregistrements de personne | [!DNL LinkedIn] uniquement (autres niveaux de personne) | Paramétrable | Via les enregistrements de compte/contact |
| Effort de maintenance | Faible | Low-Medium | Élevée | Moyenne |

### Choisir la bonne option

Utilisez les conseils de décision suivants pour sélectionner la bonne approche d’activation :

1. **Si votre objectif principal est de favoriser les leads B2B et que vous utilisez[!DNL Marketo Engage]**, choisissez l’option A. Le connecteur de diffusion en continu natif offre le délai d’action le plus rapide pour les workflows d’automatisation du marketing.

2. **Si votre objectif principal est la sensibilisation basée sur les comptes et la génération de la demande par le biais de la publicité**, choisissez l&#39;option B. [!DNL LinkedIn] Les audiences correspondantes offrent le ciblage au niveau du compte le plus puissant. Utiliser d’autres plateformes publicitaires pour une portée plus large.

3. **Si vous devez transmettre des audiences de compte à des systèmes sans connecteurs de [!DNL RT-CDP] natifs** ou si vous avez besoin d’un contrôle maximal sur le format des données et le traitement en aval, choisissez l’option C. Il s’agit également du meilleur choix pour le partage de données des partenaires ou l’enrichissement de l’entrepôt de données.

4. **Si votre objectif principal est l’activation des ventes et la visibilité CRM des comptes qualifiés pour le marketing**, choisissez l’option D. Cela ferme la boucle de transfert du marketing vers les ventes en mettant à jour les enregistrements CRM en temps quasi réel.

La plupart des entreprises B2B mettront en œuvre plusieurs options simultanément, par exemple, l&#39;option A pour les programmes de fidélisation, l&#39;option B pour la publicité [!DNL LinkedIn] et l&#39;option D pour la synchronisation CRM. Ces options ne s’excluent pas mutuellement. Une même audience de compte peut être activée vers plusieurs destinations simultanément.

## Phases de mise en œuvre

Les phases suivantes décrivent le processus détaillé de mise en œuvre de ce modèle de cas d’utilisation.

### Phase 1 : enrichissement du profil de compte

Cette phase établit des profils de compte unifiés en consolidant les données issues de la gestion de la relation client, de l’automatisation du marketing et de sources tierces.

**Fonction d’application :** [!DNL RT-CDP] B2B : unification du profil de compte, [!DNL RT-CDP] B2B : résolution d’identité B2B

**Éléments à configurer :** cette phase établit des profils de compte unifiés en consolidant les données issues de la gestion de la relation client, de l’automatisation du marketing et de sources tierces. La résolution d’identité B2B mappe les relations personne à compte afin que les données d’engagement au niveau de la personne (ouvertures d’e-mails, visites web, téléchargements de contenu) puissent être agrégées et utilisées dans l’évaluation de l’audience au niveau du compte. Cette phase s’appuie sur les fonctions fondamentales F2, F3 et F4 qui doivent déjà être en place.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : stratégie d’identifiant de compte**
>
>Quel identifiant sert de clé de compte principale sur tous les systèmes ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| ID de compte CRM (par exemple, ID de compte [!DNL Salesforce]) | Le CRM est le système d’enregistrement des comptes | Approche la plus courante. Assure l’alignement entre [!DNL RT-CDP] et CRM. Nécessite que tous les systèmes sources référencent le même identifiant de compte CRM. |
>| Identifiant de compte personnalisé | Plusieurs instances CRM ou un maître de compte propriétaire | Nécessite une couche de mappage entre les identifiants du système source et l’identifiant de compte canonique. Plus flexible, mais plus complexe. |
>| Numéro ou domaine DUNS | L’enrichissement des données tierces est la source principale du compte | Utile lorsque les fournisseurs de données démographiques sont la source principale. Peut nécessiter une correspondance approximative pour la résolution basée sur le domaine. |

>[!NOTE]
>**Décision : modèle de relation personne à compte**
>
>Comment les personnes (leads, contacts) sont-elles associées aux comptes ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Un à un (chaque personne appartient à un compte) | Modèle B2B simple avec des données CRM propres | Résolution simple. Le plus courant pour le B2B de marché intermédiaire. |
>| Plusieurs à plusieurs (les personnes peuvent appartenir à plusieurs comptes) | Relations d’entreprise complexes, consultants ou réseaux de partenaires | [!DNL RT-CDP] B2B edition le prend en charge de manière native. Augmente la complexité de l’audience, mais reflète précisément les relations du monde réel. |

**Navigation dans l’interface utilisateur :** Platform > Profils > Parcourir (pour vérifier les profils de compte unifiés)

**Détails de configuration clés :**

- Vérifiez que les schémas XDM B2B (compte professionnel XDM, compte professionnel XDM) sont en place à partir de F2.
- Confirmez que les connecteurs source CRM et [!DNL Marketo] ingèrent activement des données de compte et de personne à partir de F3.
- Vérifiez que les relations personne à compte sont résolues dans le graphique d’identité F4.
- Vérifier l’exhaustivité du profil de compte en parcourant des profils de compte types

**Documentation Experience League :**

- [Présentation de Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Schémas B2B dans Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Connecteur Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Connecteur Salesforce](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

### Phase 2 : évaluation de l’audience du compte

Cette phase définit et évalue les audiences au niveau du compte à l’aide d’une combinaison d’attributs de compte, d’attributs de personne et de données d’activité de personne.

**Fonction d’application :** [!DNL RT-CDP] B2B : évaluation de l’audience du compte, [!DNL RT-CDP] : évaluation de l’audience

**Éléments à configurer :** cette phase définit et évalue les audiences au niveau du compte à l’aide d’une combinaison d’attributs de compte, d’attributs de personne et de données d’activité de personne. Les audiences de compte dans [!DNL RT-CDP] B2B edition vous permettent de segmenter les comptes en fonction des caractéristiques firmographiques (secteur, chiffre d’affaires, nombre d’employés) et du comportement d’engagement des personnes associées à ces comptes.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : méthode d’évaluation de l’audience**
>
>À quelle vitesse l’audience du compte doit-elle être mise à jour ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Évaluation par lots (quotidienne) | Les audiences de campagne se sont actualisées quotidiennement, avec des activations basées sur des fichiers et des audiences de plateforme publicitaire | La plupart des audiences de compte utilisent l’évaluation par lots. Gère des requêtes d’entités multiples complexes qui combinent des attributs de compte et de personne. Suffisant pour la plupart des cas d’utilisation B2B où l’actualisation quotidienne est acceptable. |
>| Évaluation en flux continu | Activation de [!DNL Marketo] ou de CRM où la qualification en temps quasi réel est nécessaire | Les audiences de compte ont une éligibilité de diffusion en continu limitée. Seules les conditions d’attribut de compte simples remplissent les critères de l’évaluation en flux continu. Les conditions comportementales au niveau de la personne nécessitent généralement un lot. |

>[!NOTE]
>**Décision : approche de la définition de l’audience du compte**
>
>Comment allez-vous définir les critères d’audience du compte ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Attributs de compte uniquement | Ciblage micrographique simple (secteur, chiffre d’affaires, région) | La plus rapide à mettre en œuvre. Limité aux données au niveau du compte. À utiliser pour un ciblage large. |
>| Attributs de compte + personne | Compte de ciblage sur lequel les personnes associées correspondent à des critères spécifiques (fonction, service) | Un ciblage plus précis. Combine des données démographiques et démographiques. |
>| Compte + attributs de personne + activité de personne | Ciblage des comptes avec contacts engagés (ouvertures d’e-mails, visites web, téléchargements de contenu) | Le plus puissant mais le plus complexe. Nécessite des données d’événement comportementales provenant de F3. Nécessite généralement une évaluation par lots. |
>| Composition de l’audience | Logique d’audience complexe nécessitant des opérations de classement, de partage, d’exclusion ou d’enrichissement | Utilisez le canevas visuel Composition de l’audience pour les audiences de compte dérivées. Limité à l’évaluation par lots. |

>[!NOTE]
>**Décision : stratégie d’audience de suppression**
>
>Quels comptes doivent être exclus de l’activation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Suppression de client existant | Campagnes d’acquisition ciblant les nouveaux comptes nets | Exclure les comptes comportant des abonnements actifs ou des opportunités conclues |
>| Suppression des cycles de vente actifs | Éviter d’interférer avec les comptes dans l’engagement commercial actif | Exclure les comptes avec des opportunités ouvertes au-dessus d’une certaine étape |
>| Suppression récente d’un engagement | Empêcher la surmessagerie des comptes récemment contactés | Exclure les comptes engagés dans un intervalle de recherche en amont (par exemple, 30 jours) |
>| Aucune suppression | Campagnes de sensibilisation à la marque ciblant tous les comptes admissibles | À utiliser avec précaution ; peut entraîner des dépenses inutiles sur des comptes non admissibles |

**Navigation dans l’interface utilisateur :** Client > Audiences > Créer une audience > Créer une règle (sélectionnez Compte comme type d’audience)

**Détails de configuration clés :**

- Sélectionnez « Compte » comme type d’audience lors de la création d’une audience dans le créateur de segments.
- Les attributs de compte apparaissent sous la section Compte dans le créateur de segments (secteur, chiffre d’affaires, statut du compte)
- Les attributs et les activités de personne peuvent être ajoutés par le biais de la relation « Personnes » dans le créateur d’audiences du compte
- Configurez un planning d’évaluation par lots s’il n’existe pas déjà pour le sandbox
- Créez des audiences de ciblage (comptes à inclure) et de suppression (comptes à exclure)

**Documentation Experience League :**

- [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Phase 3 : configuration de la destination

Cette phase établit des connexions authentifiées aux destinations cibles où les audiences de compte seront diffusées.

**Fonction d’application :** [!DNL RT-CDP] B2B : configuration de la destination du compte, [!DNL RT-CDP] B2B : intégration de [!DNL Marketo Engage], [!DNL RT-CDP] : configuration de la destination

**Éléments à configurer :** cette phase établit des connexions authentifiées aux destinations cibles où les audiences de compte seront diffusées. La configuration comprend la sélection de la destination dans le catalogue, la fourniture des informations d’authentification, la configuration des mappages de champs au niveau du compte et au niveau de la personne, ainsi que la définition du planning d’exportation. Chaque type de destination a des exigences et des fonctionnalités uniques.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : sélection de la destination**
>
>Quelle(s) destination(s) recevront les audiences de compte activées ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| [!DNL Marketo Engage] | Préparation, notation et exécution de campagne des prospects B2B | Connecteur de streaming natif. Met à jour les enregistrements de lead/contact. Nécessite des informations d’identification d’API [!DNL Marketo] (Munchkin ID, Client ID, Secret client). |
>| [!DNL LinkedIn] audiences correspondantes | Publicité basée sur les comptes sur [!DNL LinkedIn] | Prend en charge la correspondance des noms de société et des domaines pour le ciblage au niveau du compte. Activation par lots. Nécessite un accès [!DNL LinkedIn] Campaign Manager. |
>| [!DNL Salesforce] CRM | Activation des ventes et synchronisation des listes de comptes CRM | Le connecteur de diffusion en continu met à jour les enregistrements de compte ou de contact. Nécessite un accès [!DNL Salesforce] à l’API avec des autorisations d’écriture. |
>| [!DNL Microsoft Dynamics 365] | Activation des ventes pour les organisations basées sur [!DNL Dynamics] | Connecteur de streaming. Nécessite un accès [!DNL Dynamics 365] à l’API . |
>| Espace de stockage ([!DNL S3], [!DNL Azure Blob], [!DNL GCS], SFTP) | Intégrations personnalisées, Data Warehouse, partage de partenaires | Exportation par lots basée sur des fichiers. Flexibilité maximale, mais nécessite un traitement en aval. |
>| Correspondance client [!DNL Google] | Rechercher et afficher le ciblage publicitaire | Correspondance au niveau de la personne par e-mail haché. Activation par lots. |
>| [!DNL The Trade Desk] | Affichage programmatique et publicité vidéo | Correspondance au niveau de la personne. Activation par lots. |

>[!NOTE]
>**Décision : stratégie de mappage des champs**
>
>Quels champs de compte et de personne doivent être mappés à la destination ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Champs d’identité uniquement | Plateformes Advertising qui n&#39;ont besoin que d&#39;identifiants correspondants | Transfert de données minimal. Correspondances de destination sur l’e-mail ou le domaine de l’entreprise. |
>| Attributs d’identité + de compte principal | CRM ou [!DNL Marketo] où le contexte du compte améliore le ciblage | Inclure le secteur, le chiffre d’affaires, le nombre d’employés, le niveau de compte. Enrichir les enregistrements en aval. |
>| Jeu complet d’attributs | Exportations d’entrepôt de données ou de stockage dans le cloud | Incluez tous les attributs de compte et de personne pertinents. Payload d’exportation la plus importante. |

**Navigation dans l’interface utilisateur :** Connexions > Destinations > Catalogue > Rechercher la destination > Configurer

**Détails de configuration clés :**

- Accédez au catalogue des destinations et sélectionnez la destination cible
- Fournir des informations d’authentification spécifiques au type de destination
- Configurer les mappages de champs connectant [!DNL RT-CDP] champs XDM aux champs de destination
- Par [!DNL Marketo Engage] : indiquez l’ID Munchkin, l’ID client et le secret client
- Par [!DNL LinkedIn] : autoriser via OAuth et sélectionner le compte publicitaire [!DNL LinkedIn]
- Pour l’espace de stockage dans le cloud : indiquez le nom du compartiment ou du conteneur, le chemin, le format de fichier et les informations d’identification
- Pour le CRM : indiquez l’URL de l’instance, les informations d’identification de l’API et le type d’objet cible (compte ou contact)

**Là où les options divergent :**

**Pour L’Option A (Diffusion En Continu [!DNL Marketo Engage]) :**

Accédez à Destinations > Catalogue > Adobe > [!DNL Marketo Engage]. Configurez l’ID Munchkin et les informations d’identification d’API. Mappez les champs d’identité [!DNL RT-CDP] (e-mail) et les attributs de profil aux champs de prospect [!DNL Marketo]. La destination gère automatiquement les mises à jour en flux continu incrémentielles.

**Pour L’Option B (Lot Advertising Platform) :**

Accédez à Destinations > Catalogue > Advertising/Social > sélectionnez la plateforme. Autoriser via OAuth. Configurez le planning d&#39;export (recommandé : quotidien). Mappez les identifiants d’e-mail hachés et tous les champs correspondants pris en charge. Par [!DNL LinkedIn], mappez également les champs nom de société et domaine pour la correspondance au niveau du compte.

**Pour L’Option C (Basée Sur Des Fichiers De Stockage Dans Le Cloud) :**

Accédez à Destinations > Catalogue > Espace de stockage > sélectionner un fournisseur. Configurez le compartiment ou le conteneur, le modèle de chemin d’accès au fichier et le format de fichier (CSV, JSON ou Parquet). Définissez le planning d’exportation et choisissez l’exportation complète ou incrémentielle. Mappez tous les champs d’attribut de compte et de personne souhaités.

**Pour l’option D (diffusion en continu CRM) :**

Accédez à Destinations > Catalogue > CRM > sélectionnez [!DNL Salesforce] ou [!DNL Dynamics]. Fournissez les informations d’identification d’API et l’URL de l’instance. Mappez les champs [!DNL RT-CDP] aux champs de compte ou de contact CRM. Assurez-vous que les champs personnalisés existent dans le CRM pour recevoir les données d’appartenance à l’audience.

**Documentation Experience League :**

- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Destination Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Destination des audiences correspondantes LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Destination Salesforce CRM](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Destination Amazon S3](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)

### Phase 4 : activation de l’audience

Cette phase publie les audiences de compte évaluées vers les destinations configurées.

**Fonction d’application :** [!DNL RT-CDP] B2B : Compte Audience Activation, [!DNL RT-CDP] : Audience Activation

**Éléments à configurer :** cette phase publie les audiences de compte évaluées vers les destinations configurées. L’activation crée le flux de données connectant l’audience du compte (source) à la destination externe (cible), applique les mappages d’attributs et lance l’exportation selon le planning ou le comportement de diffusion en continu configuré. Vous configurerez également les audiences de suppression pour exclure les comptes inéligibles de l’activation.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : type d’exportation**
>
>L’activation doit-elle exporter des instantanés d’audience complets ou uniquement des modifications incrémentielles ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Exportation incrémentielle | Destinations de diffusion en continu ([!DNL Marketo], CRM) ou par lots pour lesquelles les systèmes en aval gèrent les deltas | Un volume de données plus petit par exportation. Traitement plus rapide. Nécessite des systèmes en aval pour gérer l’état. Valeur par défaut pour les destinations de diffusion en continu. |
>| Exportation complète | Destinations par lots pour lesquelles le système en aval remplace l’audience complète à chaque exécution | Volume de données plus important mais logique en aval plus simple. Utile lorsque les systèmes en aval ne conservent pas l’état . Disponible pour les destinations basées sur des fichiers. |

>[!NOTE]
>**Décision : portée de l’activation**
>
>Combien d’audiences doivent être activées par destination ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Audience unique par flux de données | Activation simple avec un mappage audience-destination clair | Plus facile à surveiller et à dépanner. Un échec d’audience n’en affecte pas d’autres. |
>| Plusieurs audiences par flux de données | Plusieurs audiences associées allant vers la même destination | Utilisation plus efficace des connexions de destination. Toutes les audiences partagent le même mappage de champ et le même planning. |

**Navigation dans l’interface utilisateur :** Connexions > Destinations > Parcourir > Sélectionner la destination > Activer les audiences

**Détails de configuration clés :**

- Sélectionnez l’audience cible dans la liste des audiences
- Examinez et confirmez les mappages de champs configurés au cours de la phase 3
- Pour les destinations par lots : configurer le planning d’exportation (heure, fréquence)
- Pour les destinations de streaming : l’activation commence immédiatement après la configuration
- Ajoutez éventuellement des audiences de suppression à l’aide de la fonctionnalité d’exclusion
- Déclenchez une exécution d’activation de test initiale pour valider le flux de données

**Là où les options divergent :**

**Pour L’Option A (Diffusion En Continu [!DNL Marketo Engage]) :**

Sélectionnez les audiences de compte à activer. L’activation commence immédiatement. Vérifiez dans [!DNL Marketo] que les enregistrements du lead/contact sont mis à jour avec les champs d’appartenance au segment. Configurez [!DNL Marketo] campagnes intelligentes à déclencher en fonction de ces modifications de champ.

**Pour L’Option B (Lot Advertising Platform) :**

Sélectionnez les audiences du compte et configurez le planning d’exportation quotidien. Une fois la première exportation terminée, vérifiez sur la plateforme publicitaire que l’audience s’affiche et qu’elle comporte un nombre de membres renseigné. Comptez 24 à 48 heures pour que la plateforme traite le fichier d’audience initial.

**Pour L’Option C (Basée Sur Des Fichiers De Stockage Dans Le Cloud) :**

Sélectionnez les audiences de compte et configurez le planning d’exportation et le format de fichier. Après la première exportation, vérifiez que les fichiers apparaissent à l’emplacement de stockage cible avec le format et le contenu attendus. Confirmez que les processus d’importation en aval utilisent correctement les fichiers exportés.

**Pour l’option D (diffusion en continu CRM) :**

Sélectionnez les audiences de compte à activer. L’activation commence immédiatement. Vérifiez dans le CRM que les enregistrements de compte ou de contact sont mis à jour avec les champs mappés. Configurez les rapports CRM, les vues de liste ou l’automatisation des workflows pour agir sur les champs mis à jour.

**Documentation Experience League :**

- [Activer les audiences vers des destinations de diffusion en continu](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activer les audiences vers des destinations par lots](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)

### Phase 5 : gouvernance et surveillance

Cette phase garantit que l’activation de l’audience du compte respecte les politiques de gouvernance des données et les préférences de consentement, et que l’intégrité des flux de données d’activation continus est surveillée.

**Fonction d’application :** [!DNL RT-CDP] B2B : gouvernance des données B2B, [!DNL RT-CDP] : application du consentement et de la gouvernance

**Éléments que vous devez configurer :** cette phase garantit que l’activation de l’audience du compte est conforme aux politiques de gouvernance des données et aux préférences de consentement, et que l’intégrité des flux de données d’activation continus est surveillée. La gouvernance des données B2B applique des restrictions sur les attributs de compte sensibles (chiffre d’affaires, nombre d’employés provenant de fournisseurs tiers), tandis que l’application du consentement garantit que les communications au niveau de la personne respectent les préférences de désinscription. La surveillance confirme que les flux de données d’activation se terminent correctement.

**Points de décision au cours de cette phase :**

>[!NOTE]
>**Décision : niveau d’application de la gouvernance**
>
>Comment la gouvernance des données doit-elle être appliquée strictement pour les activations B2B ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Application complète (blocage en cas de violation) | Activations de production avec des données sensibles | Empêche toute activation en violation des politiques de gouvernance. Peut nécessiter des ajustements itératifs du mappage des champs pour résoudre les violations. |
>| Avertir et continuer | Environnements de développement ou de test | Autorise l’activation, mais consigne les avertissements. Utile lors de la configuration initiale pour identifier les problèmes potentiels. |

>[!NOTE]
>**Décision : approche de suivi**
>
>Comment l’intégrité de l’activation doit-elle être surveillée ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Surveillance basée sur les alertes | Environnements de production dans lesquels les échecs doivent être rapidement détectés | Configurez des alertes pour les échecs d’activation de destination, les échecs de flux source et les retards de flux de données. Nécessite une configuration d’abonnement aux alertes. |
>| Surveillance manuelle | Développement ou activations de faible volume | Examinez régulièrement les exécutions de flux de données dans l’interface utilisateur des destinations. Moins de frais généraux mais risque de détection tardive des défaillances. |
>| Les deux | Environnements de production avec activation multi-destination complexe | Alertes pour les échecs critiques et examen périodique du tableau de bord pour les tendances. Recommandé pour la plupart des implémentations B2B. |

**Navigation dans l’interface utilisateur :** Confidentialité > Politiques (pour la gouvernance), Connexions > Destinations > Parcourir > Sélectionner la destination > Exécutions de flux de données (pour la surveillance)

**Détails de configuration clés :**

- Appliquer des libellés d’utilisation des données aux jeux de données B2B contenant des attributs restreints
- Vérifiez que les politiques de gouvernance sont appliquées en évaluant l’activation par rapport à l’action marketing cible
- Configurer des alertes pour les échecs d’activation de destination et les échecs du connecteur source
- Examinez les mesures d’exécution du flux de données (profils exportés, enregistrements ayant échoué) après chaque cycle d’activation
- Configurer la révision du tableau de bord d’utilisation des licences pour suivre le volume du profil de compte par rapport aux droits

**Documentation Experience League :**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Surveillance des flux de données de destination](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## Considérations relatives à la mise en œuvre

Les sections suivantes apportent des conseils supplémentaires pour une implémentation réussie.

### Mécanismes de sécurisation et limites

Examinez les mécanismes de sécurisation et limites de plateforme suivants qui s’appliquent à ce modèle de cas d’utilisation.

- Maximum de 4 000 définitions de segment par sandbox, y compris les audiences de compte — [Mécanismes de sécurisation de segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Les audiences de compte sont principalement évaluées à l’aide de l’évaluation par lots ; l’éligibilité de diffusion en continu est limitée à de simples conditions d’attribut de compte
- Maximum de 100 flux de données par connexion de destination — [Mécanismes de sécurisation des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- Les destinations par lots exportent jusqu’à 5 millions de profils par segment de fichier
- Les destinations de diffusion en continu ont des limites de débit par seconde définies par le partenaire de destination (par exemple, les limites de débit de l’API [!DNL Marketo])
- Les audiences composées (à partir de la composition de l’audience) sont limitées à l’évaluation par lots et ne peuvent pas utiliser la diffusion en continu
- Maximum de 10 blocs de composition par zone de travail de composition d’audience
- [!DNL LinkedIn] audiences correspondantes nécessitent une taille d’audience minimale (généralement 300 membres) pour l’activation
- Les destinations de streaming CRM sont soumises aux limites de débit d’API du fournisseur CRM (par exemple, [!DNL Salesforce] limites quotidiennes d’API en masse)
- [!DNL RT-CDP] licence B2B edition régit le nombre total de profils de compte professionnel — [description du produit RT-CDP](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

### Pièges courants

Tenez compte des problèmes courants suivants lors de l’implémentation de ce modèle de cas d’utilisation.

- **Mappage personne-compte incomplet :** si les enregistrements de personne (leads, contacts) ne sont pas correctement liés aux enregistrements de compte par le biais de la résolution d’identité B2B, les audiences de compte qui dépendent des attributs de personne ou des activités sous-compteront les comptes éligibles. Validez les relations personne à compte dans F4 avant de créer des audiences de compte.

- **Données CRM obsolètes provoquant une dérive de l’audience :** si les connecteurs source CRM ne s’exécutent pas selon un planning régulier ou échouent silencieusement, les attributs de compte (secteur, chiffre d’affaires, statut) deviennent obsolètes. Par conséquent, les audiences incluent des comptes qui ne remplissent plus les critères ou excluent des comptes qui devraient remplir les critères. Surveillez l’intégrité du flux de données du connecteur source.

- **Attentes de taux de correspondance de plateforme Advertising :** lors de l’activation d’audiences de compte sur des plateformes publicitaires autres que [!DNL LinkedIn], le taux de correspondance dépend de la présence d’identifiants valides au niveau de la personne (e-mail haché) pour les contacts associés aux comptes qualifiés. Les comptes sans contact associé ayant une adresse e-mail ne correspondent pas. Surveillez les taux de correspondance et envisagez d’enrichir les données de contact.

- Mauvais alignement du mappage des champs de **[!DNL Marketo]:** lors de la diffusion en continu vers [!DNL Marketo Engage], le mappage des champs de [!DNL RT-CDP] doit cibler les champs de prospect ou de contact [!DNL Marketo] existants. Si le champ [!DNL Marketo] mappé n’existe pas, la mise à jour échoue silencieusement. Précréez tous les champs cibles dans [!DNL Marketo] avant de configurer la destination.

- **Activation du blocage des politiques de gouvernance :** les libellés d’utilisation des données sur les champs d’attribut de compte (en particulier les données firmographiques tierces) peuvent déclencher des violations de gouvernance lors de l’activation vers des destinations publicitaires. Évaluez la conformité de la gouvernance avant d’activer et d’ajuster les mappages des champs pour exclure les champs restreints si nécessaire.

- **Audience de compte combinant des données de compte et de personne avec une évaluation par lots uniquement :** les audiences de compte qui font référence à des événements comportementaux au niveau de la personne (par exemple, « comptes où au moins un contact a ouvert un e-mail au cours des 30 derniers jours ») nécessitent une évaluation par lots. Si le cas d’utilisation nécessite une qualification en temps réel, cette contrainte peut entraîner une latence inattendue.

### Bonnes pratiques

Suivez ces recommandations pour obtenir des résultats optimaux.

- Commencez par un petit nombre d’audiences de compte bien définies (niveau ICP, secteur vertical, niveau d’engagement) avant de passer à des définitions d’attributs multiples complexes
- Créez des audiences de suppression dédiées pour les clients existants, les opportunités actives et les comptes récemment engagés afin d’éviter les dépenses inutiles et les conflits de canal
- Utilisez la composition de l’audience pour créer des audiences de compte à plusieurs niveaux (engagement élevé/moyen/faible) en classant les comptes selon les scores d’engagement agrégés
- Activez la même audience de compte vers plusieurs destinations simultanément pour des campagnes multicanal coordonnées (par exemple, [!DNL LinkedIn] pour la publicité, [!DNL Marketo] pour les e-mails, CRM pour la visibilité des ventes).
- Implémenter une convention de nommage cohérente pour les audiences de compte qui inclut les critères de ciblage et le canal prévu (par exemple, « B2B_ICP_Enterprise_Tech_LinkedIn » ou « B2B_Suppression_ActiveOpps »)
- Planifiez l’activation des lots pendant les heures creuses afin de minimiser l’impact sur les systèmes en aval et de respecter les fenêtres de traitement de la plateforme publicitaire .
- Surveillez les taux de correspondance par destination après l’activation initiale et effectuez une itération sur les mappages de champs d’identité pour améliorer la correspondance
- Gérer le flux de données bidirectionnel avec [!DNL Marketo Engage] : ingérer les données d’engagement de [!DNL Marketo] dans [!DNL RT-CDP] (connecteur source) et réactiver les audiences dans [!DNL Marketo] (connecteur de destination) pour un système en boucle fermée

### Décisions de compromis

Tenez compte des compromis suivants lors de la prise de décisions de mise en œuvre.

>[!NOTE]
>**Compromis : fraîcheur d’audience par rapport à complexité de l’évaluation**
>
>Les audiences de compte qui combinent les attributs de compte aux données comportementales au niveau de la personne fournissent le ciblage le plus précis, mais sont limitées à l’évaluation par lots (actualisation quotidienne). Des audiences plus simples basées sur les attributs de compte seuls peuvent être qualifiées pour l’évaluation en flux continu avec des mises à jour en temps quasi réel.
>
>- **Favoris par lot (critères complexes) :** précision du ciblage, combinaison de signaux firmographiques et comportementaux, notation complète des comptes
>- **La diffusion en continu (critères simples) est privilégiée :** vitesse de mise à jour de l’audience, réponse en temps réel aux changements de compte, délai d’action plus rapide dans [!DNL Marketo] et CRM
>- **Recommandation :** utilisez l’évaluation par lots pour les audiences de ciblage principal où l’actualisation quotidienne est acceptable (la plupart des cas d’utilisation B2B). Réservez l’évaluation en continu pour les déclencheurs sensibles au temps tels que les changements de statut du compte ou les alertes de compte de grande valeur.

>[!NOTE]
>**Compromis : activation centralisée par rapport aux audiences spécifiques à une destination**
>
>Vous pouvez activer une audience de compte unifié unique vers plusieurs destinations ou créer des audiences spécifiques à la destination, adaptées aux fonctionnalités et aux exigences de chaque canal.
>
>- **Avantages de l’audience centralisée :** cohérence entre les canaux, gestion simplifiée de l’audience, reporting unifié.
>- **Les audiences spécifiques aux destinations privilégient :** le ciblage optimisé par canal (par exemple, [!DNL LinkedIn] bénéficie des attributs au niveau de l’entreprise tandis que [!DNL Marketo] a besoin de détails au niveau du lead), ainsi que des règles de suppression spécifiques au canal
>- **Recommandation :** commencez par des audiences centralisées pour des raisons de cohérence, puis créez des variantes spécifiques à la destination uniquement lorsque les exigences du canal divergent considérablement (par exemple, des fenêtres de suppression différentes pour la publicité et les e-mails).

>[!NOTE]
>**Compromis : synchronisation de Real-time CRM par rapport aux mises à jour CRM par lots**
>
>La diffusion en continu vers CRM offre une visibilité immédiate des ventes, mais utilise le quota d’API CRM. Les exportations de fichiers par lots sont plus efficaces, mais introduisent une latence.
>
>- **La synchronisation CRM en flux continu favorise : réactivité des ventes** alertes de compte immédiates, visibilité du pipeline en temps réel.
>- **Les mises à jour CRM par lots favorisent :** la conservation des quotas d’API, l’efficacité des mises à jour en masse, l’alignement avec les fenêtres de chargement des données CRM
>- **Recommandation :** utilisez la synchronisation CRM en flux continu pour les modifications de qualification de compte hautement prioritaires (par exemple, le compte passe au niveau « Prêt pour les ventes »). Utilisez les exportations de fichiers par lots pour les mises à jour en bloc telles que les actualisations mensuelles des scores de compte ou les listes de réaffectation de territoire.

## Documentation connexe

Les ressources suivantes fournissent un contexte supplémentaire et des conseils détaillés pour les fonctionnalités utilisées dans ce modèle de cas d’utilisation.

**[!DNL RT-CDP]B2B edition**

- [Présentation de Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Schémas B2B dans Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Audiences de compte](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Description du produit RT-CDP B2B edition](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**Évaluation et segmentation des audiences**

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Composition de l’audience](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Destinations et activation**

- [Aperçu des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Destination Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Destination des audiences correspondantes LinkedIn](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Destination Salesforce CRM](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Destination Microsoft Dynamics 365](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Destination Amazon S3](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Activer les audiences vers des destinations de diffusion en continu](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activer les audiences vers des destinations par lots](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

**Sources de données et connecteurs**

- [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Connecteur Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Connecteur Salesforce](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

**Modélisation des données et identité**

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Présentation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Présentation du profil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Gouvernance et confidentialité des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Surveillance et observabilité**

- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Surveillance des flux de données de destination](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Surveiller les flux de données sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/api-tutorials/monitor)
- [Tableau de bord d’utilisation des licences](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Rapports et analyses**

- [Présentation de CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Présentation des connexions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Présentation des vues de données](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

**Tutoriels et guides**

- [Prise en main de Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Création d’un schéma pour les sources B2B](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Outil Sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
