---
title: Cas d’utilisation des télécommunications
description: Découvrez comment les entreprises de télécommunications utilisent Adobe Experience Platform pour réduire l’attrition, favoriser les mises à niveau des appareils et améliorer l’engagement des clients.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2295'
ht-degree: 1%

---


# Cas d’utilisation des télécommunications

Les entreprises de télécommunications utilisent Adobe Experience Platform pour créer une vue d’ensemble de chaque abonné et offrir des expériences personnalisées qui réduisent le taux de résiliation, augmentent les mises à niveau de forfaits et d’appareils et renforcent les relations client à long terme. En connectant les données d&#39;utilisation du réseau, les informations de facturation et les interactions avec les clients, les fournisseurs de télécommunications peuvent anticiper les besoins des abonnés et les impliquer au bon moment via leurs canaux préférés.

## Recommandations de mise à niveau de l’appareil

Identifier les clients éligibles aux mises à niveau d’appareils et présenter des recommandations personnalisées d’appareils et des offres de mise à niveau en fonction des schémas d’utilisation et des préférences. En analysant la durée des contrats, l&#39;âge des appareils et le comportement de navigation individuel, les fournisseurs de télécommunications peuvent faire apparaître les appareils et les options de financement les plus pertinents à chaque abonné.

### Impact commercial

Les entreprises qui mettent en œuvre des recommandations de mise à niveau des appareils constatent généralement une augmentation de 30 à 40 % des taux de conversion de mise à niveau en proposant la bonne offre au bon moment par le biais du canal préféré du client.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour orchestrer des parcours de mise à niveau qui évaluent l’éligibilité de chaque abonné, ses préférences d’appareil et son affinité de canal, afin de fournir des offres de mise à niveau personnalisées par le biais d’e-mails, de notifications d’application et d’expériences en magasin.

### Considérations techniques

- Intégrer l’inventaire des appareils et les systèmes de tarification pour garantir que les recommandations reflètent la disponibilité actuelle et les prix promotionnels.
- Connectez les données de gestion des contrats pour identifier précisément les fenêtres d’éligibilité de mise à niveau et les offres de mise à niveau anticipée.
- Intégrez la télémétrie d&#39;utilisation des appareils (capacité de stockage, état de la batterie, mesures de performances) pour renforcer la pertinence des recommandations.
- Coordonnez-vous avec les plateformes de vente au détail et d’e-commerce pour maintenir une expérience de mise à niveau cohérente sur les canaux numériques et en magasin.


## Campagnes d’optimisation du plan

Analysez les schémas d’utilisation des clients et recommandez des modifications de plan optimales pour économiser de l’argent ou obtenir de meilleures fonctionnalités en fonction de leurs besoins réels. En offrant des recommandations de plan de manière proactive, vous gagnez en confiance et réduisez le risque que vos abonnés quittent pour les concurrents avec des prix plus simples.

### Impact commercial

Les campagnes d’optimisation des plans entraînent généralement une augmentation de 25 à 35 % des taux de modification des plans, ce qui améliore la satisfaction des clients tout en augmentant le chiffre d’affaires moyen par utilisateur lorsque les abonnés passent à des plans qui correspondent mieux à leur consommation.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer une campagne multipoint qui identifie les incohérences entre l’utilisation et la planification, informe les abonnés sur les meilleures options et les guide tout au long du processus de changement de planification avec des suivis opportuns.

### Considérations techniques

- Ingérez des données d’utilisation en temps réel et historiques (minutes vocales, consommation de données, appels internationaux) pour identifier précisément les incohérences du plan.
- Connectez les données du système de facturation pour calculer les économies potentielles ou les gains en termes de fonctionnalités pour chaque modification de plan recommandée.
- Tenez compte des règles de tarification promotionnelles et des obligations contractuelles lors de la génération de recommandations de plan.
- Intégrez-la aux portails en libre-service afin que les abonnés puissent effectuer les modifications de plan directement à partir des points de contact de Campaign.


## Prévention de l’attrition pour les clients à forte valeur ajoutée

Identifiez les clients à forte valeur ajoutée qui risquent de se perdre et engagez-les avec des offres de fidélisation personnalisées et un service client proactif. En combinant des signaux comportementaux tels qu&#39;une baisse de l&#39;utilisation, des appels de service répétés et une navigation concurrentielle avec des données de valeur de durée de vie, les fournisseurs peuvent intervenir avant qu&#39;un abonné décide de partir.

### Impact commercial

Les programmes de prévention du taux de résiliation ciblant les abonnés à forte valeur ajoutée permettent généralement de réduire le taux de résiliation de 20 à 30 %, de protéger les revenus récurrents importants et de réduire le coût d’acquisition des clients de remplacement.

### Mise en œuvre

Utilisez le modèle [Cross-Channel Parcours with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour surveiller les signaux de risque d’attrition en temps réel, déterminer la meilleure offre de rétention pour chaque abonné et orchestrer des activités de sensibilisation personnalisées sur les canaux numériques et le centre d’appels.

### Considérations techniques

- Créez des scores de propension à l’attrition en combinant les tendances d’utilisation, l’historique des interactions de services et les données de sentiment des transcriptions des centres d’appels.
- Intégrez les systèmes de centres d’appels et de vente au détail afin que les agents aient une visibilité sur les offres de fidélisation déjà présentées par le biais des canaux numériques.
- Connectez les données de veille concurrentielle (demandes de sortie, comparaisons de plans concurrents) pour affiner la notation des risques et les stratégies d&#39;offres.
- Établissez des règles de gouvernance pour éviter de surcontacter les abonnés à risque, ce qui peut accélérer la perte de clientèle plutôt que la prévenir.


## Nouveau Parcours d’intégration des clients

Automatisez un parcours d’intégration personnalisé pour les nouveaux clients avec des informations de bienvenue, des conseils sur la configuration du compte et des tutoriels sur les fonctionnalités. Une expérience d’intégration structurée permet aux abonnés de découvrir rapidement toute la valeur de leur forfait et de leurs services, établissant ainsi les bases d’une rétention à long terme.

### Impact commercial

Les parcours d’intégration bien conçus augmentent généralement les taux d’activation des fonctionnalités de 50 à 60 %, ce qui entraîne des scores de satisfaction plus élevés et une baisse de l’attrition au début de la vie chez les nouveaux abonnés.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer une expérience d’intégration séquentielle qui s’adapte en fonction du type de forfait, de l’appareil et de l’engagement de chaque abonné par rapport aux étapes d’intégration précédentes.

### Considérations techniques

- Intégrez des systèmes d’approvisionnement de compte pour déclencher le parcours d’intégration immédiatement après l’activation et adaptez le contenu au plan et à l’appareil spécifiques de l’abonné.
- Connectez les données d’engagement de l’application pour suivre les fonctionnalités explorées par l’abonné et ajustez les messages d’intégration suivants en conséquence.
- Coordonnez-vous avec la plateforme du service clientèle pour vous assurer que les agents connaissent l’étape d’intégration d’un abonné s’ils appellent pour des questions.
- Prise en charge de plusieurs chemins d’intégration pour différents segments de clients tels que les abonnés individuels, les administrateurs de forfaits familiaux et les comptes professionnels.


## Alertes et recommandations relatives à l’utilisation des données

Envoyez des alertes personnalisées lorsque les clients approchent des limites de données et recommandent des mises à niveau de plan ou des modules complémentaires de données en fonction des schémas d’utilisation. Des notifications opportunes et utiles transforment une expérience potentiellement frustrante en un moment d’engagement visant à renforcer la confiance.

### Impact commercial

Les alertes d’utilisation proactive des données entraînent généralement une augmentation de 40 à 50 % des achats de modules complémentaires de données, tout en réduisant les plaintes relatives aux factures-surprises et en améliorant la satisfaction globale des clients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour envoyer des alertes en temps réel lorsque les seuils d’utilisation sont dépassés, avec des recommandations personnalisées basées sur les modèles de consommation historiques et les détails du plan de l’abonné.

### Considérations techniques

- Connectez-vous aux flux de données d’utilisation du réseau qui fournissent des mises à jour de consommation en temps quasi réel pour déclencher des alertes à des seuils significatifs (75 %, 90 % et 100 % des limites du plan).
- Intégrez des systèmes de facturation et de gestion de plan pour présenter une tarification complémentaire précise et permettre des achats ponctuels directement à partir du message d’alerte.
- Tenez compte des pools de données partagés sur les plans familiaux en alertant l&#39;utilisateur individuel et l&#39;administrateur du plan.
- Mettez en œuvre le capping de la fréquence pour éviter la fatigue des alertes pour les abonnés qui utilisent constamment de grandes quantités de données à chaque cycle de facturation.


## Notifications de panne du service

Informez de manière proactive les clients des pannes de service, des problèmes de maintenance ou de réseau dans leur zone grâce à des mises à jour personnalisées et à des offres de compensation. Le fait de contacter les clients avant qu’ils ne ressentent leur frustration démontre leur responsabilité et réduit considérablement le volume d’assistance entrant.

### Impact commercial

Les notifications de panne proactives atteignent généralement un taux d’accusé de réception de 60 à 70 % et réduisent considérablement le volume du centre d’appels lors des interruptions de service, ce qui réduit les coûts de support tout en améliorant la perception des clients.

### Mise en œuvre

Utilisez le modèle [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour détecter les événements réseau et informer immédiatement les abonnés affectés par le biais de leurs canaux préférés avec des détails pertinents, des délais de résolution estimés et une compensation appropriée, le cas échéant.

### Considérations techniques

- Intégrez-la aux systèmes de surveillance des centres d&#39;exploitation réseau pour recevoir des données en temps réel sur les pannes et les événements de maintenance avec des informations sur la portée géographique.
- Utilisez les données d’adresse et de localisation des abonnés pour identifier précisément les clients concernés et éviter d’avertir ceux qui se trouvent en dehors de la zone touchée.
- Connectez-vous au système de facturation et de crédits afin d’automatiser les offres de crédit de service pour les pannes prolongées en fonction du forfait de l’abonné et de la durée de la perturbation.
- Coordonnez la messagerie sur l’ensemble des canaux pour fournir des mises à jour de statut cohérentes et éviter d’envoyer des informations conflictuelles à mesure que la situation évolue.


## Gestion du plan familial

Personnalisez les communications et les offres pour les administrateurs de plans familiaux en fonction des schémas d&#39;utilisation familiaux et des besoins individuels des membres. Les plans familiaux représentent des comptes multilignes à forte valeur ajoutée où l’engagement avec l’administrateur du plan stimule la rétention sur toutes les lignes.

### Impact commercial

Les communications personnalisées de gestion des plans familiaux augmentent généralement l&#39;engagement des plans familiaux de 30 à 40 %, ce qui se traduit par une fidélisation des lignes plus élevée et une plus grande valeur de durée de vie par compte.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour analyser l’utilisation parmi tous les membres de la famille, identifier les opportunités telles que l’ajout de lignes ou l’ajustement de limites individuelles, et fournir des recommandations personnalisées à l’administrateur du plan.

### Considérations techniques

- Modélisez les hiérarchies de comptes familiaux pour faire la distinction entre l&#39;administrateur du plan et les membres individuels, en respectant les niveaux d&#39;autorisation pour les communications et les modifications de compte.
- Agrégez les données d’utilisation sur toutes les lignes du compte pour identifier les modèles et les opportunités au niveau de la famille, tels que les données partagées sous-utilisées ou les cycles de mise à niveau inégales des appareils.
- Intégrez le contrôle parental et les systèmes de filtrage de contenu pour prendre en charge les fonctionnalités de personnalisation spécifiques à la famille.
- Assurez-vous que des contrôles de confidentialité sont en place afin que les détails d’utilisation des membres individuels soient partagés de manière appropriée avec l’administrateur du plan en fonction des autorisations du compte.


## Campagnes de mise à niveau vers la 5G

Ciblez les clients éligibles aux mises à niveau du réseau 5G avec des offres et des avantages personnalisés en fonction de leur emplacement et de leurs schémas d’utilisation. À mesure que la couverture 5G s&#39;étend, atteindre les abonnés dans les zones nouvellement couvertes avec des messages pertinents accélère l&#39;adoption et augmente l&#39;utilisation du réseau.

### Impact commercial

Les campagnes de mise à niveau 5G ciblées entraînent généralement une augmentation de 25 à 35 % des taux d’adoption de la 5G parmi les abonnés admissibles, ce qui favorise les rendements de l’investissement dans le réseau et la différenciation concurrentielle.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pour segmenter les abonnés en fonction de la disponibilité de la couverture 5G, de la compatibilité des appareils et de l’éligibilité du plan, puis diffusez des campagnes de mise à niveau personnalisées mettant en évidence les avantages les plus pertinents pour le profil d’utilisation de chaque abonné.

### Considérations techniques

- Intégrer des cartes de couverture réseau pour identifier avec précision les abonnés dans les zones où le service 5G est actif et éviter de promouvoir les mises à niveau là où la couverture n&#39;est pas encore disponible.
- Connectez les données de compatibilité des appareils pour déterminer quels abonnés ont besoin d’un nouvel appareil par rapport à ceux qui disposent déjà d’un matériel compatible 5G.
- Assurer la coordination avec les systèmes d&#39;inventaire de détail pour s&#39;assurer que les appareils et les forfaits promus sont disponibles dans le magasin préféré de l&#39;abonné ou en ligne.
- Segmentez la messagerie en fonction du profil d’utilisation afin que les utilisateurs de données volumineuses bénéficient d’avantages axés sur les performances tandis que les utilisateurs occasionnels reçoivent des messages de couverture et de fiabilité.


## Rappels de paiement de la facture

Envoyez des rappels de paiement personnalisés par le biais de canaux préférés avec des options de paiement et des informations sur le solde du compte. Des rappels opportuns et pratiques réduisent les retards de paiement et les coûts de recouvrement associés tout en maintenant une relation client positive.

### Impact commercial

Les rappels de paiement de factures personnalisés améliorent généralement les taux de paiement ponctuel de 20 à 30 %, réduisant les dépenses de recouvrement et minimisant les suspensions de service qui provoquent l&#39;insatisfaction des clients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour envoyer des rappels à des heures optimales avant la date d’échéance, personnalisés avec le solde de l’abonné, son mode de paiement préféré et un lien direct pour effectuer le paiement.

### Considérations techniques

- Intégrez-la à la plateforme de facturation pour accéder aux soldes des comptes en temps réel, aux dates d’échéance et à l’historique des paiements afin d’obtenir un contenu de rappel précis.
- Connectez-vous aux systèmes de traitement des paiements pour activer le paiement en un clic ou en un clic directement à partir du message de rappel.
- Implémentez une logique d’escalade qui ajuste l’urgence et la fréquence des rappels à l’approche de la date d’échéance, tout en respectant les préférences de communication.
- Prenez en charge plusieurs méthodes de paiement (inscription automatique, portefeuille numérique, virement bancaire) et personnalisez les options présentées en fonction de l’historique de l’abonné.


## Recommandations de service de module complémentaire

Recommandez des services complémentaires pertinents tels que l’assurance de l’appareil, l’espace de stockage dans le cloud et les lots de streaming en fonction du plan, de l’utilisation et des préférences du client ou de la cliente. Les recommandations contextuelles augmentent la valeur que les abonnés reçoivent de leur relation avec le fournisseur tout en augmentant le chiffre d’affaires moyen par utilisateur.

### Impact commercial

Les recommandations de services de module complémentaire personnalisés entraînent généralement une augmentation de 15 à 25 % des taux d’adoption des modules complémentaires, augmentant ainsi le chiffre d’affaires de la base d’abonnés existante sans le coût d’acquisition de nouveaux clients.

### Mise en œuvre

Utilisez le modèle [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pour évaluer le profil, les services actuels et les signaux comportementaux de chaque abonné afin de déterminer l’offre complémentaire la plus pertinente et de la présenter par le canal et le moment optimaux.

### Considérations techniques

- Connectez-vous au catalogue de services actuel de l&#39;abonné pour éviter de recommander des services qu&#39;il possède déjà et pour identifier les compléments naturels à son forfait existant.
- Intégrez les données des partenaires et des services tiers (fournisseurs de streaming, compagnies d&#39;assurance) pour présenter des tarifs précis et des offres groupées.
- Utilisez les données d’appareil et d’utilisation pour émettre des recommandations, telles que suggérer une assurance appareil pour les abonnés disposant de nouveaux appareils Premium ou un stockage dans le cloud pour ceux qui manquent de stockage pour l’appareil.
- Coordonnez-vous avec la personnalisation in-app et web pour renforcer les recommandations de modules complémentaires sur les points de contact en libre-service.


## Personalization des performances réseau

Personnalisez les informations et les recommandations relatives aux performances du réseau en fonction de l’emplacement, de l’appareil et des schémas d’utilisation du client. Aider les abonnés à optimiser leur expérience de connectivité crée de la confiance et réduit les contacts d’assistance associés aux problèmes de performances.

### Impact commercial

Les expériences de performances réseau personnalisées augmentent généralement l’engagement des applications de 35 à 45 %, car les abonnés reviennent pour vérifier la couverture, résoudre les problèmes et découvrir des conseils d’optimisation adaptés à leur situation.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pour fournir des tableaux de bord de performances réseau personnalisés, des informations sur la couverture et des recommandations d’optimisation dans l’application et l’expérience du compte web de l’abonné.

### Considérations techniques

- Intégrer des mesures de qualité du réseau et des données de couverture afin de fournir des informations de performances spécifiques à l&#39;emplacement, pertinentes pour la maison, le travail et les zones fréquemment visitées de l&#39;abonné.
- Connectez les données de diagnostic des appareils pour offrir des recommandations de dépannage personnalisées basées sur le modèle d’appareil et la version logicielle spécifiques à l’abonné.
- Utilisez les services Edge de [!DNL Adobe Experience Platform] pour offrir une personnalisation à faible latence dans l’expérience de l’application sans affecter les performances.
- Mettez en œuvre des boucles de rétroaction afin que les abonnés puissent signaler les problèmes de couverture, ce qui enrichit les données réseau tout en démontrant la réactivité à leur expérience.


## Engagement du programme de fidélité

Personnalisez les communications, les récompenses et les offres du programme de fidélité en fonction du niveau, du solde de points et de l’historique de remboursement du client. Une expérience de fidélité bien personnalisée renforce le lien émotionnel avec la marque et crée des coûts de changement significatifs au-delà des termes du contrat.

### Impact commercial

L’engagement personnalisé du programme de fidélité augmente généralement la participation au programme et récompense l’échange de 30 à 40 %, ce qui entraîne des taux de rétention plus élevés parmi les abonnés inscrits.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour orchestrer des communications de fidélité personnalisées qui mettent en évidence les récompenses pertinentes, notifient les abonnés de la progression de niveau et présentent des opportunités d’échange alignées sur leurs préférences et leur comportement.

### Considérations techniques

- Intégrez la plateforme de fidélité pour accéder aux soldes de points en temps réel, au statut du niveau et à l’historique des remboursements afin d’offrir une personnalisation précise.
- Connectez les catalogues de récompenses des partenaires pour présenter une large gamme d&#39;options de rachat adaptées aux intérêts démontrés et aux rachats passés de chaque abonné.
- Coordonnez les messages de fidélité avec d’autres parcours de campagne pour vous assurer que les offres de fidélité et les récompenses de fidélité se complètent plutôt qu’entrent en conflit.
- La progression du niveau de prise en charge progresse en calculant la proximité d’un abonné par rapport au niveau suivant et en présentant des étapes exploitables pour l’atteindre.
