---
title: Conférence
description: Explorez le modèle anatomique de contenu à quatre couches, les modèles d’intégration de contenu AJO et AEM, ainsi que la gouvernance de contenu assistée par l’IA pour une personnalisation à grande échelle.
doc-type: article
solution: Experience Platform
exl-id: 1ac39a70-51f8-426e-97cf-1ff08450d326
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# Conférence

## Objectifs d’apprentissage

- Expliquez pourquoi le contenu, et non les données ou les parcours, est la contrainte principale dans les programmes de personnalisation à grande échelle
- Décrire le modèle d’anatomie du contenu à quatre couches : ressources, fragments, modèles et messages
- Différenciation des fragments AJO et des fragments de contenu AEM, y compris la manière dont chacun gère la propagation
- Mappez les étapes du cycle de vie du contenu de création, de stockage, de gestion, de gouvernance, d’activation et de mesure
- Comparez les trois modèles d’intégration de contenu : AJO autonome, AJO + AEM Assets et AJO + GenStudio for Performance Marketing
- Identifier les signaux architecturaux qui indiquent quand passer d&#39;un modèle à l&#39;autre
- Décrivez les trois couches de fonctionnalités d’IA de la pile Adobe : l’assistant de contenu, les modèles personnalisés Firefly et le service de marque unifiée
- Expliquez le principe de supervision humaine dans la boucle dans les workflows de contenu assistés par l’IA
- Distinguer la véritable personnalisation de l’insertion de prénoms ou de la multiplication de ressources

## Vidéo

Dans cette vidéo, vous découvrirez le modèle d’anatomie du contenu à quatre couches, les trois modèles d’intégration de contenu d’AJO et la façon dont les fonctionnalités d’IA s’intègrent dans un système de contenu régi.

>[!VIDEO](https://video.tv.adobe.com/v/3491063/?quality=12&learn=on)

## Principaux points à retenir

Personalization à grande échelle repose sur trois piliers : le contenu, les données et les parcours. La plupart des entreprises investissent massivement dans l’orchestration des données et des parcours, mais considèrent le contenu comme une préoccupation secondaire, ce qui explique précisément pourquoi le contenu est la première cible des programmes de personnalisation. Pour un architecte AJO, comprendre comment structurer le contenu sous la forme d’un système régi, plutôt que d’une pile de ressources ponctuelles, est ce qui sépare une implémentation évolutive d’une implémentation qui s’effondre sous sa propre prolifération de modèles.

**Dans cette leçon, vous avez abordé les points suivants :**

- La thèse est la suivante : la personnalisation n’échoue pas en raison des données, mais parce que le contenu n’est pas conçu comme un système
- La structure du contenu à quatre couches : Assets (médias atomiques dans la gestion des ressources numériques), Fragments (blocs visuels ou d’expression réutilisables), Modèles (zones verrouillées ou modifiables) et Messages (sortie finale assemblée et prête pour le canal)
- Le cycle de vie du contenu : créer, stocker, gérer, gouverner, activer, mesurer et comment les échecs se répercutent de gauche à droite lorsqu’une étape est ignorée
- Modèle 1, AJO autonome : idéal pour le marché unique, à canal unique, avec moins de 50 variantes, lorsque la vitesse est la contrainte principale ; utilise AEM Assets Essentials comme gestion des ressources numériques groupées de base
- Les fragments AJO sont stockés dans AJO, copiés dans des modèles en tant que doublons, sans mises à jour automatiques et avec une limite de 30 fragments/1 niveau d’imbrication
- Modèle 2, AJO + AEM : idéal pour les variantes multi-marchés, 50+, lorsque la gouvernance est la contrainte principale ; AEM devient le système d’enregistrement, AJO le système d’activation
- Les fragments de contenu d’AEM sont référencés (et non copiés) par AJO. De ce fait, les mises à jour se propagent instantanément dans chaque modèle, parcours et campagne de référencement
- Trois scénarios interrompent silencieusement la propagation des fragments : héritage rompu (fragment déverrouillé), nouveaux attributs de personnalisation ajoutés à un fragment publié et restrictions de libellé Contrôle d’accès au niveau de l’objet (OLAC)
- Modèle 3, AJO + GenStudio for Performance Marketing : idéal pour la génération de variantes à l’échelle de la production et à volume élevé ; nécessite la gouvernance du modèle 2 comme condition préalable stricte
- Les quatre piliers qui maintiennent la génération de l’IA sur la marque : le service de marque unifié, Content Credentials, le traitement humain dans la boucle et l’intégration d’AJO
- Matrice de décision architecturale et modèle de maturité de Content Supply chain (niveaux 1 ad hoc à 5 autonomes) pour diagnostiquer l’emplacement actuel d’un client
- Une véritable personnalisation est une variation intelligente au sein d’un modèle régi unique, et non de champs de fusion de prénom ou de campagnes distinctes par segment
