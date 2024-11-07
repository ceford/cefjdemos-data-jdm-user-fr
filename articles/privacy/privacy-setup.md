<!-- Filename: J4.x:Privacy_Setup / Display title: Configuration de la confidentialité -->

## Composant de Confidentialité

Le composant de confidentialité est utilisé pour gérer les informations de confidentialité, recueillir des demandes d'information ou des demandes de suppression d'informations. Il est basé sur les adresses e-mail, donc il s'applique principalement aux utilisateurs enregistrés qui doivent fournir une adresse e-mail lors de l'enregistrement. Il s'applique également aux données sur les utilisateurs non enregistrés dont les adresses e-mail ont été fournies via le composant Contacts. Il n'implémente pas l'autorisation d'utilisation des cookies ou du suivi requise par le RGPD.

Lorsque des informations personnelles identifiables sont collectées, vous devez vous assurer :

- Que l'utilisateur est informé des raisons pour lesquelles vous demandez ces informations dans un langage clair et compréhensible.
- Que l'utilisateur connaît les données que vous collectez à son sujet.
- Que l'utilisateur sait pour quel usage vous allez utiliser les données.
- Que l'utilisateur a consenti activement à votre utilisation des données.

En général, ces informations sont décrites dans un article de Politique de Confidentialité.

## Tableau de bord de la confidentialité

Le tableau de bord de la confidentialité fournit un résumé des **Requêtes de confidentialité** et du **Statut de la confidentialité** du site. Pour y accéder :

- Sélectionnez **Utilisateurs → Confidentialité** dans le menu Administrateur.

![tableau de bord de la confidentialité](../../../en/images/privacy/privacy-dashboard.png)

Il y a deux modules affichés par défaut dans le tableau de bord de la confidentialité :

### Requêtes de confidentialité

Ce module fournit un résumé des demandes d'information en cours.

### Statut de la confidentialité

Ce module montre l'état des options auxquelles les propriétaires du site doivent prêter attention :

- **Politique de confidentialité publiée** définir un article de Politique de confidentialité dans le plugin **Système - Consentement de confidentialité**.
- **Élément de menu de formulaire de demande publié** définir un élément de menu pour permettre aux utilisateurs authentifiés de soumettre des demandes.
- **Demandes urgentes en attente** vérifier les demandes confirmées plus anciennes que l'âge spécifié dans les paramètres du composant (par défaut 14 jours) et alerter le propriétaire du site de toute demande nécessitant une attention urgente.
- **Envoi de courrier activé** le site doit pouvoir envoyer des e-mails pour traiter les demandes d'information.
- **Chiffrement de la base de données** ceci est pertinent lorsqu'une base de données distante est utilisée.

## Plugin : Système - Consentement à la confidentialité

Si ce plugin est désactivé, le panneau d'état de la confidentialité du tableau de bord indiquera que la politique de confidentialité est **Non Disponible** et fournira un lien vers le formulaire de modification du plugin. Lorsqu'il est activé, le plugin demande à tout nouvel utilisateur s'inscrivant sur votre site de consentir à la politique de confidentialité. Tous les utilisateurs existants seront redirigés vers leur profil utilisateur afin qu'ils puissent consentir.

Pour configurer les consentements :

- Sélectionnez **Accueil du Tableau de Bord** → **Plugins** dans le menu Administrateur.
- Trouvez le plugin **Système - Consentement à la confidentialité** (à ne pas confondre avec le plugin Confidentialité - Consentements).
- Choisissez d'ouvrir le formulaire d'entrée de données du plugin.

![plugin système consentement à la confidentialité](../../../en/images/privacy/plugin-system-privacy-consent.png)

- Définissez l'**État** sur **Activé**.
- Optionnel : Sélectionnez ou créez un article à lier depuis le formulaire d'inscription. Ou définissez le Type de confidentialité sur Élément de Menu et Sélectionnez ou Créez un élément de menu.
- Sélectionnez l'onglet **Expiration** et **Basculer l'aide en ligne** pour une explication de chaque champ. Activez et ajustez les paramètres **si** vous souhaitez que les consentements expirent après un nombre de jours sélectionné.

### Notes sur le consentement à la confidentialité pour les sites multilingues :

**Courte Politique de Confidentialité et Message de Redirection** Si vous utilisez le texte par défaut, alors il s'affichera dans la langue de l'utilisateur. Il n'est pas possible de traduire le texte personnalisé. Si vous souhaitez personnaliser le texte et l'afficher en plusieurs langues, vous devriez laisser ce champ vide et utiliser la fonctionnalité de substitution de langue de Joomla pour personnaliser les chaînes linguistiques `PLG_SYSTEM_PRIVACYCONSENT_NOTE_FIELD_DEFAULT` et `PLG_SYSTEM_PRIVACYCONSENT_REDIRECT_MESSAGE_DEFAULT` pour chaque langue installée.

**Article de Confidentialité** et **Élément de Menu de Confidentialité** Si vous associez cet article ou élément de menu avec des alternatives dans d'autres langues, alors la politique de confidentialité s'affichera dans la bonne langue pour l'utilisateur.  

## Plugin : Utilisateur - Conditions générales

Lorsqu'il est activé, ce plugin demande à tout nouvel utilisateur s'inscrivant sur votre site de consentir aux Conditions générales d'utilisation de votre site. Tous les utilisateurs existants seront redirigés vers leur Profil utilisateur afin qu'ils puissent consentir.

Ce plugin n'est pas activé par défaut. Pour l'activer :

- Sélectionnez **Tableau de bord d'accueil → Plugins** dans le menu Administrateur.
- Trouvez le plugin **Utilisateur - Conditions générales**.
- Sélectionnez le plugin pour ouvrir le formulaire de saisie de données.
- Réglez le **Statut** sur **Activé**.
- Optionnel : Sélectionnez ou créez un article à lier à partir du formulaire d'inscription.

### Notes sur Utilisateur - Conditions générales pour les sites multilingues

**Conditions générales courtes** : Si vous utilisez le texte par défaut, il sera affiché dans la langue de l'utilisateur. Il n'est pas possible de traduire le texte personnalisé. Si vous souhaitez personnaliser le texte et l'afficher dans plusieurs langues, vous devez laisser ce champ vide et utiliser la fonctionnalité de substitution linguistique de Joomla pour personnaliser les chaînes de langue `PLG_USER_TERMS_NOTE_FIELD_DEFAULT` pour chaque langue installée.

**Article des Conditions générales** : Si vous associez cet article à des alternatives dans d'autres langues, la politique de confidentialité sera affichée dans la langue appropriée pour l'utilisateur.

## Vue de consentement d'inscription utilisateur

Ensemble, les deux plugins apparaissent sur le formulaire d'inscription utilisateur comme dans la capture d'écran suivante :

![vue du consentement à la confidentialité du site](../../../en/images/privacy/privacy-consents-site.png)

## Élément de menu : Demande d'informations sur la confidentialité

Les utilisateurs enregistrés peuvent demander un résumé des informations ou leur suppression via un élément de menu. Configuration comme suit :

- Sélectionnez **Menus** → **Menu du bas** dans le menu de l'administrateur (utilisez le menu le plus pratique).
- Entrez un **Titre** approprié, par exemple : **Demande d'informations sur la confidentialité**.
- Utilisez le bouton **Sélectionner** pour ouvrir la boîte de dialogue contextuelle Type d'élément de menu.
- Dans la section **Confidentialité**, sélectionnez l'élément **Créer une demande**.
- Définissez le champ **Accès** sur **Enregistré**.
- **Enregistrer & Fermer**.

Accédez à la vue de votre site et vérifiez que l'élément de menu n'est pas affiché lorsque vous n'êtes pas connecté et qu'il s'affiche après la connexion. Utilisez le lien et essayez l'option **Exporter**. Vous pouvez essayer l'option **Supprimer** plus tard en utilisant un compte fictif. Si une demande est en attente, vous verrez un message d'erreur :

« Votre demande d'information n'a pas pu être créée. Il y a déjà une demande d'information active pour cette adresse e-mail et ce type de demande. Veuillez contacter le propriétaire du site pour des mises à jour sur cette demande. »

## Élément de menu : Confirmation de demande de confidentialité

Pour des raisons de SEF, vous pouvez créer un élément de menu caché pour que l'utilisateur confirme la demande. Cela sera inclus dans le lien envoyé par email.

- Sélectionnez **Menus** → **Menu caché** dans le menu de l'administrateur (créez un menu caché sans position de module assignée, ou voir ci-dessous).
- Entrez un **Titre** approprié, par exemple : **Confirmer la demande de confidentialité**.
- Utilisez le bouton **Sélectionner** pour ouvrir la boîte de dialogue contextuelle Type d'élément de menu.
- Dans la section **Confidentialité**, sélectionnez l'élément **Confirmer la demande**.
- Si vous n'avez pas de menu caché, utilisez votre menu principal et dans l'onglet Type de lien, définissez **Afficher dans le menu** sur **Non**.
- **Enregistrer & Fermer**.

## Éléments du Menu Administrateur

Jetez un coup d'œil aux autres éléments du menu du Composant de Confidentialité.

### Demandes de Confidentialité de l'Administrateur

Cet écran est le lieu central pour traiter et gérer les demandes d'informations des utilisateurs. Veuillez consulter l'article connexe sur le Flux de Travail de Confidentialité pour obtenir des conseils sur le traitement des demandes.

![demandes d'informations de confidentialité](../../../en/images/privacy/privacy-information-requests.png)

### Capacités des Extensions

Cet écran collecte et affiche des informations sur les capacités liées à la confidentialité signalées par les extensions individuelles. Il est destiné à aider à la préparation de documents tels qu'un article de politique de confidentialité ou un article sur les conditions de service.

![capacités d'informations de confidentialité](../../../en/images/privacy/privacy-extension-capabilities.png)

Le contenu de la page provient des chaînes de langue dans le noyau, dans le composant de confidentialité et dans les plugins qui mettent en œuvre l'événement onPrivacyCollectAdminCapabilities. Cela comprend :

- Authentification
- Captcha
- Installateur
- Confidentialité
- Système
- Utilisateur

Les informations seront affichées dans la langue sélectionnée pour la connexion de l'administrateur.

### Consents

Cet écran affiche une liste de consentements, les plus récents en premier. Celle-ci sera dans la langue utilisée dans le formulaire de consentement, généralement lors de l'inscription. Vous pouvez rechercher par nom un utilisateur spécifique. Notez que le consentement à accepter les Termes et Conditions du site n'est pas enregistré ici. Cela figure uniquement dans le Journal des Actions Utilisateur.

![consentements de confidentialité](../../../en/images/privacy/privacy-consents.png)

*Traduit par openai.com*

