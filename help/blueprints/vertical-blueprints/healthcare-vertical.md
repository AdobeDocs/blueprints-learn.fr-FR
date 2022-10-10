---
source-git-commit: f7104d114a2644a494003bc78eb20768904f652c
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 1%

---
﻿---
title: Soins de santé
description: Découvrez Healthcare Shield, un module complémentaire Adobe Experience Platform pour les applications basées sur Platform, telles que Real-Time CDP, Customer Journey Analytics et Adobe Journey Optimizer. Le module complémentaire permet à ces applications d’être conformes aux exigences HIPAA et PHI.
solution: Experience Platform
---
# Bouclier de santé

Healthcare Shield est un module complémentaire Adobe Experience Platform destiné aux applications Adobe Experience Platform, telles que Real-Time CDP, Customer Journey Analytics et Adobe Journey Optimizer, conçu pour préparer ces applications HIPAA à répondre aux exigences relatives au traitement et à l’utilisation des informations d’intégrité protégées (PHI).

## Questions fréquentes sur Healthcare Shield

Les questions fréquentes suivantes apportent des réponses aux questions courantes sur Healthcare Shield.

### Qu’est-ce que le HIPAA ?

Le HIPAA est le Health Insurance Porability and Accountability Act (HIPAA), un règlement américain qui établit des protections importantes pour limiter l&#39;utilisation et la divulgation d&#39;informations sur la santé protégées (PHI) lorsqu&#39;elles sont créées, reçues, gérées ou transmises par une entité couverte par le HIPAA ou des associés d&#39;entreprise (tels que les clients d&#39;Adobe) à un associé d&#39;entreprise (un partenaire technologique tel qu&#39;un Adobe).

Adobe est prêt en tant qu’associé commercial pour les solutions d’Adobe prêtes pour le HIPAA spécifiques et la conformité aux règles de sécurité, de confidentialité et de notification d’infraction du HIPAA.

### Qu’est-ce qu’un accord d’association de travail (AAA) et pourquoi est-ce important ?

Lorsqu’une entité couverte ou un associé d’entreprise (un client d’Adobe) utilise les services d’un associé d’entreprise (tel qu’un Adobe) pour créer, recevoir, gérer ou transmettre certains types de données de consommateur qui sont des données de santé protégées (PHI) ou une ePHI (version électronique de l’API), l’entité couverte et l’associé d’entreprise sont tenus de souscrire à un accord d’association d’entreprise.

Le contrat BAA requiert un Adobe, en tant qu’associé de l’entreprise pour protéger de manière appropriée l’intégrité sanitaire des données en se conformant aux exigences des règles de confidentialité, de sécurité et de notification d’infraction du HIPAA.

Grâce au module complémentaire Healthcare Shield pour Real-Time CDP, Adobe peut désormais exécuter une version BAA avec des clients qui disposent de licences pour cette fonctionnalité, ainsi que les flux de consommation d’Adobe Real-Time CDP B2P Edition et d’Adobe Real-Time CDP B2C.

### Pourquoi le Healthcare Shield pour Real-Time CDP (et les futures applications basées sur Platform) est-il disponible uniquement aux États-Unis ?

Puisque le HIPAA est une loi américaine, nous limitons la disponibilité du Healthcare Shield aux États-Unis et aux entreprises soumises à l&#39;HIPAA. Adobe a l&#39;intention d&#39;étendre la couverture à d&#39;autres juridictions à mesure que nous définissons les exigences locales et que nous sommes sûrs que nous pouvons les satisfaire.

### Qu’est-ce que le Bouclier de santé pour Real-Time CDP ?

Healthcare Shield pour Real-Time CDP est destiné aux clients qui sont une entité couverte ou un associé d’entreprise et qui ont l’intention d’exploiter l’API dans Real-Time CDP pour l’ingestion de données, la création d’audiences et l’activation cross-canal, ainsi que d’exiger un Adobe d’exécution d’une BAA. Le Bouclier de santé est requis pour les entités couvertes avec HIPAA dans les cas d’utilisation requis pour la plateforme de données clients en temps réel.

### Pourquoi les perspectives de santé de Real-Time CDP devraient-elles acheter Healthcare Shield ?

En tant que module complémentaire de Real-Time CDP, Healthcare Shield met à niveau l’application vers un statut &quot;prêt pour le HIPAA&quot;. Cela signifie que l’application a mis en place les mesures de protection pour tirer parti de l’IPS conformément aux exigences de la HIPAA. En outre, avec Healthcare Shield, l’Adobe est prêt et en mesure d’autoriser le client à importer certains types de données personnelles sensibles autorisées dans l’application prête pour le HIPAA. Adobe signera des accords d’association d’entreprise (BAA) avec des clients qui accordent une licence Healthcare Shield pour une application compatible basée sur Platform.

### Quels types de données sont autorisés pour Real-Time CDP avec Healthcare Shield (et lesquels ne le sont pas) ?

Avec Healthcare Shield, les marques peuvent introduire l’intégrité sanitaire suivante dans les applications basées sur Platform telles que Real-Time CDP (&quot;Données personnelles sensibles autorisées&quot;) : les informations financières, médicales ou de santé d’une personne. Mais nous excluons spécifiquement les données qui peuvent être utilisées pour identifier la toxicomanie, la santé mentale, les dossiers de santé génétique ou les dossiers de santé d&#39;un mineur, numéro de compte complet, numéro de carte de crédit complet, identifiants gouvernementaux (comme SSN), et les informations personnelles des enfants protégés par toute loi de protection de l&#39;enfance (comme les informations personnelles définies en vertu de la loi américaine sur la protection de la vie privée en ligne des enfants (COPPA))).

### Avec Healthcare Shield, les clients Real-Time CDP peuvent-ils utiliser n’importe quel type d’IIP pour créer des audiences et les activer ?

Même lorsqu’un client peut importer des données personnelles sensibles autorisées dans des applications natives à Platform, les clients doivent comprendre qu’ils sont seuls responsables de la conformité à toutes les réglementations applicables et de l’obtention des autorisations, consentements, autorisations et autorisations appropriées de la part des consommateurs pour utiliser les données de la manière prévue.

### Quelles sont les nuances de l’ingestion et de l’activation de données client avec des applications d’Adobe non compatibles avec HIPAA ?

Il est interdit à un client d’utiliser, d’ingérer, de collecter, de partager ou d’intégrer des données personnelles sensibles autorisées à des applications et services d’Adobe non compatibles avec HIPAA. Par exemple, un client ne doit pas activer les segments qui contiennent une API dans les applications telles que Audience Manager, Adobe Target et Adobe Analytics. Les clients qui accordent des licences pour Healthcare Shield peuvent ingérer des données personnelles sensibles aux autorisations ou des données personnelles autorisées dans des applications d’Adobe prêtes pour le HIPAA, que la source de données soit considérée comme prête ou non pour le HIPAA.

### Quelles sont les nuances de l’ingestion et de l’activation de données client avec des applications non compatibles avec les HIPAA ?

Un client qui accorde une licence pour Healthcare Shield doit faire preuve d’un bon jugement pour déterminer où il active des segments qui contiennent des PHI en dehors des applications d’Adobe. Adobe ne contrôle pas et n’est pas responsable des fournisseurs tiers et les données envoyées par un client à un fournisseur tiers peuvent ne pas prendre en charge le traitement des données conformément aux libellés d’utilisation des données d’Adobe dans le schéma des clients. De plus, Adobe ne peut pas fournir de conseils juridiques à nos clients.

## Cas d’utilisation clés des soins de santé

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

|**Cas d’utilisation standard de l’Édition B2C RTCDP**|**Description**| | : | : | |Collecte de données en flux continu|<p>- Modèles de données normalisés et flexibles utilisables sur les connexions d’Adobe et non d’Adobe</p><p>- Schémas de données basés sur les personnes et les comptes conçus pour le marketing B2C</p><p>- La gestion des balises et le transfert d’événement collectent et distribuent des données au niveau de l’événement en temps réel.</p><p>- Profils optimisés qui accélèrent le délai de diffusion de l’expérience</p>| |Gestion des profils de confiance|<p>- Profils unifiés contenant des données d’attributs du consommateur, de comportement et de préférences</p><p>- Le cadre de gouvernance des données est flexible, transparent et appliqué aux profils unifiés avec création de stratégies et application automatique afin d’empêcher toute utilisation abusive des données. </p>| |Activation en temps réel|<p>- Segmentation par glisser-déposer conçue pour les spécialistes du marketing B2C</p><p>- Résolution des identités au niveau de la personne et du compte et enrichissement des profils pour l’activation cross-canal</p><p>- Expériences client cohérentes par l’orchestration de l’audience et l’activation en temps réel sur les canaux et environnements (Adobe et non-Adobe)</p>| |Acquisition des clients|<p>- Informations sur la conversion d’utilisateurs non authentifiés en utilisateurs reconnus/authentifiés</p><p>- Encourager les utilisateurs non enregistrés à s’inscrire.</p><p>- Augmenter et/ou récupérer les abonnements</p><p>- Analysez les profils client pour comprendre la propension (par ex. . comparer des segments à forte valeur ajoutée avec des segments peu performants et optimiser pour l’acquisition) ; </p>| |Engagement du client|<p>- Ciblez les offres en fonction de la récence du comportement des consommateurs et de l’action de fréquence sur les offres (en ligne et hors ligne).</p><p>- Unifier les propriétés numériques pour une expérience connectée (par exemple, encourager les téléchargements d’applications mobiles et utiliser l’activation de segments sur plusieurs canaux pour connecter des expériences)</p>| |Personnalisation à l’échelle|<p>- Évaluation des segments sur la périphérie pour une personnalisation en temps réel de la même page et de la page suivante</p><p>- Augmentez l’engagement en fournissant des expériences ciblées et uniques aux visiteurs qui abandonnent une session au fil des parcours (par exemple, abandonnez le panier, répétez les visiteurs qui ne parviennent pas à effectuer de conversion).</p><p>- Unifier et connecter les comportements hors ligne et en ligne pour optimiser et impliquer les utilisateurs</p>| |Vente croisée / Mise à niveau|<p>- Conserver les clients tout en développant et en maintenant des relations existantes avec les utilisateurs</p><p>- Stimuler les nouveaux flux de revenus grâce à une unité opérationnelle/marque/offre interentreprises à la valeur de durée de vie du client</p><p>- Obtenir des informations sur les AOV entre les produits et les SKU (par exemple, lots fréquents, respect des prix)</p>| |Rétention/Fidélité de la clientèle|<p>- Réactiver les consommateurs pour fidéliser et éviter l’attrition des clients</p><p>: traitez les recommandations de produits personnalisés pour les clients à forte valeur ajoutée en fonction des préférences et de la propension.</p><p>- Créer une cadence standard d&#39;engagement et d&#39;offres spéciales pour les clients fidèles</p><p>- Liaison des préférences en ligne et hors ligne pour optimiser les offres sur les canaux</p>| |Collaboration de données|<p>- Créer des poignées de main dans une interface utilisateur pour créer des workflows de collaboration de données.</p><p>- (Tirez parti des recoupements de données propriétaires entre les secteurs d’activité pour prendre des décisions commerciales et des campagnes stratégiques éclairées.</p><p>- Ventiler les silos de données et comprendre le parcours client global</p><p>- Respecter les préférences et le consentement par cas d’utilisation</p>| |Efficacité et optimisation des médias/marketing|<p>- Gagnez en efficacité organisationnelle en centralisant et en gérant les canaux de données et d’activation des clients dans un seul système d’enregistrement</p><p>- Prise en charge des campagnes de suppression pour des dépenses/des gains d’efficacité des médias</p><p>- Alignement avec les politiques informatiques via la gouvernance et l’application des politiques</p><p>- Fournir l’accès aux données selon les besoins, en temps réel, pour prendre en charge les campagnes opportunes</p>|

## **3- Capacités techniques pertinentes**
![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

**Différences**:

||**Prêt à l’emploi**|**Bouclier de santé**| | : | : | : | |Cryptage|Cryptage des données dans AEP [documentation officielle](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/encryption.html?lang=en)|<p>Cryptage des données dans AEP [documentation officielle](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/encryption.html?lang=en)</p><p>+</p><p>Clés gérées par le client </p>| |Hygiène des données|<p>**Fondement**: Outil en libre-service permettant aux clients de gérer le cycle de vie des données. Cela inclut la suppression des données client, le champ</p><p>mises à jour de niveau et définition de l’expiration des données sur les jeux de données pour supprimer les données une fois expirées.</p><p>Limite de **10 000 requêtes de suppression** par mois </p><p>Limite de 2 TTL de jeux de données</p>|<p>**Premium**: Étendez la capacité/le seuil quotidiens de la fonctionnalité d’hygiène des données pour traiter des jeux de données plus volumineux en moins de temps.</p><p>Limite de **2 000 000 requêtes de suppression** par mois dans le cadre du Bouclier de santé</p><p>Limite de 20 TTL de jeux de données</p>| |Consentement|<p>**Fondement**: Consentement granulaire et préférences en ajoutant manuellement les attributs liés au consentement et aux préférences à la segmentation de l’audience.</p><p></p>|<p>**Premium**: Créez et appliquez automatiquement des stratégies sur la manière dont les données client doivent être utilisées en fonction du consentement et des préférences.</p><p></p>|

### **Gouvernance :**
- **Hygiène des données**
   - [**Présentation de l’hygiène des données**](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-hygiene/overview.html?lang=en)
   - [**Veille des données sur Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/hygiene/home.html?lang=en)
- **Application des stratégies**
   - [**Présentation de la gouvernance des données**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html?lang=en)
   - [**Présentation des stratégies d’utilisation des données**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/policies/overview.html?lang=en)
   - [**Gouvernance, confidentialité et sécurité dans Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/overview.html?lang=en#consent)

### **Confidentialité :**
- **Consentement**
   - [**Application automatique des stratégies**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/enforcement/auto-enforcement.html?lang=en#consent-policy-evaluation)

### **Sécurité :**
- **Contrôles d’accès**
   - [**Contrôle d’accès basé sur les attributs - Aperçu**](https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html)
- **Audits des activités des utilisateurs**
   - [**Journaux d’audit**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html)
- **Chiffrement amélioré**
   - [**Présentation de la sécurité Adobe Experience Platform**](https://www.adobe.com/content/dam/cc/en/security/pdfs/AEP_SecurityOverview.pdf)
   - [**Chiffrement des valeurs**](https://experienceleague.adobe.com/docs/experience-platform/tags/api/guides/encrypting-values.html?lang=en)
   - [**Cryptage des données dans Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/catalog/data-protection.html)
   - [**Fonctions de mappage de la préparation de données - Hachage**](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html?lang=en#hashing)
- [**Adobe Real-time Customer Data Platform et Healthcare Shield | Adobe Experience Cloud**](https://experienceleague.adobe.com/docs/customer-data-management-voices-events/events/healthcare-shield.html?lang=en)

La diffusion sur l’expérience promet, avec un accès à moins de données. Que vous soyez annonceur, éditeur ou agence, ce webinaire vous aidera à déverrouiller la variable

- [**Présentation des journaux d’audit | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html "https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html")

Découvrez comment les journaux d’audit vous permettent de savoir qui a effectué quelles actions dans Adobe Experience Platform.

- [**Présentation de l’hygiène des données | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/hygiene/home.html?lang=en)

L’hygiène des données Adobe Experience Platform vous permet de gérer le cycle de vie de vos données en mettant à jour ou en purgeant des enregistrements obsolètes ou inexacts.

- [**Application automatique des stratégies | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/enforcement/auto-enforcement.html?lang=en)

Ce document décrit la manière dont les stratégies d’utilisation des données sont automatiquement appliquées lors de l’activation de segments vers des destinations dans Experience Platform.

- [**Présentation du contrôle d’accès basé sur les attributs | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html "https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html")

Ce document fournit des informations sur le contrôle d’accès basé sur les attributs dans Adobe Experience Platform.
## **4 - HIPAA et produits et services d’Adobe**
Adobe continue d’innover et de s’adapter pour répondre aux besoins de ses clients dans le secteur de la santé afin de répondre à leurs besoins spécifiques en matière de confidentialité et de sécurité. 

Voici les [détails](https://www.adobe.com/trust/compliance/hipaa-ready.html).
## **5 - Diagramme de l’architecture de haut niveau**
Produits prêts (et non) pour l’application HIPAA :

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

[https://lucid.app/lucidchart/8a795213-3bfa-43f3-a542-f0de56123afd/edit?invitationId=inv_d3183739-8c07-4ca2-bfd1-16d819b911a6&amp;page=0_0#](https://lucid.app/lucidchart/8a795213-3bfa-43f3-a542-f0de56123afd/edit?invitationId=inv_d3183739-8c07-4ca2-bfd1-16d819b911a6&amp;page=0_0)

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)
## **6- Approche :**
### **Étapes de mise en oeuvre :**
![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

Aspects à prendre en compte à chaque étape :

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

Cette section décrit certaines bonnes pratiques à suivre et se divise en trois phases :
### **Phase d’entretien :**
Le processus d’entretien avec les parties prenantes est essentiel pour comprendre les aspects suivants :

- Objectif : Type de cas d’utilisation : conversion, prospection, engagement, etc.
- Performances : Toutes les attentes de niveau de service
- Sources de données : Web/Analytics, hors ligne/en ligne, CRM, fidélité, etc.
- Volume de données
- Exigences SLT/SLA
- Identités : nombre d’identités, gestion des données authentifiées ou anonymes
- Format des données : JSON, CSV, etc.
- Qualité des données, besoin de transformations des données
- N’importe quel projet de correspondance de segment (partage) avec des partenaires 
- Toute audience externe à importer
- Chiffrement : Clé gérée par défaut ou par le client
- Combinaison de données : est considéré comme un e-PHI
- Collecte de données de consentement - OneTrust, SDK de consentement
- Besoins en matière de destination : Exigences en matière de fréquence et de latence et de contrôle d’accès
- Contrôle d’accès
- Exigences de nettoyage des données
- Exigences de mise à jour des données
- Besoins en matière d’alertes
- Accès aux API

### **Phase de conception :**
Sur la base du processus d&#39;entretien, la phase de conception portera sur les points suivants. Il va sans dire que la documentation de conception doit être révisée et validée. Le document de conception peut couvrir les aspects suivants :

- Valeur des données :
   - Volume : quantité de données ingérées
   - Durée : durée de résidence des données ingérées.
   - Fidélité - Richesse des profils
- Tenez compte des barrières de sécurité AEP ainsi que des exigences SLT/SLA 
- Utilisation de la licence
- Besoins en isolation des données : plusieurs environnements de test dans une ou plusieurs organisations
- Filtrage des données
- Exigences en matière d’hygiène des données (quantité de données et fréquence)
- Processus et méthodologie pour répondre aux exigences en matière de suppression/mise à jour de données 
- Besoins en matière de transformation des données - Mise en amont, préparation des données, Query Service
- Comprendre et déterminer les identités Principal et autres
- [Conception de schéma XDM](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en)
- Déterminer le nombre de jeux de données, profilés ou non profilés
- Conception de la stratégie de fusion
- Gestion des données de consentement
- Gouvernance : Rôles, libellés, stratégies, actions marketing et contrôle d’accès
- [Enrichissement du profil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
- Exigences de conception de la segmentation pour Edge/Streaming/Batch
- Destinations attendues et plans d’activation. Tenez compte des besoins de destination prêts pour le HIPAA uniquement
- Formules pour Analytics
- Alertes
- Ajout des exigences d’accès aux API

### **Phase de mise en oeuvre :**
Une fois le document de conception examiné et approuvé, la phase de mise en oeuvre peut commencer à traiter les domaines suivants :

- Nombre d’environnements de test requis : Dev/Test/Prod
- Contrôle d’accès aux environnements de test
- Méthodologie de déploiement
- Besoins et fréquence TTL (hygiène des données)
- Schéma XDM et contrôle d’accès
- Application du consentement
- Gouvernance : Rôles, libellés, stratégies et actions marketing 
- Segmentation
- Jeux de données et contrôle d’accès
- Configuration de l’hygiène des données
- Configuration des destinations et contrôle d’accès
- Configurer des alertes
- Mise en oeuvre des exigences d’accès aux API
- Test de bout en bout avec des données fictives

