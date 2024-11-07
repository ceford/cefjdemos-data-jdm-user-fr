<!-- Filename: How_to_debug_SMTP_mail_in_Joomla_4 / Display title: SMTP mail et Gmail -->

## Introduction

Sur la page de configuration globale, dans le panneau serveur, il y a une option pour sélectionner un agent de distribution de courrier. Le paramètre par défaut est *PHP Mail*. Si cela ne fonctionne pas, il peut être conseillé d'utiliser SMTP. Cela utilise le même mécanisme que votre application de messagerie. Il y a plusieurs paramètres que vous devez ajuster correctement. En résumé :

Allez à **Configuration globale** et sélectionnez l'onglet **Serveur**. Recherchez le panneau *Mail* vers le bas du formulaire.

- **Mailer** doit être réglé sur SMTP. Plusieurs champs supplémentaires apparaissent.
- **Hôte SMTP** Par défaut, c'est localhost, mais cela est peu susceptible de fonctionner. Il doit être réglé sur l'hôte qui gère votre courrier sortant, par exemple un compte Gmail.
- **Port SMTP** Par défaut, c'est 25. Vérifiez que c'est la valeur attendue par votre hôte SMTP.
- **Sécurité SMTP** Par défaut, c'est *Aucune*, mais vous aurez probablement besoin de STARTTLS.
- **Authentification SMTP** Cela peut ne pas être nécessaire si vous utilisez un réseau domestique qui n'exige pas d'authentification pour les courriels sortants. Sinon :
- **Nom d'utilisateur SMTP** et **Mot de passe SMTP** entrez les valeurs que vous utilisez pour accéder à votre compte de messagerie sur Internet.
- Sélectionnez le bouton **Envoyer un courrier de test**.

## Utilisation de Gmail

Si vous avez un compte Gmail fonctionnel, vous pouvez utiliser Gmail comme serveur de messagerie en le configurant dans la configuration globale.

Dans l'onglet serveur, définissez les paramètres suivants :

- Mailer : SMTP
- Hôte SMTP : smtp.gmail.com
- Port SMTP : 465
- Sécurité SMTP : SSL/TLS
- Authentification SMTP : Oui
- Configurez les deux lignes suivantes avec vos informations. Vous devez utiliser un mot de passe spécifique à une application (ASP), décrit ci-dessous.
- Nom d'utilisateur SMTP : votre nom d'utilisateur Gmail
- Mot de passe SMTP : le mot de passe spécifique à l'application (ASP) que vous avez généré, décrit ci-dessous.

Les combinaisons suivantes fonctionnent également :

- Port SMTP : 587
- Sécurité SMTP : STARTTLS
- Port SMTP : 25
- Sécurité SMTP : STARTTLS

Le module SSL n'a pas besoin d'être activé dans Apache.

L'extension OpenSSL doit être activée dans PHP. Les détails peuvent être trouvés sur la [page d'installation php.net](https://www.php.net/manual/en/openssl.installation.php).

Si vous utilisez WAMP sous Windows, le module openssl n'est pas activé par défaut et vous devez l'activer. Pour ce faire :

1. Ouvrez le fichier php.ini et décommentez la ligne `extension=php_openssl.dll` en supprimant le point-virgule ; au début de la ligne.
2. Enregistrez le fichier php.ini et redémarrez le service Apache.

Notez que si vous utilisez la vérification en deux étapes dans Gmail, vous devez ajouter un nouveau mot de passe dans Paramètres - Comptes - Modifier les paramètres des comptes - Autres paramètres du compte Google - Sécurité - Vérification en deux étapes - Gérer vos mots de passe spécifiques à l'application.

Lorsque le nouveau Mot de Passe Spécifique à l'Application (ASP) est présenté sous forme de groupes de quatre caractères séparés par des espaces, assurez-vous de **ne PAS entrer les espaces** dans le mot de passe SMTP dans les paramètres du serveur de messagerie dans Joomla.

- Mots de Passe Spécifiques aux Applications (ASP) : Consultez la page d'assistance Google intitulée [Connexion avec des mots de passe d'application](https://support.google.com/accounts/answer/185833).
- Vérification en deux étapes : Consultez la page d'assistance Google intitulée [Activer la vérification en deux étapes](https://support.google.com/accounts/answer/185839).

## Débogage

Si le courrier n'est pas envoyé ou n'arrive jamais :

- Sélectionnez **Plugins** dans le **Tableau de Bord Principal → panneau du Site**.
- Trouvez et activez le plugin **System - Debug** et configurez-le :
- Définissez **Groupes Autorisés** sur *Super Utilisateurs* pour restreindre la sortie du débogueur à votre propre session de connexion à la fois dans le backend et le frontend. Si vous ne souhaitez pas vous connecter au frontend en tant que Super Utilisateur, créez un groupe d'utilisateurs unique pour vos activités de test et sélectionnez ce groupe d'utilisateurs dans la liste des groupes d'utilisateurs autorisés.
- **Enregistrer & Fermer**

- Sélectionnez **Configuration Globale** dans le **Tableau de Bord Principal → panneau du Site**.
- Dans l'onglet *Système*, réglez **Déboguer Système** sur *Oui*.
- Dans l'onglet *Serveur*, réglez **Rapport d'erreurs** sur *Maximum*.
- Dans l'onglet *Journalisation*, notez le contenu du *Chemin vers le Dossier de Journalisation*, généralement *\[quelque chose\]/administrateur/logs*.
- Réglez **Journaliser Presque Tout** sur *Oui*.
- Dans le panneau *Journalisation Personnalisée*, réglez le champ *Catégories de Journalisation* sur *mail* (sans guillemets).
- **Enregistrer** pour sauvegarder les paramètres de débogage.
- Dans l'onglet **Serveur**, sélectionnez le bouton *Envoyer un Courriel de Test* en bas de la page.

Si des problèmes surviennent dans le code lors des tests, vous devriez obtenir un *Trace de Pile* qui vous aidera, vous ou d'autres, à diagnostiquer le problème. Cherchez aussi un fichier dans le dossier des journaux avec un nom comme *administrateur/logs/everything.php* et ouvrez-le avec un éditeur de texte. Cela peut aider à voir ce qui a été journalisé lorsque le message a été envoyé.

*Traduit par openai.com*

