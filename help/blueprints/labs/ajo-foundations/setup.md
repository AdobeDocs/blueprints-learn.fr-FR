---
title: Configuration
description: Effectuez les étapes de déploiement du sandbox et de configuration de Postman requises avant de démarrer les ateliers AJO Foundations.
doc-type: article

solution: Experience Platform
exl-id: 7c1a9e3d-5b8f-4a2e-9c6d-3f7b0e4a8c2d
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 1%
---

# Configuration

Avant de commencer les ateliers AJO Foundations, effectuez les étapes de configuration ci-dessous. Les étapes à suivre dépendent de la manière dont vous effectuez ce bootcamp.

## Configuration du sandbox

>[!NOTE]
>
>Si vous participez à un cours ou à un événement de formation en direct, votre sandbox a déjà été déployé pour vous - ignorez cette section et accédez directement à la configuration de Postman ci-dessous.

Si vous ne disposez pas déjà d’un sandbox fonctionnel dans lequel les ressources de Lab sont déployées, procédez comme suit :

- [Configuration de Developer Console](sandbox-setup/developer-console-setup.md)
- [Instructions de déploiement](sandbox-setup/deployment-instructions.md)

## Configuration de Postman

Postman est requis pour les ateliers de ce cours, quelle que soit la manière dont votre sandbox a été configuré. Procédez comme suit avant de continuer :

- [Installation de Postman](postman-setup/postman-installation.md)
- [Importer le fichier d’environnement](postman-setup/import-environment-file.md)
- [Importer la collection d’API](postman-setup/import-api-collection.md)

## Préparation à la demande

Avant de commencer les exercices pratiques, effectuez la configuration Postman ci-dessus. Les élèves qui suivent un apprentissage à leur propre rythme ont également besoin d’un sous-domaine délégué pour les ateliers dépendant des e-mails et des informations d’identification SMS pour le laboratoire de lancement de téléphone Flagship.

## Conditions préalables relatives aux canaux

Deux ateliers plus tard dans ce bootcamp dépendent de comptes externes que seuls les élèves qui suivent leur propre rythme doivent organiser. Si vous suivez un cours ou un événement en direct, ces comptes sont déjà configurés pour vous.

### Sous-domaine délégué

L’atelier [Configurer les canaux e-mail](data-stores/configure-email-channels/overview.md) et tout ce qui en dépend ([Diffusion des messages en action](orchestrated-campaigns/message-delivery-in-action/overview.md), [Excitation après achat](journeys/post-purchase-excitement/overview.md) et [Marques AJO](content-authoring-with-ai/overview.md)) nécessite un sous-domaine délégué à Adobe pour l’envoi d’e-mails. Si vous n&#39;avez pas encore de domaine, enregistrez-en un auprès du bureau d&#39;enregistrement de domaines (par exemple, Namecheap). Ensuite, pour déléguer un sous-domaine (par exemple, `email.yourdomain.com`) à Adobe, suivez les instructions Adobe [délégation de sous-domaine](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/delegate-subdomains/delegate-subdomain).

>[!NOTE]
>
>La propagation de la délégation de sous-domaines peut prendre du temps. Commencez cette délégation bien avant de planifier l’accomplissement du Lab Configurer les canaux e-mail .

### Informations d’identification SMS

Le Lab [lancement téléphonique phare](orchestrated-campaigns/flagship-phone-launch/overview.md) configure un canal SMS via Twilio. Aucun message n’est envoyé, mais vous avez besoin d’informations d’identification de travail pour terminer la configuration. L’option la plus simple est un compte d’évaluation gratuit [Twilio](https://www.twilio.com/try-twilio) — consultez le [guide de prise en main](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account) de Twilio pour savoir comment vous inscrire et trouver votre SID de compte et votre jeton d’authentification.
