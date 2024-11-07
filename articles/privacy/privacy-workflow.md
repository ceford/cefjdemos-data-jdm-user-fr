<!-- Filename: J4.x:Privacy_Workflow / Display title: Flux de Travail de Confidentialité  -->

## Création d'une Demande

Le traitement des demandes d'informations personnelles est le principal objectif du composant de confidentialité. Les utilisateurs peuvent demander un résumé de leurs données personnelles ou demander que toutes leurs données personnelles soient supprimées. Une demande peut être créée soit par un utilisateur authentifié via le formulaire de demande, soit par un super utilisateur.

Dans ce contexte, un utilisateur désigne toute personne ou organisation ayant fait une demande, indépendamment de l'existence ou non d'un compte utilisateur enregistré. Par exemple, des demandes peuvent être adressées à l'administrateur du site par des personnes ou des organisations qui ont été ajoutées au site en tant que contacts.

Les données personnelles sont basées sur les adresses email et le traitement automatisé est limité aux extensions qui rapportent des capacités de confidentialité.

*IMPORTANT* Pour créer et traiter des demandes d'informations, votre site web DOIT être capable d'envoyer des emails en raison de l'exigence pour le propriétaire de l'information de confirmer la demande.

### Demande d'Utilisateur Authentifié

Les utilisateurs enregistrés peuvent soumettre une demande d'information via un lien de menu *Demande d'Information de Confidentialité* disponible uniquement après connexion. Un bon emplacement pour un tel lien est dans le même menu où se trouve un lien vers la **Politique de Confidentialité** du site. Un menu en bas de page dans le pied de page du site est souvent un emplacement privilégié. Lors de la soumission d'une demande d'information, l'utilisateur doit fournir :

- Le type de demande : Exporter ou Supprimer choisi dans la liste déroulante.

![flux de travail de confidentialité demande utilisateur](../../../en/images/privacy/privacy-workflow-user-request.png)

À la soumission, un message indiquera soit que la demande a été acceptée et qu'un email de vérification est en cours :

![flux de travail de demande utilisateur accepté](../../../en/images/privacy/privacy-workflow-user-request-accepted.png)

soit que *Votre demande d'information n'a pas pu être créée. Il y a déjà une demande d'information active pour cette adresse email et ce type de demande. Veuillez contacter le propriétaire du site pour des mises à jour sur cette demande.*

### Création par Super Utilisateur

Par le biais de la page **Confidentialité : Demandes d'Informations**, tout super utilisateur peut créer une nouvelle demande d'information. C'est la seule façon de créer des demandes d'informations pour les utilisateurs qui n'ont PAS de comptes sur le site web. Pour créer une demande :

- Sélectionnez **Utilisateurs → Confidentialité → Demandes** dans le menu de l'Administrateur.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
- Dans le champ **Email**, entrez l'adresse email de l'utilisateur.
- Dans le champ **Type de Demande**, sélectionnez Exporter ou Supprimer dans la liste déroulante.
- **Enregistrer & Fermer**.

Une fois créée, la demande ne peut être modifiée. Elle ne peut être qu'Invalidée ou Traité.

## Confirmation d'une demande

Une fois qu'une demande a été créée, peu importe comment elle est créée, l'utilisateur recevra un email contenant un lien vers un formulaire de confirmation.

![flux de travail de confidentialité confirmation de la demande de l'utilisateur](../../../en/images/privacy/privacy-workflow-user-request-confirm.png)

L'utilisateur doit entrer le jeton fourni dans l'email et soumettre le formulaire. Le jeton est valide pendant 24 heures. Si une demande n'est pas confirmée dans ce délai, elle sera marquée comme **Invalide** dans la liste des demandes de confidentialité et une nouvelle demande doit être soumise.

Une fois que l'utilisateur confirme la demande, un email sera envoyé aux Super Utilisateurs pour indiquer qu'une action est requise.

- Sélectionnez **Utilisateurs → Confidentialité → Demandes** dans le menu Administrateur.
- Les demandes nécessitant une action seront marquées comme **Confirmées**.

![flux de travail de confidentialité liste des demandes d'information](../../../en/images/privacy/privacy-workflow-information-requests-list.png)

## Traitement d'une demande d'exportation

Une fois qu'une demande d'exportation a été confirmée, deux actions sont disponibles pour les super utilisateurs.

- Exporter les données : Cela rassemblera toutes les données concernant le sujet de la demande d'information et créera un fichier XML qui sera téléchargé sur votre ordinateur. Cela permet aux propriétaires du site d'examiner l'exportation des données avant de l'envoyer à l'utilisateur.
- Envoyer l'exportation de données par email : Cela rassemblera toutes les données concernant le sujet de la demande d'information, créera un fichier XML (le même que celui généré par l'action Exporter les données) et enverra un email à l'utilisateur avec le fichier de données exporté en pièce jointe.

**Important :** L'action d'exportation ne peut collecter des données que depuis des extensions qui prennent en charge la confidentialité. Par conséquent, le super utilisateur qui traite la demande doit examiner l'exportation et, si nécessaire, inclure les données contenues dans des extensions qui stockent des données personnelles mais ne disposent pas de support de confidentialité.

## Traitement d'une Demande de Suppression

Une fois qu'une demande de suppression a été confirmée, une seule action est disponible pour les super utilisateurs.

- Supprimer les données : Ce processus anonymisera et/ou supprimera les données relatives au sujet de l'information. Pour les demandes où le propriétaire de l'information dispose également d'un compte utilisateur enregistré, ce processus anonymisera le nom, le nom d'utilisateur et l'adresse email du compte, ainsi que bloquera l'accès au compte et déconnectera l'utilisateur du site s'il est connecté au moment où la demande est traitée.

**Important :** L'action de suppression ne peut collecter des données que depuis des extensions qui disposent d'un support de confidentialité. Par conséquent, l'utilisateur super agissant sur la demande doit examiner l'exportation et, si nécessaire, anonymiser ou supprimer manuellement les données contenues dans des extensions qui stockent des données personnelles mais n'ont pas de support de confidentialité.

Lors de la sélection du bouton **Supprimer les Données**, un message de confirmation **Données Supprimées** apparaît mais la liste des Demandes d'Information : Vie Privée reste inchangée. Les données utilisateur sont supprimées ou anonymisées, mais pas les données dans les tables \#\_\_action_logs, \#\_\_messages et \#\_\_privacy_requests (voir ci-dessous).

## Terminer une demande

Après traitement de la demande, celle-ci doit être marquée comme complétée. Cela indiquera que la demande a été satisfaite et qu'aucune action supplémentaire n'est nécessaire.

- Dans la liste **Confidentialité : Demandes d'information**, sélectionnez l'adresse e-mail de la demande en cours de traitement.
- Dans le formulaire **Confidentialité : Examiner la demande d'information** :
  - Passez en revue les données.
  - Sélectionnez le bouton approprié **Exporter**, **E-mail** ou **Supprimer** dans la barre d'outils si cela n'a pas déjà été fait depuis la vue de liste.
- Sélectionnez le bouton **Compléter** dans la barre d'outils (ou le bouton **Invalider** si la demande est jugée invalide).

![examen du flux de travail de confidentialité demande d'information](../../../en/images/privacy/privacy-workflow-review-information-request.png)

## Enfin

Pour supprimer les données du journal des actions de l'utilisateur :

- Sélectionnez **Utilisateurs → Journal des actions de l'utilisateur** dans le menu Administrateur.
- Recherchez le nom d'utilisateur ou l'adresse email de l'utilisateur supprimé.
- Cochez la case **Tout sélectionner**.
- Cliquez sur le bouton **Supprimer** dans la barre d'outils.

Pour supprimer les données des messages privés et les données des requêtes de confidentialité :

- Il n'existe pas de moyen simple pour supprimer en lot l'un ou l'autre de ces types de données directement depuis Joomla. La méthode la plus rapide consiste à rechercher le nom d'utilisateur (adresse email) dans la base de données avec phpMyAdmin et à supprimer les enregistrements de cette manière. Voici un exemple de capture d'écran :

![suppression du workflow de confidentialité avec phpMyAdmin](../../../en/images/privacy/privacy-workflow-delete-with-phpmyadmin.png)

## Ressources supplémentaires

-  [Guide du développeur pour la suite d'outils de confidentialité](https://docs.joomla.org/Special:MyLanguage/J3.x:Integrate_Extensions_with_the_Privacy_Component)

*Traduit par openai.com*

