---
title: Plan directeur de Customer Journey Analytics avec Real-time Customer Data Platform
description: Unifiez et analysez les données et les comportements des clients sur l’ensemble du parcours client dans Customer Journey Analytics, publiez l’audience de CJA vers RTCDP.
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 9fe44d93dcc05711c77ce1325b6549bb6c27a860
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 100%

---

# Plan directeur de Customer Journey Analytics avec Real-time Customer Data Platform

Créez et publiez des audiences identifiées dans Customer Journey Analytics (CJA) vers le profil client en temps réel dans Adobe Experience Platform, pour le ciblage et la personnalisation des clients. Idéal pour créer des audiences à l’aide de données historiques ou des audiences plus affinées à partir d’un filtrage granulaire et de champs calculés dans Customer Journey Analytics.

## Guide de publication d’audiences Customer Journey Analytics

Consultez la documentation suivante pour obtenir des conseils sur la mise en œuvre et la configuration de la publication des audiences de Customer Journey Analytics vers Real-time Customer Data Platform. [Documentation](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=fr)

## Architecture des plans directeurs de Customer Journey Analytics

![Diagramme d’architecture](assets/CJA.svg){zoomable="yes"}

## Diagramme des mécanismes de sécurisation pour les plans directeurs de Customer Journey Analytics

* Pour des garde-fous détaillés et des latences de bout en bout, consultez le [document sur les garde-fous de déploiement](../experience-platform/deployment/guardrails.md)

![Diagramme des garde-fous](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable="yes"}

## Questions fréquentes

* S’il n’existe, dans RTCDP, aucun profil correspondant envoyé par CJA, est-ce qu’un nouveau profil est créé ou est-ce que les audiences sont uniquement enregistrées à partir de CJA pour les profils déjà présents ? Un nouveau profil est créé. Par conséquent, si votre implémentation RTCDP est destinée uniquement aux clients connus, les règles d’audience CJA doivent être écrites pour filtrer uniquement les profils comportant des identités connues. Cela permet de s’assurer que le nombre de profils RTCDP n’augmente pas à partir des profils anonymes si vous ne le souhaitez pas.

* Quelles identités CJA envoie-t-il ? CJA envoie les identités qui ont été configurées comme « ID de personne » lors de sa configuration.

* Qu’est-ce qui est défini comme identité principale ? Toute identité que l’utilisateur a sélectionnée lorsqu’il a configuré CJA en tant qu’ID de « personne » principal.

* Le service d’identités traite-t-il également les messages CJA ? En d’autres termes, CJA peut-il ajouter des identités à un graphique d’identité de profil par le biais du partage d’audience ? Non, le service d’identités ne traite pas les messages CJA.