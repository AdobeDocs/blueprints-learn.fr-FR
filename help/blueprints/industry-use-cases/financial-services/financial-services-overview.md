---
title: Cas d’utilisation des services financiers
description: Découvrez comment les entreprises de services financiers utilisent Adobe Experience Platform pour personnaliser les offres de produits, empêcher l’attrition et approfondir les relations client.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 1f22d684-11bd-473d-8b10-5f88cb0cd088
source-git-commit: 0236bd326730ee9a0be621ee0e60ddc3d352410d
workflow-type: tm+mt
source-wordcount: '4039'
ht-degree: 0%

---

# Cas d’utilisation des services financiers

Les sociétés de services financiers s’appuient sur Adobe Experience Platform pour unifier les données clients sur les canaux bancaires, de prêt et d’investissement, ce qui permet des expériences personnalisées qui renforcent les relations et stimulent la croissance. En associant l’activité du compte, l’historique des transactions et les signaux comportementaux, ces organisations peuvent proposer la bonne offre au bon moment, tout en maintenant la confiance et la conformité attendues de leurs clients.

## Formation de leads à haute valeur ajoutée

Identifiez les prospects à forte valeur ajoutée en fonction des données de profil et du comportement, puis nourrissez-les avec du contenu et des offres personnalisés grâce à des parcours automatisés. En combinant les détails démographiques, l’activité de navigation et les signaux d’engagement, les institutions financières peuvent prioriser les prospects les plus susceptibles de convertir leurs clients et les guider sur un chemin personnalisé vers leur clientèle.

### Impact commercial

Les entreprises qui mettent en œuvre des méthodes d’entretien de prospect à forte valeur ajoutée constatent une amélioration des taux de conversion de prospect à client tout en créant un pipeline des ventes plus sain et plus prévisible.

### Mise en œuvre

Utilisez le modèle Parcours orchestré en plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer des séquences de maturation automatisées qui s’adaptent en fonction de l’engagement des prospects et des signaux de préparation. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux séquentiel de plusieurs messages sur plusieurs jours avec un embranchement conditionnel basé sur les mesures d’engagement. Un message déclenché unique ne peut pas s’adapter à la logique d’entretien adaptative ou à la logique de dépendance entre les étapes de qualification.

### Considérations techniques

- Intégrez les données de score de prospect CRM et les événements comportementaux du site web dans des profils de prospects unifiés pour alimenter la logique d’entrée et de branchement du parcours.
- Assurez-vous que les préférences de consentement et d’opt-in sont appliquées à chaque point de contact, en particulier pour les communications par téléphone et par e-mail, régies par les réglementations du marketing financier.
- Configurez la limitation du parcours pour éviter de surcharger les prospects avec plusieurs communications pendant de courtes fenêtres d’évaluation.
- Tenez compte de la latence des données entre les interactions des succursales ou des conseillers et de l’engagement numérique pour maintenir la pertinence des messages de soutien.


## Recommandations de produits pour les clients existants

Recommander des produits financiers pertinents tels que des cartes de crédit, des prêts et des produits d&#39;investissement aux clients existants en fonction de leur profil, de leur historique de transactions et de leur stade de vie. Ce cas d’utilisation transforme les données de compte quotidiennes en informations exploitables qui permettent de trouver le meilleur produit pour chaque client.

### Impact commercial

Les recommandations de produits personnalisées augmentent les taux d’adoption des produits et augmentent de manière mesurable la valeur de durée de vie du client en approfondissant le partage de portefeuille.

### Mise en œuvre

Utilisez le modèle [&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pour évaluer en temps réel chaque client par rapport aux offres de produits éligibles, en classant les recommandations par pertinence et priorité commerciale. Il s’agit du bon modèle lorsque la sélection des offres doit tenir compte des règles d’adéquation financière et des contraintes d’éligibilité réglementaires, contraintes qui nécessitent une logique de prise de décision régie plutôt qu’un classement par affinités comportementales uniquement.

### Considérations techniques

- Regroupez les données de transaction, les soldes de compte et les portefeuilles de produits en un seul profil client afin que les modèles de prise de décision aient une vue complète des relations existantes.
- Appliquez les règles d&#39;adéquation financière et les contraintes d&#39;éligibilité réglementaires en tant que mécanismes de sécurisation stricts dans le moteur de décision avant de classer les offres.
- Coordonner la diffusion des offres sur les canaux banque en ligne, application mobile, e-mail et conseiller pour éviter les recommandations en conflit ou en double.
- Mettez en œuvre un capping de la fréquence par catégorie de produits pour éviter la lassitude face aux recommandations, en particulier pour les produits à forte valeur ajoutée tels que les prêts hypothécaires et les comptes de placement.


## Campagnes de prévention de l’attrition

Identifiez les clients à risque de résiliation à l’aide de la prédiction de résiliation optimisée par l’IA et impliquez-les avec des offres de rétention et des communications personnalisées. La détection précoce des signaux de désengagement permet aux institutions financières d&#39;intervenir avant qu&#39;un client ferme des comptes ou déplace des actifs ailleurs.

### Impact commercial

Les efforts proactifs de prévention de la perte de clientèle permettent de réduire l’attrition des clients, de protéger les flux de revenus récurrents et de réduire le coût de remplacement des clients.

### Mise en œuvre

Utilisez le modèle [Cross-Channel Parcours with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour déclencher des parcours de rétention lorsque les scores de risque de résiliation dépassent les seuils définis, avec une prise de décision intégrée pour sélectionner l’offre de rétention la plus attrayante. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion entre les canaux pour éviter les offres de rétention en double et lorsque la sélection de l’offre nécessite des seuils de score de risque et des contraintes commerciales - l’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision en temps réel nécessaire pour sélectionner l’offre de rétention optimale par client.

### Considérations techniques

- Intégrez les tendances d’activité des comptes, l’historique des interactions de services et la fréquence d’engagement dans [!DNL Customer AI] modèles de propension à l’attrition pour générer des scores de risque.
- Définissez des seuils de risque de résiliation spécifiques aux lignes de produits, les signaux de désengagement pour les comptes de contrôle étant différents de ceux des portefeuilles d’investissement.
- Examinez les critères de ciblage et de suppression avec vos équipes juridiques et de confidentialité pour vous assurer de la conformité aux réglementations applicables en matière de prêt équitable et d’égalité de traitement avant d’activer les offres de conservation.
- Développez une logique de suppression afin d’exclure les clients qui se désinscrivent en raison de fraudes ou de mesures de conformité, où la sensibilisation à la rétention serait inappropriée.


## Tableau de bord du compte personnalisé

Personnalisez le tableau de bord des services bancaires en ligne et l’expérience de l’application mobile en fonction de l’activité du compte, des préférences et des objectifs financiers de chaque client. Un tableau de bord personnalisé aide les clients à trouver ce qui compte le plus et affiche les informations pertinentes sans qu’ils aient à effectuer de recherches.

### Impact commercial

Les tableaux de bord personnalisés augmentent les taux d’engagement et améliorent de manière significative les scores de satisfaction client en rendant les services bancaires numériques intuitifs et pertinents.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pour diffuser des blocs de contenu personnalisés en temps réel, des spots sur les produits et des informations financières dans des expériences digitales authentifiées. Il s’agit du modèle approprié lorsque la personnalisation est pilotée par les attributs de profil et l’activité de compte plutôt que par un modèle d’affinité comportementale, et lorsque la latence inférieure à la seconde est essentielle à l’expérience utilisateur.

### Considérations techniques

- Tirez parti des [!DNL Edge Network] pour les décisions de personnalisation de moins d’une seconde dans les sessions bancaires authentifiées où la latence affecte directement l’expérience utilisateur.
- Agrégez les données de transaction en attributs de profil précalculés, tels que les catégories de dépenses et les tendances d’épargne, afin d’éviter le calcul en temps réel de jeux de données volumineux.
- Respectez les normes d’accessibilité et assurez-vous que le contenu personnalisé répond aux mêmes exigences réglementaires de divulgation que le contenu statique.
- Coordonnez la logique de personnalisation entre les canaux web et mobiles afin que les clients bénéficient d’une expérience cohérente, quel que soit l’appareil.


## Offres De Produits Basées Sur Les Étapes De Vie

Identifiez les clients qui entrent dans de nouvelles étapes de la vie, comme le mariage, l&#39;achat d&#39;une maison ou la retraite, et proposez de façon proactive des produits et services financiers pertinents. L&#39;anticipation de ces jalons permet aux établissements de se positionner en tant que partenaires de confiance lors de moments financiers cruciaux.

### Impact commercial

Les offres déclenchées par l’étape de vie atteignent des taux d’adoption de produits plus élevés, surpassent les campagnes génériques, tout en renforçant les relations client à long terme.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour détecter les indicateurs d’étape de vie et orchestrer des parcours multi-touch avec une sélection d’offres incorporée adaptée à chaque jalon. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion sur plusieurs canaux au cours de moments financiers critiques et lorsque la sélection des offres nécessite des contrôles d’adéquation et des règles métier. En effet, l’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision nécessaire pour assurer la conformité et la pertinence.

### Considérations techniques

- Combinez des signaux propriétaires tels que les changements d’adresse, les ouvertures de compte conjointes et les dépôts importants avec des données tierces autorisées pour déduire les transitions d’étape de vie.
- Gérez les événements personnels sensibles avec soin dans le ton et la fréquence des messages, car des jalons déduits de manière incorrecte peuvent éroder la confiance.
- Appliquez des contrôles d’adéquation réglementaire à Offer Decisioning afin que les produits recommandés s’alignent sur la situation financière vérifiée du client.
- Établissez des périodes de réflexion entre les campagnes d’étape de vie afin d’éviter le chevauchement des activités de sensibilisation lorsque plusieurs indicateurs se déclenchent dans une courte fenêtre.


## Alertes et recommandations basées sur les transactions

Envoyez des alertes en temps réel pour les transactions et fournissez des recommandations personnalisées basées sur les modèles de dépense et l’activité du compte. Des notifications opportunes et pertinentes permettent aux clients d’être informés et créent des moments naturels pour faire apparaître des conseils financiers utiles.

### Impact commercial

Les alertes basées sur les transactions stimulent un engagement fort, améliorant la sensibilisation à la sécurité et la création de points de contact à forte valeur ajoutée pour des recommandations personnalisées.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour répondre aux événements de transaction en temps réel avec des alertes et des recommandations pertinentes du point de vue contextuel. Il s’agit du modèle approprié lorsque le déclencheur est un événement système plutôt qu’un comportement client et lorsque la communication requise est immédiate et réactive plutôt qu’une séquence d’évolution soutenue : la latence des alertes a un impact direct sur l’efficacité de la sécurité.

### Considérations techniques

- Ingérez des événements de transaction par le biais d’un pipeline de diffusion en continu avec des exigences de diffusion à faible latence, car les alertes de sécurité perdent de la valeur si elles sont retardées de plus de quelques minutes.
- Appliquez les préférences et les seuils d’alerte définis par le client ou la cliente afin que les notifications reflètent des paramètres individuels plutôt que des règles uniformes.
- Séparez les alertes de sécurité obligatoires des messages de recommandation facultatifs dans l&#39;architecture de messagerie pour vous assurer que les notifications de conformité ne sont jamais supprimées.
- Tenez compte des volumes de transactions élevés pendant les périodes de pointe, telles que les jours de paie et les jours fériés, en concevant une capacité de débit qui évolue en fonction de la demande.


## Récupération de la demande d&#39;abandon de carte de crédit

Identifiez les clients qui ont commencé mais n’ont pas terminé leurs demandes de carte de crédit et réengagez-les avec des messages et des offres personnalisés. L’abandon d’une application représente une audience à forte intention qui n’a souvent besoin que d’un petit coup de pouce pour terminer le processus.

### Impact commercial

Les campagnes de récupération des abandons améliorent le taux d’achèvement des applications, augmentant directement l’acquisition de nouveaux comptes auprès d’une audience qui a déjà exprimé son intérêt.

### Mise en œuvre

Utilisez le modèle [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour détecter les événements d’abandon d’application et déclencher des messages de suivi opportuns qui répondent aux raisons courantes de déperdition. Il s’agit du modèle approprié lorsqu’une action client discrète (abandon) est le déclencheur et que la réponse requise est un message sensible au facteur temps diffusé avant que les données de l’application ne deviennent obsolètes : une séquence à plusieurs étapes ne peut pas prendre en charge l’urgence et une fenêtre de récupération étroite.

### Considérations techniques

- Capturez l’étape spécifique à laquelle l’application a été abandonnée afin d’adapter la messagerie, car une personne qui a déposé son dossier lors de la vérification d’identité a besoin d’une assurance différente de celle qui a quitté lors de la révision des conditions.
- Collaborez avec vos équipes juridiques et de conformité pour vérifier que toutes les communications de récupération répondent aux exigences de divulgation marketing de crédit applicables et aux règles de consentement spécifiques aux canaux avant le déploiement.
- Implémentez une logique de décroissance temporelle afin que la diffusion de la récupération s’arrête après une fenêtre définie, car les données obsolètes de l’application peuvent ne plus être valides pour la préqualification.
- Coordonnez-vous avec le système d’application afin de supprimer les messages de récupération pour les candidats qui ont répondu via un autre canal, tel qu’une visite de filiale ou un appel téléphonique.


## Recommandations relatives à Investment Portfolio

Fournir des recommandations d&#39;investissement personnalisées basées sur le profil de risque, l&#39;historique d&#39;investissement et les objectifs financiers de chaque client. Les conseils de portefeuille axés sur les données aident les clients à prendre des décisions éclairées tout en approfondissant leur engagement auprès des services de gestion de patrimoine.

### Impact commercial

Les recommandations d’investissement personnalisées favorisent l’adoption de produits d’investissement et améliorent la diversification du portefeuille au sein de la clientèle.

### Mise en œuvre

Utilisez le modèle [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) pour analyser le comportement et les préférences en matière d’investissement, puis obtenez des recommandations de portefeuille pertinentes par le biais de canaux numériques et d’outils de conseil. Il s’agit du bon modèle lorsque l’ensemble d’éléments (univers d’investissement) est volumineux et que la sélection est motivée par une affinité comportementale et une alignement des risques, plutôt que par un ensemble limité d’offres régies par des règles d’éligibilité strictes ou une prise de décision fondée uniquement sur un contrôle de l’adéquation.

### Considérations techniques

- Intégrez les flux de données de courtage et de conservation pour maintenir une vue précise et à jour des avoirs et de l&#39;allocation actuels de chaque client.
- Faites respecter les exigences de conformité exigées par les réglementations sur les valeurs mobilières afin que les recommandations s&#39;alignent sur les objectifs documentés de tolérance au risque et d&#39;investissement du client.
- Clairement étiqueter le contenu d&#39;investissement personnalisé comme étant éducatif ou informatif si nécessaire, en le distinguant des conseils d&#39;investissement officiels assortis d&#39;obligations fiduciaires.
- Actualisez régulièrement les modèles de recommandation pour tenir compte des fluctuations du marché, de la dérive du portefeuille et des changements dans les objectifs des clients.


## Personalization d’alerte de fraude

Personnalisez les alertes de fraude et les communications de sécurité en fonction des préférences de communication de chaque client et de son historique d’interactions. Les alertes personnalisées augmentent la probabilité que les clients remarquent, comprennent et agissent sur les notifications de sécurité critiques.

### Impact commercial

Les alertes de fraude personnalisées améliorent les taux de réponse aux alertes, renforcent la conformité en matière de sécurité et réduisent la fenêtre d&#39;exposition lors d&#39;activités suspectes.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour diffuser des alertes de fraude par le canal préféré de chaque client avec des détails contextuels qui facilitent la confirmation ou le litige d’activité. Il s’agit du modèle approprié lorsque le déclencheur est un événement système plutôt qu’un comportement client et lorsque la communication requise est immédiate et réactive, sans temps pour les séquences à plusieurs étapes ; la latence d’alerte est directement corrélée à l’exposition aux pertes financières.

### Considérations techniques

- Privilégiez la vitesse de livraison et la fiabilité avant toute autre considération de conception, car la latence des alertes de fraude est directement corrélée à l&#39;exposition aux pertes financières.
- Acheminez les alertes via le canal préféré vérifié du client tout en conservant les canaux de secours pour assurer la diffusion même en cas d’échec du canal principal.
- Conservez l’historique des interactions d’alerte pour améliorer la pertinence des alertes futures et réduire la fatigue des faux positifs pour les clients qui voyagent fréquemment ou effectuent des achats atypiques.
- Assurez-vous que tous les contenus et workflows d’alerte de fraude sont conformes aux réglementations de sécurité bancaire et n’exposent pas les détails de comptes sensibles dans les prévisualisations de messages ou les objets.


## Engagement du programme de fidélité

Personnalisez les communications, les récompenses et les offres des programmes de fidélité en orchestrant l’arbitrage des offres en temps réel sur les canaux des banques en ligne, des applications mobiles, des e-mails et des succursales pour empêcher les offres de fidélité en double ou conflictuelles d’atteindre le même membre simultanément. Les règles d’éligibilité basées sur les niveaux (régissant les récompenses, les promotions et les options de remboursement auxquelles chaque membre peut accéder) sont appliquées au niveau de la couche de prise de décision plutôt que résolues par la seule segmentation, afin de s’assurer que la sélection des offres respecte les contraintes du programme sur chaque canal. Les parcours de fidélité sont coordonnés avec des campagnes marketing plus larges afin que les offres de produits et de fidélité n’entrent pas en conflit, offrant ainsi aux membres une expérience cohérente plutôt que des messages concurrents.

### Impact commercial

L’engagement de fidélité personnalisé augmente la participation au programme et entraîne un taux de remboursement des points sensiblement plus élevé, renforçant ainsi la perception de la valeur du programme.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour orchestrer des communications de fidélité sur plusieurs canaux, avec une prise de décision intégrée pour sélectionner la récompense ou l’offre la plus pertinente pour chaque membre. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion sur plusieurs canaux pour éviter la fatigue des messages et les offres en conflit, et lorsque la sélection d’offres nécessite des règles basées sur le niveau et des contraintes de membre - l’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision en temps réel nécessaire pour respecter les règles de fidélité et le traitement différencié des membres.

### Considérations techniques

- Synchronisez les données de la plateforme de fidélité, y compris le statut du niveau, les soldes de points et l’historique des remboursements, dans les profils clients en temps quasi réel afin d’éviter de promouvoir des soldes expirés ou inexacts.
- Logique de parcours de segments par niveau pour offrir des expériences différenciées, car les membres de niveau supérieur s’attendent à un traitement exclusif et à un accès précoce aux promotions.
- Coordonnez les messages de fidélité avec des campagnes marketing plus larges pour éviter la fatigue des messages et les offres conflictuelles entre les programmes.
- Suivez l’attribution du remboursement sur tous les canaux pour mesurer les communications personnalisées qui génèrent le meilleur retour sur investissement du programme.


## Campagnes de pré-approbation de prêt hypothécaire

Ciblez les clients qui sont susceptibles d’être sur le marché d’un prêt hypothécaire en fonction des données de profil, des signaux comportementaux et des indicateurs relatifs au stade de vie. La sensibilisation proactive préalable à l&#39;approbation positionne l&#39;institution comme un premier choix pratique lors de l&#39;une des plus importantes décisions financières qu&#39;un client prendra.

### Impact commercial

Les campagnes ciblées de pré-approbation des prêts hypothécaires augmentent les taux de demande et améliorent le volume de demandes de prêt en atteignant des prospects qualifiés au bon moment.

### Mise en œuvre

Utilisez le modèle Parcours orchestré en plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour guider les prospects hypothécaires à travers une séquence de maturation multi-touch, de la sensibilisation à la pré-approbation, en les adaptant en fonction des signaux d’engagement et de qualification. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux séquentiel et multi-messages sur une chronologie étendue avec un embranchement conditionnel basé sur des signaux d’engagement et de qualification. Un message déclenché unique ne peut pas s’adapter à la logique d’entretien adaptative ou au transfert vers des processus d’application formels.

### Considérations techniques

- Combinez le comportement de recherche immobilière, les tendances de croissance de l&#39;épargne et les signaux d&#39;expiration de bail pour créer un modèle de propension qui identifie les demandeurs de prêt hypothécaire probables.
- Veiller à ce que tous les messages d&#39;approbation préalable soient conformes aux règlements sur la publicité hypothécaire, y compris les divulgations obligatoires, la précision des taux et la langue de l&#39;habitation.
- Coordonner le timing de la campagne avec les changements de l’environnement des taux afin que les activités de sensibilisation s’alignent sur des conditions d’emprunt favorables et évitent les références de taux obsolètes.
- Créer des workflows de remise aux responsables des prêts afin que les prospects numériquement encouragés passent facilement au processus formel de demande et de souscription.


## Contenu personnalisé d’éducation financière

Diffusez du contenu, des conseils et des ressources personnalisés en matière de formation financière, en fonction du profil financier, des objectifs et des centres d’intérêt de chaque client. Les contenus éducatifs pertinents renforcent la confiance, améliorent la littératie financière et créent des opportunités organiques pour introduire des produits pertinents.

### Impact commercial

Le contenu de formation personnalisé augmente les taux d’engagement du contenu et améliore la littératie financière des clients, ce qui permet une adoption plus confiante du produit.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour diffuser une séquence organisée de contenu éducatif sur plusieurs canaux, à l’aide de la prise de décision pour faire correspondre les sujets à la situation financière et aux intérêts de chaque client. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion sur plusieurs canaux avec des parcours d’apprentissage progressif et lorsque la sélection de sujet nécessite des règles d’éligibilité basées sur le profil financier (l’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision nécessaire pour faire correspondre le contenu à la situation financière du client ou pour empêcher les violations préalables).

### Considérations techniques

- Associez le contenu éducatif aux attributs de profil financier tels que le ratio d’endettement, le taux d’épargne et l’expérience d’investissement pour garantir la pertinence du sujet.
- Balisez le contenu avec les niveaux de difficulté et les sujets préalables afin de créer des parcours d’apprentissage progressif plutôt que de diffuser des articles ponctuels déconnectés.
- Suivez l’engagement du contenu au niveau du topic pour affiner les modèles de personnalisation et identifier les domaines d’intérêt émergents dans la base de clients.
- Veiller à ce que le contenu éducatif soit clairement distingué du marketing des produits afin de maintenir la conformité réglementaire et de préserver la confiance des clients dans l&#39;objectivité du programme.


## Guide des produits financiers d’IA

Les organismes de services financiers offrent des portefeuilles de produits — comptes chèques et d’épargne, cartes de crédit, produits de prêt, options d’assurance et véhicules d’investissement — qui sont difficiles à parcourir pour les clients sans conseils personnalisés. Les contraintes réglementaires empêchent les expériences digitales de première ligne de fournir des recommandations d’investissement personnalisées, mais il existe une valeur substantielle pour aider les clients à comprendre le fonctionnement des produits, les comptes qui répondent à leurs besoins déclarés et la façon de passer à l’étape suivante de l’application. Un guide des produits financiers basé sur l’IA engage les clients dans une conversation naturelle, leur pose des questions qualifiantes sur leurs objectifs financiers et leur étape de vie, et les guide vers les bons produits, sans pour autant empiéter sur le domaine du conseil réglementé.

### Impact commercial

La découverte conversationnelle guidée améliore les taux de démarrage des applications de produits et réduit le taux de déperdition entre la sensibilisation et l’application, tout en capturant les signaux d’intention qui améliorent les workflows de formation et de recommandation de conseillers en aval.

### Mise en œuvre

Utilisez le modèle [Expérience de conversation &#x200B;](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md). Cette approche déploie Product Advisor Agent par rapport à la bibliothèque de contenu de produit et à la base de connaissances approuvées, en utilisant AEP Agent Orchestrator et les données de profil client en temps réel pour guider les clients vers les produits appropriés par le biais d&#39;un dialogue à plusieurs tours fondé sur un contenu régi par la marque et révisé par la conformité. Il s’agit du modèle approprié lorsque l’objectif est une découverte conversationnelle interactive à plusieurs tours pour aider les clients à comprendre et à sélectionner eux-mêmes les produits financiers, ce qui se distingue des messages déclenchés par un événement, qui sont unidirectionnels et répondent à des événements de compte discrets, ainsi que des expériences web personnalisées, qui font apparaître le contenu du produit de manière passive sans impliquer les clients dans un dialogue de qualification. Cela nécessite une configuration d’AEP Agent Orchestrator et de la gouvernance de marque.

### Considérations techniques

- Les mécanismes de sécurisation de la gouvernance de marque doivent être configurés avec une conformité et une révision juridique pour définir des limites strictes de contenu : l’agent doit guider les clients vers des produits adaptés basés sur les besoins déclarés sans constituer un conseil en investissement, et les sujets interdits (projections de rendement spécifiques, garanties, allégations de performances comparatives) doivent être explicitement définis et appliqués.
- La couche d’intégration de contenu doit reposer sur des descriptions de produit, des divulgations et des questions fréquentes approuvées par les spécialistes de la conformité, plutôt que sur des réclamations générées dynamiquement, afin de s’assurer que chaque réponse fournie par l’agent a été examinée par les équipes juridiques et réglementaires avant le déploiement.
- La recherche du profil client en temps réel doit faire apparaître les données de relation (produits existants détenus, durée du compte et segment client) afin que l’agent puisse éviter de recommander des produits que le client possède déjà et puisse adapter les conseils à la relation existante du client avec l’institution.
- La remise en direct de l’agent doit être configurée pour les scénarios dans lesquels les besoins du client dépassent la portée du guide conversationnel, comme des situations de prêt complexes ou des demandes de planification financière personnalisée, avec un contexte de conversation complet transféré au conseiller récepteur pour éviter que le client ne se répète.


## Analyse du Funnel d’adoption du produit et de l’attrition des pilotes

Analysez où les clients abandonnent lors de l’ouverture de compte numérique, de la demande de prêt ou des flux d’intégration des investissements et identifiez les signaux de comportement qui précèdent l’attrition du produit. Les institutions financières qui ne peuvent pas voir ces points de chute ou ces précurseurs de l&#39;attrition sont incapables de faire la distinction entre les défaillances et la disqualification des produits, ce qui rend les efforts de remédiation imprécis.

### Impact commercial

Comprendre exactement où les demandeurs abandonnent les flux numériques et quels comportements précèdent les fermetures de compte permet aux équipes produit et marketing de donner la priorité aux améliorations de l’expérience qui réduisent les abandons et prolongent la durée de vie du client.

### Mise en œuvre

Utilisez le modèle [Customer Analytics et génération d’Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Cette approche connecte les données comportementales numériques, les enregistrements CRM et les flux d’événements de produit à Customer Journey Analytics, où les visualisations des abandons identifient les étapes de dépôt et l’analyse des cohortes fait apparaître les différences de rétention entre les lignes de produits et les segments d’acquisition. Il s’agit du bon schéma lorsque l’objectif est de comprendre et de diagnostiquer (en analysant la répartition des parcours et ce qui entraîne l’attrition) plutôt que d’activer une audience de suppression ou de déclencher un message de rétention.

### Considérations techniques

- Les données numériques d’événement d’application doivent capturer chaque étape du flux d’intégration ou d’application en tant qu’événements discrets avec des identifiants d’étape cohérents afin que l’analyse des abandons de CJA puisse isoler exactement l’endroit où le volume est perdu.
- Les données de durée du produit CRM et de statut du compte doivent être jointes dans la connexion CJA avec les données comportementales afin que l’analyse de l’attrition puisse corréler les comportements de pré-attrition avec les résultats réels de fermeture du compte.
- Les étiquettes de gouvernance des données doivent être appliquées à tous les champs financiers ou d’identité sensibles inclus dans la connexion CJA afin d’empêcher l’exposition aux informations d’identification personnelle dans les tableaux de bord partagés accessibles par les analystes sans autorisations des gestionnaires de données.
- L’analyse des cohortes de rétention nécessite une profondeur de données historiques suffisante (généralement 12 à 24 mois). Les politiques de rétention des jeux de données dans AEP doivent donc être configurées pour conserver l’historique des événements nécessaire à des comparaisons de cohortes significatives.

## Next-Best Offer Decisioning

Utilisez une logique de décision centralisée pour sélectionner l’offre la plus pertinente pour chaque client sur l’ensemble des canaux, en combinant des règles d’éligibilité, des contraintes métier et des stratégies de classement basées sur l’IA. La centralisation de la sélection des offres garantit que chaque client reçoit l’offre de produit financier la plus appropriée au contexte, tout en respectant les exigences d’éligibilité réglementaires et les contraintes commerciales.

### Impact commercial

Les organisations de services financiers qui utilisent la meilleure Offer Decisioning centralisée constatent une amélioration des taux d’adoption des produits et un chiffre d’affaires plus élevé par interaction client, avec les performances les plus élevées lorsque la sélection des offres tient compte à la fois des scores de propension et des mécanismes de sécurisation d’éligibilité.

### Mise en œuvre

Utilisez le modèle [&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pour créer un moteur de décision centralisé qui évalue l’éligibilité des clients, applique des contraintes métier et utilise le classement par l’IA pour sélectionner l’offre optimale pour chaque interaction client sur les canaux web, app et sortants. Il s’agit du modèle approprié lorsque la sélection des offres est trop complexe pour la seule personnalisation basée sur des règles, ce qui nécessite une combinaison de logique d’éligibilité, de règles de priorité et de classement adaptatif pour effectuer la sélection optimale à partir d’un catalogue d’offres.

### Considérations techniques

- Les règles d’éligibilité de l’offre doivent être conservées dans le moteur de décision et synchronisées avec les critères d’éligibilité des produits des systèmes bancaires ou de produits principaux afin d’empêcher l’affichage d’offres non éligibles.
- Les modèles de classement par l’IA nécessitent suffisamment de données de formation provenant d’interactions d’offres antérieures pour générer des scores de propension fiables. Les nouveaux produits lancés ont besoin de stratégies de classement de secours jusqu’à ce qu’une quantité suffisante de données s’accumule.
- Les exigences réglementaires des services financiers peuvent restreindre ce qui peut être proposé à qui et par quel canal ; la logique de prise de décision doit coder ces contraintes en règles strictes plutôt qu’en préférences non contraignantes.
- Le suivi de la lassitude des offres est important : les clients qui reçoivent à plusieurs reprises des offres pour le même produit qu&#39;ils n&#39;ont pas accepté doivent voir cette offre déclassée ou supprimée après un nombre défini d&#39;expositions.


## Tableau de bord Customer Journey Analytics

Créez des espaces de travail d’analyse cross-canal combinant des données web, d’application, de courrier électronique et de centre d’appel pour visualiser les parcours des clients, identifier les points de chute et mesurer l’attribution de la campagne. Un espace de travail d’analyse unifié offre aux équipes produit et marketing une vue complète de la manière dont les clients se déplacent sur les canaux et les points de contact, ce qui permet de prendre des décisions basées sur les données concernant les investissements à effectuer pour améliorer le parcours.

### Impact commercial

Les organisations de services financiers disposant d’analytique des parcours cross-canal réduisent le délai d’insight pour les équipes de campagnes et de produits, ce qui permet d’identifier plus rapidement les opportunités d’optimisation à fort impact sur les flux d’intégration, les entonnoirs d’application et les parcours de service client.

### Mise en œuvre

Utilisez le modèle [Customer Analytics et génération Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) pour regrouper les flux d’événements de tous les canaux numériques et hors ligne dans un jeu de données d’analyse unifié, puis créer des visualisations d’espace de travail qui exposent les flux de parcours, le taux de déperdition funnel et les modèles d’attribution. Il s’agit du modèle approprié lorsque l’exigence principale est l’analyse d’insight et la visualisation plutôt que l’activation en temps réel. Les données sont utilisées pour prendre des décisions éclairées plutôt que pour déclencher des actions face aux clients.

### Considérations techniques

- L’assemblage de données cross-canal nécessite un identifiant client cohérent sur tous les systèmes sources. Les entreprises dont les stratégies d’identité sont fragmentées verront des parcours incomplets qui sapent l’analyse.
- Les données du centre d’appel et des interactions hors ligne doivent être ingérées et horodatées avec précision pour les placer correctement dans la séquence du parcours par rapport aux points de contact numériques.
- La latence des données entre les systèmes sources et Analytics Workspace affecte la rapidité avec laquelle les informations sont disponibles. Les cas d’utilisation d’analyses à haute fréquence peuvent nécessiter une ingestion en temps quasi réel plutôt que des flux par lots quotidiens.
- Des contrôles de confidentialité et de gouvernance des données doivent être appliqués aux jeux de données Analytics afin d’empêcher l’affichage des informations d’identification personnelle dans les tableaux de bord accessibles aux analystes qui ne doivent pas avoir accès aux enregistrements des clients individuels.
