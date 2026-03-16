---
title: Cas D’Utilisation B2B
description: Découvrez comment les entreprises B2B utilisent Adobe Experience Platform pour accélérer le pipeline, améliorer la qualité du prospect et stimuler l’expansion des clients.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2269'
ht-degree: 1%

---


# Cas D’Utilisation B2B

Les organisations business-to-business utilisent Adobe Experience Platform pour unifier les données au niveau du compte et de la personne, ce qui permet aux équipes marketing et commerciales de fournir des expériences coordonnées et pertinentes à chaque étape du parcours d’achat. De l’accélération des pipelines à l’expansion des clients, ces cas d’utilisation montrent comment les équipes B2B transforment des données complexes en résultats commerciaux mesurables.

>[!NOTE]
>
>Pour les plans directeurs d’architecture spécifiques au B2B, y compris l’activation basée sur le compte et la gestion des groupes d’achats, consultez les plans directeurs d’activation et de marketing [B2B](/help/blueprints/b2b/overview.md).

## Account-Based Marketing Personalization

Personnalisez les communications et le contenu marketing pour les comptes cibles en fonction du profil du compte, de l’historique d’engagement et des signaux d’achat. En alignant les messages sur le contexte unique de chaque compte, les équipes marketing peuvent s’affranchir du bruit et impliquer les bonnes parties prenantes avec le contenu approprié.

### Impact commercial

Les entreprises qui mettent en œuvre la personnalisation marketing basée sur les comptes constatent généralement une augmentation de 30 à 40 % du taux d’engagement des comptes, ce qui renforce le pipeline et accélère la progression des affaires.

### Mise en œuvre

Utilisez le modèle [Audience Activation B2B](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md) pour créer des audiences au niveau du compte et activer du contenu personnalisé sur plusieurs canaux. Ce modèle est spécialement conçu pour les stratégies basées sur les comptes, prenant en charge le ciblage au niveau du compte et de la personne.

### Considérations techniques

- Intégrez les données CRM (par exemple, [!DNL Salesforce] ou [!DNL Microsoft Dynamics]) pour tenir à jour les hiérarchies de comptes, les étapes d’opportunité et les affectations de propriété.
- Configurez des schémas de profil au niveau du compte pour capturer des attributs démographiques tels que le secteur, le nombre d’employés, la fourchette de revenus et la pile technologique.
- Mappez les relations personne à compte pour vous assurer que les signaux d’engagement individuels s’affichent au niveau de la notation et de la segmentation au niveau du compte.
- Coordonnez-vous avec [!DNL Marketo Engage] pour aligner les campagnes d’automatisation marketing sur les audiences de compte pilotées par Platform.


## Notation et fidélisation des leads

Notez automatiquement les prospects en fonction des données de profil et du comportement, puis acheminez les prospects à score élevé vers les ventes à l’aide de campagnes d’éducation personnalisées pour d’autres. Cette approche permet aux équipes de vente de se concentrer sur les opportunités les plus prometteuses tandis que le marketing continue de développer des prospects à un stade précoce.

### Impact commercial

Les entreprises qui mettent en œuvre la notation comportementale des prospects et l’automatisation de la maturation obtiennent généralement une augmentation de 25 à 35 % de la conversion du prospect en opportunité, ce qui accélère la vitesse du pipeline et améliore la productivité des ventes.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour concevoir des parcours d’alimentation par embranchement qui répondent aux modifications du score du prospect et aux déclencheurs comportementaux. Ce modèle prend en charge la logique conditionnelle nécessaire pour acheminer les prospects entre les suivis de maturation et les workflows de remise des ventes.

### Considérations techniques

- Établissez une synchronisation CRM bidirectionnelle (par exemple, [!DNL Salesforce] ou [!DNL Microsoft Dynamics]) afin que les scores des prospects et les statuts de qualification restent cohérents entre les systèmes marketing et de vente.
- Définissez les dimensions de score à la fois démographiques (rôle, taille de l’entreprise, secteur) et comportementales (téléchargements de contenu, participation au webinaire, visites de pages de produits).
- Coordonner les modèles de notation des prospects avec les [!DNL Marketo Engage] afin d’éviter les conflits de notes entre les plateformes.
- Définissez des règles d’atténuation du score pour vous assurer que les prospects qui restent inactifs sont déprioritaires au fil du temps.


## Personalization de contenu pour les prospects

Personnalisez le contenu, les ressources et les offres du site web en fonction du secteur, du rôle, de la taille de l’entreprise et de l’historique d’engagement du prospect. Lorsque les prospects voient du contenu correspondant à leur situation spécifique, ils s’engagent plus profondément et se déplacent plus rapidement dans funnel.

### Impact commercial

Les entreprises B2B qui personnalisent des expériences web pour des prospects connus constatent généralement une augmentation de 20 à 30 % de l’engagement envers le contenu, ce qui entraîne un pipeline plus qualifié et des cycles de vente plus courts.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pour offrir des expériences de contenu personnalisées basées sur des profils de prospects unifiés. Ce modèle exploite les données de profil en temps réel pour fournir les ressources, les études de cas et les appels à l’action les plus pertinents pour chaque visiteur.

### Considérations techniques

- Implémentez la résolution d’identité pour faire correspondre le comportement de navigation anonyme aux enregistrements de prospects connus une fois qu’ils s’authentifient ou envoient un formulaire.
- Définissez des règles de personnalisation en fonction des attributs au niveau du compte (secteur, segment, étape de l’affaire), ainsi que des attributs au niveau individuel (rôle, consommation de contenu passée).
- Intégrez à votre système de gestion de contenu pour permuter dynamiquement les bannières principales, les recommandations de ressources et les appels à l’action.
- Assurez-vous [!DNL Marketo Engage] les flux de données de tracking web dans le profil unifié pour obtenir une vue d’ensemble complète du comportement.


## Inscription à un événement et suivi

Automatisez les confirmations d’enregistrement d’événement personnalisées, les rappels et le suivi après l’événement en fonction du type d’événement et du profil du participant. Cela permet aux prospects de rester engagés avant, pendant et après les événements, tout en libérant l’équipe marketing de la coordination manuelle.

### Impact commercial

Les workflows de communication d’événement automatisés et personnalisés entraînent généralement une augmentation de 40 à 50 % de la participation aux événements, maximisant le retour sur investissement de l’événement et renforçant les relations avec les prospects.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour orchestrer le cycle de vie complet de l’événement, depuis l’enregistrement jusqu’à la maturation post-événement. Ce modèle prend en charge les déclencheurs temporels, l’embranchement conditionnel par type d’événement et les séquences de suivi multicanaux.

### Considérations techniques

- Intégrez les données d’inscription des plateformes de webinaires (par exemple, [!DNL ON24], [!DNL Zoom Webinar]) et des systèmes d’événements en personne dans le profil unifié.
- Capturez les signaux d’assiduité et d’engagement (durée de la session, questions posées, réponses à un sondage) pour personnaliser les messages de suivi.
- Coordonnez les parcours d’événement avec les statuts de programme [!DNL Marketo Engage] afin de garantir la cohérence des rapports entre les systèmes.
- Concevez des branches de parcours distinctes pour les déclarants qui ont participé et ceux qui n’y ont pas participé, avec un contenu personnalisé pour chacun.


## Campagnes de conversion d’évaluation de produit

Faites participer les utilisateurs en évaluation avec des recommandations de produits personnalisées, des ressources de formation et des offres pour encourager la conversion vers des forfaits payants. En rencontrant les utilisateurs en évaluation lorsqu’ils sont dans l’exploration de leurs produits, les équipes peuvent supprimer les frictions et accélérer le processus d’achat.

### Impact commercial

Les entreprises qui déploient des campagnes de conversion d’essai personnalisées constatent généralement une augmentation de 25 à 35 % de la conversion d’essai à payé, ce qui a un impact direct sur les nouveaux revenus de l’entreprise et réduit les coûts d’acquisition des clients.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer des parcours de conversion temporels et comportementaux pour les utilisateurs en version d’essai. Ce modèle prend en charge les chemins conditionnels en fonction des jalons d’utilisation du produit, ce qui permet des rebonds ciblés au bon moment.

### Considérations techniques

- Ingérez des données télémétriques d’utilisation du produit (adoption des fonctionnalités, fréquence de connexion, temps passé dans le produit) pour créer des profils d’engagement d’essai en temps réel.
- Définir des jalons basés sur l’utilisation (par exemple, premier projet créé, fonctionnalité clé utilisée, collaboration invitée) comme déclencheurs parcours pour une diffusion en temps opportun.
- Synchronisez le statut d&#39;évaluation et les événements de conversion à [!DNL Salesforce] ou [!DNL Microsoft Dynamics] afin que les représentants commerciaux aient une visibilité complète sur l&#39;activité d&#39;évaluation.
- Assurer la coordination avec les programmes de soutien [!DNL Marketo Engage] afin d&#39;éviter le chevauchement des communications pendant la période d&#39;essai.


## Succès et intégration des clients

Personnalisez les parcours d’intégration des clients avec des formations, des ressources et une assistance pertinentes en fonction du produit acheté et du profil client. L’intégration efficace réduit le délai de rentabilisation et pose les bases d’une rétention et d’une croissance des clients à long terme.

### Impact commercial

Les entreprises qui disposent de programmes d’intégration personnalisés augmentent généralement l’adoption des fonctionnalités de 50 à 60 % au cours des 90 premiers jours, ce qui contribue directement à accroître les recettes liées à la rétention et à l’extension.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour orchestrer des séquences d’intégration adaptées au produit, au niveau de plan et au segment client. Ce modèle prend en charge la progression basée sur des jalons, ce qui garantit que les clients reçoivent les conseils appropriés à chaque étape de leur intégration.

### Considérations techniques

- Ingérez des données télémétriques d’utilisation du produit pour suivre les jalons d’intégration (première connexion, configuration initiale, premier workflow terminé) et déclenchez l’étape de parcours suivante en conséquence.
- Mappez les profils clients au suivi d’intégration correct en fonction du produit acheté, du niveau de plan et du nombre d’utilisateurs sous licence.
- Intégrez les données de la plateforme du succès client pour faire apparaître les scores d’intégrité et signaler les comptes à risque pour une intervention proactive.
- Synchronisez le statut d’intégration et les mesures d’adoption avec [!DNL Salesforce] ou [!DNL Microsoft Dynamics] afin que les responsables du succès client puissent donner la priorité à la sensibilisation.


## Campagnes de renouvellement de contrat

Interagissez de manière proactive avec les clients qui approchent du renouvellement de contrat avec des offres personnalisées, des informations d’utilisation et des incentives de renouvellement. Une campagne de sensibilisation au renouvellement rapide et axée sur les données réduit le taux de perte et protège les revenus récurrents.

### Impact commercial

Les entreprises qui mettent en œuvre des campagnes de renouvellement personnalisées et proactives constatent généralement une augmentation de 30 à 40 % du taux de renouvellement, ce qui permet de protéger les revenus récurrents et de réduire le coût de réacquisition des clients.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour diffuser la bonne offre de renouvellement par le bon canal au bon moment. Ce modèle associe l’orchestration des parcours à Offer Decisioning, ce qui permet des incitations de renouvellement dynamiques basées sur la valeur et l’utilisation du compte.

### Considérations techniques

- Extrayez les dates de fin de contrat, les conditions de renouvellement et la valeur de compte de [!DNL Salesforce] ou [!DNL Microsoft Dynamics] pour déclencher des parcours de renouvellement au moment approprié (par exemple, 90, 60, 30 jours à l&#39;avance).
- Intégrez les données d’utilisation des produits et les scores d’intégrité des clients pour déterminer le risque de renouvellement et adapter la stratégie d’offre en conséquence.
- Utilisez la prise de décision pour sélectionner l’incitation au renouvellement optimale (remise, conditions étendues, mise à niveau Premium) en fonction de la valeur de durée de vie du compte et de la probabilité de résiliation.
- Coordonner la sensibilisation au renouvellement avec les équipes de succès et de ventes des clients pour éviter les messages conflictuels grâce à l’affectation des tâches [!DNL Marketo Engage] et CRM.


## Opportunités de montée en gamme et d’expansion

Identifiez les clients prêts pour les mises à niveau de produits ou les licences supplémentaires en fonction des schémas d’utilisation, des indicateurs de croissance et des données de succès client. La portée de l’extension proactive transforme l’élan client en croissance du chiffre d’affaires.

### Impact commercial

Les entreprises qui identifient et agissent systématiquement sur les signaux d’extension génèrent généralement une augmentation de 20 à 30 % des revenus d’extension, ce qui améliore la rétention des revenus nets et la valeur de la durée de vie du client.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pour proposer des offres de montée en gamme et d’extension personnalisées basées sur l’utilisation en temps réel et les signaux du compte. Ce modèle utilise la prise de décision pour faire correspondre chaque compte à l’offre d’extension la plus pertinente sur l’ensemble des canaux.

### Considérations techniques

- Ingérez des données télémétriques d’utilisation du produit pour détecter des signaux d’extension tels que les seuils d’utilisation des licences, les accès aux fonctionnalités de plafond et le nombre croissant d’utilisateurs.
- Créez des modèles de propension au niveau du compte à l’aide des données d’expansion historiques, des tendances d’utilisation et des attributs micrographiques.
- Synchronisez les opportunités d’extension et les offres recommandées avec [!DNL Salesforce] ou [!DNL Microsoft Dynamics] afin que les équipes commerciales puissent assurer le suivi du pipeline généré par le marketing.
- Coordonnez-vous avec [!DNL Marketo Engage] pour vous assurer que les messages d’extension n’entrent pas en conflit avec les communications d’assistance ou de renouvellement continues.


## Campagnes de remplacement concurrentielles

Ciblez les prospects à l’aide des produits concurrents avec des messages personnalisés, des offres de migration et des comparaisons concurrentielles. En s&#39;attaquant aux problèmes spécifiques associés à chaque concurrent, les équipes marketing peuvent se différencier plus efficacement et accélérer les décisions de changement.

### Impact commercial

Les organisations B2B qui mènent des campagnes de remplacement concurrentielles ciblées obtiennent généralement une augmentation de 15 à 25 % du taux de succès concurrentiel, capturant des parts de marché et déplaçant les fournisseurs existants.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour orchestrer des campagnes concurrentielles multipoint adaptées au profil spécifique du concurrent et du prospect. Ce modèle prend en charge l’embranchement conditionnel basé sur la concurrence identifiée, ce qui permet d’envoyer un message qui résout les problèmes uniques de chaque scénario concurrentiel.

### Considérations techniques

- Intégrez les données de veille concurrentielle (p. ex., fournisseurs de technologie, champs de concurrents CRM) dans le profil unifié pour identifier le concurrent qu&#39;un prospect utilise actuellement.
- Créez des ressources de contenu spécifiques aux concurrents (guides de migration, fiches comparatives, calculateurs de retour sur investissement) et mappez-les à des blocs de contenu parcours.
- Coordonnez-vous avec [!DNL Marketo Engage] pour supprimer les campagnes concurrentielles pour les prospects qui font déjà partie des cycles de vente actifs ou pour les clients existants.
- Suivez le pipeline de déplacement concurrentiel en [!DNL Salesforce] ou en [!DNL Microsoft Dynamics] avec une attribution de campagne dédiée pour mesurer l’efficacité du programme.


## Planification des webinaires et des démonstrations

Personnalisez les invitations aux webinaires et la planification des démonstrations en fonction des centres d’intérêt, du secteur et de l’historique d’engagement des prospects. Des invitations pertinentes et opportunes augmentent la fréquentation et génèrent un pipeline de meilleure qualité à partir d&#39;interactions en direct.

### Impact commercial

Les programmes personnalisés d’invitation à des webinaires et des démonstrations permettent généralement d’augmenter de 35 à 45 % le taux de participation aux webinaires, ce qui entraîne une plus grande qualification du pipeline des opportunités d’engagement en direct.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour envoyer des invitations personnalisées lorsque les prospects montrent des signaux d’intérêt alignés sur les sujets de webinaire ou de démonstration à venir. Ce modèle répond en temps réel aux déclencheurs comportementaux, ce qui garantit que les invitations arrivent lorsque l&#39;intérêt est le plus fort.

### Considérations techniques

- Définissez des événements déclencheurs en fonction des intérêts (par exemple, la visite d’une page produit, le téléchargement d’une ressource associée, l’engagement avec une comparaison de concurrents) qui correspondent aux rubriques planifiées du webinaire ou de la démonstration.
- Intégrez les données de la plateforme de webinaire (par exemple, [!DNL ON24], [!DNL Zoom Webinar]) pour suivre les mesures d’inscription, de présence et d’engagement dans le profil unifié.
- Synchronisez les requêtes de démonstration et les données de planification avec [!DNL Salesforce] ou [!DNL Microsoft Dynamics] pour vous assurer que les équipes commerciales reçoivent les notifications et le contexte en temps opportun.
- Coordonnez le rythme des invitations avec les limites de communication [!DNL Marketo Engage] afin d’éviter les prospects et les prospects qui envoient trop de messages et qui se qualifient pour plusieurs événements.


## Étude de cas et Personalization du retour sur investissement

Proposez des études de cas personnalisées, des calculateurs de retour sur investissement et des exemples de réussite basés sur le secteur, la taille de l’entreprise et le cas d’utilisation des prospects. Lorsque les prospects voient des preuves provenant d’organisations similaires aux leurs, la confiance s’installe plus rapidement et les décisions d’achat s’accélèrent.

### Impact commercial

Les entreprises qui personnalisent le contenu probant constatent généralement une augmentation de 25 à 35 % de l’engagement dans les études de cas, ce qui contribue à renforcer la confiance dans les affaires et à accélérer les taux de conclusion de contrats.

### Mise en œuvre

Utilisez le modèle [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pour faire apparaître de manière dynamique les études de cas les plus pertinentes et les preuves de retour sur investissement en fonction du profil de chaque prospect. Ce modèle fait correspondre les attributs du visiteur à une bibliothèque de contenu, ce qui garantit que chaque prospect voit les points de démonstration de son secteur et de son groupe d’homologues.

### Considérations techniques

- Balisez les ressources de contenu d’étude de cas et de retour sur investissement avec des métadonnées (secteur, taille de l’entreprise, cas d’utilisation, produit) pour permettre une correspondance dynamique avec les profils de prospects.
- Implémentez des règles de personnalisation qui donnent la priorité aux correspondances de secteur en premier, puis à la taille de l’entreprise et au cas d’utilisation, avec du contenu de secours pour les prospects avec des données de profil limitées.
- Intégrez les signaux d’engagement du contenu (téléchargements, temps passé sur la page, partages) dans le profil unifié afin d’informer la notation des prospects et la portée des ventes.
- Coordonnez-vous avec [!DNL Marketo Engage] pour inclure du contenu de BAT personnalisé dans les séquences d’e-mails, pas seulement des expériences sur site.


## Programmes de défense des droits des clients

Identifiez et engagez des clients satisfaits pour des opportunités de plaidoyer telles que des références, des études de cas et des témoignages basés sur les données d’utilisation et de satisfaction. Une clientèle heureuse est un puissant moteur de croissance lorsqu’elle est reconnue et invitée à partager son succès.

### Impact commercial

Les programmes structurés de défense des clients entraînent généralement une augmentation de 20 à 30 % de la participation à la défense des intérêts, générant un flux régulier de références, d’études de cas et de témoignages qui soutiennent l’acquisition de nouvelles entreprises.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré en plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pour créer des workflows d’identification et d’engagement de plaidoyer qui répondent aux signaux de satisfaction et d’utilisation. Ce modèle appuie les demandes de promotion progressive, en commençant par une participation légère (p. ex., un examen) et en passant à des engagements plus profonds (p. ex., un appel de référence ou une étude de cas).

### Considérations techniques

- Ingérez les résultats de l’enquête de satisfaction (par exemple, le score net du promoteur, les scores de satisfaction de la clientèle) et les données d’utilisation des produits pour établir un score de préparation au plaidoyer pour chaque compte.
- Définissez des critères d’éligibilité de plaidoyer qui combinent des seuils de satisfaction, des jalons d’utilisation et la durée du compte pour éviter une sensibilisation prématurée.
- Synchronisez le statut de plaidoyer et l’historique de participation avec [!DNL Salesforce] ou [!DNL Microsoft Dynamics] afin que les équipes commerciales puissent référencer les défenseurs des clients lors de la prospection.
- Coordonnez-vous avec les [!DNL Marketo Engage] pour supprimer les activités de sensibilisation lors des remontées d’assistance actives ou des négociations de renouvellement.
