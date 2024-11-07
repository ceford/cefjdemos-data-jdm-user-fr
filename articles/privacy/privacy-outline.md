<!-- Filename: Help4.x:Components_Privacy_Outline / Display title: Aperçu de la Confidentialité -->

## Contenu

La suite d'outils de confidentialité Joomla se compose des parties suivantes :

- **Composant Administrateur** Gère les demandes de confidentialité des informations utilisateur.
- **Module - Tableau de bord de confidentialité** Ajoute un panneau de confidentialité sur le tableau de bord d'accueil.
- **Module - Demandes de confidentialité** Ajoute un panneau des demandes de confidentialité sur le tableau de bord de confidentialité.
- **Module - État de la confidentialité** Ajoute un panneau d'état de la confidentialité sur le tableau de bord de confidentialité.
- **Élément de menu - Créer une demande** Affiche un formulaire pour présenter une demande d'information. À créer.
- **Plugin - Système - Consentement de confidentialité** Ajoute des champs de consentement aux formulaires d'informations personnelles tels que l'enregistrement. À activer.
- **Plugin - Utilisateur - Conditions générales** Demande le consentement de l'utilisateur aux conditions générales du site. À activer.
- **Plugin - Contenu - Confirmer le consentement** Ajoute une case à cocher obligatoire à un formulaire, par exemple le formulaire de contact de base. À activer.
- **Plugin - Confidentialité - Divers** Davantage de plugins, activés par défaut, sans paramètres importants à définir.

Lors de l'installation, la suite d'outils de confidentialité est prête à être utilisée par l'administrateur sans activer de plugins ni créer d'élément de menu.  

## Flux de travail

Voici une séquence typique d'événements :

- Une demande d'information arrive. Elle doit inclure une adresse e-mail valide pour un sujet de données. Le sujet n'a pas besoin d'être un utilisateur enregistré. Par exemple, le sujet peut être un contact ajouté par un administrateur.
- Si le message n'est pas soumis par le sujet via un formulaire d'information personnelle du site :
  - L'administrateur va à **Utilisateurs → Confidentialité → Demandes → Nouvelle** pour créer une nouvelle demande d'information. Un message est envoyé à l'adresse e-mail fournie, invitant le sujet à confirmer qu'il s'agit d'une véritable demande.
- Si le message est soumis via un formulaire d'information personnelle du site, le sujet reçoit automatiquement un message de demande de confirmation.
- Le sujet sélectionne le lien dans le message e-mail pour ouvrir le formulaire de confirmation. Lors de la soumission, le sujet voit un message de confirmation.
- L'administrateur voit que les messages privés dans la barre de titre ont des messages en attente. Il y aura également un message e-mail système.
- L'administrateur va à **Utilisateurs → Confidentialité → Demandes** et voit que le statut de la demande a changé en **Confirmé**.
- Pour une demande d'exportation de données, il y a des boutons Exporter et E-mail adjacents.
  - L'administrateur sélectionne le bouton Exporter pour jeter un coup d'œil aux données à exporter. Celles-ci sont au format XML mais s'affichent correctement dans Firefox.
  - L'administrateur sélectionne le bouton E-mail pour envoyer les données exportées au sujet.
- Pour une demande de suppression de données, il y a un bouton Supprimer adjacent.
  - L'administrateur sélectionne le bouton Supprimer pour anonymiser les données pour l'utilisateur. L'utilisateur ne peut plus se connecter.
- Sélectionnez l'adresse e-mail du sujet des données pour ouvrir le formulaire de demande d'information à réviser.
- Sélectionnez le bouton Terminer dans la barre d'outils.
- La liste des demandes d'information affiche le statut comme Terminé et les boutons d'action ont disparu.

Notez que cette suite n'affiche pas un formulaire de permissions de cookies.

*Traduit par openai.com*

