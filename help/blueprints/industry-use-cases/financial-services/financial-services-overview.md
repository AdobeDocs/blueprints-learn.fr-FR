---
title: Cas d’utilisation des services financiers
description: Découvrez comment les entreprises de services financiers utilisent Adobe Experience Platform pour personnaliser les offres de produits, empêcher l’attrition et approfondir les relations client.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2209'
ht-degree: 1%

---


# Cas d’utilisation des services financiers

Les sociétés de services financiers s’appuient sur Adobe Experience Platform pour unifier les données clients sur les canaux bancaires, de prêt et d’investissement, ce qui permet des expériences personnalisées qui renforcent les relations et stimulent la croissance. En associant l’activité du compte, l’historique des transactions et les signaux comportementaux, ces organisations peuvent proposer la bonne offre au bon moment, tout en maintenant la confiance et la conformité attendues de leurs clients.

## Formation de leads à haute valeur ajoutée

Identifiez les prospects à forte valeur ajoutée en fonction des données de profil et du comportement, puis nourrissez-les avec du contenu et des offres personnalisés grâce à des parcours automatisés. En combinant les détails démographiques, l’activité de navigation et les signaux d’engagement, les institutions financières peuvent prioriser les prospects les plus susceptibles de convertir leurs clients et les guider sur un chemin personnalisé vers leur clientèle.

### Impact commercial

Les entreprises qui mettent en œuvre des méthodes d’entretien du prospect à forte valeur ajoutée constatent généralement une augmentation de 25 à 35 % des taux de conversion du prospect vers le client, tout en créant un pipeline de ventes plus sain et plus prévisible.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer des séquences de maturation automatisées qui s’adaptent en fonction de l’engagement des prospects et des signaux de préparation.

### Considérations techniques

- Intégrez les données de score de prospect CRM et les événements comportementaux du site web dans des profils de prospects unifiés pour alimenter la logique d’entrée et de branchement du parcours.
- Assurez-vous que les préférences de consentement et d’opt-in sont appliquées à chaque point de contact, en particulier pour les communications par téléphone et par e-mail, régies par les réglementations du marketing financier.
- Configurez la limitation du parcours pour éviter de surcharger les prospects avec plusieurs communications pendant de courtes fenêtres d’évaluation.
- Tenez compte de la latence des données entre les interactions des succursales ou des conseillers et de l’engagement numérique pour maintenir la pertinence des messages de soutien.


## Recommandations de produits pour les clients existants

Recommander des produits financiers pertinents tels que des cartes de crédit, des prêts et des produits d&#39;investissement aux clients existants en fonction de leur profil, de leur historique de transactions et de leur stade de vie. Ce cas d’utilisation transforme les données de compte quotidiennes en informations exploitables qui permettent de trouver le meilleur produit pour chaque client.

### Impact commercial

Les recommandations de produits personnalisées entraînent une augmentation de 20 à 30 % des taux d’adoption des produits et augmentent de manière mesurable la valeur de la durée de vie du client en approfondissant le partage du portefeuille.

### Mise en œuvre

Utilisez le modèle [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pour évaluer en temps réel chaque client par rapport aux offres de produits éligibles, en classant les recommandations par pertinence et priorité commerciale.

### Considérations techniques

- Regroupez les données de transaction, les soldes de compte et les portefeuilles de produits en un seul profil client afin que les modèles de prise de décision aient une vue complète des relations existantes.
- Appliquez les règles d&#39;adéquation financière et les contraintes d&#39;éligibilité réglementaires en tant que mécanismes de sécurisation stricts dans le moteur de décision avant de classer les offres.
- Coordonner la diffusion des offres sur les canaux banque en ligne, application mobile, e-mail et conseiller pour éviter les recommandations en conflit ou en double.
- Mettez en œuvre un capping de la fréquence par catégorie de produits pour éviter la lassitude face aux recommandations, en particulier pour les produits à forte valeur ajoutée tels que les prêts hypothécaires et les comptes de placement.


## Campagnes de prévention de l’attrition

Identifiez les clients à risque de résiliation à l’aide de la prédiction de résiliation optimisée par l’IA et impliquez-les avec des offres de rétention et des communications personnalisées. La détection précoce des signaux de désengagement permet aux institutions financières d&#39;intervenir avant qu&#39;un client ferme des comptes ou déplace des actifs ailleurs.

### Impact commercial

Les efforts proactifs de prévention de la perte de clientèle réduisent généralement l’attrition de la clientèle de 15 à 25 %, protégeant ainsi les flux de revenus récurrents et réduisant le coût de remplacement des clients.

### Mise en œuvre

Utilisez le modèle [Cross-Channel Parcours with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour déclencher des parcours de rétention lorsque les scores de risque de résiliation dépassent les seuils définis, avec une prise de décision intégrée pour sélectionner l’offre de rétention la plus attrayante.

### Considérations techniques

- Intégrez les tendances d’activité des comptes, l’historique des interactions de services et la fréquence d’engagement dans [!DNL Customer AI] modèles de propension à l’attrition pour générer des scores de risque.
- Définissez des seuils de risque de résiliation spécifiques aux lignes de produits, les signaux de désengagement pour les comptes de contrôle étant différents de ceux des portefeuilles d’investissement.
- Veiller à ce que les offres de fidélisation soient conformes aux réglementations en matière de prêt équitable et d’égalité de traitement afin que les segments à haut risque bénéficient d’un traitement équitable.
- Développez une logique de suppression afin d’exclure les clients qui se désinscrivent en raison de fraudes ou de mesures de conformité, où la sensibilisation à la rétention serait inappropriée.


## Tableau de bord du compte personnalisé

Personnalisez le tableau de bord des services bancaires en ligne et l’expérience de l’application mobile en fonction de l’activité du compte, des préférences et des objectifs financiers de chaque client. Un tableau de bord personnalisé aide les clients à trouver ce qui compte le plus et affiche les informations pertinentes sans qu’ils aient à effectuer de recherches.

### Impact commercial

Les tableaux de bord personnalisés augmentent les taux d’engagement de 30 à 40 % et améliorent de manière significative les scores de satisfaction client en donnant aux services bancaires numériques un aspect intuitif et pertinent.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pour diffuser des blocs de contenu personnalisés en temps réel, des spots sur les produits et des informations financières dans des expériences digitales authentifiées.

### Considérations techniques

- Tirez parti des [!DNL Edge Network] pour les décisions de personnalisation de moins d’une seconde dans les sessions bancaires authentifiées où la latence affecte directement l’expérience utilisateur.
- Agrégez les données de transaction en attributs de profil précalculés, tels que les catégories de dépenses et les tendances d’épargne, afin d’éviter le calcul en temps réel de jeux de données volumineux.
- Respectez les normes d’accessibilité et assurez-vous que le contenu personnalisé répond aux mêmes exigences réglementaires de divulgation que le contenu statique.
- Coordonnez la logique de personnalisation entre les canaux web et mobiles afin que les clients bénéficient d’une expérience cohérente, quel que soit l’appareil.


## Offres De Produits Basées Sur Les Étapes De Vie

Identifiez les clients qui entrent dans de nouvelles étapes de la vie, comme le mariage, l&#39;achat d&#39;une maison ou la retraite, et proposez de façon proactive des produits et services financiers pertinents. L&#39;anticipation de ces jalons permet aux établissements de se positionner en tant que partenaires de confiance lors de moments financiers cruciaux.

### Impact commercial

Les offres déclenchées par les étapes de la vie atteignent un taux d’adoption du produit de 35 à 45 %, dépassant considérablement les campagnes génériques, tout en renforçant les relations client à long terme.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour détecter les indicateurs d’étape de vie et orchestrer des parcours multi-touch avec une sélection d’offres incorporée adaptée à chaque jalon.

### Considérations techniques

- Combinez des signaux propriétaires tels que les changements d’adresse, les ouvertures de compte conjointes et les dépôts importants avec des données tierces autorisées pour déduire les transitions d’étape de vie.
- Gérez les événements personnels sensibles avec soin dans le ton et la fréquence des messages, car des jalons déduits de manière incorrecte peuvent éroder la confiance.
- Appliquez des contrôles d’adéquation réglementaire à Offer Decisioning afin que les produits recommandés s’alignent sur la situation financière vérifiée du client.
- Établissez des périodes de réflexion entre les campagnes d’étape de vie afin d’éviter le chevauchement des activités de sensibilisation lorsque plusieurs indicateurs se déclenchent dans une courte fenêtre.


## Alertes et recommandations basées sur les transactions

Envoyez des alertes en temps réel pour les transactions et fournissez des recommandations personnalisées basées sur les modèles de dépense et l’activité du compte. Des notifications opportunes et pertinentes permettent aux clients d’être informés et créent des moments naturels pour faire apparaître des conseils financiers utiles.

### Impact commercial

Les alertes basées sur les transactions atteignent un taux d’engagement de 50 à 60 %, ce qui améliore considérablement la sensibilisation à la sécurité et crée des points de contact à forte valeur ajoutée pour des recommandations personnalisées.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour répondre aux événements de transaction en temps réel avec des alertes et des recommandations pertinentes du point de vue contextuel.

### Considérations techniques

- Ingérez des événements de transaction par le biais d’un pipeline de diffusion en continu avec des exigences de diffusion à faible latence, car les alertes de sécurité perdent de la valeur si elles sont retardées de plus de quelques minutes.
- Appliquez les préférences et les seuils d’alerte définis par le client ou la cliente afin que les notifications reflètent des paramètres individuels plutôt que des règles uniformes.
- Séparez les alertes de sécurité obligatoires des messages de recommandation facultatifs dans l&#39;architecture de messagerie pour vous assurer que les notifications de conformité ne sont jamais supprimées.
- Tenez compte des volumes de transactions élevés pendant les périodes de pointe, telles que les jours de paie et les jours fériés, en concevant une capacité de débit qui évolue en fonction de la demande.


## Récupération de la demande d&#39;abandon de carte de crédit

Identifiez les clients qui ont commencé mais n’ont pas terminé leurs demandes de carte de crédit et réengagez-les avec des messages et des offres personnalisés. L’abandon d’une application représente une audience à forte intention qui n’a souvent besoin que d’un petit coup de pouce pour terminer le processus.

### Impact commercial

Les campagnes de récupération des abandons améliorent les taux d’achèvement des applications de 20 à 30 %, augmentant directement l’acquisition de nouveaux comptes auprès d’une audience qui a déjà exprimé son intérêt.

### Mise en œuvre

Utilisez le modèle [Messagerie déclenchée par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour détecter les événements d’abandon d’application et déclencher des messages de suivi opportuns qui répondent aux raisons courantes de déperdition.

### Considérations techniques

- Capturez l’étape spécifique à laquelle l’application a été abandonnée afin d’adapter la messagerie, car une personne qui a déposé son dossier lors de la vérification d’identité a besoin d’une assurance différente de celle qui a quitté lors de la révision des conditions.
- Respectez les réglementations de marketing du crédit, y compris les informations requises et les règles de prêt équitables dans toutes les communications de recouvrement.
- Implémentez une logique de décroissance temporelle afin que la diffusion de la récupération s’arrête après une fenêtre définie, car les données obsolètes de l’application peuvent ne plus être valides pour la préqualification.
- Coordonnez-vous avec le système d’application afin de supprimer les messages de récupération pour les candidats qui ont répondu via un autre canal, tel qu’une visite de filiale ou un appel téléphonique.


## Recommandations relatives à Investment Portfolio

Fournir des recommandations d&#39;investissement personnalisées basées sur le profil de risque, l&#39;historique d&#39;investissement et les objectifs financiers de chaque client. Les conseils de portefeuille axés sur les données aident les clients à prendre des décisions éclairées tout en approfondissant leur engagement auprès des services de gestion de patrimoine.

### Impact commercial

Les recommandations d’investissement personnalisées augmentent de 25 à 35 % l’adoption des produits d’investissement et améliorent la diversification du portefeuille au sein de la clientèle.

### Mise en œuvre

Utilisez le modèle [Recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) pour analyser le comportement et les préférences en matière d’investissement, puis obtenez des recommandations de portefeuille pertinentes par le biais de canaux numériques et d’outils de conseil.

### Considérations techniques

- Intégrez les flux de données de courtage et de conservation pour maintenir une vue précise et à jour des avoirs et de l&#39;allocation actuels de chaque client.
- Faites respecter les exigences de conformité exigées par les réglementations sur les valeurs mobilières afin que les recommandations s&#39;alignent sur les objectifs documentés de tolérance au risque et d&#39;investissement du client.
- Clairement étiqueter le contenu d&#39;investissement personnalisé comme étant éducatif ou informatif si nécessaire, en le distinguant des conseils d&#39;investissement officiels assortis d&#39;obligations fiduciaires.
- Actualisez régulièrement les modèles de recommandation pour tenir compte des fluctuations du marché, de la dérive du portefeuille et des changements dans les objectifs des clients.


## Personalization d’alerte de fraude

Personnalisez les alertes de fraude et les communications de sécurité en fonction des préférences de communication de chaque client et de son historique d’interactions. Les alertes personnalisées augmentent la probabilité que les clients remarquent, comprennent et agissent sur les notifications de sécurité critiques.

### Impact commercial

Les alertes de fraude personnalisées améliorent les taux de réponse des alertes de 40 à 50 %, ce qui renforce considérablement la conformité en matière de sécurité et réduit la fenêtre d’exposition lors d’activités suspectes.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour diffuser des alertes de fraude par le canal préféré de chaque client avec des détails contextuels qui facilitent la confirmation ou le litige d’activité.

### Considérations techniques

- Privilégiez la vitesse de livraison et la fiabilité avant toute autre considération de conception, car la latence des alertes de fraude est directement corrélée à l&#39;exposition aux pertes financières.
- Acheminez les alertes via le canal préféré vérifié du client tout en conservant les canaux de secours pour assurer la diffusion même en cas d’échec du canal principal.
- Conservez l’historique des interactions d’alerte pour améliorer la pertinence des alertes futures et réduire la fatigue des faux positifs pour les clients qui voyagent fréquemment ou effectuent des achats atypiques.
- Assurez-vous que tous les contenus et workflows d’alerte de fraude sont conformes aux réglementations de sécurité bancaire et n’exposent pas les détails de comptes sensibles dans les prévisualisations de messages ou les objets.


## Engagement du programme de fidélité

Personnalisez les communications, les récompenses et les offres du programme de fidélité en fonction du niveau, du solde de points et de l’historique de remboursement de chaque client. Des communications de fidélité pertinentes et opportunes maintiennent l’engagement des membres et favorisent une plus grande participation au programme.

### Impact commercial

L’engagement de fidélité personnalisé augmente la participation au programme de 30 à 40 % et entraîne un taux de remboursement des points sensiblement plus élevé, ce qui renforce la perception de la valeur du programme.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour orchestrer des communications de fidélité sur plusieurs canaux, avec une prise de décision intégrée pour sélectionner la récompense ou l’offre la plus pertinente pour chaque membre.

### Considérations techniques

- Synchronisez les données de la plateforme de fidélité, y compris le statut du niveau, les soldes de points et l’historique des remboursements, dans les profils clients en temps quasi réel afin d’éviter de promouvoir des soldes expirés ou inexacts.
- Logique de parcours de segments par niveau pour offrir des expériences différenciées, car les membres de niveau supérieur s’attendent à un traitement exclusif et à un accès précoce aux promotions.
- Coordonnez les messages de fidélité avec des campagnes marketing plus larges pour éviter la fatigue des messages et les offres conflictuelles entre les programmes.
- Suivez l’attribution du remboursement sur tous les canaux pour mesurer les communications personnalisées qui génèrent le meilleur retour sur investissement du programme.


## Campagnes de pré-approbation de prêt hypothécaire

Ciblez les clients qui sont susceptibles d’être sur le marché d’un prêt hypothécaire en fonction des données de profil, des signaux comportementaux et des indicateurs relatifs au stade de vie. La sensibilisation proactive préalable à l&#39;approbation positionne l&#39;institution comme un premier choix pratique lors de l&#39;une des plus importantes décisions financières qu&#39;un client prendra.

### Impact commercial

Les campagnes ciblées de pré-approbation des prêts hypothécaires augmentent les taux de demande de 20 à 30 % et améliorent le volume des demandes de prêt en atteignant des prospects qualifiés au bon moment.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour guider les prospects hypothécaires à travers une séquence de maturation multi-touch, de la sensibilisation à la pré-approbation, en les adaptant en fonction des signaux d’engagement et de qualification.

### Considérations techniques

- Combinez le comportement de recherche immobilière, les tendances de croissance de l&#39;épargne et les signaux d&#39;expiration de bail pour créer un modèle de propension qui identifie les demandeurs de prêt hypothécaire probables.
- Veiller à ce que tous les messages d&#39;approbation préalable soient conformes aux règlements sur la publicité hypothécaire, y compris les divulgations obligatoires, la précision des taux et la langue de l&#39;habitation.
- Coordonner le timing de la campagne avec les changements de l’environnement des taux afin que les activités de sensibilisation s’alignent sur des conditions d’emprunt favorables et évitent les références de taux obsolètes.
- Créer des workflows de remise aux responsables des prêts afin que les prospects numériquement encouragés passent facilement au processus formel de demande et de souscription.


## Contenu personnalisé d’éducation financière

Diffusez du contenu, des conseils et des ressources personnalisés en matière de formation financière, en fonction du profil financier, des objectifs et des centres d’intérêt de chaque client. Les contenus éducatifs pertinents renforcent la confiance, améliorent la littératie financière et créent des opportunités organiques pour introduire des produits pertinents.

### Impact commercial

Le contenu d’éducation personnalisé augmente les taux d’engagement du contenu de 25 à 35 % et améliore la littératie financière des clients, ce qui permet une adoption plus confiante du produit.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour diffuser une séquence organisée de contenu éducatif sur plusieurs canaux, à l’aide de la prise de décision pour faire correspondre les sujets à la situation financière et aux intérêts de chaque client.

### Considérations techniques

- Associez le contenu éducatif aux attributs de profil financier tels que le ratio d’endettement, le taux d’épargne et l’expérience d’investissement pour garantir la pertinence du sujet.
- Balisez le contenu avec les niveaux de difficulté et les sujets préalables afin de créer des parcours d’apprentissage progressif plutôt que de diffuser des articles ponctuels déconnectés.
- Suivez l’engagement du contenu au niveau du topic pour affiner les modèles de personnalisation et identifier les domaines d’intérêt émergents dans la base de clients.
- Veiller à ce que le contenu éducatif soit clairement distingué du marketing des produits afin de maintenir la conformité réglementaire et de préserver la confiance des clients dans l&#39;objectivité du programme.
