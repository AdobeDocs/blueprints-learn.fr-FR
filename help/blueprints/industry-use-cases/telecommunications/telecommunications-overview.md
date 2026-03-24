---
title: Cas d’utilisation des télécommunications
description: Découvrez comment les entreprises de télécommunications utilisent Adobe Experience Platform pour réduire l’attrition, favoriser les mises à niveau des appareils et améliorer l’engagement des clients.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 653632f0-81be-435c-a703-56c5bc132794
source-git-commit: 0236bd326730ee9a0be621ee0e60ddc3d352410d
workflow-type: tm+mt
source-wordcount: '3822'
ht-degree: 0%

---

# Cas d’utilisation des télécommunications

Les entreprises de télécommunications utilisent Adobe Experience Platform pour créer une vue d’ensemble de chaque abonné et offrir des expériences personnalisées qui réduisent le taux de résiliation, augmentent les mises à niveau de forfaits et d’appareils et renforcent les relations client à long terme. En connectant les données d&#39;utilisation du réseau, les informations de facturation et les interactions avec les clients, les fournisseurs de télécommunications peuvent anticiper les besoins des abonnés et les impliquer au bon moment via leurs canaux préférés.

## Recommandations de mise à niveau de l’appareil

Identifier les clients éligibles aux mises à niveau d’appareils et présenter des recommandations personnalisées d’appareils et des offres de mise à niveau en fonction des schémas d’utilisation et des préférences. En analysant la durée des contrats, l&#39;âge des appareils et le comportement de navigation individuel, les fournisseurs de télécommunications peuvent faire apparaître les appareils et les options de financement les plus pertinents à chaque abonné.

### Impact commercial

Les organisations qui mettent en œuvre des recommandations de mise à niveau des appareils constatent une amélioration des taux de conversion de mise à niveau en proposant la bonne offre au bon moment par le biais du canal préféré du client.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour orchestrer des parcours de mise à niveau qui évaluent l’éligibilité de chaque abonné, ses préférences d’appareil et son affinité de canal, afin de fournir des offres de mise à niveau personnalisées par le biais d’e-mails, de notifications d’application et d’expériences en magasin. Il s’agit du bon modèle lorsque la sélection des offres doit tenir compte des fenêtres d’éligibilité de l’appareil, des préférences de canal et des contraintes d’inventaire, des contraintes qui nécessitent une logique de prise de décision régie plutôt que de simples recommandations comportementales.

### Considérations techniques

- Intégrer l’inventaire des appareils et les systèmes de tarification pour garantir que les recommandations reflètent la disponibilité actuelle et les prix promotionnels.
- Connectez les données de gestion des contrats pour identifier précisément les fenêtres d’éligibilité de mise à niveau et les offres de mise à niveau anticipée.
- Intégrez la télémétrie d&#39;utilisation des appareils (capacité de stockage, état de la batterie, mesures de performances) pour renforcer la pertinence des recommandations.
- Coordonnez-vous avec les plateformes de vente au détail et d’e-commerce pour maintenir une expérience de mise à niveau cohérente sur les canaux numériques et en magasin.


## Campagnes d’optimisation du plan

Analysez les schémas d’utilisation des clients et recommandez des modifications de plan optimales pour économiser de l’argent ou obtenir de meilleures fonctionnalités en fonction de leurs besoins réels. En offrant des recommandations de plan de manière proactive, vous gagnez en confiance et réduisez le risque que vos abonnés quittent pour les concurrents avec des prix plus simples.

### Impact commercial

Les campagnes d’optimisation des plans améliorent les taux de modification des plans et la satisfaction de la clientèle, tout en augmentant le chiffre d’affaires moyen par utilisateur lorsque les abonnés passent à des plans qui correspondent mieux à leur consommation.

### Mise en œuvre

Utilisez le modèle Parcours orchestré en plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer une campagne multipoint qui identifie les incohérences entre l’utilisation et la planification, informe les abonnés sur les meilleures options et les guide tout au long du processus de changement de planification avec des suivis opportuns. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux séquentiel de plusieurs messages sur plusieurs jours avec un embranchement conditionnel basé sur l’engagement des abonnés et l’adoption du plan. Un message unique ne peut pas s’adapter au parcours éducatif et à la logique de dépendance entre les étapes de formation et de conversion.

### Considérations techniques

- Ingérez des données d’utilisation en temps réel et historiques (minutes vocales, consommation de données, appels internationaux) pour identifier précisément les incohérences du plan.
- Connectez les données du système de facturation pour calculer les économies potentielles ou les gains en termes de fonctionnalités pour chaque modification de plan recommandée.
- Tenez compte des règles de tarification promotionnelles et des obligations contractuelles lors de la génération de recommandations de plan.
- Intégrez-la aux portails en libre-service afin que les abonnés puissent effectuer les modifications de plan directement à partir des points de contact de Campaign.


## Prévention de l’attrition pour les clients à forte valeur ajoutée

Identifiez les clients à forte valeur ajoutée qui risquent de se perdre et engagez-les avec des offres de fidélisation personnalisées et un service client proactif. En combinant des signaux comportementaux tels qu&#39;une baisse de l&#39;utilisation, des appels de service répétés et une navigation concurrentielle avec des données de valeur de durée de vie, les fournisseurs peuvent intervenir avant qu&#39;un abonné décide de partir.

### Impact commercial

Les programmes de prévention du taux de résiliation ciblant les abonnés à forte valeur ajoutée permettent de réduire sensiblement le taux de résiliation, de protéger les revenus récurrents importants et de réduire le coût d’acquisition des clients de remplacement.

### Mise en œuvre

Utilisez le modèle [Cross-Channel Parcours with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour surveiller les signaux de risque d’attrition en temps réel, déterminer la meilleure offre de rétention pour chaque abonné et orchestrer des activités de sensibilisation personnalisées sur les canaux numériques et le centre d’appels. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion sur des canaux numériques et assistés par un agent pour éviter les offres de rétention en double et lorsque la sélection d’offres nécessite une évaluation des risques et des contraintes commerciales - l’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision en temps réel ou la coordination d’agent nécessaire.

### Considérations techniques

- Créez des scores de propension à l’attrition en combinant les tendances d’utilisation, l’historique des interactions de services et les données de sentiment des transcriptions des centres d’appels.
- Intégrez les systèmes de centres d’appels et de vente au détail afin que les agents aient une visibilité sur les offres de fidélisation déjà présentées par le biais des canaux numériques.
- Connectez les données de veille concurrentielle (demandes de sortie, comparaisons de plans concurrents) pour affiner la notation des risques et les stratégies d&#39;offres.
- Établissez des règles de gouvernance pour éviter de surcontacter les abonnés à risque, ce qui peut accélérer la perte de clientèle plutôt que la prévenir.


## Nouveau Parcours d’intégration des clients

Automatisez un parcours d’intégration personnalisé pour les nouveaux clients avec des informations de bienvenue, des conseils sur la configuration du compte et des tutoriels sur les fonctionnalités. Une expérience d’intégration structurée permet aux abonnés de découvrir rapidement toute la valeur de leur forfait et de leurs services, établissant ainsi les bases d’une rétention à long terme.

### Impact commercial

Des parcours d’intégration bien conçus entraînent des taux d’activation des fonctionnalités améliorés, ce qui entraîne des scores de satisfaction plus élevés et une baisse de perte de clientèle au début de la vie chez les nouveaux abonnés.

### Mise en œuvre

Utilisez le modèle Parcours orchestré en plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer une expérience d’intégration séquentielle qui s’adapte en fonction du type de forfait, de l’appareil et de l’engagement de chaque abonné par rapport aux étapes d’intégration précédentes. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux séquentiel de plusieurs messages sur plusieurs jours avec un embranchement conditionnel basé sur la découverte et l’engagement des fonctionnalités. Un message déclenché unique ne peut pas s’adapter à la logique de dépendance adaptative entre les étapes d’intégration basées sur le plan de l’abonné et le type d’appareil.

### Considérations techniques

- Intégrez des systèmes d’approvisionnement de compte pour déclencher le parcours d’intégration immédiatement après l’activation et adaptez le contenu au plan et à l’appareil spécifiques de l’abonné.
- Connectez les données d’engagement de l’application pour suivre les fonctionnalités explorées par l’abonné et ajustez les messages d’intégration suivants en conséquence.
- Coordonnez-vous avec la plateforme du service clientèle pour vous assurer que les agents connaissent l’étape d’intégration d’un abonné s’ils appellent pour des questions.
- Prise en charge de plusieurs chemins d’intégration pour différents segments de clients tels que les abonnés individuels, les administrateurs de forfaits familiaux et les comptes professionnels.


## Alertes et recommandations relatives à l’utilisation des données

Envoyez des alertes personnalisées lorsque les clients approchent des limites de données et recommandent des mises à niveau de plan ou des modules complémentaires de données en fonction des schémas d’utilisation. Des notifications opportunes et utiles transforment une expérience potentiellement frustrante en un moment d’engagement visant à renforcer la confiance.

### Impact commercial

Les alertes d’utilisation proactive des données entraînent l’amélioration des achats de modules complémentaires de données tout en réduisant les plaintes relatives aux factures-surprises et en améliorant la satisfaction globale des clients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour envoyer des alertes en temps réel lorsque les seuils d’utilisation sont dépassés, avec des recommandations personnalisées basées sur les modèles de consommation historiques et les détails du plan de l’abonné. Il s’agit du modèle approprié lorsque le déclencheur est un événement système (dépassement de seuil d’utilisation) plutôt qu’un comportement du client et que la communication requise est immédiate et réactive plutôt qu’une séquence d’entretien soutenue.

### Considérations techniques

- Connectez-vous aux flux de données d’utilisation du réseau qui fournissent des mises à jour de consommation en temps quasi réel pour déclencher des alertes à des seuils significatifs (75 %, 90 % et 100 % des limites du plan).
- Intégrez des systèmes de facturation et de gestion de plan pour présenter une tarification complémentaire précise et permettre des achats ponctuels directement à partir du message d’alerte.
- Tenez compte des pools de données partagés sur les plans familiaux en alertant l&#39;utilisateur individuel et l&#39;administrateur du plan.
- Mettez en œuvre le capping de la fréquence pour éviter la fatigue des alertes pour les abonnés qui utilisent constamment de grandes quantités de données à chaque cycle de facturation.


## Notifications de panne du service

Informez de manière proactive les clients des pannes de service, des problèmes de maintenance ou de réseau dans leur zone grâce à des mises à jour personnalisées et à des offres de compensation. Le fait de contacter les clients avant qu’ils ne ressentent leur frustration démontre leur responsabilité et réduit considérablement le volume d’assistance entrant.

### Impact commercial

Les notifications de panne proactives permettent d’obtenir de forts taux d’accusé de réception des notifications et de réduire considérablement le volume du centre d’appels lors des interruptions de service, ce qui réduit les coûts de support tout en améliorant la perception du client.

### Mise en œuvre

Utilisez le modèle [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour détecter les événements réseau et informer immédiatement les abonnés affectés par le biais de leurs canaux préférés avec des détails pertinents, des délais de résolution estimés et une compensation appropriée, le cas échéant. Il s’agit du modèle approprié lorsque le déclencheur est un événement système (panne du réseau) plutôt que le comportement du client, et que la communication requise est immédiate et réactive plutôt qu’une séquence d’entretien soutenue.

### Considérations techniques

- Intégrez-la aux systèmes de surveillance des centres d&#39;exploitation réseau pour recevoir des données en temps réel sur les pannes et les événements de maintenance avec des informations sur la portée géographique.
- Utilisez les données d’adresse et de localisation des abonnés pour identifier précisément les clients concernés et éviter d’avertir ceux qui se trouvent en dehors de la zone touchée.
- Connectez-vous au système de facturation et de crédits afin d’automatiser les offres de crédit de service pour les pannes prolongées en fonction du forfait de l’abonné et de la durée de la perturbation.
- Coordonnez la messagerie sur l’ensemble des canaux pour fournir des mises à jour de statut cohérentes et éviter d’envoyer des informations conflictuelles à mesure que la situation évolue.


## Gestion du plan familial

Personnalisez les communications et les offres pour les administrateurs de plans familiaux en fonction des schémas d&#39;utilisation familiaux et des besoins individuels des membres. Les plans familiaux représentent des comptes multilignes à forte valeur ajoutée où l’engagement avec l’administrateur du plan stimule la rétention sur toutes les lignes.

### Impact commercial

Les communications personnalisées de gestion des plans familiaux améliorent l&#39;engagement des plans familiaux, ce qui se traduit par une fidélisation des lignes plus élevée et une plus grande valeur à vie par compte.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour analyser l’utilisation parmi tous les membres de la famille, identifier les opportunités telles que l’ajout de lignes ou l’ajustement de limites individuelles, et fournir des recommandations personnalisées à l’administrateur du plan. Il s’agit du modèle approprié lorsque la sélection des offres doit tenir compte des autorisations de hiérarchie des familles, de l’agrégation des utilisations multi-membres et des contraintes de confidentialité, contraintes qui nécessitent une logique de prise de décision régie plutôt que de simples recommandations d’abonnés individuels.

### Considérations techniques

- Modélisez les hiérarchies de comptes familiaux pour faire la distinction entre l&#39;administrateur du plan et les membres individuels, en respectant les niveaux d&#39;autorisation pour les communications et les modifications de compte.
- Agrégez les données d’utilisation sur toutes les lignes du compte pour identifier les modèles et les opportunités au niveau de la famille, tels que les données partagées sous-utilisées ou les cycles de mise à niveau inégales des appareils.
- Intégrez le contrôle parental et les systèmes de filtrage de contenu pour prendre en charge les fonctionnalités de personnalisation spécifiques à la famille.
- Assurez-vous que des contrôles de confidentialité sont en place afin que les détails d’utilisation des membres individuels soient partagés de manière appropriée avec l’administrateur du plan en fonction des autorisations du compte.


## Campagnes de mise à niveau vers la 5G

Ciblez les clients éligibles aux mises à niveau du réseau 5G avec des offres et des avantages personnalisés en fonction de leur emplacement et de leurs schémas d’utilisation. À mesure que la couverture 5G s&#39;étend, atteindre les abonnés dans les zones nouvellement couvertes avec des messages pertinents accélère l&#39;adoption et augmente l&#39;utilisation du réseau.

### Impact commercial

Les campagnes de mise à niveau 5G ciblées améliorent les taux d&#39;adoption de la 5G chez les abonnés admissibles, ce qui favorise les rendements de l&#39;investissement dans le réseau et la différenciation concurrentielle.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pour segmenter les abonnés en fonction de la disponibilité de la couverture 5G, de la compatibilité des appareils et de l’éligibilité du plan, puis diffusez des campagnes de mise à niveau personnalisées mettant en évidence les avantages les plus pertinents pour le profil d’utilisation de chaque abonné. Il s’agit du modèle approprié lorsque l’audience est prédéfinie et volumineuse, que le timing de diffusion est planifié plutôt que piloté par un événement et qu’aucun embranchement ou prise de décision en temps réel n’est nécessaire. La campagne peut être entièrement planifiée à l’avance en fonction des délais de déploiement de la couverture.

### Considérations techniques

- Intégrer des cartes de couverture réseau pour identifier avec précision les abonnés dans les zones où le service 5G est actif et éviter de promouvoir les mises à niveau là où la couverture n&#39;est pas encore disponible.
- Connectez les données de compatibilité des appareils pour déterminer quels abonnés ont besoin d’un nouvel appareil par rapport à ceux qui disposent déjà d’un matériel compatible 5G.
- Assurer la coordination avec les systèmes d&#39;inventaire de détail pour s&#39;assurer que les appareils et les forfaits promus sont disponibles dans le magasin préféré de l&#39;abonné ou en ligne.
- Segmentez la messagerie en fonction du profil d’utilisation afin que les utilisateurs de données volumineuses bénéficient d’avantages axés sur les performances tandis que les utilisateurs occasionnels reçoivent des messages de couverture et de fiabilité.


## Rappels de paiement de la facture

Envoyez des rappels de paiement personnalisés par le biais de canaux préférés avec des options de paiement et des informations sur le solde du compte. Des rappels opportuns et pratiques réduisent les retards de paiement et les coûts de recouvrement associés tout en maintenant une relation client positive.

### Impact commercial

Les rappels de paiement de factures personnalisés améliorent les taux de paiement ponctuels, réduisant les dépenses de recouvrement et minimisant les suspensions de service qui provoquent l&#39;insatisfaction des clients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour envoyer des rappels à des heures optimales avant la date d’échéance, personnalisés avec le solde de l’abonné, son mode de paiement préféré et un lien direct pour effectuer le paiement. Il s’agit du modèle approprié lorsque le déclencheur est un événement système temporel (date d’échéance de facturation) plutôt que le comportement du client et que la communication requise est immédiate et transactionnelle plutôt qu’une séquence d’engagement à plusieurs étapes.

### Considérations techniques

- Intégrez-la à la plateforme de facturation pour accéder aux soldes des comptes en temps réel, aux dates d’échéance et à l’historique des paiements afin d’obtenir un contenu de rappel précis.
- Connectez-vous aux systèmes de traitement des paiements pour activer le paiement en un clic ou en un clic directement à partir du message de rappel.
- Implémentez une logique d’escalade qui ajuste l’urgence et la fréquence des rappels à l’approche de la date d’échéance, tout en respectant les préférences de communication.
- Prenez en charge plusieurs méthodes de paiement (inscription automatique, portefeuille numérique, virement bancaire) et personnalisez les options présentées en fonction de l’historique de l’abonné.


## Recommandations de service de module complémentaire

Recommandez des services complémentaires pertinents tels que l’assurance de l’appareil, l’espace de stockage dans le cloud et les lots de streaming en fonction du plan, de l’utilisation et des préférences du client ou de la cliente. Les recommandations contextuelles augmentent la valeur que les abonnés reçoivent de leur relation avec le fournisseur tout en augmentant le chiffre d’affaires moyen par utilisateur.

### Impact commercial

Les recommandations de services de module complémentaire personnalisés entraînent une amélioration des taux d’adoption des modules complémentaires, augmentant le chiffre d’affaires de la base d’abonnés existante sans le coût d’acquisition de nouveaux clients.

### Mise en œuvre

Utilisez le modèle [&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pour évaluer le profil, les services actuels et les signaux comportementaux de chaque abonné afin de déterminer l’offre complémentaire la plus pertinente et de la présenter par le canal et le moment optimaux. Il s’agit du modèle approprié lorsque la sélection des offres doit tenir compte de la propriété actuelle du service et des règles métier régissant l’éligibilité du service complémentaire. Ces règles nécessitent une logique de prise de décision régie plutôt qu’un classement par affinité comportementale uniquement.

### Considérations techniques

- Connectez-vous au catalogue de services actuel de l&#39;abonné pour éviter de recommander des services qu&#39;il possède déjà et pour identifier les compléments naturels à son forfait existant.
- Intégrez les données des partenaires et des services tiers (fournisseurs de streaming, compagnies d&#39;assurance) pour présenter des tarifs précis et des offres groupées.
- Utilisez les données d’appareil et d’utilisation pour émettre des recommandations, telles que suggérer une assurance appareil pour les abonnés disposant de nouveaux appareils Premium ou un stockage dans le cloud pour ceux qui manquent de stockage pour l’appareil.
- Coordonnez-vous avec la personnalisation in-app et web pour renforcer les recommandations de modules complémentaires sur les points de contact en libre-service.


## Personalization des performances réseau

Personnalisez les informations et les recommandations relatives aux performances du réseau en fonction de l’emplacement, de l’appareil et des schémas d’utilisation du client. Aider les abonnés à optimiser leur expérience de connectivité crée de la confiance et réduit les contacts d’assistance associés aux problèmes de performances.

### Impact commercial

Les expériences de performances réseau personnalisées améliorent l’engagement des applications, car les abonnés reviennent pour vérifier la couverture, résoudre les problèmes et découvrir des conseils d’optimisation adaptés à leur situation.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pour fournir des tableaux de bord de performances réseau personnalisés, des informations sur la couverture et des recommandations d’optimisation dans l’application et l’expérience du compte web de l’abonné. Il s’agit du modèle approprié lorsque la personnalisation est pilotée par des attributs de profil et des données d’emplacement plutôt que par un modèle d’affinité comportementale.

### Considérations techniques

- Intégrer des mesures de qualité du réseau et des données de couverture afin de fournir des informations de performances spécifiques à l&#39;emplacement, pertinentes pour la maison, le travail et les zones fréquemment visitées de l&#39;abonné.
- Connectez les données de diagnostic des appareils pour offrir des recommandations de dépannage personnalisées basées sur le modèle d’appareil et la version logicielle spécifiques à l’abonné.
- Utilisez les services Edge de [!DNL Adobe Experience Platform] pour offrir une personnalisation à faible latence dans l’expérience de l’application sans affecter les performances.
- Mettez en œuvre des boucles de rétroaction afin que les abonnés puissent signaler les problèmes de couverture, ce qui enrichit les données réseau tout en démontrant la réactivité à leur expérience.


## Engagement du programme de fidélité

Personnalisez les communications, les récompenses et les offres du programme de fidélité en fonction du niveau, du solde de points et de l’historique de remboursement du client, tout en arbitrant en temps réel sur les canaux d’application, web, SMS et de boutique de vente au détail afin d’empêcher les offres en double ou conflictuelles d’atteindre le même abonné. Les contraintes d’éligibilité basées sur les niveaux régissent les récompenses, les rachats de partenaires et les promotions auxquels chaque abonné peut accéder. Ces règles doivent être appliquées au niveau de la couche de prise de décision plutôt que d’être intégrées dans la logique de campagne individuelle. Le programme de fidélité doit également se coordonner avec les campagnes actives de rétention et de mise à niveau afin que les offres de prévention de l’attrition et les récompenses de fidélité complètent plutôt que de doubler la diffusion aux abonnés qui se trouvent simultanément sur plusieurs parcours.

### Impact commercial

L’engagement personnalisé du programme de fidélité entraîne une participation améliorée au programme et un échange de récompenses, ce qui entraîne des taux de rétention plus élevés parmi les abonnés inscrits.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour orchestrer des communications de fidélité personnalisées qui mettent en évidence les récompenses pertinentes, notifient les abonnés de la progression de niveau et présentent des opportunités d’échange alignées sur leurs préférences et leur comportement. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion sur plusieurs canaux pour éviter les offres de fidélité en double et lorsque la sélection des offres nécessite un statut de niveau et un historique de remboursement - l’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision en temps réel nécessaire.

### Considérations techniques

- Intégrez la plateforme de fidélité pour accéder aux soldes de points en temps réel, au statut du niveau et à l’historique des remboursements afin d’offrir une personnalisation précise.
- Connectez les catalogues de récompenses des partenaires pour présenter une large gamme d&#39;options de rachat adaptées aux intérêts démontrés et aux rachats passés de chaque abonné.
- Coordonnez les messages de fidélité avec d’autres parcours de campagne pour vous assurer que les offres de fidélité et les récompenses de fidélité se complètent plutôt qu’entrent en conflit.
- La progression du niveau de prise en charge progresse en calculant la proximité d’un abonné par rapport au niveau suivant et en présentant des étapes exploitables pour l’atteindre.


## Conseiller en planification de l’IA

Les abonnés aux services de télécommunication sont confrontés à un défi constant : comprendre comment leur forfait actuel se compare aux options disponibles et si un forfait différent correspondrait mieux à leur utilisation réelle. Les pages de comparaison de plans statiques exigent des abonnés qu&#39;ils interprètent eux-mêmes les données qu&#39;ils ne comprennent pas entièrement, ce qui peut entraîner des sélections de plans non optimales, un choc de facturation et une perte de clientèle évitable. Un conseiller en planification de l&#39;IA engage les abonnés dans une conversation naturelle, examine leurs schémas d&#39;utilisation à partir de leur profil en temps réel, pose des questions admissibles sur les besoins des appareils et des ménages et les guide vers le plan (ou la combinaison de plans et de modules complémentaires) qui correspond le mieux à leur situation.

### Impact commercial

Les conseils relatifs au plan de conversation réduisent le taux de perte de clientèle lié au plan, augmentent la participation aux mises à niveau pour les abonnés qui ne sont pas suffisamment servis par leur plan actuel et réduisent le volume du centre de contact pour les demandes de facturation et de modification du plan.

### Mise en œuvre

Utilisez le modèle [Expérience de conversation &#x200B;](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md). Cette approche déploie Product Advisor Agent par rapport au plan et au catalogue de modules complémentaires, en utilisant des données d’AEP Agent Orchestrator et du profil client en temps réel, y compris l’historique d’utilisation et les détails du plan actuel, pour guider les abonnés et abonnées à travers une sélection de plan personnalisée via un dialogue naturel. Il s’agit du modèle approprié lorsque l’objectif est une découverte conversationnelle interactive à plusieurs tours qui aide les abonnés à évaluer et à sélectionner activement le plan approprié, à la différence des messages déclenchés par un événement, qui avertissent les abonnés de manière réactive des seuils d’utilisation ou des changements de plan, et des expériences web personnalisées, qui affichent des comparaisons de plan de manière passive sans impliquer les abonnés dans une boîte de dialogue de qualification. Cela nécessite une configuration d’AEP Agent Orchestrator et de la gouvernance de marque.

### Considérations techniques

- La recherche du profil client en temps réel doit faire apparaître les détails actuels du plan, les schémas d&#39;utilisation des données et de la voix, la compatibilité des appareils et l&#39;état du contrat afin que le conseiller puisse fournir des conseils précis et spécifiques au compte plutôt que des descriptions génériques de plan qui obligent l&#39;abonné à s&#39;appliquer lui-même à sa situation.
- Le plan et le catalogue de modules complémentaires doivent être tenus à jour grâce à l&#39;intégration au système de gestion des produits, car recommander un plan ou un prix promotionnel qui n&#39;est plus disponible, ou omettre une nouvelle option, mine directement la confiance des abonnés et peut créer des problèmes d&#39;attente de service.
- Les mécanismes de sécurisation de la gouvernance de marque doivent définir comment l&#39;agent gère les comparaisons d&#39;opérateurs concurrents, les annonces de prix promotionnels et les discussions d&#39;engagement contractuel, en veillant à ce que les réponses de l&#39;agent soient conformes aux normes réglementaires et de marque sans créer d&#39;engagements trompeurs que l&#39;abonné peut ensuite contester.
- Les signaux de conversation, notamment la taille du foyer indiquée, le nombre d’appareils, l’intérêt pour l’utilisation internationale et l’intention de changement de plan exprimé au cours de la boîte de dialogue, doivent être capturés en tant que XDM ExperienceEvents et diffusés en continu vers AEP, afin d’enrichir les profils des abonnés pour informer les campagnes de prévention de l’attrition, de mise à niveau et de vente croisée en aval.


## Propension à l’attrition et Network Experience Analytics

Corrélez les mesures de l’expérience réseau (baisses d’appels, dégradation du débit de données, exposition aux pannes) avec les taux de contact du service client et les résultats de résiliation des abonnés afin d’identifier où les problèmes de qualité du réseau se traduisent par un risque d’attrition mesurable. Les fournisseurs de services de télécommunications qui analysent la performance du réseau et le comportement des clients dans des systèmes distincts ne peuvent pas déterminer quelles défaillances de la qualité du service entraînent réellement l&#39;attrition par rapport à celles qui sont absorbées sans conséquence.

### Impact commercial

La connexion des données d’expérience réseau aux résultats relatifs au comportement et à l’attrition des clients permet aux équipes d’exploitation, de produit et de fidélisation du réseau de hiérarchiser les investissements de remédiation en fonction de l’impact démontré de l’attrition plutôt que de la seule gravité technique.

### Mise en œuvre

Utilisez le modèle [Customer Analytics et génération d’Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Cette approche connecte les données d’événement réseau, les enregistrements d’interaction du service client, les signaux comportementaux numériques et les événements de cycle de vie des abonnés à Customer Journey Analytics, où l’analyse corrélée identifie les seuils d’expérience réseau et les modèles de contact statistiquement associés à l’attrition et au non-renouvellement des contrats. Il s’agit du modèle approprié lorsque l’objectif est la génération d’insight et l’analyse des causes profondes (la compréhension des événements de qualité de service qui entraînent l’attrition), plutôt que le déclenchement d’une offre de rétention ou l’activation d’une audience à risque d’attrition dans une plateforme CDP.

### Considérations techniques

- Les événements d’expérience réseau doivent être associés aux enregistrements d’abonné à l’aide d’identifiants d’appareil ou de compte cohérents avec l’ID de personne configuré dans la connexion CJA, car les systèmes de télémétrie réseau utilisent généralement des identifiants d’équipement plutôt que des identifiants de client en mode natif.
- Les données de contact du service client, y compris les codes de motif du contact, le canal utilisé et le statut de résolution, doivent être ingérées en tant qu’événements avec horodatages permettant aux analystes de créer des chemins séquentiels à partir d’un incident réseau via le contact de service via les visualisations de flux CJA ou d’abandons dans l’attrition.
- Les données de contrat et de plan de l’abonné, y compris les dates de fin de contrat, le niveau de plan et la durée, doivent être disponibles en tant que dimensions de recherche dans la vue de données CJA afin que l’analyse de l’attrition puisse être segmentée par niveau de proximité et de valeur du contrat plutôt que de traiter la base d’abonnés comme homogène.
- Les volumes de données de télémétrie réseau peuvent être extrêmement importants. Il convient d’envisager des stratégies d’échantillonnage des jeux de données ou une pré-agrégation dans AEP pour maintenir les performances des requêtes de connexion CJA dans des plages acceptables pour une utilisation en libre-service par les analystes.

## Prévention de l’attrition et reprise

Utilisez des modèles prédictifs et des signaux comportementaux pour identifier les clients à risque et déclenchez des campagnes de fidélisation personnalisées avec des offres personnalisées avant leur résiliation. Les fournisseurs de services de télécommunication font face à une pression persistante en matière de résiliation, et il est beaucoup plus rentable d&#39;atteindre les abonnés à risque avec la bonne offre avant qu&#39;ils ne contactent la file d&#39;attente d&#39;annulation que de mener des campagnes de reconquête après coup.

### Impact commercial

Les fournisseurs de services de télécommunication dotés de programmes proactifs de prévention de l&#39;attrition constatent des réductions significatives de l&#39;attrition volontaire pour les segments ciblés, avec l&#39;impact le plus fort parmi les clients de valeur moyenne où les offres de rétention ciblées sont plus rentables que les remises générales.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour créer un parcours de rétention qui identifie les abonnés à risque en fonction des scores de propension à l’attrition, sélectionne l’offre de rétention appropriée à l’aide d’une logique de prise de décision et la diffuse sur les canaux préférés de l’abonné avec des étapes de suivi si la première diffusion est ignorée. Il s’agit du modèle approprié lorsque la sélection des offres et l’orchestration des parcours sont requises ; un seul message déclenché ne peut pas s’adapter à la logique de classement des offres et au suivi multipoint nécessaires à une rétention efficace.

### Considérations techniques

- Les modèles de propension à la résiliation doivent être entraînés sur des données historiques de résiliation qui incluent l’expérience réseau, les événements de facturation, les appels de service et l’âge de l’appareil - les modèles entraînés sur les données d’engagement uniquement sont souvent moins performants que les pilotes de résiliation spécifiques aux télécommunications.
- Les offres de rétention doivent être contraintes par des seuils de coût de rétention par segment de valeur client. Le moteur de décision doit empêcher les offres de rétention à coût élevé d&#39;être appliquées aux abonnés à faible valeur.
- Le traitement du signal de résiliation en temps réel doit détecter les événements de demande de contrat et les visites de page d&#39;annulation de service pour déclencher des réponses urgentes de rétention avant que l&#39;abonné ne réagisse.
- L&#39;intégration du service client est essentielle : les abonnés qui appellent la file d&#39;attente de rétention doivent être reconnus comme des participants au parcours afin que les agents aient le contexte de l&#39;offre de rétention prêt avant le début de l&#39;appel.
