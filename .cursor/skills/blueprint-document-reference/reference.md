---
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---
# Référence du document de plan directeur — Guide détaillé

## Types de documents

| Type | Objectif | Emplacement / Exemple |
|------|---------|--------------------|
| **Présentation/hub** | Introduit un produit ou une zone ; liens vers des plans directeurs de scénario | par ex. `overview.md`, `journey-optimizer-overview.md` |
| **Plan directeur du scénario** | Cas pratique unique : architecture, étapes, mécanismes de sécurisation | par ex. `real-time-lookup.md`, `journey-optimizer-journeys.md` |
| **TABLE DES MATIÈRES** | Navigation ; ne pas utiliser comme modèle de contenu | `help/blueprints/TOC.md` |

&#x200B;---

## Référence de section complète

### Titre et description (frontMATTER)

- **title** : court, spécifique. Utilisez `[!DNL Product Name]` pour les noms de produits (par exemple, `[!DNL Journey Optimizer]`).
- **description** : Une phrase. Décrivez ce que le plan directeur montre et le résultat (par exemple, « Accès au profil client en temps réel à la périphérie pour la personnalisation web et mobile »).

### Sections du corps

| Section | Quand inclure | Conseils de contenu |
|---------|-----------------|-------------------|
| **Applications** | Toujours pour les plans directeurs de scénario | Liste à puces des produits/solutions Adobe impliqués (par exemple, Real-time Customer Data Platform, collecte de données). |
| **Cas pratiques** | Toujours | Liste à puces des cas d’utilisation commerciale/technique pris en charge par ce plan directeur. |
| **Conditions préalables** | Lorsque la configuration est requise | Produits, sous-domaines, SDK, configuration qui doit être en place. Lien vers Experience League pour les étapes de configuration. |
| **Diagramme d’architecture** | Toujours | Diagramme principal unique (SVG préféré). Utilisez un style cohérent : `style="width:90%; border:1px solid #4a4a4a" class="modal-image"`. Fournissez un texte `alt` significatif. |
| **Mécanismes de sécurisation** | Toujours lorsque le produit dispose de mécanismes de sécurisation | Lien vers les pages officielles du mécanisme de sécurisation d’Experience League. Ajoutez des limites spécifiques au plan directeur (par exemple, TTL, limites de débit) sous forme de puces. |
| **Modèles d’implémentation** | Lorsqu’il existe plusieurs approches | Nommez chaque modèle (par exemple, « Modèle 1 : basé sur l’appartenance à l’audience avec Web SDK ») ; utilisez des puces pour indiquer quand utiliser et pour effectuer des arbitrages. |
| **Étapes d’implémentation** | Pour les plans directeurs de scénario avec un chemin défini | Liste numérotée. Chaque étape : action + lien vers Experience League où réside la procédure. Ne copiez pas les procédures complètes. |
| **Considérations relatives à la mise en œuvre** | Lorsqu’il existe des avertissements importants | Sous-sections (par exemple, considérations d’identité, personnalisation basée sur les attributs). Puces ou paragraphes courts ; liaison pour plus de profondeur. |
| **Documentation connexe** | Toujours | Liens groupés vers Experience League (et éventuellement developer.adobe.com). Consultez la section « Groupes de liens Experience League » ci-dessous. |

### Pages de présentation/hub

- Commencez par 1 à 2 paragraphes sur le produit/la zone et sur ce que couvrent les plans directeurs.
- **Cas pratiques** : peut utiliser `>[!BEGINTABS]` / `>[!TAB ...]` / `>[!ENDTABS]` pour plusieurs catégories.
- **Architecture** : un diagramme principal.
- **Scénarios de plan directeur** ou **Modèles d’intégration** : tableau avec le nom du scénario, une brève description et un lien vers le plan directeur du scénario.
- **Conditions préalables**, **Mécanismes de sécurisation**, **Documentation connexe** : Comme ci-dessus, soyez concis.

&#x200B;---

## Adobe Experience League - Instructions de l’agent

### Quand référencer Experience League

- **Documentation du produit** : fonctionnement d’un produit, flux de l’interface utilisateur, concepts.
- **API** : points d’entrée, paramètres, exemples (Experience Platform, Edge, etc.).
- **Mécanismes de sécurisation** : pages de mécanisme de sécurisation officielles pour le produit ou le service.
- **Tutoriels** : guides détaillés (par exemple, création de schémas, activation de destinations).
- **Configuration** : flux de données, destinations, politiques de fusion, identités, etc.

Ne collez pas de procédures longues d’Experience League dans le plan directeur. Résumer et lier.

### Modèles d’URL

| Type de contenu | URL de base | Exemple de chemin |
|--------------|----------|--------------|
| Documentation Experience Platform | `https://experienceleague.adobe.com/docs/experience-platform/` | `.../profile/home.html`, `.../destinations/catalog/...` |
| Experience League (en) | `https://experienceleague.adobe.com/fr/docs/` | Même structure que ci-dessus avec `/en/`. |
| Journey Optimizer | `https://experienceleague.adobe.com/docs/journey-optimizer/` | `.../using/get-started/guardrails.html` |
| SDK web | `https://experienceleague.adobe.com/docs/experience-platform/web-sdk/` | `.../home.html`, `.../commands/command-responses.html` |
| API du serveur Edge Network | `https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/` | `.../overview.html`, `.../guardrails.html` |
| SDK Mobile | `https://developer.adobe.com/client-sdks/` | `.../home/`, `.../edge/adobe-journey-optimizer-decisioning/` |
| Balises | `https://experienceleague.adobe.com/docs/experience-platform/tags/` | `.../home.html` |
| Tutoriels sur Platform | `https://experienceleague.adobe.com/docs/platform-learn/tutorials/` | `.../profiles/create-merge-policies.html` |

Utilisez le chemin canonique qui correspond au site Experience League actuel (préférez `/en/docs/` lorsque le chemin anglais est connu).

### Formatage des liens en markdown

- **Texte du lien descriptif** : `[Create schemas](https://experienceleague.adobe.com/fr...)` pas « cliquez ici ».
- **Noms de produits dans le texte** : utilisez des `[!DNL Product Name]` selon le style Adobe (par exemple, `[!DNL Real-time Customer Profile]`).
- **Liens externes** : ajoutez des `{target="_blank"}` uniquement lorsque le modèle ou le pipeline le requiert (vérifiez les plans directeurs existants dans le référentiel).

### Documentation connexe — groupes suggérés

Utilisez ces groupes lorsqu’ils s’appliquent :

1. **Configurations de destination** (pour les plans directeurs d’activation/de personnalisation Edge)
2. **Documentation SDK** (Web SDK, Mobile SDK, API du serveur Edge Network, balises)
3. **Profil et segmentation** (profil client en temps réel, politiques de fusion, segmentation)
4. **Tutoriels** (guides détaillés sur la plateforme ou spécifiques aux produits)
5. **Documentation du produit** (page d’accueil du document produit principal ou sous-sections clés)
6. **Mécanismes de sécurisation** (s’il n’est pas déjà dans la section Mécanismes de sécurisation)

Exemple :

```markdown
## Related documentation

### Destination configurations
* [Custom Personalization Connection](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/catalog/personalization/custom-personalization)
* [Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/fr/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)

### SDK documentation
* [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=fr)
* [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=fr)

### Profile and segmentation
* [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=fr)
* [Profile Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=fr)
```

&#x200B;---

## Référentiel et table des matières

- **Chemin d’accès du contenu de plan directeur** : `help/blueprints/` (avec des sous-dossiers par zone, par exemple `audience-activation/`, `customer-journeys/journey-optimizer/`).
- **Assets** : colocalisez-le avec le plan directeur (par exemple, `assets/`, `images/`) ou dans un dossier partagé (par exemple, `experience-platform/assets/`).
- **TABLE DES MATIÈRES** : modifiez les `help/blueprints/TOC.md` lors de l’ajout, du changement de nom ou du déplacement de pages de plan directeur. Conserver le frontmaterial (`user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`) et la hiérarchie `+`.

&#x200B;---

## Exemples de références dans ce référentiel

- **Plan directeur de scénario (formulaire long)** : `help/blueprints/audience-activation/real-time-lookup.md`
- **Aperçu/hub avec onglets et tableaux** : `help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md`
- **Axé sur les mécanismes de sécurisation** : `help/blueprints/experience-platform/guardrails.md`
- **Navigation** : `help/blueprints/TOC.md`, `help/blueprints/overview.md`

Utilisez-les comme modèles pour l’ordre des sections, le frontend, le placement des diagrammes et l’utilisation des liens Experience League.
