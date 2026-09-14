---
title: Jeton d’accès
description: Générez un jeton d’accès serveur à serveur OAuth dans Postman et découvrez les en-têtes requis pour authentifier les appels API AEP.
doc-type: article
solution: Experience Platform
exl-id: e38a1bd4-5a09-40c6-8303-c3770801c864
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%
---

# Jeton d’accès

## Présentation de la sécurité des API



Pour établir une connexion d’API sécurisée à un produit Adobe, Adobe fournit la création d’informations d’identification de serveur à serveur OAuth. Pour ce faire, vous devez d’abord créer un projet de développement dans le Adobe Developer Console. Pour pouvoir accéder au Developer Console, des droits de développeur doivent vous avoir été attribués dans le Adobe Admin Console. Une fois que vous disposez de ces droits, vous créez des projets de développement qui utilisent diverses API liées au produit Adobe. À ce stade, vous utilisez les informations d’identification de serveur à serveur OAuth. Pour générer un jeton d’accès, vous devez transmettre un certain ensemble de revendications au service Identity Management (IMS) d’Adobe. Pour les informations d’identification de serveur à serveur OAuth, un exemple d’appel ressemble à ceci :

```curl
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3?client_id={CLIENT_ID}' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'client_secret={CLIENT_SECRET}&grant_type=client_credentials&scope={SCOPE}'
```

>[!NOTE]
>
>Apprenez-en davantage sur le processus e2e pour créer le projet de développement à l’aide des informations d’identification de serveur à serveur OAuth [ici](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens). Pour le bootcamp, cette étape est délibérément simplifiée.



## Adobe Experience Platform + Adobe IMS

Chaque requête envoyée à un service Adobe doit inclure le jeton d’accès dans l’en-tête d’autorisation avec le secret client généré lors de la création du projet de développement. En outre, Experience Platform et ses applications associées nécessitent deux autres paramètres d’en-tête pour chaque requête.

- `x-gw-ims-org-id` - ce paramètre spécifie le `IMS Org` auquel appartient la demande et garantit que le traitement des demandes est résolu sur l’environnement SaaS approprié
- `x-sandbox-name` - ce paramètre spécifie le sandbox dans lequel traiter la demande dans Experience Platform

Maintenant que vous comprenez un peu comment Adobe sécurise ses API et ce qui est nécessaire pour les utiliser, utilisez-les maintenant.

>[!CAUTION]
>
>Ne pas spécifier le paramètre `x-sandbox-name` n’entraîne pas l’échec de la requête. Au lieu de cela, elle définit par défaut la requête à traiter dans le sandbox `default` automatiquement configuré avec n’importe quel environnement Experience Platform

>[!NOTE]
>
>Ce bootcamp comprend un projet de développeur et un fichier d’environnement Postman avec toutes les valeurs nécessaires pour demander une `access_token`. Ce fichier d’environnement est ce que vous avez chargé lors des étapes précédentes du Lab

## S’authentifier avec Postman

1. Lancez Postman, accédez au répertoire intitulé `IMS Authenticate` et ouvrez la requête en cliquant dessus
1. Un menu déroulant d’environnement s’affiche ensuite dans le coin supérieur droit de Postman. Sélectionnez l’environnement de `AEP Bootcamp` dans la liste déroulante.
1. Exécutez maintenant l’appel en cliquant sur le bouton « Envoyer »

![Requête Postman après l’envoi de l’appel d’authentification IMS pour générer un jeton d’accès](assets/access-token-execute-ims-authenticate-request.png)

Une réponse réussie doit se présenter comme suit :

```none
200 OK Successful Authentication
```

Réponse réussie

```json
{
    "token_type": "bearer",
    "access_token": "<value>",
    "expires_in": 86399979
}
```

`token_type` - est toujours de type porteur

`access_token` : prouve l’autorisation et est obligatoire dans l’en-tête d’autorisation de tous les appels API.

`expires_in` - millisecondes avant l’expiration du jeton d’accès (période d’expiration de 24 heures aujourd’hui)

>[!SUCCESS]
>
>Félicitations ! Vous vous êtes authentifié avec succès et votre jeton d’accès est maintenant enregistré dans votre fichier d’environnement



## Erreurs courantes

### Jeton non valide

Cette erreur se produit lorsque le `private_key` de votre fichier d’environnement est malformé ou n’est plus valide. Si cette erreur s’affiche, vérifiez que vous avez copié la clé entière, y compris les sauts de ligne

Exemple :

```none
-----BEGIN PRIVATE KEY----- 
some uber long varchar set is here
-----END PRIVATE KEY----- 
```

```none
400 invalid_token
```

>[!NOTE]
>
>Applicable uniquement lors de l’utilisation de l’authentification basée sur JWT

### IMS\_ORG non valide

Cette erreur se produit lorsque vous oubliez de définir votre environnement Postman à partir de la liste déroulante

![IMS_ORG introuvable dans l’erreur d’environnement actif lorsqu’aucun environnement Postman n’est sélectionné](assets/access-token-forgot-to-select-postman-environment.png)

>[!NOTE]
>
>N’oubliez pas de définir votre environnement Postman lors de l’exécution des appels API
>
>![Sélection de l’environnement du Bootcamp AEP dans le menu déroulant Environnement Postman &#x200B;](assets/access-token-set-postman-environment.png)
