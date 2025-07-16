---
title: Parcours B2B utilisant le plan directeur des données Marketo
description: Plan directeur pour le déploiement rapide de Journey Optimizer B2B edition à l’aide des données Marketo Engage.
solution: Journey Optimizer B2B Edition
source-git-commit: 29ac41aa5d1d33b63c094ef56b03af73b88f96af
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 3%

---

# Parcours B2B utilisant le plan directeur des données Marketo

Ce guide complet décrit le processus d’intégration de Marketo Engage à Adobe Journey Optimizer B2B edition. Il couvre la configuration de schémas personnalisés, l’ingestion de profils et de comptes, ainsi que l’orchestration de parcours personnalisés pour les groupes d’achats. En utilisant les données de Marketo Engage, ce plan directeur assure un ciblage et un engagement précis sur plusieurs canaux, ce qui entraîne une demande plus qualifiée et améliore l’expérience client.

## Cas d’utilisation

* **Créer et gérer des groupes d’achats** : utilisez l’IA générative pour assembler et gérer des groupes d’achats dans les comptes cibles, en assurant une couverture complète des principales parties prenantes
* **Automatiser l’affectation des membres** : affectez automatiquement des membres aux rôles des groupes d’achats en fonction de critères définis, tels que la consommation de contenu et les données CRM
* **Parcours personnalisés** : concevez et visualisez des parcours à plusieurs étapes adaptés à chaque groupe d’achats et membre en fonction de son rôle, de son compte, de l’intérêt du produit et de l’étape de son cycle de vie
* **Automatisation en temps réel** : automatisez la progression des comptes et des groupes d’achats par le biais de parcours avec des déclencheurs d’engagement en temps réel et le score de qualification
* **Cross-Channel Engagement** : engagez des groupes d&#39;achats sur plusieurs canaux, notamment les e-mails, les SMS, les publicités, le chat, les événements et les webinaires, afin de rationaliser la génération et la qualification de la demande
* **Informations basées sur l’IA** : utilisez les informations basées sur l’IA pour optimiser la diffusion de contenu et les stratégies d’engagement pour les acheteurs individuels et les groupes d’achats entiers
* **Activation des données unifiées** : activez les listes de comptes unifiées d’Adobe Real-Time Customer Data Platform afin de fournir les données les plus récentes et complètes pour la création et la gestion des groupes d’achats
* **Enhanced Collaboration** : coordonner les efforts de marketing et de vente pour créer des opportunités de vente plus précises et accélérer la création de pipelines

## Applications

* Journey Optimizer édition B2B
* Édition B2B Real-time Customer Data Platform
* Marketo Engage

## Modèles d’intégration

| Intégration | Description |
| :-- | :--- |
| [Connecteur Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) | Adobe Experience Platform facilite l’ingestion des données à partir de Marketo et offre des fonctionnalités pour structurer, étiqueter et améliorer les données à l’aide de ses services. |
| [Journey Optimizer B2B edition - Action Marketo Engage](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes/action-nodes#marketo-engage-actions) | Synchronisez Account-Based Marketing dans Journey Optimizer B2B edition avec les efforts basés sur les prospects dans Marketo Engage à l’aide d’actions basées sur les personnes pour gérer les appartenances aux listes, les partitions de personnes et les campagnes de demandes. |
| [Journey Optimizer B2B edition - Ressources Marketo Engage](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content-management/assets/marketo-engage-dam/marketo-engage-design-studio) | Marketo Engage Design Studio est la source de ressources par défaut de Journey Optimizer B2B edition, ce qui facilite la gestion des ressources pour les parcours de compte. |

## Architecture

![Architecture de solution pour AJO B2B avec des données Marketo uniquement](./assets/ajo-b2b-marketo-only.png){zoomable="yes"}

## Garde-fous

* Limité à 50 segments de compte par sandbox.
* Évaluation de la segmentation par lots.
   * Automatiquement évalué toutes les 24 heures après la fin de l’exécution de l’audience par lots et des tâches d’exportation de profils.
   * Aucune prise en charge de l’évaluation Edge, en flux continu ou ad hoc.
* Les attributs de compte sont disponibles pour l’exportation.
* Événements de personnes.
   * Jusqu’à 30 jours de recherche en amont d’événement, aucun ordre de prédicats d’événement.
   * ET / OU est pris en charge (de sorte que vous pouvez dire « A et B doivent se produire »,  mais on ne peut pas dire « A doit arriver 3 jours avant B »).
* Maximum de 5 millions de comptes sur tous les parcours de compte
* 40 millions de personnes au maximum sur tous les parcours de compte
* Maximum de 1 000 personnes par compte dans un groupe d&#39;achat et un parcours
* [Garde-fous de profil et de segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

## Étapes de mise en œuvre

* Installez les schémas et les espaces de noms B2B à l’aide de l’une des options ci-dessous
   * Utilisation de la collection [Postman](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility)
   * Utilisation de [ modèles ](https://experienceleague.adobe.com/en/docs/experience-platform/sources/ui-tutorials/templates) dans l’interface utilisateur de Platform
* Créer un dictionnaire de données définissant le mappage entre les champs Marketo et le schéma XDM Experience Platform
   * Utiliser les [métadonnées d&#39;objet Marketo](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/field-management/export-all-object-metadata) comme point de départ
   * [Personnaliser le schéma XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/fields/overview) pour inclure vos champs personnalisés
   * Examinez les [champs XDM](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/field-mapping) standard pris en charge par Journey Optimizer B2B edition. Si vous avez besoin de champs supplémentaires, ouvrez un ticket d’assistance pour les configurer
      * **workEmail.address** est obligatoire sur le jeu de données Personne
      * **accountName** est requis sur le jeu de données Compte
   * Ajoutez une nouvelle colonne de champ XDM à la feuille de calcul des métadonnées Marketo exportées pour enregistrer le mappage prévu
* Configurer le connecteur source [Marketo Engage](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
   * Utilisez le dictionnaire de données défini ci-dessus pour définir le [mappage d’importation](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/ui/mapping#import-mapping) pour le connecteur source
   * Il est recommandé de ne pas activer le profil avant de prendre en compte les [considérations d’implémentation](#implementation-considerations)
   * Recommandation d’ingérer au minimum les personnes, entreprises, opportunités et activités , car ces objets sont les plus utiles lors de la création des audiences de votre compte
* Implémentez des [règles de liaison de graphiques d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-graph-linking-rules/overview) pour les personnes :
   * Définissez comment les enregistrements de personne sont liés à l’aide des espaces de noms d’identité (par exemple, e-mail, b2b_person).
   * Configurez les espaces de noms d’identité et les règles d’assemblage d’identités dans AEP.
   * Validez la liaison à l’aide des exemples de données Personne et des outils de prévisualisation.
* Activez les jeux de données Personne, Entreprises, Opportunités et Activités pour [profil](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/user-guide#enable-profile)
* Définir votre première [audience du compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/account-audience-overview)
* Définissez des [groupes d’achats](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/buying-groups/buying-groups-overview) ou un [parcours de compte](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview) à l’aide de l’audience du compte
   * La tâche de groupe d’achats s’exécute quotidiennement, traitant les nouveaux comptes qualifiés d’audience de compte ou les personnes nouvellement associées
   * La maintenance du groupe d&#39;achat s&#39;effectue tous les vendredis à minuit CT, de sorte que le retrait des membres ou l&#39;ajout de membres nouvellement qualifiés ne se produit que le vendredi

## Configuration recommandée

Pour rationaliser l’implémentation et assurer la compatibilité avec Adobe Journey Optimizer B2B edition, la configuration suivante est recommandée :

* **Utiliser les champs d’identité par défaut :**
   * _e-mail_ et _b2b_person_ doivent être conservés en tant que champs d’identité dans le schéma Personne pour prendre en charge le regroupement d’identités et l’activation de l’audience.
* **Utilisez les mappages par défaut pour le connecteur Source Marketo :**
   * Tirez parti des mappages de champs prêts à l’emploi fournis par Adobe pour simplifier l’ingestion des données et réduire la surcharge de configuration.
* **Utiliser les mappages par défaut pour AJO B2B:**
   * Adoptez les [mappages de champs standard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/field-mapping) pour Journey Optimizer B2B edition afin d’assurer la compatibilité avec la logique de groupe d’achats et l’orchestration des parcours.
* **Bloquer les mises à jour des champs sur tous les champs à l’exception des e-mails :**
   * Dans Marketo Engage, configurez la gestion des champs pour [bloquer les mises à jour](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field) à partir de Adobe Experience Platform pour tous les champs à l’exception des champs _e-mail_. Cela permet de maintenir l’intégrité des données tout en activant la résolution d’identité.
* **Implémenter des règles de liaison d’identité en utilisant l’e-mail comme espace de noms d’identité unique**
   * Configurez les [règles de liaison de graphiques d’identités](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-graph-linking-rules/overview) dans Adobe Experience Platform pour utiliser _e-mail_ explicitement comme espace de noms d’identité unique. Ces règles garantissent que les profils sont regroupés avec précision entre les sources de données où _e-mail_ est présent, ce qui permet une résolution d’identité robuste. En suivant les bonnes pratiques d’Adobe, définissez des règles de liaison qui donnent la priorité aux e-mails en tant qu’identifiant stable et global unique afin de conserver un graphique d’identités cohérent et conforme à la confidentialité.
Cette configuration offre un équilibre entre la facilité de déploiement et la gouvernance des données, garantissant ainsi une base fiable pour orchestrer les parcours B2B.

## Considérations relatives à la mise en œuvre

Lors de la mise en œuvre de Adobe Journey Optimizer B2B edition, il est essentiel de comprendre les fonctionnalités de combinaison d’identités fournies par Real-time Customer Data Platform. Cette plateforme effectue la combinaison d’identités aux niveaux de la personne et du compte, garantissant ainsi une vue unifiée des données client.

### Points clés

* **Combinaison d’identités** : la plateforme regroupe les identités à l’aide d’identifiants par défaut tels que l’identifiant Marketo, l’identifiant CRM ou l’adresse e-mail. Cela permet de créer un profil complet en fusionnant des données provenant de différentes sources.
* **Risques potentiels** : l’utilisation de l’e-mail comme identifiant pour l’assemblage peut entraîner un effondrement involontaire de l’identité. Cela signifie que différentes personnes partageant la même adresse e-mail peuvent être fusionnées de manière incorrecte en un seul profil. Cet effondrement de l’identité peut avoir un impact négatif sur la précision des données CRM et compromettre leur intégrité.
* **Stratégie de fusion** : B2B CDP utilise une stratégie de fusion temporelle, où la dernière date de dernière mise à jour (lastUpdatedDate) pour un attribut de profil particulier est utilisée. Cette stratégie permet de s’assurer que les données les plus récentes sont reflétées dans le profil.
* **Considérations relatives aux e-mails** : il est essentiel d’évaluer minutieusement l’utilisation des e-mails en tant qu’identifiant pour la fusion de fragments de profil. Bien que cela puisse être bénéfique, le risque d&#39;effondrement de l&#39;identité doit être soigneusement considéré par rapport aux avantages. Un inconvénient est que sans e-mail comme identifiant, l’appartenance à une audience externe créée par AJO B2B ne s’intègre pas au profil existant.
* **Intégration d’une personne Marketo** : AJO B2B utilise la personne Marketo avec l’ID de lead le plus bas lorsque plusieurs enregistrements Marketo fusionnent en un seul profil.

En gardant ces points à l’esprit, vous pouvez prendre des décisions éclairées sur la manière de configurer l’assemblage des identités dans Adobe Journey Optimizer B2B edition, afin de garantir des profils client précis et fiables.

### Évaluation des résultats de l’assemblage des identités

Query Service peut être utilisé pour voir l’impact de l’assemblage d’identités dans un jeu de données non activé pour profile. La requête suivante peut être utilisée pour effectuer l’évaluation

#### Nombre d’enregistrements ingérés

Cette requête renvoie le nombre total d&#39;enregistrements ingérés dans le jeu de données de profil de personne

```sql
select
    count(distinct b2b.personKey.sourceKey)
from
    marketo_person_ajo_b2b
```

#### Dupliquer les e-mails

Cette requête renvoie le nombre d’enregistrements de personne qui seront fusionnés dans le cadre de la combinaison d’identités de la plateforme

```sql
select
    SUM(personCount)
from
    (
        select
            emailAddress,
            count(*) as personCount
        from
            (
                select
                    MAX(workemail.address) as emailAddress
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
```

#### Adresses e-mail avec enregistrements en double

Cette requête renvoie les e-mails avec le plus grand nombre d’enregistrements en double dans le jeu de données.  Cette liste peut être utilisée pour vérifier certains de ces enregistrements afin de mieux comprendre l’impact de la liaison des identités sur Marketo et CRM.  Consultez la [ présentation d’Identity Service ](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) pour plus d’informations sur le fonctionnement de la liaison d’identités.

```sql
select
    *
from
    (
        select
            emailAddress,
            MAX(personId) as personId,
            count(*) as personCount
        from
            (
                select
                    b2b.personKey.sourceKey,
                    MAX(workemail.address) as emailAddress,
                    MAX(b2b.personKey.sourceId) as personId
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
order by
    personCount desc
```

### Options

#### Suppression de l’e-mail en tant qu’identité

Après votre analyse, si vous déterminez que l’e-mail n’est pas un champ valide à utiliser comme champ d’identité, le schéma Personne peut être modifié pour [supprimer l’e-mail en tant que champ d’identité](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/fields/identity)

#### Bloquer les mises à jour depuis Adobe Experience Platform

Si le maintien de l’e-mail en tant que champ d’identité est préférable pour vos cas d’utilisation, il existe une option permettant de [bloquer les mises à jour des champs](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field) provenant d’AJO B2B et permettant à AJO B2B de s’exécuter principalement sur les données Marketo.

## Documentation connexe

* [Édition B2B de Real-time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [Prise en main du B2B edition Real-time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [Mécanismes de sécurisation pour Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform)
* [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
* [Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)
* [Adobe Experience Platform - Connecteur source Marketo](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
* [Documentation Adobe Journey Optimizer B2B edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
