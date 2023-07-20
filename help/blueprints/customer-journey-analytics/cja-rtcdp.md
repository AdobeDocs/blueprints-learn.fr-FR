---
title: Plan directeur de Customer Journey Analytics avec Real-time Customer Data Platform
description: Unifiez et analysez les données et les comportements des clients sur l’ensemble du parcours client dans Customer Journey Analytics, publiez l’audience de CJA vers RTCDP.
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 70e7bfb3a6d7bad858bd72b6329602bdfb822505
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 100%

---

# Plan directeur de Customer Journey Analytics avec Real-time Customer Data Platform

Créez et publiez des audiences identifiées dans Customer Journey Analytics (CJA) vers le profil client en temps réel dans Adobe Experience Platform, pour le ciblage et la personnalisation des clients. Idéal pour créer des audiences à l’aide de données historiques ou des audiences plus affinées à partir d’un filtrage granulaire et de champs calculés dans Customer Journey Analytics.

## Guide de publication d’audiences Customer Journey Analytics

Consultez la documentation suivante pour obtenir des conseils sur la mise en œuvre et la configuration de la publication des audiences de Customer Journey Analytics vers Real-time Customer Data Platform. [Documentation](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=fr)

## Architecture des plans directeurs de Customer Journey Analytics

![Diagramme d’architecture](assets/CJA.svg){zoomable=&quot;yes&quot;}

## Diagramme des mécanismes de sécurisation pour les plans directeurs de Customer Journey Analytics

* Pour des garde-fous détaillés et des latences de bout en bout, consultez le [document sur les garde-fous de déploiement](../experience-platform/deployment/guardrails.md)

![Diagramme du mécanisme de sécurisation](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable=&quot;yes&quot;}

## Questions fréquentes

* S’il n’existe, dans RTCDP, aucun profil correspondant envoyé par CJA, est-ce qu’un nouveau profil est créé ou est-ce que les audiences sont uniquement enregistrées à partir de CJA pour les profils déjà présents ? Un nouveau profil est créé. Par conséquent, si votre implémentation RTCDP est destinée uniquement aux clients connus, les règles d’audience CJA doivent être écrites pour filtrer uniquement les profils comportant des identités connues. Cela permet de s’assurer que le nombre de profils RTCDP n’augmente pas à partir des profils anonymes si vous ne le souhaitez pas.

* CJA transmet-il les données d’audience sous la forme d’événements de pipeline ou d’un fichier plat qui accède également au lac de données ? Les audiences CJA sont diffusées sur le pipeline vers le service de profil RTCDP, mais les données sont également stockées dans le lac de données sous la forme d’un jeu de données.

* Quelles identités CJA envoie-t-il ? CJA envoie les identités qui ont été configurées comme « ID de personne » lors de sa configuration.

* Qu’est-ce qui est défini comme identité principale ? Toute identité que l’utilisateur a sélectionnée lorsqu’il a configuré CJA en tant qu’ID de « personne » principal.

* Le service d’identités traite-t-il également les messages CJA ? En d’autres termes, CJA peut-il ajouter des identités à un graphique d’identité de profil par le biais du partage d’audience ? Non, le service d’identités ne traite pas les messages CJA.

## Articles de blog connexes

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184)
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17)
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1)
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281)
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34)
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9)
