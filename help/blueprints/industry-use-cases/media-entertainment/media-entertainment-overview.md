---
title: Cas d’utilisation des médias et du divertissement
description: Découvrez comment les médias et les entreprises de divertissement utilisent Adobe Experience Platform pour personnaliser la découverte de contenu, réduire le taux de perte d’abonnés et augmenter l’engagement du public.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: cfcf689f-9579-447f-9ef9-72e0c80c1f27
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '3363'
ht-degree: 0%

---

# Cas d’utilisation des médias et du divertissement

Les médias et les entreprises de divertissement utilisent Adobe Experience Platform pour unifier les données d’audience des plateformes de diffusion en continu, des bibliothèques de contenu et des comptes d’abonnés en une vue unique de chaque visionneuse ou écouteur. Cette base permet la découverte de contenu personnalisé, la rétention proactive des abonnés et les stratégies d’engagement qui encouragent le retour des audiences.

## Moteur de recommandation de contenu

Fournissez des recommandations de contenu personnalisé, notamment des films, des émissions télévisées, de la musique et des articles, en fonction de l’historique de visionnage et d’écoute, des préférences et du comportement similaire de l’utilisateur. Lorsque le public voit du contenu adapté à ses intérêts, il passe plus de temps à explorer le catalogue et à découvrir des titres qu’il aurait autrement ratés.

### Impact commercial

Les entreprises qui déploient des moteurs de recommandation de contenu personnalisé bénéficient d’un engagement amélioré du contenu et d’une augmentation significative du temps total de visionnage ou d’écoute par utilisateur.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Cette approche utilise des modèles de recommandation pilotés par l’IA qui apprennent en permanence des interactions de l’audience pour faire apparaître le contenu le plus pertinent pour chaque individu. Il s’agit du modèle approprié lorsque le jeu d’éléments est volumineux et en constante évolution (catalogues de contenu) et que la sélection est pilotée par l’affinité comportementale apprise à partir de l’historique de visionnage, plutôt que par un ensemble limité d’offres régies par des règles d’éligibilité.

### Considérations techniques

- Les métadonnées de catalogue de contenu, notamment le genre, la distribution, le réalisateur, les balises d’humeur et les évaluations de contenu, doivent être ingérées et tenues à jour pour que les recommandations reflètent l’ampleur des titres disponibles.
- Les signaux d’affichage et d’écoute doivent circuler en temps quasi réel afin que les recommandations soient mises à jour au cours d’une seule session de navigation lorsqu’un utilisateur ou une utilisatrice regarde ou ignore du contenu.
- Les modèles de recommandation nécessitent une stratégie de démarrage à froid pour les nouveaux abonnés qui ne disposent pas d’un historique d’affichage, qui retombent généralement sur le contenu en tendance, traité par des éditoriaux ou populaire selon la région.
- Les fenêtres de licence et de disponibilité du contenu doivent être prises en compte dans la logique de recommandation afin que les utilisateurs ne soient jamais recommandés pour des titres qui ne sont pas disponibles dans leur région ou qui ont été supprimés du catalogue.


## Prévention de la résiliation des abonnements

Identifiez les abonnés qui risquent d’être annulés et impliquez-les dans des recommandations de contenu personnalisé, des offres et des campagnes de fidélisation. Il est beaucoup plus rentable de conserver les abonnés existants que d&#39;en acquérir de nouveaux, et des activités de sensibilisation proactives au bon moment peuvent prévenir une part importante des annulations.

### Impact commercial

Des programmes efficaces de prévention du taux de résiliation permettent de réduire significativement le taux de résiliation des abonnés, de protéger les revenus récurrents et d’améliorer la valeur de l’audience à long terme.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Cette approche associe l&#39;orchestration des parcours à la prise de décision en temps réel afin de sélectionner la meilleure offre de rétention ou la meilleure recommandation de contenu pour chaque abonné à risque sur chaque canal. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion entre les canaux pour éviter les offres de conservation en double et lorsque la sélection de l’offre nécessite des règles d’éligibilité en fonction de la valeur de l’abonné et du niveau de risque - l’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision en temps réel nécessaire.

### Considérations techniques

- La notation du risque de résiliation doit incorporer des signaux d’engagement, tels que la baisse du temps de veille, la réduction de la fréquence de connexion et les baisses d’achèvement du contenu, pour identifier les abonnés à risque avant qu’ils n’atteignent la page d’annulation.
- Les offres de rétention doivent être hiérarchisées en fonction de la valeur des abonnés et du niveau de risque, allant des mises en avant de contenu personnalisé aux extensions de plan à prix réduit, afin d’équilibrer la protection des revenus avec l’impact sur la marge.
- Le parcours doit supprimer les messages de rétention pour les abonnés qui ont déjà renouvelé ou mis à niveau, nécessitant une intégration en temps réel au système de facturation des abonnements.
- Les règles de prise de décision [!DNL Journey Optimizer] doivent tenir compte du type de plan de l’abonné, de la durée et de l’historique des rachats d’offres passés afin d’éviter de présenter des offres qui semblent génériques ou répétitives.


## Notifications de mise à jour du nouveau contenu

Informer les abonnés des nouvelles mises à jour de contenu correspondant à leurs préférences et à leur historique d’affichage. Des notifications opportunes sur les nouveaux contenus entraînent un engagement immédiat et rappellent aux abonnés la valeur actuelle de leur abonnement.

### Impact commercial

Les notifications de mises à jour personnalisées encouragent l’engagement des nouveaux contenus au cours de la première semaine suivant leur publication, accélérant l’audience et augmentant les mesures de performances du contenu.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche répond aux événements de publication de contenu, en associant les nouveaux titres aux profils de préférences des abonnés afin de fournir des notifications pertinentes et en temps opportun. Il s’agit du modèle approprié lorsque le déclencheur est un événement système (libération de contenu) plutôt que le comportement du client et que la communication requise est immédiate et réactive plutôt qu’une séquence d’entretien soutenue.

### Considérations techniques

- Les calendriers de publication de contenu doivent être intégrés afin que les notifications puissent être planifiées ou déclenchées au moment où de nouveaux titres sont disponibles, ce qui évite des alertes prématurées pour le contenu qui n’est pas encore accessible.
- La correspondance des préférences des abonnés doit prendre en compte plusieurs dimensions, notamment l’affinité avec le genre, les acteurs ou réalisateurs préférés, les séries précédemment visionnées et les intérêts de franchise, pour que les notifications se sentent personnellement pertinentes.
- Le volume des notifications doit être géré avec précaution par le biais du capping de la fréquence afin d’éviter que les abonnés ne se sentent dépassés par les périodes de publications de contenu volumineuses.
- Le fuseau horaire et les données d’habitude de visionnage doivent informer le timing de la diffusion afin que les notifications arrivent au moment où chaque abonné est le plus susceptible d’interagir, plutôt qu’à une seule heure d’envoi globale.


## Expérience de page d’accueil personnalisée

Personnalisez de manière dynamique les pages d’accueil et de découverte de contenu afin d’afficher d’abord le contenu le plus pertinent en fonction du profil et du comportement de chaque utilisateur. Lorsque les visiteurs voient du contenu correspondant à leurs goûts immédiatement après l’ouverture de l’application, ils interagissent plus rapidement et naviguent plus longtemps.

### Impact commercial

Les expériences de page d’accueil personnalisées améliorent l’engagement de la page d’accueil et la découverte de contenu, en particulier pour les plateformes disposant de bibliothèques de contenu volumineuses et en croissance.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Cette approche utilise des stratégies de sélection et des modèles de classement pour réorganiser les lignes de contenu et les titres présentés sur la page d’accueil en fonction du profil de chaque visiteur et de son comportement en temps réel. Il s’agit du modèle approprié lorsque le jeu d’éléments est volumineux et qu’il change en permanence, et que la sélection est pilotée par une affinité comportementale pour classer les lignes de contenu de manière dynamique, plutôt que par un jeu traité statique ou une simple personnalisation basée sur les attributs.

### Considérations techniques

- La personnalisation de la page d’accueil doit s’exécuter suffisamment rapidement pour éviter les retards de charge perçus. La prise de décision Edge ou le rendu côté serveur est souvent nécessaire pour répondre aux attentes en matière de temps de réponse inférieur à la seconde.
- La logique de personnalisation doit combiner les préférences individuelles aux priorités éditoriales et promotionnelles, en veillant à ce que les versions de tentpole, le contenu saisonnier et les titres promus par les partenaires bénéficient toujours d’une visibilité appropriée.
- Les stratégies de lignes de contenu, telles que « Continuer à regarder », « Parce que vous avez regardé » et « Tendance actuelle », nécessitent chacune des entrées de données et une logique de classement distinctes qui doivent être orchestrées dans une mise en page cohérente.
- [!DNL Experience Platform] mise en œuvre de Web SDK doit capturer les interactions de la page d’accueil, notamment le défilement des lignes, les clics sur les mosaïques et le comportement du pointeur, afin d’affiner en permanence les modèles de classement.


## Rappels de la watchlist et des favoris

Envoyez des rappels aux utilisateurs et utilisatrices à propos du contenu de leur liste de surveillance qu’ils ou elles n’ont pas encore visionné, ainsi que des recommandations personnalisées pour des titres similaires. Les watchlists représentent des signaux forts d&#39;intention, et des rappels doux peuvent convertir cette intention en affichage réel.

### Impact commercial

Les programmes de rappel de la watchlist améliorent les taux d’achèvement de la watchlist, transformant l’intention enregistrée en engagement actif et augmentant l’utilisation globale de la plateforme.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche déclenche des rappels en fonction des signaux d’activité et d’inactivité de la liste de contrôle, envoyant des conseils opportuns lorsque le contenu a été enregistré mais n’a pas encore commencé. Il s’agit du modèle approprié lorsqu’un signal comportemental discret (inactivité de la liste de surveillance) est le déclencheur et que la réponse requise est un message unique sensible au temps, plutôt qu’une séquence à plusieurs étapes ou un flux de recommandations continu.

### Considérations techniques

- Le timing des rappels doit être calibré en fonction de la durée pendant laquelle le contenu est resté sur la liste de surveillance et si l&#39;utilisateur a été actif sur la plateforme récemment, en évitant les rappels pendant les périodes d&#39;engagement important lorsqu&#39;ils sont inutiles.
- Les données de la watchlist doivent être synchronisées entre les appareils en temps réel afin qu’un titre ajouté sur le mobile soit immédiatement reflété dans les calculs d’éligibilité du rappel et non dupliqué sur les plateformes.
- Les rappels doivent mettre en évidence les détails contextuels, tels que les fenêtres de disponibilité arrivant à expiration ou les nouvelles saisons de séries enregistrées, afin de créer une urgence naturelle sans sentiment d’insistance.
- Le contenu qui a été supprimé du catalogue ou qui n’est plus disponible dans la région de l’abonné doit être automatiquement exclu des messages de rappel et remplacé par d’autres recommandations.


## Campagnes de conversion d’essai gratuites

Faites participer des utilisateurs en version d’essai gratuite avec des recommandations et des offres de contenu personnalisées pour encourager la conversion des abonnements avant la fin de la période d’essai. La fenêtre d’évaluation est une occasion cruciale de démontrer que les utilisateurs sont prêts à payer suffisamment pour cela. En outre, un parcours de conversion structuré est nettement plus performant qu’un seul rappel de fin d’évaluation.

### Impact commercial

Des campagnes de conversion d’essai bien conçues permettent d’améliorer de manière significative les taux de conversion d’essai à payant, ce qui accroît directement l’efficacité d’acquisition des abonnés et réduit le coût par acquisition.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Ce parcours d’évaluation multipoint guide les utilisateurs à travers une séquence de messages de découverte de contenu, de démonstration de valeur et de conversion, en s’adaptant en fonction de leur engagement tout au long de l’évaluation. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux séquentiel de plusieurs messages sur plusieurs jours avec un embranchement conditionnel basé sur les événements d’engagement et le temps d’essai restant. Un message déclenché unique ne peut pas s’adapter à la logique de dépendance entre les étapes ou au besoin d’ajustements de cadence.

### Considérations techniques

- Le parcours doit effectuer le suivi précis des dates de début et de fin des essais, avec une logique d’embranchement qui ajuste la cadence des messages en fonction des jours d’essai restants et des niveaux d’engagement observés.
- Les recommandations de contenu au sein du parcours doivent donner la priorité aux titres les plus attrayants et exclusifs de la plateforme afin de maximiser la valeur perçue d’un abonnement payant pendant la fenêtre d’essai restreinte.
- Les utilisateurs qui effectuent une conversion avant la fin de l’essai doivent être automatiquement déplacés du parcours de conversion vers un nouveau flux de bienvenue d’abonné, ce qui empêche la poursuite de la messagerie axée sur l’essai.
- [!DNL Journey Optimizer] conditions de parcours doivent tenir compte du type de plan d’évaluation, de la source de référence et de l’utilisation de l’appareil afin d’adapter l’approche de conversion aux différents segments d’audience.


## Rappels d’affichage d’événements en direct

Informer les utilisateurs des événements en direct, des jeux de sport ou des avant-premières à venir qui correspondent à leurs centres d’intérêt et à leur historique de visionnage. Le contenu en direct stimule l’affichage des rendez-vous, ce qui renforce les habitudes des abonnés. Des rappels opportuns garantissent que les audiences ne manquent pas les événements qui leur tiennent à cœur.

### Impact commercial

Les rappels d’événements en direct personnalisés améliorent l’audience des événements en direct, maximisant ainsi l’audience pour une programmation en temps réel de grande valeur.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche déclenche des notifications en fonction des données de planning d’événement, associant les événements à venir aux profils d’intérêt des abonnés afin de fournir des rappels opportuns. Il s’agit du modèle approprié lorsque le déclencheur est un événement système (planning d’événement) plutôt que le comportement du client, et que la communication requise est immédiate et limitée dans le temps plutôt qu’une séquence d’entretien soutenue.

### Considérations techniques

- Les données sur le planning des événements, y compris les heures de début, les équipes ou les talents participants, et les détails de diffusion, doivent être ingérées à partir des systèmes de programmation et tenues à jour pour gérer les changements ou annulations de dernière minute.
- La durée de diffusion des rappels doit tenir compte des fuseaux horaires et des délais d’avance standard avant l’événement ; un rappel envoyé trop tôt est oublié, tandis qu’un rappel envoyé trop tard manque le début.
- La correspondance des intérêts doit intégrer à la fois des préférences explicites, telles que les équipes ou les genres préférés, et des signaux implicites tels que les schémas d’affichage des événements en direct passés pour identifier les événements pertinents pour chaque abonné.
- La coordination des notifications multi-appareils est importante afin qu&#39;un abonné ne reçoive pas de rappels redondants sur son téléphone, sa tablette et sa télévision intelligente simultanément.


## Génération de listes de lecture personnalisées

Générez et mettez à jour automatiquement des listes de lecture personnalisées en fonction de l’historique d’écoute, des préférences et des indicateurs d’humeur de chaque utilisateur. Les listes de lecture sélectionnées réduisent l’effort de sélection du contenu et maintiennent l’engagement des auditeurs pour des sessions plus longues.

### Impact commercial

La génération de listes de lecture personnalisées améliore l’engagement des listes de lecture et allonge de manière significative la durée moyenne de la session d’écoute, renforçant les habitudes d’utilisation quotidienne des plateformes.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Cette approche utilise des modèles pilotés par l’IA qui analysent les modèles d’écoute, le comportement d’omission et les signaux contextuels afin de générer et d’actualiser des listes de lecture adaptées à chaque utilisateur. Il s&#39;agit du bon modèle lorsque l&#39;ensemble d&#39;éléments est volumineux et change en permanence et que la sélection est motivée par une affinité comportementale provenant de l&#39;historique d&#39;écoute et des signaux d&#39;humeur, plutôt que par un ensemble limité de listes de lecture régies par des règles éditoriales.

### Considérations techniques

- Les métadonnées du catalogue musical, notamment le tempo, le genre, les balises d’humeur, les relations entre artistes et les fonctionnalités audio, doivent être balisées en profondeur pour permettre une sélection nuancée de la liste de lecture qui va au-delà de la simple correspondance de genre.
- La fréquence d’actualisation de la liste de lecture doit trouver le juste équilibre entre fraîcheur et familiarité ; les auditeurs s’attendent à de nouvelles découvertes, mais souhaitent également revoir leurs favoris ; les modèles doivent donc allier exploration et confort.
- Les signaux contextuels tels que l&#39;heure, le jour de la semaine et le dispositif d&#39;écoute peuvent informer l&#39;humeur et le niveau d&#39;énergie de la playlist, créant des playlists qui se sentent appropriées pour le moment.
- [!DNL Experience Platform] données comportementales doivent capturer des événements d’écoute granulaires, notamment des événements d’omission, de relecture, d’enregistrement et de durée de session, afin d’affiner en permanence les modèles de recommandation.


## Synchronisation de contenu sur plusieurs plateformes

Fournissez une expérience de contenu transparente sur tous les appareils en synchronisant l’historique de visionnage, les préférences et les recommandations en temps réel. Les utilisateurs s’attendent à ce que les visionneuses s’arrêtent sur un appareil et reprennent sur un autre sans perdre leur place. Une expérience cohérente sur toutes les plateformes renforce les habitudes d’utilisation quotidiennes.

### Impact commercial

La synchronisation de contenu entre plateformes améliore l’engagement entre plusieurs appareils et réduit significativement les frictions qui peuvent entraîner l’abandon de session lorsque les utilisateurs passent d’un appareil à l’autre.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Cette approche personnalise l’expérience des utilisateurs identifiés sur les plateformes web et d’applications, en garantissant la cohérence de l’état du contenu et des recommandations, quel que soit l’appareil. Il s’agit du modèle approprié lorsque la personnalisation est pilotée par les attributs de profil (identité entre appareils, état de progression de la surveillance) et l’appartenance à un segment, plutôt que par un modèle d’affinité comportementale ou une séquence d’orchestration de parcours.

### Considérations techniques

- La résolution d’identité entre appareils doit lier de manière fiable les sessions utilisateur sur les télévisions intelligentes, les applications mobiles, les tablettes et les navigateurs web afin de conserver un profil unifié unique pour chaque abonné.
- Les données de progression de la lecture, y compris la position exacte de la lecture, l’état d’achèvement de l’épisode et les préférences de sous-titre ou de piste audio, doivent être synchronisées avec une latence minimale pour offrir une expérience de reprise réellement transparente.
- Les modèles de recommandation doivent tenir compte du contexte de l’appareil, car les préférences de contenu peuvent différer entre une session de déplacement mobile et une session de salon en soirée sur un grand écran.
- [!DNL Real-Time Customer Data Platform] stratégies de fusion de profil doivent être configurées pour gérer des sessions simultanées sur plusieurs appareils sans créer de mises à jour d’état en conflit.


## Personalization de partage sur les réseaux sociaux

Personnalisez les invites et les recommandations de partage sur les réseaux sociaux en fonction des connexions et des préférences de contenu de chaque utilisateur. Faciliter et séduire le partage de ce qu&#39;ils aiment transforme les abonnés satisfaits en défenseurs organiques qui favorisent la sensibilisation et l&#39;acquisition.

### Impact commercial

Le partage social personnalisé permet d&#39;obtenir des taux de partage social améliorés, amplifiant la portée organique et réduisant les coûts d&#39;acquisition payés.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Cette approche personnalise les expériences de partage in-app pour les utilisateurs et utilisatrices identifiés, en affichant des invites de partage pertinentes selon les préférences et les schémas d’engagement de l’utilisateur ou utilisatrice. Il s’agit du modèle approprié lorsque la personnalisation est pilotée par des attributs de profil et un contexte d’engagement connu plutôt qu’un modèle d’affinité comportementale, et l’objectif est d’améliorer l’expérience instantanée sans orchestrer une séquence de parcours.

### Considérations techniques

- Les invites de partage doivent être déclenchées à des moments naturels de plaisir, comme terminer une série digne d&#39;intérêt ou découvrir un nouvel artiste favori, plutôt qu&#39;à des intervalles arbitraires qui se sentent intrusifs.
- Les images et messages de partage pré-renseignés doivent être générés dynamiquement en fonction du contenu spécifique partagé, y compris les miniatures appropriées, les descriptions et les liens profonds qui renvoient les destinataires vers la plateforme.
- Les contrôles de confidentialité doivent s’assurer que l’activité de visionnage n’est partagée que lorsque l’utilisateur ou l’utilisatrice lance explicitement le partage ; le partage passif ou automatique de l’historique de visionnage sans consentement peut nuire à la confiance.
- L’intégration des plateformes sociales doit respecter les politiques de partage de chaque réseau et gérer les exigences d’authentification, de limites de débit et de format de contenu pour les plateformes telles qu’Instagram, TikTok et X.


## Premium Feature Upsell

Identifiez les utilisateurs qui bénéficieraient des fonctionnalités Premium et présentez des offres de montée en gamme personnalisées en fonction de leurs schémas d’utilisation. Un message de montée en gamme ciblé destiné aux utilisateurs qui démontrent déjà des comportements conformes à la valeur premium est beaucoup plus efficace que des campagnes de mise à niveau générales.

### Impact commercial

Les campagnes de montée en gamme premium personnalisées favorisent l’adoption des fonctionnalités premium, augmentant le chiffre d’affaires moyen par utilisateur tout en fournissant des fonctionnalités qui correspondent véritablement aux besoins des abonnés.

### Mise en œuvre

Utilisez le modèle [&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Cette approche utilise une logique de décision centralisée pour évaluer les schémas d’utilisation de chaque abonné et sélectionner l’offre premium la plus pertinente au bon moment. Il s’agit du modèle approprié lorsque la sélection des offres doit tenir compte des contraintes de modèle d’utilisation et des règles d’éligibilité de niveau Premium, contraintes qui nécessitent une logique de prise de décision régie plutôt qu’un classement par affinité comportementale seul.

### Considérations techniques

- L’analyse des modèles d’utilisation doit identifier les comportements spécifiques qui indiquent une préparation à Premium, tels que l’utilisation fréquente des fonctionnalités disponibles sous une forme limitée dans le plan de base, l’utilisation de plusieurs appareils ou un volume de consommation de contenu élevé.
- La présentation de l’offre doit mettre en évidence les avantages Premium spécifiques les plus pertinents pour le comportement de chaque utilisateur plutôt que de répertorier toutes les fonctionnalités Premium de manière générique. Un utilisateur qui télécharge fréquemment du contenu doit privilégier l’affichage hors ligne.
- Le moment de la montée en gamme doit éviter les moments de frustration, par exemple immédiatement après un blocage de paywall, et tirer plutôt parti des moments d&#39;engagement positifs lorsque l&#39;abonné est le plus réceptif.
- Les règles de prise de décision [!DNL Journey Optimizer] doivent coordonner les offres de montée en gamme dans les messages in-app, les e-mails et les notifications push afin de présenter une offre cohérente sans surcharger l’abonné sur l’ensemble des canaux.


## Campagnes d’achèvement du contenu

Rappelez aux utilisateurs de terminer de regarder ou d’écouter le contenu qu’ils ont commencé mais n’ont pas terminé, accompagné de recommandations personnalisées pour savoir quoi apprécier ensuite. Un contenu incomplet représente un engagement non réalisé et un petit coup de pouce convertit souvent une session abandonnée en une expérience terminée.

### Impact commercial

Les campagnes d’achèvement du contenu entraînent une amélioration des taux d’achèvement du contenu, ce qui augmente le temps d’engagement total et renforce la perception des abonnés quant à la valeur de la plateforme.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche déclenche des rappels en fonction des événements d’abandon de contenu, envoyant des messages opportuns lorsqu’un utilisateur ou une utilisatrice s’est arrêté au cours d’un titre et n’a pas renvoyé de message dans une fenêtre définie. Il s’agit du modèle approprié lorsqu’un signal comportemental discret (abandon de contenu) est le déclencheur et que la réponse requise est un message unique et sensible au temps avec un contexte, plutôt qu’un parcours à plusieurs étapes ou une sélection d’offres dynamique.

### Considérations techniques

- Les seuils d’abandon doivent être calibrés par type de contenu ; un film suspendu à 80 % est un bon candidat pour l’achèvement, tandis qu’un podcast arrêté après deux minutes peut indiquer un désintérêt plutôt qu’une écoute interrompue.
- Les messages de rappel doivent inclure un titre de contenu spécifique, une miniature visuelle et un lien profond direct qui reprend la lecture à l’endroit exact où l’utilisateur s’est arrêté.
- Le capping de la fréquence doit éviter les rappels excessifs pour les utilisateurs et utilisatrices qui échantillonnent régulièrement du contenu sans y mettre fin. Les incitations répétées pour le contenu qu’un utilisateur ou une utilisatrice a choisi d’abandonner peuvent sembler intrusives.
- La disponibilité du contenu doit être vérifiée au moment de l’envoi, car les titres peuvent quitter la plateforme ou changer de région de disponibilité entre l’événement d’abandon et la diffusion de rappel.


## Pilote de résiliation des abonnés et analyse de l’engagement du contenu

Identifiez les modèles de consommation de contenu, les modifications de la fréquence d’engagement et les comportements d’interaction de catalogue qui précèdent l’annulation des abonnés, et mesurez la manière dont l’affinité du contenu varie entre les segments d’abonnés et les cohortes d’acquisition. Les entreprises de streaming et de publication qui ne peuvent pas associer le comportement du contenu aux résultats de résiliation prennent des décisions d’investissement en fonction du nombre de vues agrégées plutôt que de l’impact sur la rétention.

### Impact commercial

La corrélation des modèles d’engagement du contenu avec les résultats de rétention des abonnés donne aux équipes produit, stratégie de contenu et marketing une base factuelle pour hiérarchiser les investissements dans les catalogues et concevoir des campagnes de réengagement autour des comportements qui soutiennent réellement les abonnements.

### Mise en œuvre

Utilisez le modèle [Customer Analytics et génération d’Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Cette approche connecte les données d’événement de diffusion en continu, les métadonnées de contenu, les enregistrements de cycle de vie des abonnements et l’historique des interactions de la campagne à Customer Journey Analytics, où l’analyse de rétention des cohortes mesure la corrélation entre l’affinité du contenu et la durée de vie des abonnés et où l’analyse des abandons identifie les modèles de réduction de l’engagement qui précèdent l’annulation. Il s’agit du modèle approprié lorsque l’objectif est de comprendre les facteurs comportementaux de l’attrition et des performances du contenu, plutôt que de déclencher un message de reconquête ou d’activer une audience à risque d’attrition pour la suppression.

### Considérations techniques

- Les événements de consommation de contenu doivent inclure à la fois les identifiants de contenu et les métadonnées au niveau de la session (événements de début, de pause, d’achèvement et d’omission) afin que la profondeur d’engagement puisse être mesurée au-delà du nombre de lectures brutes dans CJA.
- Les événements de cycle de vie des abonnements, notamment le début de l’essai, la conversion, l’échec du paiement, la rétrogradation et l’annulation, doivent être ingérés en tant qu’événements discrets avec des horodatages précis afin que les fenêtres comportementales de pré-annulation puissent être définies précisément dans les filtres CJA.
- Les attributs de catalogue de contenu tels que le genre, le format, l’association de séries et la récence de publication doivent être disponibles en tant que jeu de données de recherche dans la connexion CJA afin que l’analyse de l’engagement du contenu puisse être divisée par dimension de catalogue plutôt que de nécessiter une analyse au niveau du titre individuel.
- L’analyse des cohortes comparant les courbes de rétention par canal d’acquisition et le contenu original consulté nécessite que la source d’acquisition et le contenu consulté en premier soient capturés en tant que dimensions de profil ou de premier événement, disponibles pour la définition de la cohorte dans CJA.
