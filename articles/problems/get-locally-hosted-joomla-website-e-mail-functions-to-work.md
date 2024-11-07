<!-- Filename: Get_locally_hosted_Joomla!_website_e-mail_functions_to_work / Display title: E-mail d'hôte local  -->

## Hébergement Local

La plupart des FAI bloquent le port 25 pour empêcher l'envoi d'e-mails depuis le serveur SMTP de votre propre ordinateur. Cela vise à bloquer les spammeurs. Si vous n’avez pas l’intention de faire du spam, vous pouvez utiliser le serveur de messagerie de votre FAI.

Pour utiliser la fonction email depuis le serveur SMTP de votre FAI même si vous hébergez votre propre site Joomla sur votre propre ordinateur, connectez-vous à votre site Joomla en tant que Super Utilisateur et allez à l'onglet **Serveur** de la page **Configuration Globale**. Dans la section **Mail**, vos données devraient ressembler à ce qui suit :

    De l'Email : someone@example.com (habituellement vous)
    Nom de l'Expéditeur : SomeName

    Mailer : SMTP
    Hôte SMTP : smtp.charter.net (Ce que votre FAI vous indique pour leurs serveurs SMTP)
    Chemin Sendmail : /usr/sbin/sendmail
    Port SMTP : 25
    Sécurité SMTP : STARTTLS
    Authentification SMTP : Oui (ou Non)
    Nom d'utilisateur SMTP : johndoe (nom d’utilisateur de l’un de vos comptes e-mail chez votre FAI)
    Mot de passe SMTP : trr33459 (mot de passe de l’un de vos comptes e-mail chez votre FAI)

Envoyez un message de test pour vérifier si cela fonctionne.

Le Nom d'utilisateur, Mot de passe, et Hôte SMTP sont les mêmes champs que vous entrez lors de l'ajout d'un compte Outlook Express, ou Eudora, ou tout client de messagerie que vous utilisez sur votre ordinateur.

Vous pourriez rencontrer des problèmes avec des extensions qui modifient l'adresse *De* dans les e-mails envoyés. Par exemple, l'extension ProjectFork envoie parfois des e-mails comme s'ils provenaient de la personne en charge du projet. Cela peut poser problème car certains serveurs SMTP des FAI n'autorisent pas une adresse "de" qui ne correspond pas au nom d'utilisateur (par exemple, Rogers au Canada). Vous recevrez un message comme celui-ci : "PHPMAILER_FROM_FAILEDname@whatever.com." Une solution de contournement est de vous assurer que vous utilisez toujours une adresse e-mail valide de votre FAI pour vos utilisateurs.

*Traduit par openai.com*

