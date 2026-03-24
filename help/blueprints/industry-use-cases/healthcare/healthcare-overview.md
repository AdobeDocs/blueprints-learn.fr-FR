---
title: Cas d’utilisation des soins de santé
description: Découvrez comment les organismes de santé utilisent Adobe Experience Platform pour améliorer l'engagement des patients, rationaliser la coordination des soins et obtenir de meilleurs résultats en matière de santé.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 8da82711-a783-488d-a0ed-070b33ecbbc4
source-git-commit: 0236bd326730ee9a0be621ee0e60ddc3d352410d
workflow-type: tm+mt
source-wordcount: '3818'
ht-degree: 0%

---

# Cas d’utilisation des soins de santé

Les établissements de santé utilisent Adobe Experience Platform pour créer des profils de patients unifiés et fournir des communications personnalisées et opportunes sur chaque point de contact. En reliant les données cliniques, comportementales et de préférences au même endroit, les équipes soignantes peuvent impliquer les patients plus efficacement, tout en maintenant les normes les plus élevées en matière de confidentialité et de conformité.

>[!IMPORTANT]
>Les cas d’utilisation liés aux soins de santé impliquent des informations de santé protégées (IPS) soumises à la loi HIPAA et aux autres réglementations en vigueur. Avant d’implémenter l’un de ces modèles, assurez-vous que [!DNL Adobe Experience Platform] est configuré en tant que service éligible au HIPAA et qu’un accord d’association commerciale (BAA) est en place avec Adobe. Les considérations techniques de chaque section mettent en évidence les principales exigences de conformité, mais ne sont pas exhaustives. Collaborez avec vos équipes juridiques, de conformité et de sécurité pour valider votre mise en œuvre par rapport à toutes les exigences réglementaires applicables.

## Automatisation des rappels de rendez-vous

Envoyer des rappels de rendez-vous personnalisés par e-mail, SMS et notifications push en fonction des préférences de communication et du type de rendez-vous de chaque patient. Les rappels automatisés réduisent les rendez-vous manqués et assurent le bon fonctionnement des horaires, ce qui permet au personnel de se concentrer sur les soins aux patients.

### Impact commercial

Les organisations qui mettent en œuvre des rappels de rendez-vous automatisés constatent des améliorations mesurables dans les taux de présentation des rendez-vous et une réduction significative des absences coûteuses.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les événements de création de rendez-vous et de mise à jour du système de planification servent de déclencheurs naturels pour des messages de rappel opportuns et pertinents. Il s’agit du modèle approprié lorsqu’un événement de rendez-vous discret est le déclencheur et que la réponse requise est une notification unique et urgente, plutôt qu’une séquence d’engagement soutenue, car les patients ont besoin d’une confirmation immédiate sans étapes de suivi.

### Considérations techniques

- Veiller à ce que toutes les coordonnées du patient et les informations de rendez-vous soient transmises et stockées conformément aux exigences de la loi HIPAA, en utilisant des libellés d&#39;utilisation des données appropriés pour restreindre l&#39;accès non autorisé.
- Intégrer au système de planification des dossiers de santé électroniques pour capturer la création, l&#39;annulation et la replanification des rendez-vous en temps réel.
- Appliquez des politiques de gestion du consentement afin que les rappels ne soient envoyés que par les canaux que le patient a explicitement acceptés.
- Configurez les règles de suppression pour éviter les rappels en double ou excessifs lorsque des rendez-vous sont replanifiés en succession rapide.


## Campagnes d’observance des médicaments

Envoyer des rappels personnalisés et du contenu éducatif pour aider les patients à rester sur la bonne voie avec leurs calendriers de médicaments et leurs plans de traitement. Des messages personnalisés basés sur le type de médicament, le calendrier d&#39;administration et les antécédents des patients entraînent une meilleure observance et de meilleurs résultats de santé.

### Impact commercial

Les campagnes personnalisées d&#39;observance des médicaments contribuent à améliorer les taux d&#39;observance, ce qui se traduit par de meilleurs résultats de santé et moins de réadmissions à l&#39;hôpital.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). [L’observance médicamenteuse nécessite une approche multipoint soutenue, avec des rappels croissants, des points de contact éducatifs et des bilans de suivi tout au long du plan de traitement. Il s’agit du schéma approprié, car la gestion des médicaments nécessite un flux séquentiel de plusieurs messages sur plusieurs jours ou semaines, avec une ramification conditionnelle basée sur les événements de remplissage et les signaux d’engagement. Un seul message déclenché ne peut pas s’adapter à la logique de dépendance entre les étapes éducatives et les chemins d’escalade.

### Considérations techniques

- Appliquer des étiquettes d&#39;utilisation des données strictes à toutes les informations de santé protégées liées aux médicaments et aux données de diagnostic afin d&#39;empêcher l&#39;activation non autorisée en aval.
- Intégrer aux systèmes de dossiers de santé électroniques et de pharmacie pour recevoir les données de remplissage et de renouvellement des ordonnances qui déclenchent des étapes de parcours.
- Mettre en œuvre une gestion rigoureuse du consentement pour s’assurer que les patients ont accepté de recevoir des communications liées aux médicaments et peuvent retirer leur consentement à tout moment.
- Concevez une logique de parcours pour détecter les schémas de non-engagement et envoyez les notifications à l’équipe de soins lorsqu’un patient risque de ne pas respecter les directives.


## Rappels concernant les soins préventifs

Rappeler de manière proactive aux patients les soins préventifs recommandés tels que les vaccinations, les dépistages et les bilans annuels en fonction de leur âge, de leurs antécédents médicaux et des facteurs de risque. Des rappels opportuns sur les soins préventifs aident à combler les lacunes dans les soins et à améliorer la santé globale de la population.

### Impact commercial

La sensibilisation proactive en matière de soins préventifs permet d’améliorer les taux d’achèvement des soins préventifs, contribuant ainsi à améliorer la santé de la population et à réduire les coûts de traitement à long terme.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Les rappels de soins préventifs sont mieux diffusés par le biais de campagnes par lots planifiées qui évaluent l&#39;éligibilité des patients par rapport aux directives cliniques à une cadence régulière. Il s’agit du modèle approprié lorsque l’audience est prédéfinie par des critères de directives cliniques, que le timing de diffusion est planifié à une cadence régulière plutôt que selon un événement et qu’aucun embranchement ou prise de décision en temps réel n’est nécessaire.

### Considérations techniques

- Créez des segments d’audience à l’aide de critères de recommandations cliniques (âge, sexe, antécédents familiaux, dates de dépistage précédentes) tout en appliquant des libellés d’utilisation des données à toutes les informations de santé protégées utilisées dans la segmentation.
- Assurer la coordination avec les équipes cliniques pour que le contenu du rappel soit conforme aux lignes directrices actuelles en matière de soins préventifs fondés sur des données probantes et aux protocoles organisationnels.
- Mettre en œuvre un capping de la fréquence pour éviter d&#39;accabler les patients qui remplissent les critères de plusieurs recommandations de soins préventifs simultanément.
- Tenez un journal d’audit de toutes les communications relatives aux soins préventifs envoyées pour les rapports réglementaires et la documentation sur les mesures de qualité.


## Campagnes De Suivi Post-Visite

Envoyez automatiquement des enquêtes post-visite, des instructions de soins et des rappels de rendez-vous de suivi en fonction du type de visite et des besoins spécifiques de chaque patient. Le suivi en temps opportun améliore la satisfaction du patient et assure la continuité des soins après chaque rencontre.

### Impact commercial

Les campagnes automatisées de suivi post-visite permettent d’améliorer les taux de réponse aux questionnaires et les scores de satisfaction des patients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les événements de fin de visite du système de dossiers de santé électroniques constituent un déclencheur naturel et opportun pour des communications de suivi adaptées au type de rencontre. Il s’agit du modèle approprié lorsqu’un événement de fin de visite distinct est le déclencheur et que la réponse requise est un suivi immédiat adapté au type de rencontre, plutôt qu’une séquence à plusieurs étapes, puisque chaque visite génère son propre besoin de suivi indépendant.

### Considérations techniques

- Intégrer au système de dossiers de santé électroniques pour recevoir les événements de sortie de visite qui comprennent le type de visite, le fournisseur et les instructions de soins pertinentes sans exposer les notes cliniques complètes.
- Appliquez des libellés d’utilisation des données à tout contenu d’instructions de soins pour vous assurer que les informations de santé protégées ne sont partagées que par le biais de canaux sécurisés autorisés par le patient.
- Configurer des règles de durée qui tiennent compte du type de visite — par exemple, les suivis post-chirurgicaux peuvent nécessiter une durée différente de celle des examens de routine.
- Inclure des liens sécurisés vers le portail des patients pour l&#39;achèvement de l&#39;enquête et la planification des rendez-vous plutôt que de collecter des informations de santé par des canaux non sécurisés.


## Programmes De Prise En Charge Des Maladies Chroniques

Personnalisez les communications relatives à la prise en charge des maladies chroniques, le contenu éducatif et les rappels de surveillance en fonction de l’état spécifique et du plan de traitement de chaque patient. Un engagement durable et pertinent aide les patients à jouer un rôle actif dans la gestion de leur santé au fil du temps.

### Impact commercial

Les programmes personnalisés de prise en charge des maladies chroniques voient augmenter les taux d’engagement des programmes, ce qui permet d’améliorer les résultats de la prise en charge des maladies et de réduire le recours aux soins d’urgence.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). [La prise en charge des maladies chroniques est intrinsèquement une expérience de longue durée et à points de contact multiples qui nécessite des messages adaptatifs basés sur l’engagement des patients et les jalons de santé. Il s’agit du modèle approprié, car la prise en charge des maladies chroniques nécessite des messages adaptatifs sur une longue période avec une ramification conditionnelle basée sur les mesures cliniques et les schémas d’engagement. Les messages déclenchés par un événement ne peuvent pas gérer la réévaluation dynamique en cours nécessaire pour ajuster les interventions en fonction de l’évolution des données de santé.

### Considérations techniques

- Concevez une logique d’embranchement des parcours qui s’adapte en fonction de mesures spécifiques à la maladie (par exemple, les tendances de glycémie pour la prise en charge du diabète ou les mesures de pression artérielle pour les programmes d’hypertension).
- Implémentez une gouvernance stricte des données avec des libellés d’utilisation des données [!DNL Adobe Experience Platform] pour classer et protéger les données d’intégrité spécifiques aux conditions dans l’ensemble du parcours.
- Intégrer aux dispositifs de surveillance à distance des patients et aux systèmes de résultats signalés par les patients pour alimenter en temps réel les données de santé en points de décision parcours.
- Établir des voies d’escalade pour l’équipe de soins au sein du parcours afin que les tendances de non-engagement ou préoccupantes en matière de santé déclenchent des alertes pour le personnel clinique approprié.


## Nouveau Parcours d’intégration des patients

Automatisez un parcours d&#39;intégration en plusieurs étapes pour les nouveaux patients qui comprend des informations de bienvenue, des instructions d&#39;accès au portail patient et des conseils pour la planification des rendez-vous. Une expérience d’intégration fluide donne le ton à une relation engagée et à long terme avec les patients.

### Impact commercial

Les nouveaux parcours automatisés d’intégration des patients contribuent à améliorer les taux d’activation du portail et à renforcer l’engagement précoce des patients.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). [L’intégration du patient est un processus naturellement séquentiel à plusieurs étapes où chaque communication s’appuie sur la précédente et s’adapte selon que le patient a terminé ou non des actions clés. Il s’agit du modèle approprié, car l’intégration nécessite un flux dépendant séquencé sur plusieurs jours avec embranchement en fonction des actions du patient (activation du portail, achèvement du formulaire). Une approche par message unique ou par lots ne peut pas s’adapter aux interdépendances entre les étapes ni à l’achèvement progressif.

### Considérations techniques

- Intégrer au système d&#39;enregistrement des patients pour déclencher le parcours d&#39;intégration immédiatement après la création d&#39;un nouveau dossier patient, afin de garantir une première impression en temps voulu.
- Utilisez la résolution d&#39;identité pour fusionner tous les enregistrements préexistants (par exemple, d&#39;une visite de site Web ou d&#39;une demande de rendez-vous) avec le nouveau profil du patient afin d&#39;éviter les communications en double.
- Assurez-vous que les liens et les informations d’identification d’activation du portail sont diffusés par des canaux sécurisés et conformes à la loi HIPAA et expirent après une période définie.
- Concevez le parcours pour détecter l&#39;activation du portail et les événements d&#39;achèvement afin que les étapes suivantes s&#39;adaptent plutôt que de répéter les informations que le patient a déjà utilisées.


## Diffusion de contenu d’intégrité personnalisée

Fournir du contenu personnalisé d&#39;éducation sanitaire, des conseils de bien-être et des ressources adaptés aux conditions, aux intérêts et aux objectifs de santé de chaque patient. Les contenus pertinents renforcent la confiance, améliorent les connaissances en matière de santé et permettent aux patients de prendre des décisions éclairées concernant leurs soins.

### Impact commercial

La diffusion personnalisée de contenu médical permet d’obtenir des taux d’engagement plus élevés, ce qui améliore l’éducation des patients et les connaissances en santé.

### Mise en œuvre

Utilisez le modèle Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). [La diffusion des contenus relatifs à l’intégrité s’appuie sur une prise de décision en temps réel qui sélectionne les contenus les plus pertinents pour chaque patient en fonction de ses affections, préférences et engagements passés, diffusés par le biais de son canal préféré. Il s’agit du modèle approprié lorsque la sélection de contenu doit tenir compte des conditions du patient, des préférences de consentement et des préférences de canal, tout en empêchant la diffusion en double ou fastidieuse. L’orchestration à plusieurs étapes ne fournit pas à elle seule la couche de prise de décision en temps réel nécessaire pour faire correspondre l’inventaire de contenu dynamique aux besoins individuels des patients.

### Considérations techniques

- Appliquer des étiquettes de classification du contenu et d&#39;utilisation des données à tous les documents d&#39;éducation sanitaire pour s&#39;assurer que le contenu spécifique à une maladie est uniquement diffusé aux patients qui ont consenti à recevoir des informations de santé sur ce sujet.
- Intégrez le moteur de prise de décision à un référentiel de contenu régulièrement examiné et approuvé par les équipes cliniques pour garantir la précision médicale.
- Implémentez des règles de fatigue du contenu pour éviter la diffusion excessive de contenu sur un seul sujet et pour équilibrer le matériel éducatif sur les différents besoins de santé d&#39;un patient.
- Suivez les signaux d’engagement du contenu (ouvertures, clics, temps passé) pour affiner en permanence la pertinence du contenu sans collecter ni stocker d’autres informations d’intégrité protégées.


## Notification des résultats de l’atelier

Avertissez les patients lorsque les résultats de laboratoire sont disponibles via leur canal de communication préféré avec une messagerie personnalisée et sécurisée. Une notification rapide encourage les patients à consulter rapidement les résultats et à contacter leur équipe soignante si nécessaire.

### Impact commercial

Les notifications automatisées de résultats de laboratoire permettent d&#39;augmenter les taux de visualisation des résultats, d&#39;améliorer la communication avec les patients et d&#39;accélérer le suivi clinique lorsque les résultats nécessitent une action.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). La disponibilité des résultats de laboratoire est un événement discret qui nécessite une notification immédiate et unique via le canal préféré du patient. Il s&#39;agit du bon schéma lorsqu&#39;un événement de résultat de laboratoire discret est le déclencheur et que la réponse requise est une notification unique et immédiate, plutôt qu&#39;une séquence de messages multiples, puisque les patients ont besoin d&#39;une alerte rapide pour vérifier leur portail sans communications de suivi supplémentaires.

### Considérations techniques

- N&#39;incluez jamais les valeurs réelles des résultats de laboratoire dans les messages de notification — informez uniquement le patient que les résultats sont disponibles et dirigez-le vers le portail sécurisé des patients pour plus de détails.
- Intégrer au système d&#39;information de laboratoire pour recevoir les événements prêts à produire des résultats tout en appliquant des étiquettes d&#39;utilisation des données strictes pour empêcher toute donnée clinique de circuler dans les canaux de marketing.
- Implémentez une logique de maintien du fournisseur afin que les notifications ne soient envoyées qu&#39;après que le médecin prescripteur a examiné et publié les résultats pour que le patient les consulte.
- Assurez-vous que tous les liens de notification pointent vers des sessions authentifiées et chiffrées du portail patient qui répondent aux exigences de sécurité HIPAA.


## Vérification de la couverture d&#39;assurance

Vérifiez et communiquez de manière proactive les informations de couverture d&#39;assurance aux patients avant leurs rendez-vous afin de réduire les surprises de facturation et d&#39;améliorer l&#39;expérience globale des patients. Une communication claire et directe renforce la confiance et réduit les litiges de facturation après la visite.

### Impact commercial

La vérification proactive de la couverture d&#39;assurance se traduit par une amélioration des taux de confirmation de la couverture avant la visite et une réduction significative des litiges de facturation et des plaintes des patients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les événements de planification des rendez-vous servent de déclencheur pour lancer la vérification de la couverture et communiquer les résultats au patient avant la visite. Il s’agit du schéma approprié lorsqu’un événement de planification de rendez-vous discret est le déclencheur et que la réponse requise est une notification unique et urgente concernant la couverture, plutôt qu’une séquence d’engagement à plusieurs étapes, puisque le patient a besoin d’un message clair avant son rendez-vous.

### Considérations techniques

- Intégrez-la aux systèmes de vérification de l’éligibilité des assurances pour récupérer l’état de la couverture en temps réel sans stocker toutes les données de demande d’indemnisation dans la plateforme de données client.
- Appliquez des libellés d’utilisation des données à toutes les informations financières et d’assurance afin de limiter leur utilisation aux communications liées à la facturation uniquement.
- Configurez le délai d&#39;envoi des messages afin de laisser suffisamment de temps avant le rendez-vous pour que les patients résolvent les problèmes de couverture ou contactent leur fournisseur d&#39;assurance.
- Inclure des instructions claires et les coordonnées du service de facturation afin que les patients puissent poser des questions ou fournir des détails d&#39;assurance à jour avant leur visite.


## Rappels de rendez-vous de télésanté

Envoyer des rappels personnalisés pour les rendez-vous de télésanté qui comprennent des instructions de branchement, des conseils de préparation et des renseignements sur le soutien technique. Des rappels de télésanté efficaces réduisent les visites virtuelles manquées et aident les patients à se sentir en confiance en utilisant des outils de soins numériques.

### Impact commercial

Les rappels de rendez-vous de télésanté personnalisés aident à améliorer les taux de visites virtuelles et à accélérer l&#39;adoption globale de la télésanté dans la population de patients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les rendez-vous de télésanté fournissent un déclencheur naturel pour des rappels opportuns qui incluent des détails de connexion et des conseils de préparation. C&#39;est la bonne façon de procéder lorsqu&#39;un événement de rendez-vous de télésanté distinct est le déclencheur et que la réponse requise est un rappel unique et immédiat accompagné de conseils techniques, plutôt qu&#39;une séquence à plusieurs étapes, puisque les patients ont besoin d&#39;instructions claires avant le rendez-vous sans message de suivi ultérieur.

### Considérations techniques

- Inclure des instructions de connexion spécifiques à la plateforme (ordinateur de bureau ou mobile) en fonction des préférences connues du patient en matière d&#39;appareil ou des données de session de télésanté antérieures.
- S&#39;assurer que tous les liens de connexion de télésanté et les identifiants de session sont fournis par des canaux chiffrés et conformes à la loi HIPAA et expirent après la période de rendez-vous prévue.
- Intégrer à la plateforme de télésanté pour détecter quand un patient a réussi à se connecter afin que les messages de rappel secondaires puissent être supprimés.
- Fournir un chemin de secours vers les informations de contact du support technique pour les patients qui ne sont pas connectés dans un intervalle défini avant l&#39;heure de début du rendez-vous.


## Participation au programme de mieux-être

Personnalisez les communications, les défis et les récompenses du programme de bien-être en fonction des objectifs de santé, du niveau d&#39;activité et des préférences de chaque patient. Les programmes de bien-être motivent les patients à adopter des habitudes plus saines et à maintenir leur bien-être à long terme.

### Impact commercial

Les campagnes d&#39;engagement personnalisées du programme de mieux-être permettent d&#39;augmenter les taux de participation au programme, contribuant ainsi à de meilleurs résultats de santé et à une plus grande fidélisation des patients.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). [Les programmes de bien-être sont des expériences d’engagement soutenu avec plusieurs jalons, défis et points de contact de récompense qui nécessitent une orchestration adaptative basée sur la participation et les progrès du patient. Il s’agit du modèle approprié, car les programmes de bien-être nécessitent un flux séquentiel et multi-messages sur une période prolongée avec embranchement conditionnel basé sur les jalons de participation et les schémas d’engagement. Les messages déclenchés par un événement ne peuvent pas gérer l’orchestration adaptative prolongée nécessaire pour ajuster les défis et les récompenses en fonction du suivi continu des progrès.

### Considérations techniques

- Intégrez-les aux flux de données d&#39;application d&#39;appareil portable et de fitness tout en appliquant des étiquettes d&#39;utilisation de données claires pour distinguer les données de bien-être des données de santé cliniques soumises à des exigences réglementaires plus strictes.
- Implémenter la gestion du consentement qui permet aux patients d&#39;accorder et de révoquer l&#39;autorisation de collecte de données sur le bien-être indépendamment de leurs préférences de communication clinique.
- Concevez une logique de parcours qui ajuste les difficultés et la fréquence de communication en fonction des schémas d&#39;engagement de chaque patient afin d&#39;éviter le découragement ou la fatigue.
- Assurez-vous que le suivi des récompenses et des incitations est conforme aux réglementations sanitaires applicables en matière d’incitations pour les patients et d’exigences antikickback.


## Coordination de l’équipe soignante

Permettre une communication et une coordination personnalisées entre les patients et les membres de leur équipe soignante en fonction du plan de soins et des préférences individuelles. Une meilleure coordination permet des transitions de soins plus fluides et de meilleurs résultats pour les patients ayant des besoins de soins complexes.

### Impact commercial

Des communications efficaces de coordination des équipes de soins permettent d&#39;améliorer l&#39;engagement des équipes de soins et les résultats de la coordination des soins dans les plans de soins multi-prestataires.

### Mise en œuvre

Utilisez le modèle Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). [La coordination de l&#39;équipe de soins implique plusieurs parties prenantes et des flux de communication continus qui doivent s&#39;adapter en fonction des jalons du plan de soins, des changements de statut du patient et des actions du fournisseur. Il s’agit du modèle approprié, car la coordination des soins nécessite des flux de messages adaptatifs à plusieurs étapes qui se divisent en fonction des jalons du plan de soins et des actions des prestataires de services de plusieurs parties prenantes. Un message unique ou un modèle plus simple ne peut pas s’adapter aux interdépendances complexes et au routage des messages en fonction des rôles nécessaires entre les équipes cliniques.

### Considérations techniques

- Mettre en œuvre des contrôles d’accès et des étiquettes d’utilisation des données basés sur les rôles pour s’assurer que chaque membre de l’équipe de soins ne reçoit que les informations relatives au rôle du patient dans le plan de soins.
- Intégrer aux systèmes de gestion des soins et de dossiers de santé électroniques pour recevoir les mises à jour des plans de soins, les recommandations terminées et les événements de transition des soins qui déclenchent des messages de coordination.
- Concevez des voies de communication distinctes pour les messages destinés aux patients et aux fournisseurs, en veillant à ce que la terminologie clinique soit utilisée de manière appropriée pour les fournisseurs tout en maintenant les messages des patients clairs et accessibles.
- Tenez un journal d’audit complet de toutes les communications de coordination des soins pour assurer la conformité aux réglementations en matière de continuité des soins et aux exigences d’accréditation.


## Analyse des écarts entre les soins et la Funnel du Parcours des patients

Cartographier le parcours de bout en bout des patients à partir de la recherche initiale sur le Web, en passant par la planification des rendez-vous, la prestation des soins et le suivi pour déterminer où les patients se désengagent et quelles populations présentent des lacunes dans les soins préventifs ou chroniques recommandés. Les systèmes de santé qui manquent de visibilité sur le parcours cross-canal ne peuvent pas faire la distinction entre la friction en matière d’horaires et le désengagement des patients, ce qui limite leur capacité à améliorer l’accès et à combler les lacunes en matière de soins à grande échelle.

### Impact commercial

Comprendre où les patients abandonnent les parcours de soins et quels segments des membres ont la plus forte concentration de lacunes en matière de soins permet aux équipes de gestion des soins et de marketing de concentrer les ressources de sensibilisation sur les populations et les points de friction qui produiront la plus grande amélioration de l&#39;observance des soins.

### Mise en œuvre

Utilisez le modèle [Customer Analytics et génération d’Insight](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md). Cette approche connecte les données comportementales web et de portail, les enregistrements de système de rendez-vous et les données de demandes de soins à Customer Journey Analytics, où l’analyse des abandons mesure la chute à chaque planification ou étape de soins et l’analyse des cohortes identifie les segments de membres ayant les taux d’observance des soins les plus faibles. Il s’agit du bon modèle lorsque l’objectif est la génération d’insight et l’analyse au niveau de la population (comprendre où les parcours se répartissent et qui est le plus à risque), plutôt que de déclencher des actions de sensibilisation ou d’activer une liste de suppression.

### Considérations techniques

- Les données de rendez-vous et de demandes de remboursement des systèmes cliniques doivent être mappées aux schémas XDM conformes à la loi HIPAA avant l’ingestion dans AEP. Les libellés d’utilisation des données doivent également être appliqués pour restreindre l’accès aux informations de santé protégées dans les vues de données CJA.
- Les identifiants du patient ou du membre sur le portail web, le système de planification et le dossier de santé électronique doivent être résolus en un ID de personne cohérent dans la connexion CJA pour produire une vue cohérente du parcours sur l’ensemble du système sans dupliquer les individus.
- L’analyse des lacunes en matière de soins nécessite des jeux de données de recherche qui codent des définitions de lignes directrices cliniques, telles que les intervalles de dépistage recommandés par âge et par état, de sorte que les champs dérivés de CJA puissent signaler les membres qui n’ont pas terminé les soins recommandés dans la fenêtre des lignes directrices.
- L’analyse du funnel de planification doit capturer les sessions de planification terminées et abandonnées, y compris les points de sortie dans les flux de planification à plusieurs étapes, de sorte que les points de friction soient visibles au niveau de l’étape plutôt que sous la forme de taux de déperdition agrégés.


## Personalization de contenu du portail patient

Personnalisez l&#39;expérience du portail patient authentifié en affichant le contenu, les outils et les ressources les plus pertinents en fonction du comportement de navigation et de l&#39;historique d&#39;engagement de chaque patient au cours de la session. Un portail qui s&#39;adapte à ce qu&#39;un patient recherche activement — plutôt que de présenter la même expérience statique à chaque visiteur — permet aux patients de trouver plus facilement ce dont ils ont besoin et encourage un engagement plus profond avec les ressources de santé disponibles.

### Impact commercial

La personnalisation de l&#39;expérience du portail patient en fonction du comportement de l&#39;engagement améliore les taux de découverte de contenu et d&#39;achèvement du libre-service, aidant les patients à parcourir leurs soins plus en confiance sans nécessiter l&#39;intervention de l&#39;équipe soignante.

### Mise en œuvre

Utilisez le modèle [recommandation comportementale](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Les signaux comportementaux en session émis à partir du portail authentifié, notamment les pages vues du contenu, l&#39;utilisation des outils de santé, l&#39;engagement sur les sujets les plus fréquemment abordés et l&#39;activité de planification des rendez-vous, forment un modèle de recommandation qui permet d&#39;afficher les ressources les plus pertinentes pour chaque patient en fonction de ce qu&#39;il explore activement, sans avoir besoin de données cliniques comme entrée. Il s’agit du modèle approprié lorsque la personnalisation est pilotée par des signaux comportementaux implicites au sein d’une session authentifiée et que l’objectif est le classement de pertinence d’un catalogue de contenu et de ressources, plutôt que la prise de décision d’éligibilité régie, ce qui est plus approprié lorsque les critères cliniques doivent déterminer ce qu’un patient voit.

### Considérations techniques

- Limitez les signaux comportementaux utilisés pour les recommandations aux données d’interaction du portail (vues de contenu, utilisation des outils et schémas de navigation) et implémentez des libellés d’utilisation des données qui empêchent tout intérêt présumé pour la santé de circuler en dehors de la session du portail authentifié ou dans les canaux marketing.
- Implémentez une bibliothèque de contenu examinée cliniquement comme pool de recommandations afin que le modèle puisse uniquement afficher des documents d’éducation à la santé préapprouvés, en veillant à ce que chaque ressource recommandée ait été validée pour son exactitude avant son déploiement.
- S’assurer que le système de recommandation répond aux exigences de protection technique de la loi HIPAA pour l’environnement de portail authentifié, y compris les contrôles de temporisation de session et la journalisation d’audit du contenu présenté à chaque patient et à quel moment.
- Fournir aux patients des contrôles visibles pour effacer l’historique de navigation de leur portail et se désabonner de la personnalisation comportementale, en maintenant la transparence et la confiance dans la manière dont leurs données d’engagement sont utilisées dans l’expérience du portail.

## Rappels sur l’engagement et les rendez-vous des patients

Envoyez des rappels de rendez-vous personnalisés, des conseils de santé et des communications de suivi par le biais de parcours multicanaux conformes et tenant compte du consentement. Les rappels de rendez-vous personnalisés et automatisés réduisent les taux de non-présentation tout en veillant à ce que les communications soient conformes aux réglementations de confidentialité des soins de santé et aux préférences de consentement des patients.

### Impact commercial

Les établissements de santé disposant de programmes automatisés de rappels de rendez-vous observent des réductions significatives des taux de non-présentation et d&#39;annulation tardive, améliorant l&#39;utilisation du calendrier des prestataires et les résultats de santé des patients grâce à une meilleure observance des rendez-vous.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pour répondre aux événements de planification de rendez-vous avec des rappels personnalisés et opportuns programmés à intervalles optimaux avant la date du rendez-vous. Il s’agit du modèle approprié lorsque la communication est déclenchée par un événement spécifique d’interaction avec le patient et que la réponse est un message personnalisé sensible au temps, plutôt qu’une séquence d’évolution de plusieurs semaines ou une sélection d’offres complexe.

### Considérations techniques

- Toutes les communications des patients doivent respecter les réglementations applicables en matière de confidentialité des soins de santé ; le contenu des messages doit éviter d&#39;inclure des informations de santé protégées au-delà de ce qui est strictement nécessaire pour la communication.
- La gestion du consentement doit être appliquée au niveau du canal : les patients qui n’ont pas opté pour les rappels par SMS ne doivent pas recevoir de SMS, même si les SMS sont le canal de rappel le plus efficace pour leur population.
- L&#39;intégration au système d&#39;ordonnancement doit fournir des événements de rendez-vous en temps quasi réel pour permettre un minutage de rappel précis par rapport à l&#39;horaire réel de rendez-vous, y compris les replanifications et les annulations le même jour.
- Les séquences de rappels multicanaux doivent inclure une logique de suppression afin que les patients qui confirment leur rendez-vous ne continuent pas à recevoir des messages de rappel pour ce rendez-vous.
