<!-- Filename: J3.x:Plugin_Joomla_Update_Notification / Display title: Notification de mise à jour de Joomla! -->

## Icône et Tâche

Il existe deux plugins avec des noms similaires :

* **Icône rapide - Notification de mise à jour Joomla!**
* **Tâche - Notification de mise à jour Joomla!**

Le premier vérifie les mises à jour de Joomla et vous en informe lorsque vous visitez la page du tableau de bord d'accueil. Il a un paramètre : le groupe de ce plugin (cette valeur est comparée à la valeur de groupe utilisée dans les modules d'icônes rapides pour injecter des icônes).

Le second vérifie périodiquement la disponibilité de nouvelles versions de Joomla!. Lorsqu'une nouvelle version est trouvée, il déclenche une tâche pour envoyer un rappel de mise à jour par email aux Super Utilisateurs. L'email peut être personnalisé via *Système → Modèles de mails*.

Les emails envoyés par les plugins du système de notification de mise à jour Joomla! visent à aider à maintenir le logiciel à jour, ce qui aide le site web à rester sécurisé. Les mises à jour doivent être installées dès que possible après leur publication.

## État du Plugin

Les deux plugins distincts peuvent être activés ou désactivés.

- Avec **Icône Rapide ... Désactivée**, l'icône *Vérification de Joomla ...* sur le tableau de bord principal reste inactive, bien que vous puissiez la sélectionner pour accéder à la page de mise à jour de Joomla.
- Avec **Tâche ... Désactivée :** la tâche consistant à envoyer un e-mail n'est pas déclenchée.

## Paramètres des tâches

Depuis le menu Administrateur, allez à **Système / Tâches planifiées** et sélectionnez l'élément **Notification de mise à jour** dans la liste des *Tâches planifiées*. Il y a un certain nombre d'onglets de paramètres et d'informations à consulter et à modifier si nécessaire.

### Fréquence des e-mails de notification

La fréquence d'exécution des tâches est fixée par défaut à 24 heures. Cela signifie que le site Joomla vérifiera une mise à jour du core et de toutes les extensions, plugins, modules et gabarits installés à des intervalles de 24 heures. Une valeur de 0 enverrait un e-mail de mise à jour chaque fois que le site est consulté. 0 est seulement pour les tests !

Notez que la tâche est déclenchée par l'activité du site. Si vous êtes le seul utilisateur, elle sera déclenchée à votre prochaine visite si plus de 24 heures se sont écoulées.

### E-mails des Super Utilisateurs

La notification par e-mail est envoyée uniquement aux utilisateurs qui ont le privilège de Super Utilisateur. Ce champ vous permet de sélectionner quels Super Utilisateurs recevront les notifications par e-mail.

- S'il est laissé vide, tous les Super Utilisateurs du site recevront l'e-mail de notification de mise à jour.
- Pour limiter quels Super Utilisateurs reçoivent la notification de mise à jour, entrez ici les adresses e-mail des Super Utilisateurs. Si plusieurs adresses e-mail de Super Utilisateurs sont utilisées, séparez-les par une virgule.

### Langue de l'e-mail

La notification peut être envoyée dans n'importe quelle langue que vous utilisez sur votre site.

- **Auto (par défaut)** envoie l'e-mail de notification de mise à jour dans la langue par défaut du site.
- Sélectionner une langue autre que Auto (par défaut) force l'envoi des e-mails de notification de mise à jour dans cette langue spécifique.

## Conseils

- Pour désactiver les notifications par e-mail des mises à jour de Joomla!, il suffit de désactiver le plugin.
- Le sujet et le texte du corps de l'e-mail peuvent être modifiés via la liste **Système / Modèles d'e-mails**. Sélectionnez l'élément **Joomla: Notification de mise à jour**. Sur un site multilingue, il sera dans la langue actuellement sélectionnée.
  - **Sujet** Notez que les espaces réservés {SITENAME} – {URL} sont remplacés lorsque le message est envoyé.
  - **Corps** Il y a aussi plus d'espaces réservés là !

*Traduit par openai.com*

