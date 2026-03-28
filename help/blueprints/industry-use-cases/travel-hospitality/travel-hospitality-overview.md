---
title: Cas d’utilisation des voyages et de l’hébergement
description: Découvrez comment les agences de voyage et d’accueil utilisent Adobe Experience Platform pour personnaliser les expériences de réservation, récupérer les réservations abandonnées et fidéliser les clients.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: fbdcc015-96a4-4015-93e2-3fc7db375c13
source-git-commit: 3542d76106fada9019b70a8cc9fd4c74872d4995
workflow-type: tm+mt
source-wordcount: '4015'
ht-degree: 0%

---

# Cas d’utilisation des voyages et de l’hébergement

Les agences de voyage et d’accueil utilisent Adobe Experience Platform pour rassembler les données des clients issues des moteurs de réservation, des programmes de fidélité, des systèmes de gestion des propriétés et des points de contact numériques en une vue unique de chaque voyageur. Cette base unifiée alimente des expériences personnalisées qui inspirent les réservations, récupèrent les réservations abandonnées et construisent le type de fidélité des clients qui entraîne les visites répétées.

## Page d’accueil personnalisée pour les nouveaux visiteurs

Affichez des recommandations de croisière, d’hôtel et de destination personnalisées sur la page d’accueil en fonction de l’emplacement géographique et du comportement de navigation du visiteur. Les nouveaux visiteurs qui voient immédiatement des options de voyage pertinentes sont beaucoup plus susceptibles d&#39;explorer davantage et d&#39;entamer le processus de réservation.

### Impact commercial

La personnalisation de la page d’accueil pour les nouveaux visiteurs entraîne une amélioration des taux de conversion en présentant des options de voyage qui correspondent au lieu et aux intérêts du visiteur plutôt qu’un contenu générique.

### Mise en œuvre

Utilisez le modèle Personalization Web de visiteur anonyme[&#128279;](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md). Cette approche fournit du contenu personnalisé aux visiteurs qui ne se sont pas encore identifiés, en utilisant les signaux disponibles tels que la géolocalisation, le type d’appareil et la source de référence pour personnaliser l’expérience à partir de la toute première page. Il s’agit du modèle approprié lorsque le visiteur ne s’est pas encore identifié et que la personnalisation doit s’appuyer sur les signaux disponibles tels que la géolocalisation, le type d’appareil et la source de référence. La personnalisation d’un visiteur connu nécessite un profil authentifié qui n’existe pas encore.

### Considérations techniques

- Les données de géolocalisation doivent être résolues avec précision à la périphérie pour servir les destinations, les devises et les ports de départ appropriés à la région sans ajouter de latence à la charge de la page d’accueil.
- Les règles de Personalization doivent tenir compte des tendances saisonnières des voyages par région, en faisant apparaître les destinations par temps chaud aux visiteurs dans des climats froids pendant les mois d&#39;hiver, par exemple.
- Les stratégies de contenu de secours sont essentielles pour les visiteurs dont l’emplacement ne peut pas être déterminé ou qui arrivent par le biais de services d’anonymisation.
- L’intégration au flux de disponibilité du système de réservation garantit que les propriétés et les itinéraires présentés sont en fait réservables, évitant ainsi la frustration de promouvoir les options épuisées.


## Parcours de récupération après abandon de panier

Détecter automatiquement lorsqu’un client abandonne son panier de réservation et déclencher un parcours d’e-mail à plusieurs étapes avec des offres personnalisées pour encourager l’achèvement de l’opération. Les réservations abandonnées représentent l&#39;une des plus importantes fuites de revenus en matière de voyages et d&#39;accueil, et le suivi opportun pendant que l&#39;intention de voyage est encore fraîche récupère une part significative de ces réservations.

### Impact commercial

Les programmes de récupération des réservations efficaces atteignent des taux de récupération des paniers significatifs et peuvent générer un revenu incrémentiel significatif en fonction du volume de réservation et de la valeur moyenne du voyage.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche répond à un événement d’abandon de panier en temps réel, en envoyant un rappel en temps opportun pendant que l’intention de voyage du client est toujours élevée. Il s’agit du modèle approprié lorsque le déclencheur est un événement de comportement client en temps réel et que la réponse requise est un message unique et sensible au temps, plutôt qu’une séquence d’entretien à plusieurs étapes ou une sélection d’offres dynamique qui change en fonction de la réponse du client.

### Considérations techniques

- Les seuils de détection d’abandon de panier devraient tenir compte des cycles de réflexion plus longs typiques dans les achats de voyage ; un délai de 2 à 4 heures avant le premier rappel est souvent plus approprié que les 30 à 60 minutes utilisées dans la vente au détail.
- Le contenu des e-mails doit extraire dynamiquement le prix actuel, la disponibilité des chambres ou des cabines et les images du système de réservation au moment de l’envoi, car l’inventaire et les tarifs des voyages changent fréquemment.
- Les incentives personnalisés, tels que les mises à niveau ou les crédits de séjour gratuits, doivent être gérés au moyen de règles commerciales qui tiennent compte de la marge, de la saisonnalité et du niveau de fidélité du client.
- La logique de suppression doit exclure les clients qui ont effectué leur réservation par un autre canal, tel qu’un centre d’appel ou une agence de voyages, afin d’éviter les messages de suivi non pertinents.


## Ciblage des visiteurs à forte intention

Identifiez les visiteurs avec une intention d’achat élevée à l’aide du score de propension optimisé par l’IA et ciblez-les avec des offres et du contenu personnalisés. En identifiant les visiteurs les plus susceptibles de réserver, l’organisation peut concentrer ses offres et ses efforts de vente les plus attrayants sur les voyageurs les plus proches de la prise de décision.

### Impact commercial

Cibler les visiteurs à forte intention avec des offres personnalisées améliore la conversion de ces segments, en concentrant les investissements marketing là où ils offrent le meilleur rendement.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Cette approche utilise des données de profil en temps réel et des signaux comportementaux pour personnaliser l’expérience web des visiteurs identifiés, en fournissant du contenu et des offres adaptés qui correspondent à leur niveau de préparation à l’achat. Il s’agit du modèle approprié lorsque la personnalisation est pilotée par des attributs de profil et des scores de propension pour les clients identifiés plutôt que par un modèle d’affinité comportementale, et lorsque le client s’est déjà authentifié, ce qui rend disponibles ses signaux d’appartenance au segment et d’intention.

### Considérations techniques

- Les modèles de propension doivent être entraînés sur des signaux d’intention spécifiques au voyage, tels que les recherches de dates, les pages vues pour les prix, l’activité de comparaison de chambres et les visites répétées à la même destination dans une courte fenêtre.
- Les interventions à forte intention, telles que les invites de chat en direct ou les offres à durée limitée, doivent apparaître aux points de décision naturels dans le flux de réservation plutôt que d’interrompre l’expérience de navigation.
- Le modèle de notation devrait faire la distinction entre l’intention de recherche et l’intention de réservation, puisque les voyageurs font souvent des recherches plusieurs mois avant d’être prêts à acheter.
- [!DNL Real-Time Customer Data Platform] attributs calculés peuvent agréger les signaux comportementaux entre les sessions afin de maintenir à jour le score d’intention de chaque visiteur.


## Campagnes de montée en gamme après réservation

Une fois qu’un client a effectué une réservation, déclenchez automatiquement des campagnes de montée en gamme pour des mises à niveau de cabines, des excursions à terre, des forfaits repas et d’autres accessoires. La période entre la réservation et le voyage est celle où les clients sont les plus enthousiastes quant à leur prochain voyage et les plus réceptifs à l&#39;amélioration de leur expérience.

### Impact commercial

Les campagnes de montée en gamme après réservation augmentent la valeur moyenne des commandes et augmentent les recettes accessoires, transformant une réservation unique en une transaction beaucoup plus précieuse.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Ce parcours en plusieurs étapes guide les clients qui ont réservé dans une séquence temporelle d’opportunités de montée en gamme, en adaptant les offres en fonction de ce que le client a déjà acheté et de son engagement par rapport à des messages précédents. Il s’agit du modèle approprié lorsque le cas d’utilisation nécessite un flux séquentiel de plusieurs messages sur plusieurs jours avec un embranchement conditionnel basé sur les événements d’engagement et la disponibilité de l’inventaire. Un message déclenché unique ne peut pas s’adapter à la logique de dépendance entre les moments de montée en gamme ou les ajustements de minutage basés sur la proximité de la date de voyage.

### Considérations techniques

- Le parcours doit s&#39;intégrer au système de réservation pour savoir exactement ce que le client a réservé, quelles améliorations sont disponibles pour son itinéraire spécifique et le prix actuel pour chaque option accessoire.
- Le calendrier de montée en gamme doit être échelonné stratégiquement ; des mises à niveau de cabines peuvent être proposées peu après la réservation, tandis que les excursions et les forfaits repas se portent mieux à l&#39;approche de la date de voyage.
- L&#39;inventaire et la disponibilité des produits auxiliaires doivent être vérifiés au moment de la présentation de l&#39;offre, car la capacité d&#39;excursion et la disponibilité de mise à niveau changent en permanence.
- [!DNL Journey Optimizer] personnalisation doit tenir compte du nombre de voyageurs dans la réservation, en recommandant des excursions adaptées à la famille pour les réservations en famille et des expériences orientées vers les couples pour les réservations à deux personnes.


## Campagnes de reconquête pour les clients obsolètes

Identifiez les clients qui n’ont pas réservé depuis douze mois ou plus et faites-les participer avec des offres de reconquête personnalisées et du contenu basé sur leurs préférences de voyage passées. Réengager les clients périmés est beaucoup plus rentable que d&#39;acquérir de nouveaux clients, et les anciens voyageurs ont déjà une familiarité avec la marque qui réduit l&#39;obstacle à la reréservation.

### Impact commercial

Des campagnes de reconquête bien ciblées permettent d’obtenir des taux de réactivation significatifs parmi les clients obsolètes, en récupérant les recettes des clients qui, autrement, ne reviendraient jamais.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Ce parcours en plusieurs étapes réengage les clients obsolètes avec une série progressive de messages qui évoluent de l’inspiration à l’incitation en fonction de la réponse du client. Il s’agit du bon modèle lorsqu’il n’y a pas d’événement déclencheur distinct et que le timing doit être calculé à partir des modèles de cycle de vie du client et des modèles de réservation saisonniers. Les messages déclenchés par un événement ne peuvent pas gérer la logique d’escalade progressive ni la nécessité de chronométrer les offres autour des fenêtres de planification de voyage standard.

### Considérations techniques

- La segmentation des clients obsolète doit tenir compte de la fréquence de réservation type dans la catégorie de voyage. Un client qui effectue des réservations annuelles ne doit pas être marqué comme obsolète après seulement six mois d&#39;inactivité.
- Le contenu de reconquête doit faire référence aux préférences de voyage passées du client, telles que les destinations préférées, les types de cabines ou les saisons de voyage, afin de démontrer que la marque s’en souvient et les apprécie.
- Les offres doivent passer à l&#39;échelle du parcours, en commençant par un contenu inspirant et en progressant vers des incitations monétaires uniquement si les messages précédents ne génèrent pas d&#39;engagement.
- Les enregistrements des clients doivent être vérifiés par rapport au système de réservation pour toutes les réservations effectuées par le biais de canaux hors ligne tels que les agents de voyage ou les centres d’appels afin d’éviter d’envoyer des messages de reconquête aux clients qui sont réellement actifs.


## Recommandations d’itinéraires dynamiques

Affichez les itinéraires et les destinations de croisière personnalisés en fonction des réservations passées, de l’historique de navigation et des préférences déclarées du client. Lorsque les voyageurs voient des itinéraires adaptés à leurs intérêts et à leur style de voyage, ils s&#39;engagent plus profondément dans l&#39;expérience de planification et procèdent plus rapidement à la réservation.

### Impact commercial

Les recommandations d’itinéraire personnalisées améliorent l’engagement des clients grâce à des pages d’itinéraire, ce qui les aide à trouver plus rapidement le bon voyage et à réduire le taux de chute qui se produit lorsque les voyageurs se sentent dépassés par un trop grand nombre d’options.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Cette approche personnalise le contenu du site web pour les visiteurs identifiés, en utilisant leurs données de profil et leur historique comportemental pour faire apparaître les itinéraires et destinations les plus pertinents. Il s’agit du modèle approprié lorsque la personnalisation est pilotée par les attributs de profil et l’historique de réservation plutôt que par un modèle d’affinité comportementale, ce qui permet à la logique basée sur des règles de tenir compte de la logistique des voyages, telle que les ports de départ et les dates, parallèlement aux préférences des clients.

### Considérations techniques

- La logique de recommandation d&#39;itinéraire doit intégrer les dates de navigation ou de séjour, les ports de départ et les préférences de durée ainsi que l&#39;intérêt de destination afin de présenter des options à la fois attrayantes et pratiques pour le client.
- L&#39;intégration avec le système central de réservation garantit que les itinéraires recommandés disposent de stocks disponibles et reflètent les prix actuels, empêchant la frustration de promouvoir les trajets à guichet fermé ou les propriétés entièrement réservées.
- Les facteurs saisonniers devraient fortement influencer les recommandations ; les clients qui ont déjà réservé des croisières d&#39;été en Méditerranée devraient voir des options saisonnières similaires plutôt que des alternatives hors saison.
- Les politiques de fusion de profils [!DNL Experience Platform] doivent correctement unifier le comportement de navigation de plusieurs appareils afin que les recherches menées sur les appareils mobiles soient reflétées dans les recommandations sur les ordinateurs de bureau.


## Produits récemment consultés sur la page d&#39;accueil

Affichez les croisières, les hôtels ou les destinations récemment consultés sur la page d’accueil pour rappeler aux visiteurs leur intérêt et encourager les visites récurrentes. Les voyageurs font souvent des recherches au cours de plusieurs sessions avant de réserver, et l’affichage de leurs centres d’intérêt précédents élimine les frictions liées au fait de recommencer leur recherche à chaque retour.

### Impact commercial

L’affichage des produits de voyage récemment consultés sur la page d’accueil accroît l’engagement des visites récurrentes, ce qui permet aux clients de reprendre là où ils en étaient et raccourcit le chemin de la réservation.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md). Cette approche utilise les données de profil stockées du visiteur pour effectuer le rendu des éléments précédemment consultés sur la page d’accueil, créant ainsi une continuité entre les sessions de navigation. Il s’agit du modèle approprié lorsque la personnalisation repose sur des données de profil persistantes entre les sessions et les appareils plutôt que sur une affinité comportementale en temps réel, et lorsque les règles de pertinence sont basées sur le temps (récence) plutôt que sur un classement algorithmique.

### Considérations techniques

- Les données récemment consultées doivent persister sur les appareils et les sessions à l’aide de la résolution d’identité, de sorte qu’un client qui navigue sur son téléphone voit les mêmes éléments lorsqu’il revient sur un bureau.
- Les articles affichés doivent afficher le statut actuel de la tarification et de la disponibilité, avec des indicateurs clairs si une option précédemment consultée n’est plus disponible ou si le prix a changé depuis la dernière visite.
- La fenêtre de récence pour les articles affichés doit être adaptée aux cycles de réservation de voyage ; montrer une croisière consultée il y a trois mois peut encore être pertinent, contrairement à un produit de vente au détail consulté il y a si longtemps.
- Pour des raisons de confidentialité, le contenu récemment consulté doit être lié au statut de consentement du client. De plus, une option permettant d’effacer l’historique de navigation doit être facilement accessible.


## Boîte de dialogue modale d’intention de sortie avec les offres ciblées

Lorsqu’un visiteur affiche son intention de sortie, affichez une fenêtre modale personnalisée avec des offres pertinentes en fonction de son comportement de navigation au cours de la session. Attraper un visiteur au départ avec une offre attrayante et pertinente du point de vue contextuel fournit une dernière occasion de convertir l’intérêt en une réservation avant son départ.

### Impact commercial

Les modèles d’intention de sortie avec des offres de voyage personnalisées récupèrent des conversions significatives parmi les visiteurs qui quitteraient autrement sans réserver, capturant des recettes qui seraient entièrement perdues.

### Mise en œuvre

Utilisez le modèle [&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Cette approche utilise une logique de décision centralisée pour évaluer toutes les offres disponibles et sélectionner la plus pertinente pour le visiteur sortant en fonction du comportement de sa session et des données de profil. Il s’agit du modèle approprié lorsque la sélection des offres doit tenir compte de l’éligibilité du niveau de fidélité et des contraintes commerciales autour du capping de la fréquence, contraintes qui nécessitent une logique de prise de décision régie plutôt qu’une simple recommandation comportementale ou un message déclenché unique.

### Considérations techniques

- La détection de l’intention de sortie sur les sites de réservation de voyages doit tenir compte du comportement de navigation à plusieurs onglets, car les voyageurs ouvrent fréquemment plusieurs itinéraires ou propriétés dans des onglets distincts sans avoir réellement l’intention de partir.
- La sélection d’offres doit refléter ce que le visiteur a parcouru au cours de sa session, en présentant une remise sur la destination ou la propriété spécifique qu’il a explorée plutôt qu’une promotion générique.
- La fréquence modale doit être strictement limitée pour empêcher les visiteurs de voir la même offre à chaque visite, ce qui érode l’urgence et l’exclusivité perçue de la promotion.
- [!DNL Journey Optimizer] règles d’éligibilité de l’offre doivent tenir compte du niveau de fidélité du visiteur et de son historique de réservation pour présenter des incentives valorisés de manière appropriée, offrant aux clients premium des avantages significatifs plutôt que de petites remises.


## Personalization du programme de fidélité

Personnalisez l’expérience, les offres et les communications du site web en fonction du niveau de fidélité, de l’équilibre des points et de l’historique d’engagement du client. Les membres du programme de fidélité qui voient leur statut reflété à chaque point de contact se sentent reconnus et valorisés, ce qui renforce leur engagement envers la marque et encourage l’avancement de niveau.

### Impact commercial

La personnalisation basée sur les niveaux entraîne une amélioration de l’engagement des membres fidèles, un approfondissement de la relation et une accélération des comportements de rémunération et de remboursement qui soutiennent le chiffre d’affaires à long terme.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision[&#128279;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). Cette approche associe l’orchestration des parcours à la prise de décision en temps réel afin de diffuser la bonne offre par le bon canal pour chaque membre du programme de fidélité, en s’adaptant à son niveau, à ses préférences et à son activité récente. Il s’agit du modèle approprié lorsque le parcours doit coordonner la diffusion entre les canaux pour éviter les offres en double et lorsque la sélection des offres nécessite des règles d’éligibilité et des contraintes de remboursement basées sur le niveau - l’orchestration des parcours seule ne fournit pas la couche de prise de décision multicanal nécessaire.

### Considérations techniques

- Les données du programme de fidélité, notamment le statut du niveau, les soldes de points et l’historique des gains, doivent être ingérées et tenues à jour pour s’assurer que la personnalisation et les offres du site web reflètent la réputation réelle du client.
- Les avantages propres à chaque niveau, tels que l’accès anticipé aux réservations, les mises à niveau gratuites et les tarifs exclusifs, doivent être appliqués au moment du remboursement, ce qui nécessite une intégration étroite avec les systèmes de réservation et de tarification.
- Les modifications du solde de points des réservations, des séjours et des transactions de partenaire doivent déclencher le recalcul des règles de personnalisation en temps quasi réel, de sorte qu’un client qui vient de gagner suffisamment de points pour une récompense voit immédiatement cette option.
- Les audiences [!DNL Real-Time Customer Data Platform] doivent être structurées autour des niveaux de fidélité et des jalons d’engagement clés, tels que l’approche du niveau suivant ou le risque de rétrogradation.


## Rappels de réservation multicanaux

Envoyez des rappels de réservation personnalisés par e-mail, SMS et notifications push aux clients qui ont commencé mais n’ont pas terminé leurs réservations. Les voyageurs commencent fréquemment le processus de réservation et sont interrompus, et le fait de les joindre par l&#39;intermédiaire de leurs canaux préférés avec un rappel et les détails de leur voyage enregistré les ramène à effectuer la réservation.

### Impact commercial

Les rappels de réservation multicanaux améliorent les taux d’achèvement des réservations, récupérant un chiffre d’affaires important des clients qui avaient l’intention de réserver, mais ont été laissés de côté avant de terminer.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Cette approche déclenche automatiquement des rappels lorsqu’un événement de réservation incomplet est détecté, fournissant des messages opportuns sur les canaux préférés du client. Il s’agit du modèle approprié lorsque le déclencheur est une action client discrète (qui commence une réservation) et que la réponse requise est une diffusion sensible au temps sur les canaux préférés, plutôt qu’une séquence à plusieurs étapes où chaque message dépend de l’engagement précédent ou des modifications de disponibilité.

### Considérations techniques

- La logique de sélection de canal doit respecter les préférences de communication des clients et optimiser la diffusion en fonction des schémas d’engagement passés, en envoyant des notifications push aux clients qui répondent bien aux communications mobiles et des e-mails à ceux qui la préfèrent.
- Le contenu du rappel doit inclure un lien profond qui ramène directement le client à sa réservation enregistrée avec toutes les sélections intactes, éliminant la friction liée à la saisie de nouvelles dates de voyage, préférences de chambre et détails du client.
- Les règles de minutage et de fréquence doivent être coordonnées entre les canaux pour éviter de surcharger le client ; un e-mail et une notification push sur la même réservation doivent être espacés de manière appropriée plutôt qu&#39;envoyés simultanément.
- L&#39;intégration avec la gestion des biens immobiliers ou le système central de réservation doit vérifier que le type de chambre, le taux et les dates sélectionnés à l&#39;origine sont toujours disponibles avant d&#39;envoyer le rappel, en mettant à jour le message si la disponibilité a changé.


## Personalization de campagne saisonnière

Personnalisez les campagnes et les offres en fonction des préférences saisonnières, des réservations saisonnières antérieures et des tendances saisonnières actuelles. Les voyageurs sont très influencés par les saisons, et les campagnes qui correspondent à leurs intérêts saisonniers avérés et aux tendances actuelles en matière de voyage sont beaucoup plus attrayantes que les promotions génériques.

### Impact commercial

Les campagnes personnalisées selon les saisons augmentent la conversion des réservations saisonnières, ce qui garantit que l’investissement marketing est concentré sur les destinations et les produits de voyage les plus susceptibles de trouver un écho auprès de chaque client.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Cette approche diffuse des messages de campagne saisonniers personnalisés à de grandes audiences selon un calendrier précis, en segmentant les clients selon leurs modèles de voyage saisonniers et leurs préférences. Il s’agit du modèle approprié lorsque l’audience est volumineuse et prédéfinie par l’historique des réservations saisonnières, que le moment de la diffusion est planifié en fonction des fenêtres de planification saisonnière plutôt que selon l’événement et qu’aucune ramification ou prise de décision en temps réel n’est nécessaire.

### Considérations techniques

- Les profils des préférences saisonnières des clients doivent être créés à partir de données de réservation historiques, en identifiant des modèles tels que des vacances à la plage en été cohérentes ou des randonnées à ski en hiver pour informer le ciblage de la campagne.
- La planification de la campagne doit tenir compte des délais de l&#39;industrie du voyage ; les campagnes de vacances d&#39;été devraient être lancées au début du printemps lorsque les familles planifient, et non en juin lorsque la plupart des réservations sont déjà effectuées.
- Les prix et les flux de disponibilité pour les stocks saisonniers doivent être intégrés de sorte que les offres promotionnelles reflètent les taux en temps réel et la disponibilité réelle des chambres ou des cabines pendant les périodes de voyage en question.
- [!DNL Experience Platform] audiences doivent combiner les données de préférences saisonnières avec les indicateurs de récence pour donner la priorité aux clients qui se trouvent dans leur fenêtre de planification habituelle pour la saison à venir.


## Recommandations de réservation de groupe

Identifiez les clients qui réservent fréquemment des voyages de groupe et recommandez de manière proactive des forfaits de groupe, des options adaptées aux familles ou des réservations de plusieurs chambres. Les réservations de groupe représentent un chiffre d’affaires nettement plus élevé par transaction, et les clients ayant démontré un modèle de voyage de groupe réagissent bien aux options sélectionnées qui simplifient le processus de planification.

### Impact commercial

Les recommandations proactives en matière de réservation de groupe augmentent la valeur moyenne des commandes par réservation, capturant ainsi la valeur totale des transactions de voyage de groupe qui pourraient autrement être fractionnées entre plusieurs réservations individuelles.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Cette approche utilise des modèles pilotés par l’IA qui tirent des enseignements des modèles et des comportements de réservation des clients pour recommander les options de voyage de groupe les plus pertinentes pour chaque client. Il s’agit du bon modèle lorsque l’ensemble d’articles est volumineux et change en permanence (les offres groupées évoluent avec les prix et la disponibilité) et que la sélection est déterminée par les modèles comportementaux de l’historique de réservation de groupe plutôt que par un ensemble limité d’offres régies par des règles d’éligibilité.

### Considérations techniques

- L&#39;identification des voyages de groupe nécessite l&#39;analyse de l&#39;historique des réservations pour des modèles tels que les réservations multi-chambres, les réservations avec plusieurs passagers et les réservations coordonnées faites à peu près pour les mêmes dates et destinations.
- Le prix du forfait de groupe doit être extrait du système de réservation de manière dynamique, car les tarifs de groupe diffèrent souvent des tarifs individuels et peuvent nécessiter des tailles de partie minimales ou des fenêtres de réservation anticipée.
- Le contenu de la recommandation doit répondre aux besoins uniques des organisateurs de groupes, y compris des informations sur les options de repas de groupe, les espaces de réunion, les réductions pour les réservations en bloc et la disponibilité des excursions de groupe.
- L’enrichissement du profil [!DNL Real-Time Customer Data Platform] doit signaler les clients comme organisateurs de voyages de groupe en fonction de leurs modèles de réservation, ce qui permet des campagnes ciblées pendant les périodes de planification de groupe de pointe, telles que la saison des réunions de famille ou les périodes de retraite d’entreprise.


## Concierge de réservation IA

Les agences de voyage et d’accueil proposent des parcours d’achat complexes et à haute considération dans lesquels les clients doivent naviguer entre les vols, les chambres, les catégories de chambres, les services auxiliaires et les avantages de fidélité avant de s’engager à réserver. Les interfaces statiques de navigation et de filtrage entraînent une lassitude des décisions et une augmentation des abandons. Un concierge de réservation d&#39;IA engage les clients dans une conversation naturelle pour comprendre leur intention de voyage, la taille de leur fête, leurs préférences et leur budget, puis les guide pas à pas à travers la planification de leur itinéraire, la sélection de leur hébergement et les options de module complémentaire, tout en explorant les avantages de fidélité pertinents pour le niveau du client.

### Impact commercial

Les conseils de réservation par conversation améliorent les taux d&#39;achèvement de l&#39;itinéraire et les pièces jointes accessoires, tout en réduisant le volume du centre d&#39;appels pour les invités qui autrement téléphoneraient pour clarifier les options.

### Mise en œuvre

Utilisez le modèle [Expérience de conversation &#x200B;](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md). Cette approche déploie le Product Advisor Agent par rapport au catalogue de propriétés et d’itinéraires, en utilisant AEP Agent Orchestrator et les données de profil client en temps réel pour faire apparaître des options personnalisées et des recommandations relatives à la fidélité par le biais d’une boîte de dialogue guidée multi-tour. Il s’agit du modèle approprié lorsque l’objectif est une découverte conversationnelle interactive à plusieurs tours qui s’oriente vers une décision de réservation complexe, distincte des messages déclenchés par un événement, qui réagissent aux actions discrètes des voyageurs par une sensibilisation unidirectionnelle, et des expériences web personnalisées, qui font apparaître des recommandations passivement sans impliquer le client dans le dialogue. Cela nécessite une configuration d’AEP Agent Orchestrator et de la gouvernance de marque.

### Considérations techniques

- Les données relatives à la disponibilité et aux tarifs doivent être tenues à jour grâce à une intégration en temps quasi réel entre le système de réservation et la couche de contenu Brand Concierge, car recommander des types de chambres indisponibles ou un prix incorrect dans une conversation érode immédiatement la confiance.
- La recherche du profil client en temps réel doit faire apparaître le niveau de fidélité, l’historique des séjours et les préférences déclarées afin que l’agent puisse reconnaître de manière proactive le statut du client ou de la cliente et personnaliser les recommandations sans exiger que le client ou la cliente réexplique ses préférences à chaque visite.
- La gouvernance de la marque doit définir comment l’agent gère les demandes de correspondance de tarifs, les références de concurrents et les situations où les dates ou le type de chambre préférés de l’invité ne sont pas disponibles, en s’assurant que l’agent répond de manière élégante au sein de la voix de la marque plutôt que de présenter une impasse.
- Les signaux d’intention de conversation (notamment l’intérêt de la destination, la composition des parties de voyage et les préférences accessoires exprimées au cours du dialogue) doivent remonter à AEP en tant que données ExperienceEvent, afin d’enrichir les profils des invités pour informer les campagnes par e-mail, de fidélité et de réengagement en aval.

## Campagnes d’anniversaire pour les invités

Ciblez les invités le jour de leur anniversaire avec un message d’anniversaire personnalisé et une offre exclusive. Les campagnes d&#39;anniversaire renforcent les relations avec les invités en reconnaissant un jalon personnel et en encourageant une réservation ou une visite de célébration.

### Impact commercial

Les messages d’anniversaire créent un point de contact émotionnel qui différencie la marque et entraîne des réservations incrémentielles, car les clients sont plus susceptibles de planifier une escapade ou une expérience culinaire autour de leur anniversaire lorsqu’ils reçoivent une offre attrayante et personnalisée.

### Mise en œuvre

Utilisez le modèle [Message d’anniversaire déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour envoyer un message d’anniversaire personnalisé et une offre lorsque la date d’anniversaire de l’invité arrive. Il s’agit du modèle approprié lorsqu’un seul message piloté par un événement est envoyé en fonction d’un déclencheur de date d’attribut de profil.

### Considérations techniques

- La date d’anniversaire doit être capturée dans le profil de l’invité et validée afin d’éviter d’envoyer des messages à des dates incorrectes.
- Les offres doivent avoir une période de validité définie (par exemple, le mois de l’anniversaire) afin de donner aux clients un temps raisonnable pour planifier et réserver un séjour ou une expérience.
- Les invités qui n&#39;ont pas d&#39;anniversaire dans leur dossier doivent être exclus de la campagne plutôt que d&#39;envoyer un message générique.
- La personnalisation de l’offre doit tenir compte des préférences de réservation passées (destination, type de propriété, catégorie de chambre) pour présenter des suggestions pertinentes.

## Campagnes de promotion de destination

Ciblez les invités à effectuer une réservation pendant une promotion de destination de voyage en cours. Les promotions de destination stimulent les réservations en mettant en relation les voyageurs avec des offres opportunes pour des destinations promues alignées sur leurs intérêts.

### Impact commercial

Les promotions de destination ciblées améliorent la conversion des réservations en atteignant les voyageurs les plus susceptibles d’être intéressés en fonction de leurs antécédents de voyage et de leurs préférences déclarées, ce qui réduit le gaspillage promotionnel et améliore le retour sur investissement de la campagne.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pour envoyer des messages promotionnels à des segments d’audience qualifiés pendant les fenêtres de campagne de destination actives. Il s’agit du modèle approprié lorsqu’un lot planifié de messages promotionnels personnalisés doit atteindre une audience définie au cours d’une campagne limitée dans le temps.

### Considérations techniques

- Les dates de début et de fin de la promotion doivent être gérées pour vous assurer que les messages ne sont envoyés que pendant la fenêtre de promotion active.
- La segmentation de l’audience doit tirer parti de l’historique de réservation, du comportement de navigation et de l’affinité de destination passés pour cibler les invités les plus susceptibles d’interagir avec la destination promue.
- Les clients qui ont déjà réservé pour la destination et les dates de voyage promues doivent être supprimés des messages d’acquisition.
