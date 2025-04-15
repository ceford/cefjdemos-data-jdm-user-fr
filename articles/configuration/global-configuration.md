<!-- Filename: J4.x:Global_Configuration / Display title: Configuration Globale -->

## Aperçu

Lors de l'installation, un site Joomla crée un fichier nommé **configuration.php** à la racine du site. Ce fichier contient les valeurs des variables de configuration qui s'appliquent au site dans son ensemble. Des exemples incluent le nom du site et les informations d'identification de la base de données qui ont été saisies pendant le processus d'installation. Il existe de nombreuses autres variables qui reçoivent des valeurs initiales appropriées.

Le formulaire de Configuration Globale permet à un Super Utilisateur de modifier les variables de configuration pour répondre aux besoins du site. En plus des variables stockées dans configuration.php, le formulaire garde une trace des informations de Journalisation, de Filtrage et de Contrôle d'Accès, dont certaines sont stockées dans la base de données.  

## Capture d'écran

Le formulaire de configuration globale comporte six onglets, dont certains contiennent de longues listes de paramètres. Utilisez le bouton *Basculer l'aide en ligne* dans la barre d'outils pour afficher plus ou moins d'informations sur chaque paramètre.

![Onglet site de configuration globale](../../../en/images/configuration/global-configuration-site-tab.png)

Certains paramètres affichent ou masquent d'autres paramètres lorsqu'ils sont sélectionnés. Par exemple, le bouton **Site hors ligne** affiche plus de champs lorsqu'il est réglé sur *Oui* que lorsqu'il est réglé sur *Non*. Avec l'aide en ligne développée, la plupart des champs sont suffisamment bien documentés pour ne nécessiter aucune explication supplémentaire ici, à l'exception de quelques notes supplémentaires pour l'utilisateur sur chaque onglet.

## Onglet du site

### Panneau du site

- **Nom du site** C'est le nom du site qui apparaît dans le formulaire de connexion de l'administrateur et dans le lien du site dans la barre de titre. Modifiez-le si nécessaire.
- **Site hors ligne** Il existe un [tutoriel](jdocmanual?article=user/configuration/site-offline) distinct sur cet élément.
- **Limite de liste par défaut** fixe le nombre maximum par défaut d'éléments par page dans les vues en liste. Par défaut, ce paramètre est défini sur 20, mais les vues en liste incluent généralement une liste déroulante pour sélectionner d'autres valeurs allant de 5 à 100. Moins de valeurs sont plus rapides à traiter et nécessitent moins de défilement pour l'utilisateur.

### Panneau des métadonnées

- **Description des métadonnées du site** C'est la description des métadonnées par défaut utilisée si une telle description n'est pas précisée dans un champ de description méta d'article ou un champ de description méta de menu. Si les trois sont vides, la description des métadonnées est omise de la sortie de la page. Les moteurs de recherche l'utilisent souvent pour fournir un texte descriptif d'une page. Si elle est absente, les moteurs de recherche peuvent utiliser le texte du contenu de la page, ce qui peut être inapproprié. Une description du but du site d'environ 20 mots est recommandée.
- **Droits de contenu** définit l'entrée des métadonnées *droits*. Si approprié, décrivez ici quels droits ont les autres pour utiliser ce contenu. Cette entrée de métadonnées est omise des pages web si cette entrée est vide. Exemple : Licence Creative Commons Attribution 4.0 International (voir le [bouton de sélection de licence Creative Commons](https://creativecommons.org/choose/)).

### Panneau SEO

SEO est un acronyme pour *l'optimisation pour les moteurs de recherche*. Les réglages de ce groupe modifient le format des URLs pour les pages du site web et cela peut avoir un effet significatif sur le classement de recherche des pages individuelles et du site dans son ensemble. Les URLs SEO sont plus lisibles par les humains.

**Conseil** Après avoir apporté des modifications aux paramètres de ce groupe, actualisez l'une des pages du site web déjà ouvertes dans votre navigateur (Ctrl+R ou Cmd+R le font généralement). Ne pas actualiser peut signifier que le format des liens web internes au site ne correspond plus à ce que Joomla attend et peut donc donner l'apparence de liens brisés.

**Conseil** Si possible, évitez de modifier les paramètres SEO une fois que le site est établi. Faire ainsi peut entraîner des liens brisés provenant d'autres sites et peut-être une diminution temporaire du classement dans les moteurs de recherche.

- **Alias Unicode** Modifier ce paramètre ne change pas rétroactivement les alias, cela ne fait que modifier le comportement de génération automatique d'alias pour l'édition et la création de contenu futurs. *Translittération* (Non) est le paramètre par défaut.

### Panneau des cookies

- **Domaine des cookies** Remplace le domaine de cookie par défaut du site par le domaine ajouté ici. La situation la plus probable où cela serait nécessaire est lorsque le site Joomla est "relié" à d'autres sites (par exemple forum ou e-commerce) dans des sous-domaines du site Joomla. Le domaine de cookie par défaut peut être quelque chose comme `www.example.com`, mais utiliser `.example.com` (notez le point devant) ici livrera des cookies valides pour tout sous-domaine de example.com.
- **Chemin des cookies** Remplace le chemin par défaut du site pour lequel le cookie est valide par le chemin ajouté ici. Cela peut être nécessaire si vous avez plusieurs installations Joomla dans des dossiers frères.

## Onglet Système

![Onglet système de configuration globale](../../../en/images/configuration/global-configuration-system-tab.png)

### Panneau de débogage

Les éléments de ce panneau sont bien expliqués par l'aide en ligne. Cependant, si vous rencontrez un problème qui empêche l'accès normal à l'interface Administrateur, vous devrez peut-être configurer le système de débogage en modifiant le fichier configuration.php avec un éditeur de texte. Sur la plupart des systèmes d'hébergement basés sur Linux, les permissions de fichier sont définies sur 444, ce qui empêche la sauvegarde depuis un éditeur de texte. Changez la permission en 644 avant de modifier le fichier. Puis, définissez \$debug = `true`; et réglez \$error_reporting = `'maximum'`; et sauvegardez. Vous devriez alors obtenir une trace de la pile identifiant exactement où le problème se produit. Vous pouvez utiliser cela pour demander de l'aide sur les Forums. La plupart des problèmes proviennent d'extensions tierces incompatibles ou de problèmes avec l'environnement d'hébergement.

## Onglet Serveur

![Onglet serveur de configuration globale](../../../en/images/configuration/global-configuration-server-tab.png)


### Panneau de messagerie

Un site Joomla doit être capable d’envoyer des e-mails sortants. Entre autres choses, il enverra des messages automatiques au propriétaire du site lorsque des mises à jour seront disponibles. Cependant, certains services d’hébergement restreignent les méthodes par lesquelles les e-mails sortants peuvent être envoyés.

#### Envoyer un e-mail de test

Avant Joomla 5.3, le bouton **Envoyer un e-mail de test** envoyait un message à l’adresse configurée dans le champ **E-mail de l’expéditeur**. Depuis la version 5.3, l’e-mail de test est envoyé directement à l’adresse e-mail de l’administrateur connecté.

- Essayez d'abord PHP Mail et sélectionnez le bouton *Envoyer un mail de test*. Si l'e-mail arrive, tout va bien. Sinon :
- Essayez l'option Sendmail. Si cela ne fonctionne pas :
- Essayez l'option SMTP. Cela doit être configuré pour un serveur de messagerie spécifique. Cela pourrait être celui fourni par votre service d'hébergement. Cela pourrait être un compte GMail.
- **Hôte SMTP** Le nom d'hôte du serveur SMTP (par exemple *smtp.exemple.com*).
  - **Port SMTP** Le port à utiliser lors de la connexion au serveur SMTP. Ce sera généralement *25* quand la sécurité SMTP est réglée sur *Aucune*, ou *465* ou *587* quand la sécurité SMTP est réglée sur `SSL/TLS` ou `STARTTLS`. Demandez à votre fournisseur de service SMTP quel port utiliser.
  - **Sécurité SMTP** La forme de sécurité requise par le serveur SMTP : *Aucune*, *SSL/TLS* ou *STARTTLS*. La valeur par défaut est *Aucune*.
  - **Authentification SMTP** Indique si le serveur SMTP externe nécessite une authentification avant d'accepter les courriels sortants. La valeur par défaut est *Non*.
  - **Nom d'utilisateur SMTP** Le nom d'utilisateur à utiliser lors de la connexion au serveur SMTP en mode SSL ou TLS. Peut rester vide s'il n'y a pas d'authentification SMTP.
  - **Mot de passe SMTP** Le mot de passe à utiliser lors de la connexion au serveur SMTP en mode SSL ou TLS. Peut rester vide s'il n'y a pas d'authentification SMTP.

### Utilisation de Gmail comme serveur de messagerie

Si vous avez un compte Gmail fonctionnel, vous pouvez utiliser Gmail comme votre serveur de messagerie en le configurant dans la configuration globale. Dans l'onglet serveur, configurez les éléments suivants :

- Mailer : SMTP
- Hôte SMTP : smtp.gmail.com
- Port SMTP : 465
- Sécurité SMTP : SSL/TLS
- Authentification SMTP : Oui
- Configurez les deux lignes suivantes avec vos informations. Vous devez utiliser un mot de passe d'application spécifique (ASP), décrit ci-dessous.
- Nom d'utilisateur SMTP : votre nom d'utilisateur gmail
- Mot de passe SMTP : le mot de passe d'application spécifique (ASP) que vous avez généré, décrit ci-dessous.

Les combinaisons suivantes fonctionnent également :

- Port SMTP : 587
- Sécurité SMTP : STARTTLS
- Port SMTP : 25
- Sécurité SMTP : STARTTLS

#### Notes

- Le module SSL n'a pas besoin d'être activé dans Apache.
- L'extension OpenSSL doit être activée dans PHP. Les détails peuvent être trouvés sur la [page d'installation php.net](https://www.php.net/manual/en/openssl.installation.php).
- Si vous utilisez WAMP sur Windows, le module openssl n'est pas activé par défaut et vous devez l'activer. Pour ce faire :
  - Ouvrez le fichier php.ini et décommentez la ligne `extension=php_openssl.dll` en supprimant le point-virgule ; au début de la ligne.
  - Sauvegardez le fichier php.ini et redémarrez le service Apache.
- Si vous utilisez la vérification en deux étapes dans Gmail, vous devez ajouter un nouveau mot de passe dans Paramètres - Comptes - Modifier les paramètres des comptes - Autres paramètres du compte Google - Sécurité - Vérification en deux étapes - Gérer vos mots de passe spécifiques à une application.
- Lorsque le nouveau mot de passe spécifique à l'application (ASP) est présenté en groupes de quatre caractères séparés par des espaces, assurez-vous de **NE PAS saisir les espaces** dans le mot de passe SMTP dans les paramètres du serveur de messagerie dans Joomla.
- Pour les mots de passe spécifiques à l'application (ASP) : Voir la page de support Google sur la façon de [se connecter avec des mots de passe d'application](https://support.google.com/accounts/answer/185833).
- Vérification en deux étapes : Voir la page de support Google sur comment [activer la vérification en deux étapes](https://support.google.com/accounts/answer/185839).

## Onglet Journalisation

![Onglet de configuration globale du site](../../../en/images/configuration/global-configuration-logging-tab.png)

En fonctionnement normal, un site Joomla doit avoir la journalisation désactivée. S'il y a des problèmes, vous pouvez activer la journalisation en définissant le champ **Journaliser presque tout** sur `Oui`. La fonction **Journaliser l'API obsolète** est vraiment réservée aux développeurs. Le champ **Chemin vers le dossier des journaux** vous indique où chercher les journaux si vous avez configuré la journalisation pour faciliter le débogage. Les journaux d'erreurs que vous y trouvez sont uniquement ceux interceptés par Joomla. Il peut y avoir d'autres erreurs qui n'apparaîtront que dans les journaux d'erreurs de votre serveur.

## L'onglet Filtres de texte

![Onglet de configuration globale du site](../../../en/images/configuration/global-configuration-filters-tab.png)

Les paramètres de filtrage du texte seront appliqués à tous les champs de l'éditeur de texte soumis par les utilisateurs des groupes sélectionnés. Ces options de filtrage offrent plus de contrôle sur le HTML que vos fournisseurs de contenu soumettent. Vous pouvez être aussi strict ou libéral que nécessaire pour répondre aux besoins de votre site. Le filtrage est optionnel et les paramètres par défaut offrent une bonne protection contre le balisage couramment associé aux attaques sur les sites web.

## Onglet Permissions

![Onglet du site de configuration globale](../../../en/images/configuration/global-configuration-permissions-tab.png)

Les permissions contrôlent ce que les utilisateurs de chaque groupe d'utilisateurs peuvent voir et faire. Les entrées dans l'onglet Permissions définissent les autorisations par défaut pour le site.

Il existe des descriptions complètes de l'utilisation des paramètres sous cet onglet et des principes généraux de fonctionnement et de configuration des permissions dans un [Tutoriel sur la Liste de Contrôle d'Accès](jdocmanual?article=user/users/access-control).

*Traduit par openai.com*

