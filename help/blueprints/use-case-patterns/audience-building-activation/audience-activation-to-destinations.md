---
title: Activation de l’audience vers les destinations
description: Découvrez comment évaluer et publier des segments d’audience vers des destinations externes à des fins de ciblage ou de suppression à l’aide d’Adobe Real-Time CDP.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '7005'
ht-degree: 1%

---


# Activation de l’audience vers les destinations

Ce guide fournit une référence d’implémentation complète pour l’activation des audiences d’Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP) vers des destinations externes. Il est conçu pour les architectes de solution, les technologues marketing et les ingénieurs d’implémentation qui ont besoin d’évaluer les segments d’audience et de les publier sur des plateformes publicitaires, un stockage dans le cloud, des systèmes de gestion de la relation client ou des partenaires de données pour le ciblage, la suppression, la modélisation semblable ou l’enrichissement des analyses.

Il présente toutes les options de mise en œuvre viables avec une analyse des compromis, une orientation des décisions, des chemins de navigation dans l’interface utilisateur et des références à la documentation d’Experience League.

Le guide couvre le cycle de vie complet de l’activation des audiences, depuis la définition et l’évaluation des segments d’audience jusqu’à la surveillance de l’intégrité de l’activation et l’application de la conformité en matière de gouvernance, en passant par la configuration des connexions de destination et la publication des audiences.

## Présentation du cas d’utilisation

Les entreprises ont besoin de diffuser des données d’audience vers des systèmes externes pour alimenter des campagnes multimédia payantes, enrichir les enregistrements CRM, partager des données avec des partenaires ou alimenter des analyses en aval. Audience Activation vers les destinations est le modèle d’activation fondamental de RT-CDP : il évalue les profils qui remplissent les critères d’une audience cible, se connecte à une ou plusieurs destinations externes, mappe les attributs de profil aux champs spécifiques à la destination et publie l’audience pour la consommation en aval.

Ce modèle s’applique chaque fois que l’objectif est d’envoyer les données d’audience à un système externe dans le bon format au bon moment. Il n’implique pas de diffusion de messages, de personnalisation sur site ou d’analyse. Il s’agit du point de départ le plus courant pour les implémentations de RT-CDP et sert de bloc de création que d’autres modèles complètent.

Les parties prenantes incluent généralement les équipes de marketing numérique qui gèrent les médias achetés, les équipes de données qui enrichissent les entrepôts, les équipes de gestion de la relation client qui préparent les listes de contacts pour les campagnes et les équipes de confidentialité qui assurent la conformité de la gouvernance sur les flux de données sortants.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont atteints par ce modèle d’utilisation.

### Acquérir de nouveaux clients

Étendez votre base de clients grâce à des campagnes d’acquisition ciblées, des audiences semblables et l’optimisation des médias achetés.

**KPI : nouveaux clients** coût d’acquisition client, conversion des prospects et des leads

[En savoir plus sur l’acquisition de nouveaux clients](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Réduire le coût d’acquisition du client

Améliorez l’efficacité du ciblage, supprimez les clients existants des campagnes d’acquisition et optimisez les dépenses multimédia.

**KPI :** coût d’acquisition client, coût par lead, efficacité

[En savoir plus sur la réduction du coût d’acquisition des clients](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Optimiser les dépenses marketing et le retour sur investissement

Améliorez le retour sur investissement marketing grâce à un meilleur ciblage, une meilleure attribution, la suppression de l’audience et une affectation budgétaire plus efficace.

**KPI :** économies de coûts, coût d’acquisition client, revenus incrémentiels

[En savoir plus sur l’optimisation des dépenses marketing et du retour sur investissement](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Exemples de cas d’utilisation tactiques

- **Ciblage des audiences de plateforme publicitaire** — Envoyez les segments qualifiés par push aux plateformes de médias payants pour le ciblage des campagnes
- **Suppression payante des médias des clients existants** — Excluez les clients connus des campagnes d’acquisition sur les plateformes publicitaires afin d’éliminer le gaspillage
- **Audiences de contrôle semblables** — Intégrez les segments clients à forte valeur ajoutée à Facebook, Google Ads ou The Trade Desk en tant qu’audiences de contrôle pour le développement semblables
- **Synchronisation CRM pour l’activation des ventes** — Activez les audiences à forte intention ou à forte valeur afin que les équipes commerciales puissent donner la priorité à la sensibilisation.
- **Partage d’audiences des partenaires de données** — Partagez des segments d’audience qualifiés avec des partenaires de données pour le ciblage ou la mesure de coopération
- **Exportation de l’espace de stockage pour l’enrichissement de l’entrepôt de données** — Exportez les attributs d’appartenance et de profil de l’audience vers Amazon S3, Azure Blob, Google Cloud Storage ou SFTP pour les analyses en aval
- **Activation du reciblage d’audience** — Activez les visiteurs du site qui n’ont pas effectué de conversion vers des plateformes de reciblage
- **Synchronisation de la liste de contacts avec les fournisseurs de services de messagerie** — Intégrer l’appartenance de l’audience aux plateformes de messagerie tierces pour une diffusion coordonnée

## Indicateurs clés de performance

| KPI | Description | Guide de mesure |
| --- | --- | --- |
| Coût d’acquisition client (CAC) | Coût d’acquisition d’un nouveau client via des audiences activées | Total des dépenses média / nouveaux clients attribués aux audiences activées |
| Taux de correspondance d’audience | Pourcentage de profils activés correspondant avec succès à la destination | Profils correspondants à la destination / profils exportés depuis RT-CDP |
| Économies de suppression | Dépenses de médias évitées en supprimant les clients existants des campagnes d’acquisition | CPM estimée x taille d’audience supprimée |
| Taux De Diffusion D’Activation | Pourcentage de profils envoyés avec succès à la destination | Profils diffusés / profils dans l’audience source |
| Délai d’activation | Temps écoulé entre la définition de l’audience et la première diffusion à la destination | Mesure de la création du segment à la première exécution confirmée du flux de données |
| Précision de la population d’audience | Alignement entre les tailles d’audience attendue et réelle au niveau de la destination | Nombre de profils des audiences de destination/nombre de profils des audiences RT-CDP |

## Modèle de cas d’utilisation

**Audience Activation vers les destinations** — Évaluez et publiez un segment ciblé vers des destinations externes à des fins de ciblage ou de suppression.

**Chaîne de fonctions :** Évaluation d’audience > Configuration de la destination > Audience Activation > Surveillance

## Applications

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — Évaluation de l’audience, gestion de la destination, activation de l’audience, consentement et application de la gouvernance
- **Adobe [!DNL Experience Platform] (AEP)** — Banque de profils, service d’identités, moteur de segmentation, gouvernance des données

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction fondamentale | Etat | Ce qui doit être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Supposé en place | La sandbox RT-CDP est configurée et active. Autorisations de gestion et d’activation des destinations attribuées aux rôles d’implémentation. Identifiants du compte de destination disponibles pour les plateformes cibles. | [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Le schéma de profil doit inclure des attributs qui seront mappés aux champs de destination (par exemple, e-mail, téléphone, identifiants hachés, attributs démographiques). Le schéma doit être activé pour le profil avec les jeux de données recevant activement des données. | [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Principes de base de la composition des schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Sources et collecte de données | Supposé en place | Les données de profil qui alimentent l’évaluation des audiences doivent être ingérées et actuelles. Les pipelines d’ingestion par lots et/ou en flux continu sont opérationnels. SDK Web, connecteurs source ou ingestion par lots transmettant des données dans des jeux de données activés pour les profils. | [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Configuration des identités et des profils | Obligatoire | Les espaces de noms d’identité pour la correspondance de destinations doivent être configurés (par exemple, e-mail haché pour les audiences personnalisées Facebook, correspondance client Google Ads). Les politiques de fusion doivent produire des profils unifiés avec tous les attributs requis pour l’activation. | [présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home), [présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Définition et segmentation de l’audience | Obligatoire | Audience cible définie à l’aide du créateur de segments, de la composition de l’audience ou de la composition d’audiences fédérées. Méthode d’évaluation (par lots, en flux continu ou Edge) sélectionnée en fonction des besoins de latence d’activation. Cette fonction est exercée à la phase 1 du plan. | [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder) |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Pourquoi est-ce important ? | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Recommandé | Les attributs calculés tels que la valeur de durée de vie, le score d’engagement ou le score de propension améliorent la précision de l’audience et fournissent des attributs d’enrichissement à mapper aux destinations. Particulièrement utile lorsque les destinations bénéficient d’une segmentation d’audience basée sur les valeurs ou sur les scores. | [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Gestion du cycle de vie des données | Recommandé | Les politiques d’expiration des jeux de données et des profils garantissent la fraîcheur et la conformité des données. La configuration du schéma de consentement garantit que seuls les profils consentis sont activés. Critique pour la conformité réglementaire lors de l’exportation de données vers des systèmes externes. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Recommandé | Les étiquettes et les politiques de gouvernance empêchent l’activation de données restreintes vers des destinations non autorisées (par exemple, les informations d’identification personnelles vers les plateformes publicitaires, les segments sensibles vers les partenaires de données). Particulièrement important pour l’activation des audiences vers des systèmes tiers externes. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Présentation des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview) |
| Surveillance et observabilité | Inclus | La surveillance de l’activation fait partie de la chaîne fonctionnelle (phase 5). Couvre la surveillance de l’exécution du flux de données, les alertes de statut de diffusion, le suivi de la population d’audiences et la visibilité de l’utilisation des licences. | [Surveillance des flux de données de destination](https://experienceleague.adobe.com/fr/docs/experience-platform/dataflows/ui/monitor-destinations), [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview) |
| Rapports et analyses | Recommandé | L’analyse CJA de l’efficacité de l’activation des audiences permet de mesurer les performances des audiences activées (par exemple, l’effet élévateur de conversion suite à la suppression, le retour sur dépenses publicitaires suite à des audiences semblables). | Présentation de [CJA](https://experienceleague.adobe.com/fr/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Real-Time CDP] (RT-CDP)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Évaluation d’audience | Phase 1 : évaluation de l’audience | Définissez des règles d’audience et évaluez l’appartenance à un segment à l’aide de méthodes d’évaluation par lots, en flux continu ou Edge |
| Composition de l’audience | Phase 1 : évaluation de l’audience | Vous pouvez éventuellement composer des audiences dérivées à l’aide d’opérations d’enrichissement, de classement, de partage, d’exclusion et de jointure pour une logique d’audience complexe |
| Configuration de la destination | Phase 2 : configuration de la destination | Configurer des connexions authentifiées à des destinations externes avec des paramètres de mappage et de planification des champs |
| Activation d’audience | Phase 3 : Audience Activation | Publier les audiences évaluées vers des destinations configurées avec le mappage des attributs et la planification des exportations |
| Application du consentement et de la gouvernance | Phase 4 : validation de la gouvernance | Application des préférences de consentement et des politiques d’utilisation des données avant et pendant l’activation de l’audience aux systèmes externes |

## Conditions préalables

- [ ] licence RT-CDP est active avec les droits d’activation d’audience
- [ ] sandbox Target est configuré et accessible à l’équipe d’implémentation
- [ ] Les rôles utilisateur incluent les autorisations de gestion des destinations et d’activation des audiences
- [ ] informations d’authentification pour chaque destination cible sont disponibles (jetons OAuth, clés API, clés d’accès S3 ou informations d’identification de compte de service)
- [ ] schéma Profil comprend tous les attributs qui doivent être mappés aux champs de destination
- [ ] espaces de noms d’identité requis pour la correspondance de destinations sont configurés (par exemple, e-mail haché, téléphone, identifiants d’appareil)
- [ ] Les pipelines d’ingestion de données sont opérationnels et les profils renseignent la banque de profils
- [ ] Les étiquettes et les politiques de gouvernance des données sont examinées pour les attributs activés (en particulier pour les destinations externes)
- [ ] champs de consentement sont renseignés sur les profils si le filtrage basé sur le consentement est obligatoire

## Options de mise en œuvre

Les options d’implémentation suivantes sont disponibles pour ce modèle de cas d’utilisation. Examinez chaque option et le tableau de comparaison pour déterminer la meilleure approche pour vos besoins.

### Option A : activation de la destination de diffusion en continu

**Idéal pour** mises à jour en temps réel de l’abonnement des audiences sur les plateformes publicitaires ou les systèmes partenaires : audiences personnalisées de Facebook, correspondance client Google Ads, audiences correspondantes LinkedIn, Trade Desk et autres destinations basées sur les API de streaming similaires.

**Fonctionnement :**

L’activation de la destination de diffusion en continu apporte des modifications d’appartenance à l’audience à la destination en temps quasi réel à mesure que les profils sont qualifiés ou disqualifiés du segment. Lorsqu’un attribut de profil change ou qu’un événement comportemental se produit, entraînant l’entrée ou la sortie d’un profil dans une audience, la mise à jour d’abonnement est diffusée en continu vers la destination en quelques minutes.

Cette approche nécessite un connecteur de destination de diffusion en continu (la plupart des principales plateformes publicitaires le prennent en charge) et une méthode d’évaluation d’audience en flux continu ou Edge. L’évaluation de l’audience surveille en permanence les modifications de profil admissibles et le flux de données d’activation envoie les mises à jour au fur et à mesure. La destination reçoit des modifications d’adhésion incrémentielles plutôt que des instantanés d’audience complets.

L’activation par flux est la valeur par défaut pour la plupart des destinations de plateforme publicitaire dans le catalogue RT-CDP. Le connecteur de destination gère automatiquement l’authentification de l’API, la limitation du débit et la logique de reprise.

**Considérations principales :**

- L’évaluation de l’audience doit utiliser l’évaluation Edge ou en flux continu (les audiences par lots uniquement ne peuvent pas alimenter les destinations en flux continu en temps réel)
- Toutes les expressions de segment ne sont pas qualifiées pour l’évaluation en flux continu : les agrégations complexes, les requêtes d’entités multiples et certaines fonctions temporelles nécessitent des lots
- Les limites de débit de l’API du partenaire de destination peuvent affecter le débit pendant les événements de qualification d’audience volumineux
- Les mises à jour des attributs de profil sont envoyées avec les modifications d’appartenance, pour maintenir les données de destination à jour

**Avantages :**

- Actualisation de l’audience en temps quasi réel au niveau de la destination (minutes, et non heures)
- Les mises à jour incrémentielles réduisent le volume de transfert de données par rapport aux exportations complètes
- Gestion automatique des événements de qualification et de disqualification
- La plupart des destinations de plateforme publicitaire prennent en charge la diffusion en continu de manière native

**Limitations :**

- Nécessite des définitions de segment éligibles à la diffusion en continu (ensemble de fonctions de segment limité)
- Aucun contrôle sur le format de fichier ou la structure d’exportation - format de données déterminé par le connecteur de destination
- Impossible d’exporter vers des destinations de stockage basées sur des fichiers (S3, Azure Blob, SFTP)
- Les limites de débit de l’API de destination peuvent ralentir les modifications de volume importantes

**Experience League:**

- [Activer les audiences vers des destinations de diffusion en continu](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Catalogue des destinations de diffusion en continu](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/overview)

### Option B : activation de la destination par lots (exportation de fichiers)

**Idéal pour :** les exportations d’audiences planifiées vers des espaces de stockage dans le cloud, des entrepôts de données ou des systèmes qui consomment des importations basées sur des fichiers : Amazon S3, stockage d’objets blob Azure, stockage dans le cloud Google, SFTP, zone d’atterrissage des données.

**Fonctionnement :**

L’activation de la destination par lots évalue les audiences à une cadence planifiée et exporte les résultats sous forme de fichiers (CSV, JSON ou Parquet) vers la destination de stockage configurée. L’exportation peut inclure des instantanés d’audience complets ou des modifications incrémentielles (nouvelles qualifications et disqualifications depuis la dernière exportation).

L’implémentation implique la configuration d’une connexion de destination basée sur des fichiers avec des informations d’identification de stockage, des préférences de format de fichier (délimiteur, compression, convention d’affectation des noms) et un planning d’exportation (quotidien, toutes les 3 heures, toutes les 6 heures, etc.). Chaque exécution d’exportation génère des fichiers contenant l’appartenance à l’audience et les attributs de profil mappés.

Cette approche prend en charge le plus grand nombre de consommateurs en aval, car l’échange de données basé sur des fichiers est universellement pris en charge. Il s’agit également de la seule option pour les cas d’utilisation de stockage dans le cloud et d’enrichissement de l’entrepôt de données.

**Considérations principales :**

- L’évaluation de l’audience peut utiliser n’importe quelle méthode (par lots, en flux continu ou Edge) - l’exportation elle-même s’exécute selon un planning, indépendamment de
- Les conventions de format de fichier, de compression et de dénomination sont configurables par destination
- Prend en charge les exportations incrémentielles (modifications uniquement) et les exportations complètes (instantané d’audience complet)
- Exporter les plages de granularité de planification de toutes les 3 heures à tous les jours

**Avantages :**

- Contrôle complet du format des fichiers d’exportation (CSV, JSON, Parquet), de la compression et de l’attribution de noms
- Compatible avec tout système en aval pouvant consommer des fichiers
- Prend en charge les modes d’exportation incrémentiel et complet.
- Peut exporter des audiences avec n’importe quelle méthode d’évaluation (y compris les segments par lots uniquement avec une logique de segmentation complexe)
- Prend en charge les exécutions d’exportation ad hoc (à la demande) en dehors du planning normal

**Limitations :**

- La latence est intrinsèquement plus élevée : les données d’audience arrivent à destination selon un calendrier et non en temps réel
- Les exportations basées sur des fichiers nécessitent que le système de destination traite et ingère les fichiers
- Coûts de stockage à la destination pour les fichiers exportés
- Volumes de données plus importants par exportation par rapport aux mises à jour incrémentielles en flux continu

**Experience League:**

- [Activer les audiences vers des destinations d’exportation de profils par lots](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Catalogue des destinations basées sur des fichiers](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage)

### Option C : activation multidestination

**Idéal pour :** activer la même audience vers plusieurs destinations simultanément ; par exemple, envoyer une liste de suppression à toutes les plateformes publicitaires, synchroniser un segment à forte valeur ajoutée aux plateformes CRM et publicitaires ou coordonner la portée de l’audience entre plusieurs partenaires médias.

**Fonctionnement :**

L’activation multidestination n’est pas un mécanisme technique distinct, mais une composition des options A et B appliquée à la même audience sur plusieurs connexions de destination. La même audience est activée vers deux destinations ou plus, chacune ayant sa propre configuration de connexion, son propre mappage de champs et sa propre planification.

Chaque connexion de destination fonctionne indépendamment : une activation en flux continu vers Facebook et une exportation par lots vers S3 peuvent s’exécuter simultanément à partir de la même audience source. Les mappages de champs sont configurés par destination, de sorte que différents attributs puissent être envoyés à différents systèmes en fonction de ce dont chaque destination a besoin et de ce que les politiques de gouvernance autorisent.

Il s’agit d’un modèle de production courant pour les organisations qui opèrent sur plusieurs plateformes publicitaires, assurent la synchronisation du CRM avec l’activation des médias ou qui ont besoin de distribuer les données d’audience aux systèmes opérationnels et analytiques.

**Considérations principales :**

- Chaque destination dispose d’un mappage des champs, d’une planification et d’une évaluation de la gouvernance indépendants
- Les politiques de gouvernance sont appliquées par destination ; différents attributs peuvent être autorisés pour différents types de destination.
- Une seule audience peut être activée pour un mélange de destinations de diffusion en streaming et par lots simultanément
- L’ajout d’une nouvelle destination ne nécessite pas de modifier les activations existantes

**Avantages :**

- Répartition coordonnée de l’audience sur tous les systèmes externes à partir d’une définition d’audience unique
- Une configuration indépendante par destination permet d’optimiser les mappages et les plannings
- L’application de la gouvernance par destination garantit la conformité entre différents types de destination
- Centralise la gestion des audiences tout en prenant en charge l’activation distribuée

**Limitations :**

- Plus de connexions de destination à configurer, authentifier et gérer
- La complexité de la surveillance augmente avec chaque destination ; les échecs d’activation doivent être suivis par destination
- L’utilisation des licences (profils activés) peut être comptabilisée par destination en fonction des droits
- La maintenance du mappage des champs sur plusieurs destinations nécessite une coordination

**Experience League:**

- [Aperçu des destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/overview)

### Comparaison des options

| Critères | Option A : Diffusion En Continu | Option B : Lot (Exportation De Fichier) | Option C : Destination Multiple |
| --- | --- | --- | --- |
| Idéal pour | Ciblage et suppression de la plateforme publicitaire en temps réel | Enrichissement de Data Warehouse, intégration de systèmes basés sur des fichiers | Répartition coordonnée des audiences sur plusieurs plateformes |
| Complexité | Faible | Moyenne | Élevée |
| Latence | Minutes (temps quasi réel) | Heures (planifiées) | Combinaison de minutes et d’heures par destination |
| Contrôle du format de fichier | Aucun (la destination détermine le format) | Complet (CSV, JSON, Parquet, compression, dénomination) | Par destination |
| Évaluation d’audience | Diffusion en continu ou Edge requise | Toute méthode (lot, streaming, edge) | Exigences par destination |
| Requiert | Connecteur de destination de diffusion en continu, segment éligible à la diffusion en continu | Connecteur de destination basé sur des fichiers, informations d’identification de stockage | Plusieurs connecteurs de destination et informations d’identification |
| Gouvernance | Évaluation d’une destination unique | Évaluation d’une destination unique | Évaluation par destination |

### Choisir la bonne option

Utilisez la logique de décision suivante pour sélectionner l’approche d’implémentation appropriée :

1. **De combien de destinations avez-vous besoin ?** Si vous devez activer la même audience vers deux destinations ou plus, vous mettez en œuvre l’option C (qui comprend les options A et B par destination). Passez aux questions 2 et 3 pour chaque destination.

2. **La destination prend-elle en charge la diffusion en continu ?** Si la destination est une plateforme publicitaire (Facebook, Google Ads, LinkedIn, The Trade Desk) ou l’intégration d’un partenaire à une API de streaming, utilisez l’option A pour cette destination. Si la destination est l’espace de stockage (S3, Azure Blob, GCS, SFTP) ou un système qui consomme des fichiers, utilisez l’option B.

3. **À quelle vitesse l’audience doit-elle arriver à destination ?** Si l’appartenance à l’audience doit se refléter à la destination en quelques minutes (par exemple, la suppression en temps réel pendant les campagnes actives), utilisez l’option A. Si une diffusion quotidienne ou multi-horaire est suffisante (par exemple, actualisation hebdomadaire de l’entrepôt de données, synchronisation par lots CRM), utilisez l’option B.

4. **Votre audience utilise-t-elle une logique de segmentation complexe ?** Si la définition de l’audience inclut des agrégations multi-événements, des fenêtres temporelles volumineuses ou des fonctions qui ne remplissent pas les critères de l’évaluation par flux, utilisez l’option B (destinations par lots) ou assurez-vous que les destinations Option A reçoivent également des audiences évaluées par lots selon un planning.

## Phases de mise en œuvre

La mise en œuvre suit ces phases. Chaque phase comprend des détails de configuration, des points de décision et des liens vers la documentation d’Experience League.

### Phase 1 : évaluation de l’audience

**Fonction d’application :** RT-CDP : évaluation de l’audience, RT-CDP : composition de l’audience

**Ce que vous allez configurer :** définissez l’audience cible qui sera activée vers les destinations. Cela inclut la spécification des critères d’audience (quels profils remplissent les critères), la sélection de la méthode d’évaluation (la rapidité de mise à jour des adhésions) et la validation de la population de l’audience. Il s’agit du point de départ de toute activation : sans audience définie et évaluée, il n’y a rien à activer.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : méthode de création d’audience**
>
>Comment l’audience cible doit-elle être définie ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Créateur de segments (basé sur des règles) | Définition d’audience standard à l’aide d’attributs de profil, d’événements comportementaux et de conditions d’appartenance au segment | Définition de règle la plus flexible possible. Prend en charge l’évaluation Edge et la diffusion en continu pour les expressions éligibles. Idéal pour les audiences à une seule condition ou modérément complexes. |
>| Composition de l’audience | L’audience nécessite de combiner, classer, fractionner ou exclure des audiences existantes | Zone de travail visuelle pour les opérations séquentielles. Les résultats sont évalués par lots uniquement. 10 blocs de composition max. par zone de travail. |
>| Composition d’audience fédérée | Les critères d’audience doivent être évalués par rapport aux données des entrepôts de données externes sans les ingérer dans AEP | Interroge directement les bases de données externes ; évite la duplication des données ; nécessite une licence Federated Audience Composition |

>[!NOTE]
>
>**Décision : méthode d&#39;évaluation**
>
>À quelle vitesse les profils doivent-ils entrer dans l’audience et la quitter ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Lot | Campagnes planifiées, actualisations quotidiennes de l’audience ou logique de segmentation complexe non éligible à la diffusion en continu | Traite jusqu’à 24 millions de profils par tâche ; toutes les fonctions de segmentation sont prises en charge ; s’exécute selon un planning (planning cron quotidien par défaut ou personnalisé). |
>| Diffusion en continu | Modifications de l’appartenance à l’audience en temps réel nécessaires pour l’activation de la destination de diffusion ou les cas d’utilisation déclenchés par un événement | Temps quasi réel (secondes à minutes) ; ensemble de fonctions de segmentation limité : événements simples, comparaisons d’attributs et fenêtres de temps limitées uniquement ; aucune requête d’entités multiples. |
>| Edge | Personnalisation de la même page ou qualification d’audience instantanée nécessaire à la périphérie | Latence en millisecondes ; ensemble de règles le plus restrictif : attributs de profil et simples vérifications d’appartenance au segment uniquement ; principalement utilisé pour la personnalisation sur site (moins courant pour l’activation de destination). |

>[!NOTE]
>
>**Décision : politique de fusion**
>
>Quelle politique de fusion l’évaluation d’audience doit-elle utiliser ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Horodatage ordonné (par défaut) | La plupart des cas d’utilisation : les données récentes doivent être prioritaires en cas de conflit entre des fragments de profil | Plus courant ; utilise la valeur d’attribut la plus récemment mise à jour |
>| Priorité du jeu de données | Les sources de données spécifiques doivent remplacer les autres, quel que soit l’horodatage | Nécessite de définir un ordre de priorité des jeux de données ; utile lorsqu’un système d’enregistrement CRM doit toujours remplacer les données collectées sur le web. |

**Navigation dans l’interface utilisateur :** Client > Audiences > Créer une audience > Créer une règle (pour le créateur de segments) ou Composer une audience (pour la composition d’audience)

**Détails de configuration clés :**

- Définissez des critères d’audience en fonction du cas d’utilisation : attributs de profil, événements comportementaux, appartenance à un segment ou conditions temporelles
- Appliquez des règles de suppression pour exclure les profils qui ne doivent pas être activés (par exemple, récemment convertis, désabonnés au niveau mondial)
- Validez la taille de la population de l’audience avant de passer à l’activation
- Confirmez que la méthode d’évaluation s’aligne sur le type de destination sélectionné lors de la phase 2

**Là où les options divergent :**

**Pour L’Option A (Activation De Destination De Diffusion En Continu) :**
L’audience doit utiliser la diffusion en continu ou l’évaluation Edge pour diffuser des mises à jour d’abonnement en temps réel. Vérifiez que l’expression de règle de segment est admissible pour l’évaluation en flux continu - évitez les fonctions d’agrégation basées sur le temps, les requêtes d’entités multiples et les références `inSegment()` aux segments par lots uniquement.

**Pour L’Option B (Activation De Destination Par Lots) :**
Toute méthode d’évaluation fonctionne. L’évaluation par lots est le choix le plus courant, car l’exportation elle-même s’exécute selon un planning. Vérifiez qu’un planning d’évaluation par lots existe dans le sandbox ou créez-en un.

**Pour L’Option C (Activation Multidestination) :**
La méthode d’évaluation doit s’adapter à la destination la plus exigeante. Si une destination nécessite une diffusion en continu, l’audience doit utiliser l’évaluation de diffusion en continu. Si toutes les destinations sont par lots, l’évaluation par lots est suffisante.

**Documentation Experience League :**

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/pql/overview)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Présentation de la composition de l’audience](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/audience-composition)
- [Méthodes d’évaluation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)


### Phase 2 : configuration de la destination

**Fonction d’application :** RT-CDP : configuration de la destination

**Éléments à configurer :** établir des connexions authentifiées aux destinations externes où les audiences seront publiées. Cela inclut la sélection de la destination dans le catalogue, la fourniture d’informations d’authentification et la configuration de paramètres spécifiques à la destination tels que le format de fichier, l’emplacement de stockage et la planification de l’exportation. Chaque destination nécessite sa propre configuration de connexion.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : type de destination**
>
>Où les audiences doivent-elles être diffusées ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Destination Advertising (streaming) | Ciblage ou suppression sur les plateformes publicitaires (Facebook, Google Ads, LinkedIn, The Trade Desk, etc.) | Connecteurs de diffusion en continu ; mises à jour d’abonnement en temps quasi réel ; correspondance d’identité par e-mail, téléphone ou ID d’appareil hachés |
>| Destination de stockage dans le cloud (par lots) | Exporter vers S3, Azure Blob, GCS, SFTP ou Data Landing Zone pour l’enrichissement de l’entrepôt de données | Exportation basée sur des fichiers ; format configurable (CSV, JSON, Parquet) ; cadence planifiée |
>| Destination CRM | Synchroniser les audiences avec Salesforce, Microsoft Dynamics ou HubSpot pour l’activation des ventes | En règle générale, la diffusion en continu ; nécessite un mappage de champs spécifique au CRM ; peut nécessiter des autorisations d’administrateur CRM |
>| Destination du partenaire de données | Partage des données d’audience avec les partenaires de mesure ou de ciblage | Varie selon le partenaire ; examine les implications du partage des données en externe pour la gouvernance |
>| Destination personnalisée (Destination SDK) | Système cible non disponible dans le catalogue | Nécessite de créer une destination personnalisée à l’aide de Destination SDK ; effort d’implémentation plus important |

>[!NOTE]
>
>**Décision : méthode d’authentification**
>
>Quelles informations d’identification la destination requiert-elle ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| OAuth 2.0 | Plateformes publicitaires et destinations SaaS (Facebook, Google, Salesforce) | Nécessite un flux d’autorisation initial ; les jetons s’actualisent automatiquement ; plus courant pour les destinations de diffusion en streaming |
>| Clé d’accès / Clé secrète | Stockage dans le cloud (S3, Azure Blob) | Informations d’identification statiques. La rotation doit être planifiée, adaptée aux destinations basées sur des fichiers. |
>| Compte de service/clé API | API des partenaires et intégrations personnalisées | Nécessite la configuration des informations d’identification du partenaire de destination |
>| Chaîne de connexion | Destinations basées sur Azure | Chaîne unique contenant tous les paramètres de connexion |

>[!NOTE]
>
>**Décision : type d’exportation (destinations par lots uniquement)**
>
>Comment les données d’audience doivent-elles être compilées pour l’exportation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Exportation incrémentielle | Seules les nouvelles qualifications et les déchéances depuis la dernière exportation | Taille de fichier réduite ; traitement plus rapide à la destination ; nécessite que le système de destination conserve l’état |
>| Exportation complète | Instantané d’audience complet sur chaque exécution | Fichiers plus volumineux ; la destination obtient une image complète à chaque fois ; plus simple pour les systèmes qui effectuent un remplacement complet |

**Navigation dans l’interface utilisateur :** Connexions > Destinations > Catalogue > [Sélectionner la destination] > Configurer

**Détails de configuration clés :**

- Parcourez le catalogue de destinations et sélectionnez la destination cible
- Fournir des informations d’authentification et tester la connexion
- Pour les destinations par lots : configurer le format de fichier (CSV, JSON, Parquet), la compression, le modèle de dénomination de fichier et le planning d’exportation
- Pour les destinations en flux continu : la connexion est généralement établie via un flux d’autorisation OAuth
- Vérifiez que le statut de connexion de destination s’affiche comme actif avant de passer à l’activation

**Là où les options divergent :**

**Pour L’Option A (Activation De Destination De Diffusion En Continu) :**
Sélectionnez une destination de diffusion en continu dans le catalogue (catégories Advertising ou Social). Terminez le flux d’autorisation OAuth. La connexion est prête à être activée une fois l’autorisation confirmée.

**Pour L’Option B (Activation De Destination Par Lots) :**
Sélectionnez une destination basée sur des fichiers dans le catalogue (catégorie Espace de stockage). Configurez le chemin de stockage, le format de fichier, la compression, la convention de nommage et le planning d’exportation. Testez la connexion en vérifiant l&#39;accès en écriture à l&#39;emplacement de stockage.

**Pour L’Option C (Activation Multidestination) :**
Répétez cette phase pour chaque destination. Chaque connexion est indépendante : vous pouvez avoir un mélange de destinations de diffusion en streaming et par lots. Documentez l’authentification et la configuration de chaque connexion pour une référence opérationnelle.

**Documentation Experience League :**

- [Catalogue des destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/overview)
- [Aperçu des destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/home)
- [Activer les audiences vers des destinations d’exportation de profils par lots](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activer les audiences vers des destinations de diffusion en continu](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Présentation de Destination SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/destination-sdk/overview)
- [Options de configuration de Destination SDK](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/destination-sdk/functionality/configuration-options)


### Phase 3 : activation de l’audience

**Fonction d’application :** RT-CDP : Audience Activation

**Ce que vous allez configurer :** publiez l’audience évaluée dans la destination configurée en créant le flux de données d’activation. Cela implique de sélectionner les audiences à activer, de mapper les attributs de profil aux champs de destination et de configurer le planning d’exportation. Le flux de données d’activation connecte l’audience source à la destination cible et gère la diffusion continue des données.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : mappage des attributs**
>
>Quels attributs de profil doivent être inclus dans l’activation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Champs d’identité uniquement | La destination ne doit correspondre qu’aux profils (par exemple, l’appartenance à une audience sur des plateformes publicitaires) | Transfert de données minimal ; confidentialité maximale ; typique du ciblage et de la suppression de la plateforme publicitaire |
>| Identité + attributs de profil | La destination a besoin d’attributs d’enrichissement pour la personnalisation ou la segmentation (par exemple, synchronisation CRM, partage de partenaire). | Plus de données transférées ; nécessite une révision de la gouvernance pour chaque attribut ; vérifier les libellés d’utilisation des données par rapport à l’action marketing de destination |
>| Identité + attributs calculés | La destination bénéficie de scores ou d’agrégations dérivés (par exemple, le niveau de valeur de durée de vie, le score de propension pour le ciblage du partenaire). | Nécessite la configuration des attributs calculés ; enrichissement à forte valeur ajoutée pour les systèmes en aval |

>[!NOTE]
>
>**Décision : planification des exportations (destinations par lots uniquement)**
>
>À quelle fréquence les données d’audience doivent-elles être exportées ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Quotidienne | Fréquence d’actualisation standard ; la plupart des cas d’utilisation par lots | Équilibre fraîcheur et coût de traitement ; le plus courant par défaut |
>| Toutes les 3 à 6 heures | Cas d’utilisation à plus haute fréquence, tels que l’optimisation des campagnes au cours de la journée | Génération de fichiers plus fréquente ; charge de stockage et de traitement plus élevée à la destination |
>| À la demande (ad hoc) | Exportation ponctuelle ou activation urgente hors cycle | Le déclenchement manuel contourne le planning ; utile pour les tests ou les besoins urgents de la campagne |

**Navigation dans l’interface utilisateur :** Connexions > Destinations > Parcourir > [Sélectionner la destination] > Activer les audiences

**Détails de configuration clés :**

- Sélectionnez une ou plusieurs audiences à activer vers la destination
- Mapper les attributs de profil et les champs d’identité aux champs spécifiques à la destination
- Pour les destinations de streaming : vérifiez le mappage des espaces de noms d’identité (par exemple, l’e-mail haché sur l’extern_id de Facebook)
- Pour les destinations par lots : configurez le planning d’exportation, sélectionnez le mode d’exportation incrémentiel ou complet, puis définissez la première date d’exportation
- Consultez la synthèse de l’activation pour confirmer tous les mappages et plannings avant la publication

**Là où les options divergent :**

**Pour L’Option A (Activation De Destination De Diffusion En Continu) :**
Sélectionnez les audiences et mappez les espaces de noms d’identité aux champs d’identité de destination. L’activation commence immédiatement après la publication : l’appartenance à l’audience change de diffusion vers la destination en temps quasi réel. Aucun planning d’exportation n’est nécessaire ; l’activation est continue.

**Pour L’Option B (Activation De Destination Par Lots) :**
Sélectionnez les audiences, mappez les attributs de profil et configurez le planning d’exportation. Choisissez entre les modes d’exportation incrémentiel et complet. Déclenchez éventuellement une exportation ad hoc pour une diffusion immédiate en dehors du planning normal.

**Pour L’Option C (Activation Multidestination) :**
Répétez le workflow d’activation pour chaque destination. Une même audience peut être activée vers plusieurs destinations avec différents mappages d’attributs par destination. Par exemple, envoyez uniquement des e-mails hachés aux plateformes publicitaires, mais incluez les attributs démographiques dans le CRM.

**Documentation Experience League :**

- [Activer les audiences vers des destinations de diffusion en continu](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activer les audiences vers des destinations d’exportation de profils par lots](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activer les audiences à la demande vers des destinations par lots](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Surveillance des flux de données pour les destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/dataflows/ui/monitor-destinations)


### Phase 4 : validation de la gouvernance

**Fonction d’application :** RT-CDP : application du consentement et de la gouvernance

**Éléments à configurer :** vérifiez que les politiques de gouvernance et les préférences de consentement sont correctement appliquées avant et pendant l’activation. Cette phase garantit que les données restreintes (PII, attributs sensibles) ne sont pas envoyées vers des destinations non autorisées et que les profils sans consentement valide sont exclus de l’activation. L’application de la gouvernance se produit automatiquement au moment de l’activation, mais la validation proactive empêche les activations bloquées et les violations de conformité.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : approche d’application de la gouvernance**
>
>Quand la conformité en matière de gouvernance doit-elle être validée ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Proactive (pré-activation) | Recommandé pour toutes les implémentations, en particulier lors de l’activation sur des systèmes tiers externes | Examinez les libellés et les politiques d’utilisation des données avant de configurer les mappages des champs ; empêche les échecs d’activation et assure la conformité dès le départ |
>| Réactif (au moment de l’activation) | Lorsque les politiques de gouvernance sont déjà bien établies et que l’équipe a confiance en leur conformité | Platform applique automatiquement les politiques lors de l’activation ; les violations bloquent l’activation ou excluent les attributs restreints ; peuvent entraîner des échecs inattendus si les politiques ne sont pas bien comprises |

>[!NOTE]
>
>**Décision : filtrage du consentement**
>
>Comment les préférences de consentement affectent-elles l’activation ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Application du consentement activée | Obligatoire lors de l’activation vers des destinations publicitaires ou marketing pour lesquelles le consentement est légalement obligatoire | Les profils sans consentement valide (consentements.marketing.{channel}.val = « y ») sont automatiquement exclus de l’activation. Nécessite que les données de consentement soient ingérées |
>| Aucun filtrage de consentement | Destinations d’utilisation interne pour les exportations Analytics lorsque le consentement ne s’applique pas au transfert de données | Uniquement approprié lorsque l’utilisation des données ne constitue pas une action marketing nécessitant un consentement ; consultez l’équipe juridique/de confidentialité. |

**Navigation dans l’interface utilisateur :** Confidentialité > Politiques > Politiques de consentement (pour la révision du consentement) ; Gouvernance des données > Politiques (pour la révision des politiques d’utilisation des données)

**Détails de configuration clés :**

- Vérifier les libellés d’utilisation des données appliqués aux jeux de données et aux champs de schéma activés
- Vérifiez que les politiques de gouvernance sont actives pour l’action marketing associée à la destination (par exemple, « Exporter vers un tiers » pour les plateformes publicitaires).
- Vérifiez que les champs de consentement sont renseignés sur les profils et que l’application du consentement est activée pour les canaux appropriés
- Si des violations de politique sont détectées, résolvez-les en supprimant les champs restreints du mappage de destination ou en sélectionnant une autre destination

**Documentation Experience League :**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Application des politiques](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/enforcement/overview)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Application de la politique de consentement](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/user-guide)


### Phase 5 : suivi et validation

**Fonction d’application :** Surveillance et observabilité

**Éléments à configurer :** configurez la surveillance continue des flux de données d’activation, configurez des alertes pour les échecs, validez la population d’audiences au niveau des destinations et suivez l’utilisation des licences. La surveillance est essentielle pour les activations de production où les échecs de diffusion ont un impact direct sur les performances des campagnes et les dépenses multimédia.

**Détails de configuration clés :**

- Vérifiez le statut d’exécution du flux de données pour chaque destination active afin de confirmer que les audiences sont diffusées avec succès
- Configurez des alertes pour les échecs d’activation de destination, les retards de flux de données et les anomalies de population d’audience
- Suivi des profils exportés par rapport aux profils ayant échoué par exécution de flux de données
- Surveillez les taux de correspondance d’audience à la destination (où des rapports de destination sont disponibles).
- Examiner l’utilisation des licences pour suivre le volume de profils activés par rapport aux droits

**Navigation dans l’interface utilisateur :** Connexions > Destinations > Parcourir > [Sélectionner la destination] > Exécutions de flux de données (pour la surveillance de l’activation) ; Alertes > Règles d’alerte > S’abonner (pour la configuration des alertes) ; Administration > Utilisation des licences (pour le suivi des licences)

**Documentation Experience League :**

- [Surveillance des flux de données pour les destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home)
- [Tableau de bord d’utilisation des licences](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

## Considérations relatives à la mise en œuvre

Examinez les points suivants avant et pendant l’implémentation.

### Mécanismes de sécurisation et limites

- **Limite de définition de segment :** maximum de 4 000 définitions de segment par sandbox — [Mécanismes de sécurisation de segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- **Flux de données par destination :** maximum de 100 flux de données par connexion de destination — [Mécanismes de sécurisation des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- **Taille du fichier d’exportation par lots :** les destinations basées sur des fichiers ont des limites de taille de fichier d’exportation maximales ; les audiences volumineuses sont automatiquement fractionnées sur plusieurs fichiers
- **Débit des destinations de diffusion en continu :** des limites de débit par seconde sont définies par chaque partenaire de destination ; les modifications d’audience importantes peuvent être limitées
- **Capacité d’évaluation par lots :** jusqu’à 24 millions de profils par traitement d’évaluation de segment par défaut
- **Composition de l’audience :** un maximum de 10 blocs de composition par zone de travail ; les audiences composées sont évaluées par lots uniquement
- **Graphique d’identités :** 50 identités au maximum par graphique — [Mécanismes de sécurisation du service d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
- **Attributs calculés :** un maximum de 25 attributs calculés par sandbox — [Mécanismes de sécurisation des attributs calculés](https://experienceleague.adobe.com/fr/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **Présentation des mécanismes de sécurisation d’activation :** [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### Pièges courants

- **Segment de diffusion en continu avec logique de règle non éligible :** définition d’une audience avec des fonctions d’agrégation complexes ou des requêtes d’entités multiples et attente d’une évaluation de diffusion en continu. Ces segments reviennent silencieusement à l’évaluation par lots, ce qui entraîne une latence inattendue. Prévention : passez en revue les exigences d’éligibilité de diffusion en continu avant de définir l’audience.

- **Aucun profil exporté en raison du filtrage de consentement :** tous les profils de l’audience ne disposent pas de valeurs de consentement valides, ce qui entraîne le filtrage de l’audience entière au moment de l’activation. Prévention : vérifiez que l’ingestion des données de consentement est opérationnelle et que les champs de consentement sont renseignés avant l’activation.

- **Blocage inattendu de l’activation par la politique de gouvernance :** les libellés d’utilisation des données sur les champs de schéma déclenchent des violations de politique qui empêchent l’activation. Prévention : évaluez la conformité de la gouvernance de manière proactive (phase 4) avant de configurer les mappages de champs. Vérifiez quels libellés sont hérités du schéma.

- **Expiration des informations d’identification de destination :** les jetons OAuth ou les clés API expirent, provoquant des échecs d’activation sans alerte immédiate. Prévention : configurez des alertes pour les échecs d’activation de destination et établissez un planning de rotation des informations d’identification.

- **Espaces de noms d’identité incompatibles :** l’espace de noms d’identité configuré dans le mappage d’activation ne correspond pas à ce que la destination attend (par exemple, l’envoi d’un e-mail en texte brut lorsque la destination nécessite un e-mail haché SHA-256). Prévention : consultez la documentation de destination pour connaître les formats d’identité requis avant de configurer le mappage.

- **Erreurs de mappage de champ provoquant des échecs d’exportation :** mappage d’un attribut de profil à un champ de destination avec un type ou un format de données incompatible. Prévention : testez d’abord l’activation avec une petite audience et passez en revue les détails d’exécution du flux de données pour détecter les erreurs de mappage avant de mettre à l’échelle les audiences d’exploitation.

- **Dérive de la population d’audience entre RT-CDP et la destination :** le nombre de profils des audiences dans RT-CDP ne correspond pas au nombre à la destination en raison de différences de correspondance d’identité, d’une logique de déduplication de destination ou de la synchronisation. Il s’agit d’un comportement attendu : prévention : documenter les taux de correspondance attendus par destination et surveiller les écarts importants.

### Bonnes pratiques

- **Commencez avec une audience de test :** activez une petite audience de test bien comprise dans chaque nouvelle destination avant d’activer les audiences de production. Validez les mappages de champs, la correspondance d’identités et les mesures de diffusion avec l’audience de test.

- **Gouvernance de couche précoce :** appliquez des libellés d’utilisation des données et configurez des politiques de gouvernance avant de configurer les activations de destination. Cela empêche les activations bloquées et garantit la conformité dès le départ.

- **Utiliser des exportations incrémentielles pour les destinations par lots :** les exportations incrémentielles réduisent la taille des fichiers, accélèrent le traitement à la destination et réduisent les coûts de stockage. Utilisez les exportations complètes uniquement lorsque le système de destination nécessite un remplacement complet de l’audience.

- **Normaliser les conventions de nommage :** établir des noms cohérents pour les audiences, les connexions de destination et les flux de données dans l’ensemble de l’organisation. Incluez le cas d’utilisation, la destination et la méthode d’évaluation dans les noms (par exemple, « Suppression_ExistingCustomers_Facebook_Streaming »).

- **Surveiller les taux de correspondance :** suivez le ratio des profils exportés de RT-CDP aux profils correspondants à chaque destination. Des baisses significatives du taux de correspondance peuvent indiquer des problèmes de résolution d’identité, des problèmes d’informations d’identification ou des modifications de l’API de destination.

- **Coordonner la suppression entre les destinations :** lors de l’utilisation des audiences de suppression (par exemple, en excluant les clients existants des campagnes d’acquisition), activez simultanément l’audience de suppression sur toutes les plateformes publicitaires pertinentes pour maintenir la cohérence.

- **Vérifier et supprimer les activations inactives :** vérifier régulièrement les flux de données de destination et désactiver les audiences qui ne sont plus nécessaires. Les activations inactives consomment de la capacité de licence et ajoutent une surcharge de surveillance.

### Décisions de compromis

>[!NOTE]
>
>**Compromis : fraîcheur d’audience par rapport à flexibilité de segmentation**
>
>L’évaluation par flux fournit des mises à jour d’audience en temps quasi réel, mais limite les fonctions de règle de segment que vous pouvez utiliser. L’évaluation par lots prend en charge l’ensemble complet des fonctions de règles de segment, mais introduit une latence (heures au lieu de minutes).
>
>- **Favoris de streaming :** cas d’utilisation en temps réel où l’appartenance à l’audience doit se refléter à la destination en quelques minutes (suppression active de la campagne, reciblage en temps réel).
>- **Favoris par lot :** logique d’audience complexe nécessitant des fonctions d’agrégation, des requêtes d’entités multiples ou des conditions de fenêtre temporelle étendue (niveaux de valeur de vie, segments comportementaux multipoint).
>- **Recommandation :** utilisez l’évaluation du streaming pour les audiences activées vers les destinations de streaming où l’actualisation en temps réel génère de la valeur commerciale. Utilisez l’évaluation par lots pour les audiences complexes activées vers des destinations basées sur des fichiers ou lorsque l’actualisation quotidienne est suffisante. Pour les audiences qui ont besoin des deux, pensez à créer deux versions : un segment de diffusion en continu simplifié pour l’activation en temps réel et un segment par lots complet pour un enrichissement périodique.

>[!NOTE]
>
>**Compromis : exportation minimale des données par rapport au mappage d’attributs riches**
>
>L’exportation de champs d’identité uniquement (e-mail haché, identifiant d’appareil) réduit l’exposition des données et simplifie la gouvernance. L’exportation d’attributs de profil supplémentaires (données démographiques, niveau de valeur, score d’engagement) enrichit la destination, mais augmente la complexité de la gouvernance et la responsabilité des données.
>
>- **Favoris minimaux à l’exportation :** approche privilégiant la confidentialité ; risque de gouvernance réduit ; mappage des champs plus simple ; suffisant pour la plupart des cas d’utilisation de ciblage et de suppression de plateforme publicitaire.
>- **Favoris d’exportation enrichis :** personnalisation en aval à la destination ; enrichissement du CRM ; partage des données des partenaires qui nécessite des détails au niveau des attributs
>- **Recommandation :** par défaut pour les exportations d’identité uniquement minimales pour les destinations publicitaires. Ajoutez des attributs de profil uniquement lorsque le cas d’utilisation de destination les requiert spécifiquement et que la révision de la gouvernance confirme la conformité. Utilisez des attributs calculés pour fournir des valeurs d’enrichissement agrégées et moins sensibles au lieu des PII brutes.

>[!NOTE]
>
>**Compromis : audience unique par destination par rapport aux flux de données consolidés à plusieurs audiences**
>
>L’activation de chaque audience sous la forme d’un flux de données distinct permet une isolation et une surveillance granulaire. L’activation de plusieurs audiences par le biais d’un seul flux de données vers une destination simplifie la gestion, mais réduit l’isolement.
>
>- **Les flux de données distincts sont favorisés :** surveillance indépendante, dépannage plus facile, possibilité de suspendre les activations d’audiences individuelles sans affecter les autres
>- **Les flux de données consolidés sont favorisés :** moins de connexions à gérer, gestion simplifiée des informations d’identification, réduction des frais généraux d’exploitation
>- **Recommandation :** utilisez des flux de données consolidés lors de l’activation de plusieurs audiences associées vers la même destination (par exemple, tous les segments de suppression vers Facebook). Utilisez des flux de données distincts lorsque les audiences ont des SLA différents, des mappages d’attributs différents ou lorsque l’isolation des échecs est essentielle.

## Documentation connexe

**Destinations**

- [Aperçu des destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/home)
- [Catalogue des destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/overview)
- [Activer les audiences vers des destinations de diffusion en continu](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activer les audiences vers des destinations d’exportation de profils par lots](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activer les audiences à la demande vers des destinations par lots](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Mécanismes de sécurisation des destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Présentation de Destination SDK](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/destination-sdk/overview)

**Audiences et segmentation**

- [Présentation de Segmentation Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Guide de l’interface utilisateur du créateur de segments](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/segment-builder)
- [Référence de Profile Query Language](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/pql/overview)
- [Segmentation par flux](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation Edge](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Présentation de la composition de l’audience](https://experienceleague.adobe.com/fr/docs/experience-platform/segmentation/ui/audience-composition)
- [Mécanismes de sécurisation de la segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Identité et profil**

- [Présentation d’Identity Service](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/home)
- [Présentation des espaces de noms d’identité](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)
- [Règles de liaison des graphiques d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Présentation du profil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Présentation des politiques de fusion](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Modélisation des données et schémas**

- [Présentation du système XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Principes de base de la composition de schémas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Gouvernance des données**

- [Aperçu de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Vue d’ensemble des libellés d’utilisation des données](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/labels/overview)
- [Politiques de gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview)
- [Application des politiques](https://experienceleague.adobe.com/fr/docs/experience-platform/data-governance/enforcement/overview)
- [Consentement et préférences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Surveillance et observabilité**

- [Surveillance des flux de données pour les destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Présentation des alertes](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/alerts/overview)
- [Présentation d’Observability Insights](https://experienceleague.adobe.com/fr/docs/experience-platform/observability/home)
- [Tableau de bord d’utilisation des licences](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Attributs calculés**

- [Présentation des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Guide de l’interface utilisateur des attributs calculés](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

**Collecte de données et sources**

- [Présentation des sources](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

**Administration**

- [Présentation des sandbox](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)
- [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Contrôle d’accès basé sur les attributs](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/abac/overview)

**Mécanismes de sécurisation**

- [Mécanismes de sécurisation du profil client en temps réel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Mécanismes de sécurisation d’Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
- [Mécanismes de sécurisation d’activation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Mécanismes de sécurisation de l’ingestion](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
