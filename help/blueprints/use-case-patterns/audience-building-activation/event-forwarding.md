---
title: Transfert d’événement
description: Découvrez comment transférer des données d’événement en temps réel collectées via Edge Network vers des destinations autres qu’Adobe à des fins d’analyse, de stockage ou de publicité.
solution: Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6342'
ht-degree: 0%

---


# Transfert d’événement

Ce guide couvre l’implémentation du transfert d’événement côté serveur à l’aide d’[!DNL Adobe Experience Platform] Edge Network. Il est conçu pour les architectes de solution, les techniciens marketing et les ingénieurs d’implémentation qui ont besoin de distribuer des données d’événement en temps réel collectées via Edge Network vers des destinations non Adobe, telles que des plateformes d’analyse tierces, des points d’entrée de stockage dans le cloud, des réseaux publicitaires ou des webhooks personnalisés.

Il présente toutes les approches viables pour configurer le transfert d’événement, explique les compromis entre elles et fournit des liens vers [!DNL Adobe Experience League] documentation pour des instructions procédurales détaillées.

## Présentation du cas d’utilisation

Les entreprises qui collectent des données comportementales par le biais de [!DNL Adobe Experience Platform] Web SDK, Mobile SDK ou de l’API Server doivent souvent partager le même flux d’événement avec des systèmes non Adobe : plateformes d’analyse telles que [!DNL Google Analytics] ou [!DNL Snowflake], réseaux publicitaires pour le suivi des conversions, entrepôts de données pour le stockage à long terme ou services internes personnalisés. Traditionnellement, cela nécessitait une prolifération des balises côté client, ce qui augmente le poids de la page, introduit une latence et crée des risques en matière de confidentialité et de gouvernance.

Le transfert d’événement résout ce problème en opérant côté serveur sur Edge Network. Lorsqu’une interaction d’un visiteur déclenche un événement via le Web SDK ou l’API du serveur, cet événement est acheminé vers Edge Network par le biais d’un flux de données. Les règles de transfert d’événement, configurées dans une propriété de transfert d’événement dédiée, évaluent les données d’événement entrantes et les transfèrent de manière sélective vers une ou plusieurs destinations configurées. Cette approche côté serveur réduit la surcharge des balises côté client, améliore les performances de la page, centralise la gouvernance des données et donne à l’entreprise le contrôle sur les données qui quittent exactement l’écosystème Adobe.

L’audience cible de ce modèle comprend les organisations qui ont déjà déployé (ou prévoient de déployer) l’API [!DNL Adobe Experience Platform] Web SDK ou Server pour la collecte de données et qui souhaitent étendre cet investissement en distribuant des données d’événement aux points d’entrée autres qu’Adobe sans ajouter de balises JavaScript côté client.

## Objectifs commerciaux clés

Les objectifs commerciaux suivants sont pris en charge par ce modèle de cas d’utilisation.

### Améliorer la qualité et la gouvernance des données

Garantissez des données propres, complètes et conformes pour un ciblage précis, une réduction des déchets et des analyses fiables. Le transfert d’événement centralise la distribution des données côté serveur, ce qui permet à l’organisation de disposer d’un point de contrôle unique pour les données partagées avec des systèmes externes, ce qui réduit le risque de fuite de données et garantit l’application de politiques de gouvernance avant que les données ne quittent [!DNL Adobe] Edge Network.

**KPI : efficacité** économies

Pour plus d’informations, voir [Améliorer la qualité et la gouvernance des données](../../business-objectives/cost-efficiency/improve-data-quality-governance.md).

### Consolider et moderniser la technologie marketing

Réduisez la fragmentation des outils et la dette technique en migrant vers des plateformes unifiées et évolutives. Le transfert d’événement permet aux entreprises de remplacer plusieurs balises de fournisseur côté client par un seul mécanisme de distribution de données côté serveur, ce qui réduit la surcharge de chargement des pages et simplifie la pile technologique.

**KPI :** des économies, efficacité, rapidité de mise sur le marché

Pour plus d’informations, voir [Consolider et moderniser la technologie marketing](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md).

## Exemples de cas d’utilisation tactiques

Vous trouverez ci-dessous des scénarios tactiques courants où s’applique ce modèle de cas d’utilisation.

- **Enrichissement d’analyses tierces** — Transférez les événements de page vue, de clic et de conversion vers [!DNL Google Analytics], [!DNL Snowflake] ou d’autres plateformes d’analyse en temps réel sans ajouter de balises côté client
- **Suivi des conversions Advertising** — Envoyez des événements d’achat et de génération de piste à l’API, à l’[!DNL Google Ads], à l’[!DNL TikTok] ou à l’[!DNL Snap] de [!DNL Meta] Conversions pour la mesure et l’optimisation des conversions côté serveur
- **Diffusion en continu de Data Warehouse** - Acheminez les données brutes des événements vers un entrepôt de données cloud ([!DNL Google BigQuery], [!DNL Amazon S3], [!DNL Azure Event Hubs]) pour un stockage à long terme et une analyse hors ligne
- **Intégration webhook personnalisée** - Transférez les données d’événement filtrées ou transformées vers des microservices internes, des systèmes CRM ou des plateformes partenaires via des points d’entrée HTTP
- **Réduction des balises et amélioration des performances des pages** — Remplacez plusieurs balises JavaScript de fournisseur côté client par une seule implémentation de Web SDK, ainsi que des règles de transfert d’événement côté serveur, ce qui réduit le poids de la page et améliore Core Web Vitals
- **Partage de données conforme à la confidentialité** — Appliquez le filtrage des données et les règles de rédaction au niveau du champ côté serveur avant de partager des données d&#39;événement avec des tiers, en vous assurant que les informations d&#39;identification personnelles sont supprimées ou hachées avant d&#39;atteindre des systèmes externes
- **Distribution d’événements multi-cloud** - Transférez simultanément le même flux d’événements vers plusieurs destinations (par exemple, les analyses, la publicité et l’entrepôt de données) à partir d’un seul ensemble de règles côté serveur
- **Transfert de signaux de fraude en temps réel** — Transférer des événements de transaction de grande valeur à des systèmes de détection de fraude pour une évaluation des risques et des alertes en temps réel

## Indicateurs clés de performance

Les indicateurs de performance clés suivants permettent de mesurer le succès de ce modèle de cas d’utilisation.

- **Réduction du temps de chargement des pages** — Amélioration mesurée de la vitesse de chargement des pages et de Core Web Vitals après la migration des balises côté client vers le transfert d’événement côté serveur
- **Taux de succès de la diffusion des données** — Pourcentage d’événements transférés avec succès vers des points d’entrée de destination sans erreurs ni délais
- **Réduction du nombre de balises** — Nombre de balises fournisseur côté client supprimées après l’implémentation d’équivalents côté serveur
- **Actualisation des données/latence** — Temps écoulé entre l’occurrence de l’événement sur le client et l’arrivée de l’événement au point d’entrée de destination (cible : sous-seconde à secondes)
- **Taux de conformité de la gouvernance** — Pourcentage de partages de données sortantes qui passent par des règles de filtrage côté serveur, s’assurant qu’aucune PII ou donnée restreinte n’atteint des destinations non autorisées
- **Efficacité opérationnelle** — Réduction du temps consacré par les développeurs à la gestion des déploiements de balises côté client et à la résolution des conflits de balises

## Modèle de cas d’utilisation

Cette section décrit le modèle et la chaîne de fonctions utilisés pour implémenter le transfert d’événement.

**Transfert d’événement** — Transférez les données d’événement en temps réel collectées via Edge Network vers des destinations autres qu’Adobe à des fins d’analyse, de stockage ou de publicité.

**Chaîne De Fonctions:** Configuration De Flux De Données > Définition De Règle D’Événement > Mappage De Destination > Exécution Du Transfert > Surveillance

## Applications

Les applications suivantes sont utilisées dans ce modèle de cas d’utilisation.

- **[!DNL Adobe Experience Platform] (Edge Network)** : reçoit et achemine les données d’événement en temps réel depuis Web SDK, Mobile SDK ou l’API du serveur via les flux de données configurés
- **[!DNL Adobe Experience Platform] (Transfert d’événement)** — Fournit le moteur de règles côté serveur pour évaluer, filtrer, transformer et transférer des données d’événement vers des destinations externes
- **[!DNL Adobe Experience Platform] (Balises/Collecte de données)** — Gère le cycle de vie des propriétés de transfert d&#39;événement, les extensions, les règles et le workflow de publication

## Fonctions fondamentales

Les fonctionnalités fondamentales suivantes doivent être en place pour ce modèle de cas d’utilisation. Pour chaque fonction, le statut indique si elle est généralement requise, supposée être préconfigurée ou non applicable.

| Fonction Fondamentale | Etat | Éléments devant être en place | Référence Experience League |
| --- | --- | --- | --- |
| Administration et gouvernance | Obligatoire | Un sandbox doit être actif avec les rôles utilisateur et les autorisations appropriés configurés. Les utilisateurs gérant le transfert d’événement ont besoin d’autorisations de collecte de données dans [!DNL Adobe Admin Console], notamment de droits pour gérer les propriétés, les extensions et les règles de transfert d’événement. | [Présentation du contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Modélisation et préparation des données | Obligatoire | Les schémas XDM doivent être définis pour les données d’événement qui transitent par Edge Network. Le flux de données doit référencer un schéma XDM ExperienceEvent valide afin que les règles de transfert d’événement puissent accéder aux champs structurés pour le filtrage, la transformation et le mappage. | [&#x200B; Présentation du système XDM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Sources et collecte de données | Obligatoire | Un mécanisme de collecte de données doit être actif (Web SDK, Mobile SDK ou l’API Edge Network Server) et envoyer des événements par le biais d’un flux de données configuré. Le flux de données est la couche de routage de base qui connecte la collecte côté client au transfert d’événement côté serveur. | [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Configuration des identités et des profils | Sans objet | Le transfert d’événement fonctionne sur les données d’événement brutes au niveau de la couche Edge Network, avant que la résolution d’identité ou l’unification de profil ne se produise. Les espaces de noms d’identité et les politiques de fusion ne sont pas requis, sauf si les événements transférés doivent également contribuer au profil client en temps réel (qui est une configuration de service de flux de données distincte, et non une préoccupation de transfert d’événement). | |
| Définition et segmentation de l’audience | Sans objet | Le transfert d’événement traite les événements individuels en temps réel et n’évalue pas l’appartenance à l’audience. Le filtrage basé sur l’audience ne fait pas partie de la chaîne de fonctions de transfert d’événement. Si l’activation basée sur l’audience est nécessaire, consultez le plan de référence d’Audience Activation vers les destinations . | |

## Fonctions annexes

Les fonctionnalités suivantes complètent ce modèle de cas d’utilisation, mais ne sont pas requises pour l’exécution principale.

| Fonction de support | Etat | Importance de la résolution | Référence Experience League |
| --- | --- | --- | --- |
| Création d’attributs calculés/dérivés | Sans objet | Le transfert d’événement fonctionne sur les données d’événement brutes, et non sur les attributs calculés au niveau du profil. Les attributs calculés ne sont pas disponibles dans le contexte du transfert d’événement. | |
| Gestion du cycle de vie des données | Recommandé | Si des données d’événement sont également ingérées dans des jeux de données AEP (via le même flux de données), des politiques de conservation des données (expiration) doivent être configurées pour ces jeux de données afin de gérer les coûts de stockage et la conformité à la réglementation. Le transfert d’événement lui-même ne stocke pas de données, contrairement au chemin d’ingestion AEP parallèle. | [Présentation de la gestion avancée du cycle de vie des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Étiquetage et application de l’utilisation des données | Recommandé | Bien que les règles de transfert d’événement fournissent un filtrage au niveau du champ (vous permettant d’exclure des données sensibles des payloads transférées), l’application de libellés d’utilisation des données aux schémas et jeux de données sous-jacents garantit que les politiques de gouvernance sont appliquées si les mêmes données sont utilisées pour l’activation ou la personnalisation de l’audience. | [Présentation de la gouvernance des données](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Surveillance et observabilité | Inclus | La surveillance est essentielle pour le transfert d’événement. Le tableau de bord de surveillance du transfert d’événement offre une visibilité sur les taux de succès du transfert, les taux d’erreur et les codes de réponse de destination. Les alertes doivent être configurées pour les échecs de destination. | [Surveillance du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring) |
| Rapports et analyses | Recommandé | Si les événements transférés alimentent une plateforme d’analyse tierce, pensez à connecter les mêmes jeux de données d’événement AEP à CJA pour obtenir une vue cross-canal unifiée. Cela permet de comparer les analyses côté Adobe et côté tiers. | Présentation de [CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Fonctions d&#39;application

Ce plan exerce les fonctions suivantes à partir du catalogue des fonctions d&#39;application. Les fonctions sont associées à des phases d’implémentation plutôt qu’à des étapes numérotées.

### [!DNL Adobe Experience Platform] (AEP)

| Fonction | Phase de mise en œuvre | Description |
| --- | --- | --- |
| Configuration du flux de données | Phase 1 : configuration du flux de données | Configurer un flux de données pour recevoir des événements Edge Network et activer le service de transfert d’événement |
| Configuration de la propriété Transfert d’événement | Phase 2 : propriété de transfert d’événement et extensions | Créer une propriété de transfert d’événement et installer des extensions spécifiques à la destination |
| Définition de règle d’événement | Phase 3 : définition des règles d’événement | Définissez des règles qui évaluent les données d’événement entrantes et déterminent ce qu’il faut transférer et où |
| Mappage de destination | Phase 3 : définition des règles d’événement | Mappage des éléments de données d’événement aux formats de payload spécifiques à la destination dans les règles de transfert |
| Exécution du transfert | Phase 4 : publication et activation | Publiez la configuration de transfert d’événement dans Edge Network pour une exécution en direct |
| Surveillance | Phase 5 : surveillance et validation | Surveiller les taux de réussite du transfert, les codes d’erreur et l’intégrité de la destination |

## Conditions préalables

Assurez-vous que les éléments suivants sont en place avant de commencer la mise en œuvre.

- [ ] licence [!DNL Adobe Experience Platform] avec droits Edge Network et Transfert d’événement
- [ ] des autorisations de collecte de données configurées dans [!DNL Adobe Admin Console] (gérer les propriétés, les extensions, les règles et la publication pour le transfert d’événement)
- [ ] au moins un mécanisme de collecte de données actif (Web SDK, Mobile SDK ou API du serveur) envoyant des événements par le biais d’un flux de données
- [ ] schéma XDM ExperienceEvent défini pour les données d’événement collectées
- [ ] Flux de données créé et lié au mécanisme de collecte
- [ Informations d’identification et documentation du point d’entrée de destination ] disponibles (par exemple, jeton d’accès de l’API [!DNL Meta] Conversions, identifiant de mesure [!DNL Google Analytics], URL webhook, informations d’identification d’espace de stockage dans le cloud).
- [ ] Compréhension du modèle de données d’événement et des champs/événements requis par chaque destination

## Options de mise en œuvre

Cette section décrit les approches disponibles pour la mise en œuvre du transfert d’événement et fournit des conseils sur le choix de la bonne option.

### Option A : transfert d’événement basé sur une extension

**Idéal pour :** les équipes qui utilisent des plateformes de destination bien prises en charge ([!DNL Meta], [!DNL Google], [!DNL AWS], [!DNL Azure], [!DNL Snowflake], etc.) qui disposent d’extensions de transfert d’événement préconfigurées disponibles dans le catalogue de collecte de données.

**Fonctionnement :**

Le transfert d’événement basé sur une extension tire parti d’intégrations préconfigurées gérées par Adobe ou des partenaires tiers. Chaque extension est conçue spécifiquement pour une destination spécifique et gère l’authentification, le formatage de la payload et la communication de point d’entrée. L’implémenteur installe l’extension dans la propriété de transfert d’événements, configure les informations d’authentification et crée des règles qui mappent les éléments de données XDM aux champs d’action de l’extension.

Cette approche réduit le développement personnalisé, car l’extension abstrait les exigences d’API de la destination. Par exemple, l’extension d’API Conversions [!DNL Meta] [!DNL Meta] traduit les événements XDM Commerce au format attendu, en gérant le hachage des champs d’informations d’identification personnelles, les paramètres de déduplication et la gestion des jetons d’accès. De même, les extensions [!DNL Google Cloud Platform] ou [!DNL AWS] gèrent l’authentification et le formatage de la payload pour leurs services cloud respectifs.

L’inconvénient est que la disponibilité de l’extension détermine les destinations prises en charge. S’il n’existe aucune extension pour une destination cible, l’option B (Custom Webhook) doit être utilisée à la place.

**Considérations principales :**

- La disponibilité des extensions varie : consultez le [catalogue d’extensions de la collecte de données](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview) avant de planifier.
- Les extensions sont conservées par Adobe ou ses partenaires ; les mises à jour peuvent introduire des modifications importantes qui nécessitent des ajustements de règles
- Certaines extensions ne prennent en charge que des types d’événements spécifiques ou nécessitent des mappages de champs XDM spécifiques
- Les extensions gèrent l’authentification et la gestion des informations d’identification dans leur interface utilisateur de configuration

**Avantages :**

- Délai d’implémentation le plus rapide pour les destinations prises en charge
- Le formatage de la payload préconfigurée réduit les erreurs de mappage
- Authentification et gestion des informations d’identification gérées par l’extension
- Géré et mis à jour par Adobe ou par des partenaires certifiés
- Réduction du code personnalisé et de la charge de maintenance

**Limitations :**

- Limité aux destinations avec des extensions disponibles
- Moins de flexibilité dans la personnalisation de la payload par rapport aux Webhooks personnalisés
- Les mises à jour d’extension peuvent nécessiter une reconfiguration des règles
- Certaines extensions peuvent ne pas prendre en charge toutes les fonctionnalités de l’API de destination

**Experience League:**

- [Catalogue des extensions de transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Extension de l’API de conversions Meta](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Extension Google Cloud Platform](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [Extension AWS](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Extension Snowflake](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)

### Option B : transfert d’événement webhook personnalisé (API de récupération)

**Idéal pour :** les équipes qui doivent transférer des événements vers des destinations sans extension préconfigurée ou qui nécessitent un contrôle total sur la payload, les en-têtes et le mécanisme d’authentification des requêtes HTTP.

**Fonctionnement :**

Le transfert d’événement basé sur webhook personnalisé utilise l’extension [!DNL Adobe Cloud Connector] (incluse par défaut) pour effectuer des requêtes HTTP arbitraires vers n’importe quel point d’entrée. L’implémenteur définit des éléments de données pour extraire et transformer des valeurs de l’événement XDM entrant, puis configure une action de règle à l’aide du type d’action « Effectuer un appel de récupération » de Cloud Connector. Cette action permet un contrôle complet de la méthode HTTP, de l’URL, des en-têtes et du corps de la requête.

Le corps de la requête est généralement construit à l’aide d’éléments de données et de code personnalisé pour formater la payload en fonction de la spécification d’API de la destination. Cette approche prend en charge tout point d’entrée accessible via HTTP (API REST, webhooks, fonctions cloud ou services internes), ce qui en fait l’option la plus flexible.

Le compromis est un effort de mise en œuvre plus important et une maintenance continue. L’implémenteur doit comprendre l’API de destination, gérer l’authentification manuellement (par exemple, définir les en-têtes d’autorisation, gérer l’actualisation du jeton) et gérer le format de la payload si l’API de destination évolue.

**Considérations principales :**

- Nécessite une compréhension de la spécification de l’API de destination (méthode HTTP, structure d’URL, format de payload, authentification)
- Les informations d’authentification doivent être gérées manuellement dans les éléments de données ou les secrets
- Un code personnalisé peut être nécessaire pour la transformation de la payload (hachage, codage, restructuration)
- Aucune mise à jour automatique lorsque l’API de destination change — maintenance manuelle requise
- La fonctionnalité Secrets de la collecte de données peut stocker en toute sécurité les clés et jetons API

**Avantages :**

- Prend en charge tout point d’entrée accessible via HTTP — aucune dépendance d’extension
- Contrôle total de la payload, des en-têtes et de l’authentification des requêtes
- Peut transférer vers des services internes, des API personnalisées ou des plateformes de niche
- Activation de transformations de payload complexes à l’aide de code personnalisé
- Possibilité d’implémenter une logique de reprise et une gestion des erreurs dans le code personnalisé

**Limitations :**

- Effort d’implémentation initial plus élevé
- Responsabilité de maintenance continue pour le format et l’authentification de la payload
- Aucune gestion d’erreur préconfigurée ni aucune rotation d’informations d’identification ne doivent être mises en œuvre manuellement
- Nécessite une expertise en développement sur les protocoles HTTP et les spécificités des API de destination

**Experience League:**

- [Extension Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Secrets de transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

### Option C : hybride (extensions + webhooks personnalisés)

**Idéal pour :** les organisations qui transfèrent des événements vers plusieurs destinations où certaines disposent d’extensions préconfigurées et d’autres nécessitent une intégration personnalisée.

**Fonctionnement :**

L’approche hybride combine le transfert basé sur les extensions pour les destinations bien prises en charge avec des actions webhook personnalisées pour les destinations qui ne disposent pas d’extensions. Une seule propriété de transfert d’événement contient plusieurs règles, certaines utilisant des actions d’extension (par exemple, l’extension [!DNL Meta] Conversions API pour le suivi des conversions publicitaires) et d’autres utilisant des actions de récupération Cloud Connector (par exemple, le transfert vers un point d’entrée interne du lac de données).

Cette approche optimise la couverture tout en réduisant le développement personnalisé inutile. Chaque règle fonctionne indépendamment. De ce fait, les règles basées sur des extensions bénéficient d’une mise en forme de payload préconfigurée, tandis que les règles personnalisées conservent une flexibilité totale.

**Considérations principales :**

- La complexité de la propriété augmente avec le nombre de règles et de destinations
- Les tests et le débogage peuvent nécessiter différentes approches pour les règles basées sur les extensions par rapport aux règles personnalisées
- Les modifications de publication affectent toutes les règles de la propriété : utilisez des bibliothèques et des environnements pour transférer les modifications en toute sécurité
- Pensez à organiser les règles avec des conventions de nommage claires pour distinguer les actions basées sur les extensions des actions personnalisées

**Avantages :**

- Meilleure couverture pour divers types de destinations
- Exploite les extensions préconfigurées lorsque disponibles, ce qui réduit les efforts
- Maintient la flexibilité pour les destinations personnalisées
- Une propriété de transfert d’événement unique gère toute la logique de transfert

**Limitations :**

- Complexité de propriété plus élevée avec plusieurs types de règle
- Modèle de maintenance mixte : certaines règles sont mises à jour automatiquement via des extensions, d’autres nécessitent une maintenance manuelle
- Le débogage nécessite une connaissance des configurations d’extension et des modèles d’appels de récupération personnalisés

**Experience League:**

- [Présentation du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Prise en main du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)

### Comparaison des options

Le tableau suivant compare les trois options d’implémentation.

| Critères | Option A : Fondé Sur Une Extension | Option B : Webhook Personnalisé | Option C : Hybride |
| --- | --- | --- | --- |
| Idéal pour | Destinations prises en charge ([!DNL Meta], [!DNL Google], [!DNL AWS], etc.) | Points d’entrée personnalisés, plateformes de niche, services internes | Destinations multiples avec prise en charge mixte |
| Complexité | Faible | Medium-Grand | Moyenne |
| Délai de mise en œuvre | Jours | Jours-Semaines | Varie selon le mix de destination |
| Flexibilité | Limité aux fonctionnalités d’extension | Contrôle complet | Contrôle complet si nécessaire |
| Maintenance | Faible (géré par extension) | Élevée (maintenance manuelle) | Mixte |
| Requiert | Extension disponible pour la destination | Documentation de l’API de destination | Les deux, selon la destination |
| Code personnalisé nécessaire | Minimal | Modéré-Significatif | Variable |

### Choisir la bonne option

Commencez par inventorier vos destinations cibles et par vérifier s’il existe des extensions de transfert d’événement préconfigurées pour chacune d’elles.

1. **Si toutes les destinations ont des extensions** — Choisissez l’option A. Vous bénéficiez ainsi de la mise en œuvre la plus rapide et de la maintenance la moins lourde. Les extensions gèrent l’authentification, le formatage de la payload et la gestion des versions d’API.

2. **Si aucune destination n’a d’extensions ou si vous avez besoin d’un contrôle complet de la payload** — Choisissez l’option B. Utilisez l’extension Cloud Connector pour effectuer des requêtes HTTP personnalisées vers n’importe quel point d’entrée. Il s’agit également du bon choix lorsque vous devez appliquer des transformations complexes, un hachage personnalisé ou un envoi à des services internes.

3. **Si vous avez à la fois des destinations prises en charge et non prises en charge** — Choisissez l’option C. Utilisez des extensions pour les plateformes telles que [!DNL Meta], [!DNL Google] et [!DNL AWS], et des webhooks personnalisés pour tout le reste. Il s’agit du scénario de production le plus courant pour les organisations disposant de diverses piles d’analyses et de publicités.

## Phases de mise en œuvre

Les phases suivantes décrivent le processus de mise en œuvre de bout en bout du transfert d’événement.

### Phase 1 : configuration du flux de données

**Fonction d’application :** AEP : configuration du flux de données

**Ce que vous allez configurer :** un flux de données qui reçoit des événements de votre implémentation de SDK Web, de Mobile SDK ou de l’API Server et les achemine vers Edge Network où les règles de transfert d’événement peuvent les traiter. Si le transfert d’événement est ajouté à un déploiement de collecte de données existant, vous activerez le transfert d’événement sur le flux de données existant.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : nouveau flux de données par rapport au flux de données existant**
>
>Devez-vous créer un flux de données pour le transfert d’événement ou activer le transfert d’événement sur un flux de données existant ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Utiliser un flux de données existant | Web SDK ou l’API Server envoient déjà des événements par le biais d’un flux de données | Scénario le plus courant : le transfert d’événement est simplement activé en tant que service supplémentaire sur le flux de données. Aucune modification côté client n’est nécessaire. |
>| Créer un flux de données | Il s’agit d’une implémentation entièrement nouvelle, sans collecte de données existante, ou vous avez besoin d’un flux de données distinct pour des types d’événements spécifiques | Nécessite une configuration SDK côté client pour pointer vers le nouvel identifiant de flux de données. Permet une configuration isolée. |

>[!NOTE]
>
>**Décision : quels services AEP activer avec le transfert d’événement**
>
>Le flux de données peut acheminer simultanément des événements vers plusieurs services AEP. Le transfert d’événement est un service ; d’autres (AEP data ingestion, [!DNL Target], [!DNL Analytics]) peuvent s’exécuter en parallèle.
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Transfert d’événement uniquement | Vous avez uniquement besoin de transférer des événements vers des destinations non Adobe et vous n’avez pas besoin des données des jeux de données AEP | Réduit les coûts de traitement des données. Les événements traversent Edge Network jusqu’aux règles de transfert, mais ne sont pas ingérés dans le lac de données AEP. |
>| Transfert d’événement + ingestion AEP | Vous avez besoin des mêmes événements dans AEP (pour les profils, les audiences, les parcours) et transférés vers des systèmes externes | Le plus souvent, pour les organisations qui utilisent [!DNL RT-CDP] ou [!DNL AJO] avec des analyses tierces. Le flux de données envoie des événements aux jeux de données AEP et aux règles de transfert d’événement. |
>| Transfert d’événement + plusieurs services Adobe | Vous avez besoin d’événements acheminés simultanément vers des destinations AEP, [!DNL Target], [!DNL Analytics] et externes | Activez tous les services requis sur le flux de données. Chaque service reçoit l’événement indépendamment. |

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Collecte de données > Flux de données > Sélectionner ou créer un flux de données

**Détails de configuration clés :**

- Le transfert d’événement doit être activé pour le flux de données dans ses paramètres avancés ou sa configuration de service
- Liez la propriété de transfert d’événement (créée à la phase 2) au flux de données
- Vérifiez que le schéma XDM affecté au flux de données correspond à la structure d’événement envoyée par votre mécanisme de collecte

**Documentation Experience League :**

- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation des flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Présentation du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)

### Phase 2 : propriété et extensions du transfert d’événement

**Fonction d’application :** AEP : configuration de la propriété de transfert d’événement

**Ce que vous allez configurer :** une propriété de transfert d’événement dans l’interface utilisateur de la collecte de données, ainsi que les extensions nécessaires à vos destinations cibles. La propriété de transfert d’événement est le conteneur de toutes les règles, de tous les éléments de données et de toutes les extensions qui définissent votre logique de transfert côté serveur.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : propriété unique ou propriétés multiples**
>
>Devriez-vous utiliser une seule propriété de transfert d’événement pour toutes les destinations ou des propriétés distinctes ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Propriété unique | La plupart des implémentations ; toutes les règles de transfert partagent le même flux d’événement | Plus simple à gérer, workflow de publication unique, toutes les règles sont évaluées par rapport à chaque événement. Utilisez des conditions de règle pour filtrer les événements qui vont vers les destinations. |
>| Plusieurs propriétés | Vous avez besoin de différentes équipes pour gérer différentes intégrations de destinations de manière indépendante ou vous avez des exigences strictes d’isolation de l’environnement | Chaque propriété possède son propre workflow de publication et peut être liée à différents flux de données. Augmente les frais de gestion, mais améliore les limites du contrôle d’accès. |

>[!NOTE]
>
>**Décision : quelles extensions installer**
>
>Sélectionnez les extensions en fonction de vos destinations cibles et de l’option d’implémentation choisie (A, B ou C ci-dessus).
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Extensions spécifiques à une destination ([!DNL Meta], [!DNL Google], [!DNL AWS], etc.) | La destination dispose d’une extension préconfigurée et vous souhaitez une configuration personnalisée minimale (option A ou C) | Chaque extension nécessite des informations d’identification spécifiques à la destination (jetons API, identifiants de mesure, identifiants de compte). Consultez la documentation de l’extension pour les types d’événement pris en charge et les champs obligatoires. |
>| Extension Cloud Connector uniquement | Toutes les destinations utiliseront des requêtes HTTP personnalisées (option B) | L’extension Cloud Connector est installée par défaut. Utilisez la fonctionnalité Secrets pour stocker en toute sécurité les clés API et les jetons d’authentification. |
>| Spécifiques à la destination et Cloud Connector | Vous disposez d’une combinaison de destinations prises en charge et personnalisées (option C) | Installez des extensions spécifiques pour les destinations correctement prises en charge et utilisez Cloud Connector pour les autres. |

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Collecte de données > Transfert d’événement > Créer une propriété (ou sélectionner existante)

**Détails de configuration clés :**

- Nommez la propriété avec une convention claire (par exemple, « Transfert d’événement - Production » ou « EF - Analytics et Advertising »).
- Installer l’extension [!DNL Adobe Cloud Connector] (incluse par défaut pour les actions webhook personnalisées)
- Installation d’extensions spécifiques à une destination et configuration de leurs informations d’identification
- Utilisez la fonctionnalité Secrets (Collecte de données > Transfert d’événement > Secrets) pour stocker en toute sécurité les clés API, les jetons et les informations d’identification
- Configurez des environnements (développement, évaluation, production) pour des workflows de publication sécurisés

**Documentation Experience League :**

- [Prise en main du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Catalogue des extensions de transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Secrets de transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)
- [Extension Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Phase 3 : définition des règles d’événement

**Fonction d’application :** AEP : Définition de règle d’événement, AEP : Mappage de destination

**Éléments à configurer :** règles qui évaluent les données d’événement entrantes, appliquent des conditions pour filtrer les événements à transférer et définissent des actions qui envoient les données aux points d’entrée de destination. Chaque règle se compose de conditions (quand déclencher) et d’actions (que faire). Les éléments de données extraient et transforment des valeurs de la payload d’événement XDM pour les utiliser dans des conditions de règle et des configurations d’action.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : stratégie de filtrage des événements**
>
>Comment devez-vous déterminer les événements qui sont transférés à chaque destination ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Transférer tous les événements | La destination a besoin d’un flux d’événements complet (par exemple, data warehouse pour le stockage brut des événements) | Configuration la plus simple : aucune condition requise. Volume de données élevé à la destination. Tenez compte des limites de coût et de taux de destination. |
>| Filtrer par type d’événement | Différentes destinations ont besoin de différents types d’événements (par exemple, achats vers publicité, pages vues vers analytics) | Utilisez des conditions basées sur des champs XDM `arc.event.xdm.eventType` ou similaires. Réduit les données inutiles à la destination. |
>| Filtrer par attributs d’événement | Seuls les événements spécifiques répondant à certains critères doivent être transférés (par exemple, les achats supérieurs à un seuil, les événements provenant de chemins de page spécifiques). | Utilisez des valeurs d’élément de données dans des conditions de règle. Plus complexe mais réduit le bruit à destination. |

>[!NOTE]
>
>**Décision : approche de la transformation des données**
>
>Comment les données d’événement XDM doivent-elles être transformées pour la payload de destination ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Mappage direct des champs XDM via des éléments de données | Les champs de destination correspondent parfaitement aux champs XDM (communs avec le transfert basé sur une extension) | Créez des éléments de données qui référencent des chemins XDM (par exemple, `arc.event.xdm.commerce.order.priceTotal`). Les extensions fournissent souvent une interface utilisateur de mappage. |
>| Transformation du code personnalisé | La destination nécessite un format de payload considérablement différent de XDM ou les champs nécessitent un hachage, une concaténation ou une restructuration | Utilisez des éléments de données de code personnalisé ou du code personnalisé de niveau action pour transformer la payload. Plus flexible mais plus difficile à gérer. |
>| Combinaison d’éléments de données et de code personnalisé | Certains champs sont directement mappés, tandis que d’autres doivent être transformés. | Utilisez des éléments de données pour les mappages simples et des blocs de code personnalisés pour les transformations complexes. Équilibrez la maintenabilité et la flexibilité. |

>[!NOTE]
>
>**Décision : gestion des PII dans les données transférées**
>
>Comment les informations d’identification personnelle doivent-elles être traitées avant le transfert ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Exclure entièrement les champs PII | La destination n’a pas besoin de PII et les politiques de gouvernance limitent le partage | Configurez des règles pour omettre les champs PII de la payload transférée. Approche la plus simple pour la conformité en matière de confidentialité. |
>| Hacher les champs PII avant le transfert | La destination nécessite des identifiants hachés (par exemple, [!DNL Meta] nécessite un e-mail haché SHA-256 pour l’API Conversions). | Utilisez des éléments de données de code personnalisé pour appliquer le hachage SHA-256. Certaines extensions gèrent automatiquement le hachage. |
>| Transférer les PII avec une base contractuelle | La destination dispose d’un accord de traitement des données et la base juridique du partage des informations d’identification personnelle existe | Assurez-vous que les libellés d’utilisation des données et les politiques de gouvernance (S3) permettent le partage. Documentez la base juridique. |

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Collecte de données > Transfert d’événement > Sélectionner une propriété > Éléments de données / Règles

**Détails de configuration clés :**

- **Éléments de données** référencez l’événement XDM entrant à l’aide du `arc.event.xdm.` de préfixe de chemin (par exemple, `arc.event.xdm.web.webPageDetails.URL` pour l’URL de la page)
- **Conditions des règles** évaluez les valeurs des éléments de données pour déterminer si la règle doit se déclencher
- **Actions de règle** utilisez des actions spécifiques à l’extension (pour l’option A) ou des actions « Effectuer un appel de récupération » du connecteur cloud (pour l’option B) pour envoyer des données aux destinations
- Chaque règle peut comporter plusieurs actions, ce qui permet de transférer un seul événement vers plusieurs destinations
- Utilisez l’ordre des règles pour contrôler la séquence d’évaluation lorsque plusieurs règles peuvent se déclencher pour le même événement
- Testez minutieusement les règles dans l’environnement de développement avant de les publier en production.

**Là où les options divergent :**

**Pour L’Option A (Basée Sur Une Extension) :**

Configurez les actions de règle à l’aide des types d’actions préconfigurés de l’extension de destination. Par exemple, l’extension d’API Conversions [!DNL Meta] fournit une action « Envoyer l’événement » dans laquelle vous mappez les champs XDM aux paramètres d’événement [!DNL Meta] (event_name, event_time, user_data, custom_data). L’extension gère le formatage, le hachage et la communication d’API de la payload.

**Pour L’Option B (Webhook Personnalisé) :**

Configurez les actions de règle à l’aide de l’action « Effectuer l’appel de récupération » de l’extension Cloud Connector. Spécifiez l’URL de destination, la méthode HTTP (généralement POST), les en-têtes de requête (y compris l’autorisation) et construisez le corps de la requête à l’aide d’éléments de données et/ou de code personnalisé. Il vous incombe de correspondre exactement au format de payload attendu de l’API de destination.

**Pour L’Option C (Hybride) :**

Créez des règles distinctes pour chaque destination. Les règles basées sur des extensions utilisent les types d’action de l’extension. Les règles personnalisées utilisent les appels de récupération de Cloud Connector. Toutes les règles coexistent dans la même propriété et sont évaluées indépendamment par rapport à chaque événement entrant.

**Documentation Experience League :**

- [Règles de transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Éléments de données dans le transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/data-elements)
- [Règles de la collecte de données](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/rules)
- [Extension Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Phase 4 : publication et activation

**Fonction d’application :** AEP : transfert d’exécution

**Ce que vous allez configurer :** workflow de publication qui promeut vos règles de transfert d’événement du développement à la production en passant par l’évaluation. Le transfert d’événement utilise le même modèle de publication basé sur une bibliothèque que les balises, avec des environnements et des artefacts de build qui contrôlent la configuration active au niveau d’Edge Network.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : rigueur du workflow de publication**
>
>Quelle doit être la rigueur du processus de publication ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Direct à la production (développement > production) | Petites équipes, destinations à faible risque ou implémentations de preuve de concept | Déploiement plus rapide mais risque plus élevé de problèmes de production. Convient pour les tests initiaux avec des destinations non critiques. |
>| Progression complète de l’environnement (Développement > Évaluation > Production) | Implémentations de production avec des destinations critiques (plateformes publicitaires, entrepôts de données) | Recommandé pour tous les cas d’utilisation en production. L’évaluation permet la validation avec du trafic réel avant le déploiement en production. |

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Collecte de données > Transfert d’événement > Sélectionner une propriété > Flux de publication

**Détails de configuration clés :**

- Créez une bibliothèque contenant toutes les règles, les éléments de données et les configurations d’extension à publier
- Créez et testez-les dans l’environnement de développement à l’aide de l’outil de surveillance du transfert d’événement pour vérifier que les événements sont transférés correctement
- Promouvoir dans l’évaluation pour la validation de pré-production avec trafic en direct
- Publier en production uniquement après avoir confirmé la réussite de la diffusion de l’événement dans l’évaluation
- Utilisez le contrôle de version des bibliothèques pour suivre les modifications et activer la restauration si nécessaire

**Documentation Experience League :**

- [Présentation de la publication](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview)
- [Bibliothèques](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/libraries)
- [Environnements](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/environments)
- [Versions](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/builds)

### Phase 5 : suivi et validation

**Fonction d’application :** AEP : Surveillance

**Éléments à configurer :** surveiller les tableaux de bord et les processus de validation pour confirmer que les événements sont transférés avec succès, diagnostiquer les échecs et maintenir l’intégrité opérationnelle du déploiement du transfert d’événement.

**Points de décision au cours de cette phase :**

>[!NOTE]
>
>**Décision : profondeur de surveillance**
>
>À quel niveau le transfert d’événement doit-il être surveillé ?
>
>| Option | Quand choisir | Considérations |
>| --- | --- | --- |
>| Tableau de bord de surveillance du transfert d’événement uniquement | Surveillance de base des destinations non critiques ou des déploiements initiaux | Fournit un aperçu des taux de réussite/échec du transfert et des codes de réponse de destination. Suffisant pour la plupart des implémentations. |
>| Surveillance du transfert d’événement + validation côté destination | Destinations critiques où l’exhaustivité des données affecte directement les résultats commerciaux (suivi des conversions publicitaires, intégrité de l’entrepôt de données) | Référencez les mesures de transfert côté Adobe avec la confirmation de réception côté destination. Capture les cas Edge où la destination accepte la requête mais ne parvient pas à traiter les données. |
>| Pile d’observabilité complète (surveillance du transfert d’événement + validation de destination + alertes AEP) | Déploiements à l’échelle de l’entreprise avec des exigences SLA en matière de diffusion de données | Combinez la surveillance du transfert d’événement aux alertes de la plateforme AEP pour obtenir une vue d’ensemble complète. Configurez les notifications d’alerte pour le transfert des seuils d’échec. |

**Navigation dans l’interface utilisateur :** [!DNL Experience Platform] > Collecte de données > Transfert d’événement > Sélectionner une propriété > Surveillance

**Détails de configuration clés :**

- L’outil de surveillance du transfert d’événement affiche le volume des événements, les taux de succès et les détails des erreurs par règle et par destination
- Surveiller les codes de réponse HTTP des destinations : 2xx indique la réussite, 4xx indique des erreurs client (problèmes probables de payload ou d’authentification), 5xx indique des échecs côté destination
- Utilisez l’extension de navigateur [!DNL Adobe Experience Platform Debugger] pour inspecter les événements provenant du client via Edge Network vers les règles de transfert d’événement
- Validez le processus de bout en bout en vérifiant que les événements transférés apparaissent dans le système de destination (par exemple, vérifiez [!DNL Google Analytics] rapports en temps réel, [!DNL Meta] le gestionnaire d’événements ou les tables de l’entrepôt de données).
- Configurez des alertes AEP pour les échecs de source et de flux de données afin de détecter les problèmes en amont qui empêcheraient les événements d’atteindre les règles de transfert d’événement

**Documentation Experience League :**

- [Surveillance du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/en/docs/experience-platform/debugger/home)
- [Présentation des alertes](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

## Considérations relatives à la mise en œuvre

Cette section couvre les mécanismes de sécurisation, les pièges courants, les bonnes pratiques et les décisions d’arbitrage à garder à l’esprit tout au long de la mise en œuvre.

### Mécanismes de sécurisation et limites

- Le transfert d’événement traite les événements en temps réel dans Edge Network. Par défaut, il n’existe pas de mode par lot ni de file d’attente de reprises pour les diffusions ayant échoué
- Les limites de débit d’Edge Network s’appliquent au volume total d’événements traités par flux de données - [mécanismes de sécurisation d’Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/guardrails)
- Les règles de transfert d’événement s’exécutent côté serveur et ne peuvent pas accéder aux ressources côté client (DOM, cookies, localStorage)
- Le code personnalisé des règles de transfert d’événements s’exécute dans un environnement en sandbox ; toutes les API JavaScript de navigateur ne sont pas disponibles
- L’appel de récupération de Cloud Connector présente des limites de délai d’expiration : les destinations qui répondent lentement peuvent entraîner des délais d’expiration
- Le transfert d’événement est soumis au routage géographique d’Edge Network. Les événements sont traités à l’emplacement Edge le plus proche
- La taille maximale de la payload pour les requêtes transférées est régie par les limites d’Edge Network

### Pièges courants

- **Transfert de tous les champs XDM sans filtrage :** l’envoi de la payload complète de l’événement XDM vers une destination qui n’a besoin que de quelques champs réduit la bande passante, augmente les coûts de destination et peut partager des informations d’identification personnelles par inadvertance. Mappez toujours uniquement les champs obligatoires dans vos règles de transfert.

- **Ne pas sécuriser les informations d’identification avec des secrets :** le codage en dur des clés API ou des jetons dans les éléments de données ou les actions de règle crée un risque pour la sécurité. Utilisez toujours la fonction Secrets de la collecte de données pour stocker les informations d’identification en toute sécurité et les référencer dans des règles.

- **Ignorer les limites de taux de destination :** les destinations tierces ont souvent des limites de taux d’API. Si le volume de vos événements dépasse la capacité d’une destination, les événements peuvent être ignorés ou votre accès à l’API peut être limité. Consultez la documentation de destination pour connaître les limites de débit et implémentez le filtrage afin de réduire le volume d’événements si nécessaire.

- **Publication directe en production sans évaluation :** l’omission de l’environnement d’évaluation signifie que les erreurs ne sont découvertes qu’en production, ce qui peut entraîner une perte de données au niveau des destinations critiques. Commencez toujours par valider dans l’évaluation avec le trafic en direct.

- **Ne pas surveiller les codes de réponse HTTP :** une règle qui se déclenche sans erreur ne garantit pas que la destination a traité les données avec succès. Surveillez les codes de réponse de destination (disponibles dans l’outil de surveillance du transfert d’événements) et recherchez toutes les réponses autres que 2xx.

- **Références de chemin XDM mal configurées :** les éléments de données utilisent le préfixe `arc.event.xdm.` pour référencer les champs d’événement entrants. Un chemin d’accès incorrect (par exemple, il manque un niveau d’imbrication) produit silencieusement des valeurs nulles au lieu de générer des erreurs. Validez les valeurs des éléments de données à l’aide du débogueur.

### Bonnes pratiques

- **Commencez avec une seule destination et développez-la progressivement** — Validez le transfert d’événement de bout en bout avec une destination avant d’ajouter des règles et des destinations supplémentaires. Cela simplifie le débogage et renforce la confiance dans l’infrastructure.

- **Utiliser des conventions de nommage cohérentes** — Nommez les éléments de données, les règles et les bibliothèques avec une convention claire qui identifie la destination, le type d’événement et l’environnement (par exemple, « Règle : Meta - Événements d’achat », « DE : Total de la commande »).

- **Mettre en œuvre le filtrage au niveau des champs à des fins de confidentialité** — Même si la destination prétend gérer les informations d’identification personnelles de manière appropriée, appliquer un filtrage côté serveur pour supprimer ou hacher les champs sensibles avant qu’ils ne quittent Edge Network. Il s’agit du principal avantage du transfert d’événement en matière de gouvernance par rapport aux balises côté client.

- **Version de vos configurations** — Utilisez le workflow de publication de bibliothèque pour conserver des instantanés avec version de votre configuration de transfert d&#39;événement. Documentez ce que chaque version de bibliothèque contient à des fins d’audit et de restauration.

- **Tester avec Platform Debugger** — L’extension [!DNL Adobe Experience Platform Debugger] offre une visibilité sur le cycle de vie des événements, depuis SDK côté client jusqu’au traitement Edge Network. Utilisez-le pendant le développement et le dépannage.

- **Aligner les règles de transfert d’événement sur votre conception de schéma XDM** — Si le transfert d’événement est une exigence connue, concevez votre schéma XDM et votre taxonomie d’événement pour inclure les champs dont les destinations auront besoin. La mise à niveau des modifications de schéma après le déploiement est plus perturbatrice.

### Décisions de compromis

>[!NOTE]
>
>**Compromis : simplicité de l’extension par rapport à la flexibilité du webhook**
>
>Les extensions préconfigurées réduisent les efforts d’implémentation et de maintenance, mais elles vous limitent aux fonctionnalités et aux formats de payload pris en charge par l’extension. Les webhooks personnalisés offrent un contrôle total, mais nécessitent davantage de développement et de maintenance continue.
>
>- **L’option A (extension) privilégie :** mise sur le marché rapide, dépendance réduite envers les développeurs, gestion automatique des informations d’identification, maintenance réduite
>- **L’option basée sur Webhook (option B) privilégie :** contrôle complet de la payload, prise en charge de n’importe quel point d’entrée HTTP, logique de transformation personnalisée, indépendance par rapport aux cycles de publication des extensions
>- **Recommandation** utilisez des extensions lorsqu’elles sont disponibles et suffisantes. Revenez aux Webhooks personnalisés uniquement lorsque la destination ne dispose pas d’extension ou lorsque l’extension ne prend pas en charge les fonctionnalités d’API spécifiques dont vous avez besoin. L’approche hybride (option C) est le choix pragmatique pour la plupart des organisations.

>[!NOTE]
>
>**Compromis : transférer tous les événements par rapport au filtrage sélectif**
>
>Le transfert de tous les événements vers une destination garantit l’exhaustivité, mais augmente le volume de données, les coûts de destination et la vulnérabilité en matière de confidentialité. Le filtrage sélectif réduit le bruit, mais risque d’ignorer des événements qui peuvent s’avérer utiles.
>
>- **Transférer tous les événements privilégie :** l’exhaustivité, la simplicité et la pérennisation des données (les données sont là si nécessaire ultérieurement)
>- **Le filtrage sélectif favorise :** rentabilité, risque réduit pour la confidentialité, données de destination plus propres, conformité aux principes de minimisation des données.
>- **Recommandation :** par défaut, le filtrage sélectif est basé sur le type d’événement et la pertinence commerciale. Transférez uniquement les événements et champs dont chaque destination a réellement besoin. Cela est conforme aux principes de minimisation des données (article 5 du RGPD) et réduit les coûts opérationnels.

>[!NOTE]
>
>**Compromis : propriété unique par rapport à plusieurs propriétés**
>
>La gestion d’une seule propriété de transfert d’événement est plus simple, mais cela signifie que toutes les règles partagent un seul workflow de publication. Plusieurs propriétés assurent l’isolement, mais augmentent les frais de gestion.
>
>- **La propriété unique privilégie :** simplicité, publication unifiée, éléments de données partagés, débogage plus facile.
>- **Avantages de plusieurs propriétés :** contrôle d’accès au niveau de l’équipe, cadences de publication indépendantes, isolation des échecs de destination
>- **Recommandation :** commencez avec une seule propriété pour la plupart des implémentations. Ne les diviser en plusieurs propriétés que si différentes équipes possèdent différentes intégrations de destination et ont besoin de cycles de publication indépendants ou si les exigences réglementaires exigent une isolation stricte entre les flux de données.

## Documentation connexe

Les ressources suivantes apportent des détails supplémentaires sur les sujets abordés dans ce guide.

**Transfert d’événement**

- [Présentation du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Prise en main du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Surveillance du transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Secrets de transfert d’événement](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

**Extensions de transfert d’événement**

- [Catalogue des extensions côté serveur](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Extension Adobe Cloud Connector](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Extension de l’API de conversions Meta](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Extension Google Cloud Platform](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [Extension AWS](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Extension Snowflake](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Extension Google Ads Enhanced Conversions](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Extension Mailchimp](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**Collecte de données et Edge Network**

- [Configurer les flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Présentation des flux de données](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Présentation de Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Présentation de l’API du serveur Edge Network](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Présentation des balises](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
