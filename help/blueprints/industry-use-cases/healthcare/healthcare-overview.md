---
title: Cas d’utilisation des soins de santé
description: Découvrez comment les organismes de santé utilisent Adobe Experience Platform pour améliorer l'engagement des patients, rationaliser la coordination des soins et obtenir de meilleurs résultats en matière de santé.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2356'
ht-degree: 1%

---


# Cas d’utilisation des soins de santé

Les établissements de santé utilisent Adobe Experience Platform pour créer des profils de patients unifiés et fournir des communications personnalisées et opportunes sur chaque point de contact. En reliant les données cliniques, comportementales et de préférences au même endroit, les équipes soignantes peuvent impliquer les patients plus efficacement, tout en maintenant les normes les plus élevées en matière de confidentialité et de conformité.

## Automatisation des rappels de rendez-vous

Envoyer des rappels de rendez-vous personnalisés par e-mail, SMS et notifications push en fonction des préférences de communication et du type de rendez-vous de chaque patient. Les rappels automatisés réduisent les rendez-vous manqués et assurent le bon fonctionnement des horaires, ce qui permet au personnel de se concentrer sur les soins aux patients.

### Impact commercial

Les organisations qui mettent en œuvre des rappels de rendez-vous automatisés constatent généralement une amélioration de 30 à 40 % des taux de présentation des rendez-vous et une réduction significative des absences coûteuses.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les événements de création de rendez-vous et de mise à jour du système de planification servent de déclencheurs naturels pour des messages de rappel opportuns et pertinents.

### Considérations techniques

- Veiller à ce que toutes les coordonnées du patient et les informations de rendez-vous soient transmises et stockées conformément aux exigences de la loi HIPAA, en utilisant des libellés d&#39;utilisation des données appropriés pour restreindre l&#39;accès non autorisé.
- Intégrer au système de planification des dossiers de santé électroniques pour capturer la création, l&#39;annulation et la replanification des rendez-vous en temps réel.
- Appliquez des politiques de gestion du consentement afin que les rappels ne soient envoyés que par les canaux que le patient a explicitement acceptés.
- Configurez les règles de suppression pour éviter les rappels en double ou excessifs lorsque des rendez-vous sont replanifiés en succession rapide.


## Campagnes d’observance des médicaments

Envoyer des rappels personnalisés et du contenu éducatif pour aider les patients à rester sur la bonne voie avec leurs calendriers de médicaments et leurs plans de traitement. Des messages personnalisés basés sur le type de médicament, le calendrier d&#39;administration et les antécédents des patients entraînent une meilleure observance et de meilleurs résultats de santé.

### Impact commercial

Les campagnes personnalisées d&#39;observance des médicaments entraînent généralement une amélioration de 20 à 30 % des taux d&#39;observance, ce qui se traduit par de meilleurs résultats de santé mesurables et moins de réadmissions à l&#39;hôpital.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’observance médicamenteuse nécessite une approche multipoint soutenue, avec des rappels croissants, des points de contact éducatifs et des bilans de suivi tout au long du plan de traitement.

### Considérations techniques

- Appliquer des étiquettes d&#39;utilisation des données strictes à toutes les informations de santé protégées liées aux médicaments et aux données de diagnostic afin d&#39;empêcher l&#39;activation non autorisée en aval.
- Intégrer aux systèmes de dossiers de santé électroniques et de pharmacie pour recevoir les données de remplissage et de renouvellement des ordonnances qui déclenchent des étapes de parcours.
- Mettre en œuvre une gestion rigoureuse du consentement pour s’assurer que les patients ont accepté de recevoir des communications liées aux médicaments et peuvent retirer leur consentement à tout moment.
- Concevez une logique de parcours pour détecter les schémas de non-engagement et envoyez les notifications à l’équipe de soins lorsqu’un patient risque de ne pas respecter les directives.


## Rappels concernant les soins préventifs

Rappeler de manière proactive aux patients les soins préventifs recommandés tels que les vaccinations, les dépistages et les bilans annuels en fonction de leur âge, de leurs antécédents médicaux et des facteurs de risque. Des rappels opportuns sur les soins préventifs aident à combler les lacunes dans les soins et à améliorer la santé globale de la population.

### Impact commercial

La diffusion proactive des soins préventifs se traduit généralement par une augmentation de 25 à 35 % des taux d’achèvement des soins préventifs, contribuant ainsi à améliorer la santé de la population et à réduire les coûts de traitement à long terme.

### Mise en œuvre

Utilisez le modèle [Activation des messages sortants par lots](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Les rappels de soins préventifs sont mieux diffusés par le biais de campagnes par lots planifiées qui évaluent l&#39;éligibilité des patients par rapport aux directives cliniques à une cadence régulière.

### Considérations techniques

- Créez des segments d’audience à l’aide de critères de recommandations cliniques (âge, sexe, antécédents familiaux, dates de dépistage précédentes) tout en appliquant des libellés d’utilisation des données à toutes les informations de santé protégées utilisées dans la segmentation.
- Assurer la coordination avec les équipes cliniques pour que le contenu du rappel soit conforme aux lignes directrices actuelles en matière de soins préventifs fondés sur des données probantes et aux protocoles organisationnels.
- Mettre en œuvre un capping de la fréquence pour éviter d&#39;accabler les patients qui remplissent les critères de plusieurs recommandations de soins préventifs simultanément.
- Tenez un journal d’audit de toutes les communications relatives aux soins préventifs envoyées pour les rapports réglementaires et la documentation sur les mesures de qualité.


## Campagnes De Suivi Post-Visite

Envoyez automatiquement des enquêtes post-visite, des instructions de soins et des rappels de rendez-vous de suivi en fonction du type de visite et des besoins spécifiques de chaque patient. Le suivi en temps opportun améliore la satisfaction du patient et assure la continuité des soins après chaque rencontre.

### Impact commercial

Les campagnes automatisées de suivi post-visite permettent généralement d&#39;obtenir une amélioration de 40 à 50 % des taux de réponse à l&#39;enquête et des scores de satisfaction des patients sensiblement plus élevés.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les événements de fin de visite du système de dossiers de santé électroniques constituent un déclencheur naturel et opportun pour des communications de suivi adaptées au type de rencontre.

### Considérations techniques

- Intégrer au système de dossiers de santé électroniques pour recevoir les événements de sortie de visite qui comprennent le type de visite, le fournisseur et les instructions de soins pertinentes sans exposer les notes cliniques complètes.
- Appliquez des libellés d’utilisation des données à tout contenu d’instructions de soins pour vous assurer que les informations de santé protégées ne sont partagées que par le biais de canaux sécurisés autorisés par le patient.
- Configurer des règles de durée qui tiennent compte du type de visite — par exemple, les suivis post-chirurgicaux peuvent nécessiter une durée différente de celle des examens de routine.
- Inclure des liens sécurisés vers le portail des patients pour l&#39;achèvement de l&#39;enquête et la planification des rendez-vous plutôt que de collecter des informations de santé par des canaux non sécurisés.


## Programmes De Prise En Charge Des Maladies Chroniques

Personnalisez les communications relatives à la prise en charge des maladies chroniques, le contenu éducatif et les rappels de surveillance en fonction de l’état spécifique et du plan de traitement de chaque patient. Un engagement durable et pertinent aide les patients à jouer un rôle actif dans la gestion de leur santé au fil du temps.

### Impact commercial

Les programmes personnalisés de prise en charge des maladies chroniques voient généralement une augmentation de 30 à 40 % des taux d’engagement dans les programmes, ce qui entraîne une amélioration des résultats de prise en charge des maladies et une réduction de l’utilisation des soins d’urgence.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). La prise en charge des maladies chroniques est intrinsèquement une expérience de longue durée et à points de contact multiples qui nécessite des messages adaptatifs basés sur l’engagement des patients et les jalons de santé.

### Considérations techniques

- Concevez une logique d’embranchement des parcours qui s’adapte en fonction de mesures spécifiques à la maladie (par exemple, les tendances de glycémie pour la prise en charge du diabète ou les mesures de pression artérielle pour les programmes d’hypertension).
- Implémentez une gouvernance stricte des données avec des libellés d’utilisation des données [!DNL Adobe Experience Platform] pour classer et protéger les données d’intégrité spécifiques aux conditions dans l’ensemble du parcours.
- Intégrer aux dispositifs de surveillance à distance des patients et aux systèmes de résultats signalés par les patients pour alimenter en temps réel les données de santé en points de décision parcours.
- Établir des voies d’escalade pour l’équipe de soins au sein du parcours afin que les tendances de non-engagement ou préoccupantes en matière de santé déclenchent des alertes pour le personnel clinique approprié.


## Nouveau Parcours d’intégration des patients

Automatisez un parcours d&#39;intégration en plusieurs étapes pour les nouveaux patients qui comprend des informations de bienvenue, des instructions d&#39;accès au portail patient et des conseils pour la planification des rendez-vous. Une expérience d’intégration fluide donne le ton à une relation engagée et à long terme avec les patients.

### Impact commercial

Les nouveaux parcours automatisés d&#39;intégration des patients améliorent généralement de 50 à 60 % les taux d&#39;activation du portail et augmentent considérablement l&#39;engagement précoce des patients.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). L’intégration du patient est un processus naturellement séquentiel à plusieurs étapes où chaque communication s’appuie sur la précédente et s’adapte selon que le patient a terminé ou non des actions clés.

### Considérations techniques

- Intégrer au système d&#39;enregistrement des patients pour déclencher le parcours d&#39;intégration immédiatement après la création d&#39;un nouveau dossier patient, afin de garantir une première impression en temps voulu.
- Utilisez la résolution d&#39;identité pour fusionner tous les enregistrements préexistants (par exemple, d&#39;une visite de site Web ou d&#39;une demande de rendez-vous) avec le nouveau profil du patient afin d&#39;éviter les communications en double.
- Assurez-vous que les liens et les informations d’identification d’activation du portail sont diffusés par des canaux sécurisés et conformes à la loi HIPAA et expirent après une période définie.
- Concevez le parcours pour détecter l&#39;activation du portail et les événements d&#39;achèvement afin que les étapes suivantes s&#39;adaptent plutôt que de répéter les informations que le patient a déjà utilisées.


## Diffusion de contenu d’intégrité personnalisée

Fournir du contenu personnalisé d&#39;éducation sanitaire, des conseils de bien-être et des ressources adaptés aux conditions, aux intérêts et aux objectifs de santé de chaque patient. Les contenus pertinents renforcent la confiance, améliorent les connaissances en matière de santé et permettent aux patients de prendre des décisions éclairées concernant leurs soins.

### Impact commercial

La diffusion personnalisée de contenus de santé entraîne généralement une augmentation de 35 à 45 % des taux d’engagement dans le contenu, ce qui entraîne une amélioration mesurable de l’éducation des patients et des connaissances en matière de santé.

### Mise en œuvre

Utilisez le modèle [Parcours cross-canal avec prise de décision](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md). La diffusion des contenus relatifs à l’intégrité s’appuie sur une prise de décision en temps réel qui sélectionne les contenus les plus pertinents pour chaque patient en fonction de ses affections, préférences et engagements passés, diffusés par le biais de son canal préféré.

### Considérations techniques

- Appliquer des étiquettes de classification du contenu et d&#39;utilisation des données à tous les documents d&#39;éducation sanitaire pour s&#39;assurer que le contenu spécifique à une maladie est uniquement diffusé aux patients qui ont consenti à recevoir des informations de santé sur ce sujet.
- Intégrez le moteur de prise de décision à un référentiel de contenu régulièrement examiné et approuvé par les équipes cliniques pour garantir la précision médicale.
- Implémentez des règles de fatigue du contenu pour éviter la diffusion excessive de contenu sur un seul sujet et pour équilibrer le matériel éducatif sur les différents besoins de santé d&#39;un patient.
- Suivez les signaux d’engagement du contenu (ouvertures, clics, temps passé) pour affiner en permanence la pertinence du contenu sans collecter ni stocker d’autres informations d’intégrité protégées.


## Notification des résultats de l’atelier

Avertissez les patients lorsque les résultats de laboratoire sont disponibles via leur canal de communication préféré avec une messagerie personnalisée et sécurisée. Une notification rapide encourage les patients à consulter rapidement les résultats et à contacter leur équipe soignante si nécessaire.

### Impact commercial

Les notifications automatisées de résultats de laboratoire entraînent généralement une augmentation de 60 à 70 % des taux d&#39;affichage des résultats, améliorant ainsi la communication avec les patients et permettant un suivi clinique plus rapide lorsque les résultats nécessitent une action.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). La disponibilité des résultats de laboratoire est un événement discret qui nécessite une notification immédiate et unique via le canal préféré du patient.

### Considérations techniques

- N&#39;incluez jamais les valeurs réelles des résultats de laboratoire dans les messages de notification — informez uniquement le patient que les résultats sont disponibles et dirigez-le vers le portail sécurisé des patients pour plus de détails.
- Intégrer au système d&#39;information de laboratoire pour recevoir les événements prêts à produire des résultats tout en appliquant des étiquettes d&#39;utilisation des données strictes pour empêcher toute donnée clinique de circuler dans les canaux de marketing.
- Implémentez une logique de maintien du fournisseur afin que les notifications ne soient envoyées qu&#39;après que le médecin prescripteur a examiné et publié les résultats pour que le patient les consulte.
- Assurez-vous que tous les liens de notification pointent vers des sessions authentifiées et chiffrées du portail patient qui répondent aux exigences de sécurité HIPAA.


## Vérification de la couverture d&#39;assurance

Vérifiez et communiquez de manière proactive les informations de couverture d&#39;assurance aux patients avant leurs rendez-vous afin de réduire les surprises de facturation et d&#39;améliorer l&#39;expérience globale des patients. Une communication claire et directe renforce la confiance et réduit les litiges de facturation après la visite.

### Impact commercial

La vérification proactive de la couverture d&#39;assurance se traduit généralement par une amélioration de 25 à 35 % des taux de confirmation de la couverture avant la visite et par une réduction significative des litiges de facturation et des plaintes des patients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les événements de planification des rendez-vous servent de déclencheur pour lancer la vérification de la couverture et communiquer les résultats au patient avant la visite.

### Considérations techniques

- Intégrez-la aux systèmes de vérification de l’éligibilité des assurances pour récupérer l’état de la couverture en temps réel sans stocker toutes les données de demande d’indemnisation dans la plateforme de données client.
- Appliquez des libellés d’utilisation des données à toutes les informations financières et d’assurance afin de limiter leur utilisation aux communications liées à la facturation uniquement.
- Configurez le délai d&#39;envoi des messages afin de laisser suffisamment de temps avant le rendez-vous pour que les patients résolvent les problèmes de couverture ou contactent leur fournisseur d&#39;assurance.
- Inclure des instructions claires et les coordonnées du service de facturation afin que les patients puissent poser des questions ou fournir des détails d&#39;assurance à jour avant leur visite.


## Rappels de rendez-vous de télésanté

Envoyer des rappels personnalisés pour les rendez-vous de télésanté qui comprennent des instructions de branchement, des conseils de préparation et des renseignements sur le soutien technique. Des rappels de télésanté efficaces réduisent les visites virtuelles manquées et aident les patients à se sentir en confiance en utilisant des outils de soins numériques.

### Impact commercial

Les rappels de rendez-vous de télésanté personnalisés entraînent généralement une amélioration de 40 à 50 % des taux de visites virtuelles et accélèrent l&#39;adoption globale de la télésanté dans la population de patients.

### Mise en œuvre

Utilisez le modèle [Message déclenché par un événement](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Les rendez-vous de télésanté fournissent un déclencheur naturel pour des rappels opportuns qui incluent des détails de connexion et des conseils de préparation.

### Considérations techniques

- Inclure des instructions de connexion spécifiques à la plateforme (ordinateur de bureau ou mobile) en fonction des préférences connues du patient en matière d&#39;appareil ou des données de session de télésanté antérieures.
- S&#39;assurer que tous les liens de connexion de télésanté et les identifiants de session sont fournis par des canaux chiffrés et conformes à la loi HIPAA et expirent après la période de rendez-vous prévue.
- Intégrer à la plateforme de télésanté pour détecter quand un patient a réussi à se connecter afin que les messages de rappel secondaires puissent être supprimés.
- Fournir un chemin de secours vers les informations de contact du support technique pour les patients qui ne sont pas connectés dans un intervalle défini avant l&#39;heure de début du rendez-vous.


## Participation au programme de mieux-être

Personnalisez les communications, les défis et les récompenses du programme de bien-être en fonction des objectifs de santé, du niveau d&#39;activité et des préférences de chaque patient. Les programmes de bien-être motivent les patients à adopter des habitudes plus saines et à maintenir leur bien-être à long terme.

### Impact commercial

Les campagnes de mobilisation personnalisées du programme de mieux-être permettent généralement d&#39;augmenter de 30 à 40 % les taux de participation au programme, ce qui contribue à améliorer les résultats en matière de santé et à fidéliser davantage les patients.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Les programmes de bien-être sont des expériences d’engagement soutenu avec plusieurs jalons, défis et points de contact de récompense qui nécessitent une orchestration adaptative basée sur la participation et les progrès du patient.

### Considérations techniques

- Intégrez-les aux flux de données d&#39;application d&#39;appareil portable et de fitness tout en appliquant des étiquettes d&#39;utilisation de données claires pour distinguer les données de bien-être des données de santé cliniques soumises à des exigences réglementaires plus strictes.
- Implémenter la gestion du consentement qui permet aux patients d&#39;accorder et de révoquer l&#39;autorisation de collecte de données sur le bien-être indépendamment de leurs préférences de communication clinique.
- Concevez une logique de parcours qui ajuste les difficultés et la fréquence de communication en fonction des schémas d&#39;engagement de chaque patient afin d&#39;éviter le découragement ou la fatigue.
- Assurez-vous que le suivi des récompenses et des incitations est conforme aux réglementations sanitaires applicables en matière d’incitations pour les patients et d’exigences antikickback.


## Coordination de l’équipe soignante

Permettre une communication et une coordination personnalisées entre les patients et les membres de leur équipe soignante en fonction du plan de soins et des préférences individuelles. Une meilleure coordination permet des transitions de soins plus fluides et de meilleurs résultats pour les patients ayant des besoins de soins complexes.

### Impact commercial

Des communications efficaces de coordination des équipes de soins se traduisent généralement par une amélioration de 35 à 45 pour cent de l&#39;engagement des équipes de soins et par de meilleurs résultats mesurables de coordination des soins dans les plans de soins multi-prestataires.

### Mise en œuvre

Utilisez le modèle [Parcours orchestré à plusieurs étapes](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). La coordination de l&#39;équipe de soins implique plusieurs parties prenantes et des flux de communication continus qui doivent s&#39;adapter en fonction des jalons du plan de soins, des changements de statut du patient et des actions du fournisseur.

### Considérations techniques

- Mettre en œuvre des contrôles d’accès et des étiquettes d’utilisation des données basés sur les rôles pour s’assurer que chaque membre de l’équipe de soins ne reçoit que les informations relatives au rôle du patient dans le plan de soins.
- Intégrer aux systèmes de gestion des soins et de dossiers de santé électroniques pour recevoir les mises à jour des plans de soins, les recommandations terminées et les événements de transition des soins qui déclenchent des messages de coordination.
- Concevez des voies de communication distinctes pour les messages destinés aux patients et aux fournisseurs, en veillant à ce que la terminologie clinique soit utilisée de manière appropriée pour les fournisseurs tout en maintenant les messages des patients clairs et accessibles.
- Tenez un journal d’audit complet de toutes les communications de coordination des soins pour assurer la conformité aux réglementations en matière de continuité des soins et aux exigences d’accréditation.
