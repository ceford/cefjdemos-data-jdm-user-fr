<!-- Filename: J4.x:User_Actions_Log / Display title: Journal des actions utilisateur  -->

## Introduction

Le composant User Actions Log (com_actionlogs) fournit une infrastructure pour créer un journal d'audit des activités du site web. Les actions qui sont enregistrées peuvent être finement ajustées par l'administrateur du site. Les extensions tierces peuvent s'intégrer au composant pour ajouter des messages personnalisés ou faire traiter par le système les actions standard de l'administrateur.

**Remarque :** Seuls les Super Utilisateurs ont accès au composant User Actions Log.

## Journal des actions de l'utilisateur

Pour afficher la liste du Journal des actions de l'utilisateur :

- Sélectionnez **Utilisateurs → Journal des actions de l'utilisateur** dans le menu Administrateur.

![page de la liste du journal des actions de l'utilisateur](../../../en/images/users/user-actions-log-list.png)

Depuis cette page, un Super Utilisateur a une vue d'ensemble globale de toutes les activités des utilisateurs effectuées sur un site.

- Exporter les éléments sélectionnés au format CSV : ce bouton exporte uniquement les éléments sélectionnés dans la liste visible.
- Exporter tout au format CSV : ce bouton exporte tous les enregistrements. Les filtres sont ignorés.
- Supprimer : ce bouton supprime les éléments sélectionnés.
- Effacer le journal : ce bouton supprime toutes les entrées du journal.
- Options : un formulaire de configuration pour définir les options de journalisation.
```

## Options

Le formulaire Options du Journal des actions de l'utilisateur permet au Super Utilisateur de sélectionner les événements à enregistrer et de décider d'inclure ou non les adresses IP dans les données du journal.

![page des options du journal des actions de l'utilisateur](../../../en/images/users/user-actions-log-options.png)

## Plugins

Le système de journalisation des actions utilise plusieurs plugins :

### Journal d'actions - Joomla

Lorsqu'il est activé, ce plugin enregistre les actions principales des utilisateurs, y compris des actions telles que la connexion/déconnexion, la mise à jour d'article, l'ajout de module. Le plugin n'a pas de paramètres.

### Système - Journal des actions utilisateur

Lorsqu'il est activé, ce plugin définit le nombre de jours après lesquels les journaux seront supprimés. Une valeur de zéro signifiera que les journaux ne sont jamais supprimés automatiquement.

### Confidentialité - Journaux d'actions

Lorsqu'il est activé, ce plugin exporte les données du journal des actions pour une demande de confidentialité d'un utilisateur.

## Module des Dernières Actions

Ce module est affiché uniquement pour les Super Utilisateurs dans le tableau de bord d'accueil.

![module de journal des actions de l'utilisateur](../../../en/images/users/user-actions-log-module.png)

## Comment connecter une extension au système

N'hésitez pas à éditer cette section en l'améliorant ou en la corrigeant.

### Script d'installation du composant

Ajoutez l'extension à la table (`#__action_logs_extensions`) afin qu'elle apparaisse dans la configuration des journaux d’actions utilisateur.
```php
            $extension = 'com_mycomponent';
            $db = Factory::getDbo();
            $db->setQuery(' INSERT into #__action_logs_extensions (extension) VALUES ('.$db->Quote($extension).') ' );
            try {
                // Si l'insertion échoue, elle lancera une RuntimeException
                $result = $db->execute();
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Ajoutez la configuration de l'extension à la table (`#__action_log_config`) pour que vos données d'actions soient capturées.
```php
           $logConf = new stdClass();
            $logConf->id = 0;
            $logConf->type_title = 'transaction';
            $logConf->type_alias = $extension;
            $logConf->id_holder = 'id';
            $logConf->title_holder = 'trans_desc';
            $logConf->table_name = '#__mycomponent_transaction';
            $logConf->text_prefix = 'COM_MYCOMPONENT_TRANSACTION';

            try {
                // Si l'insertion échoue, elle lancera une RuntimeException
                // Insérez l'objet dans la table.
                $result = Factory::getDbo()->insertObject('#__action_log_config', $logConf);
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Bien sûr, il serait préférable de faire quelques vérifications pour s'assurer que l'enregistrement n'existe pas déjà.

### Helper du composant

Dans cet exemple, le helper du composant est utilisé pour effectuer le stockage des actions.
```php
       /**
         * Enregistrer les détails de la transaction dans le journal
         * @param   object  $user    Évite de récupérer l'utilisateur actuel de nouveau.
         * @param   int     $tran_id  L'id de la transaction nouvellement créée ou mise à jour
         * @param   int     $id  Référence d'id transmise à partir du formulaire pour identifier si c'est un nouvel enregistrement
         * @return  boolean True
         */
        public static function recordActionLog($user = null, $tran_id = 0, $id = 0)
        {
                // obtenir les détails du composant tels que l'id
            $extension =  MycomponentHelper::getExtensionDetails('com_mycomponent');
            // obtenir les détails de la transaction pour utilisation dans le journal pour une référence facile
            $tran = MycomponentHelper::getTransaction($tran_id);
            $con_type = "transaction";
            if ($id === 0) { $type = 'Nouvelle '; } else { $type = 'Mise à jour '; }

            $message = array();
            $message['action'] = $con_type;
            $message['type'] = $type . $tran->tran_type . ' - '.$tran->tran_desc . ' $' . $tran->tran_amount;
            $message['id'] = $tran->id;
            $message['title'] = $extension->name;
            $message['extension_name'] = $extension->name;
            $message['itemlink'] = "index.php?option=com_mycomponent&task=transaction.edit&id=".$tran->id;
            $message['userid'] = $user->id;
            $message['username'] = $user->username;
            $message['accountlink'] = "index.php?option=com_users&task=user.edit&id=".$user->id;

            $messages = array($message);

            $messageLanguageKey = Text::_('COM_MYCOMPONENT_TRANSACTION_LINK');
            $context = $extension->name.'.'.$con_type;

            $fmodel = MycomponentHelper::getForeignModel('Actionlog', 'ActionlogsModel');

            $fmodel->addLog($messages, $messageLanguageKey, $context, $user->id);

            return true;
        }

        /**
         * Obtenir le modèle d'un autre composant pour l'utiliser
         * @param   string  $name    Nom du modèle. Optionnel. Par défaut sur le mien pour plus de sécurité.
         * @param   string  $prefix  Préfixe de la classe. Optionnel
         * @param   array   $config  Tableau de configuration pour le modèle. Optionnel
         * @return object   Le modèle
         */
        public function getForeignModel($name = 'Transaction', $prefix = 'MycomponentModel', $config = array('ignore_request' => true))
        {
            \Joomla\CMS\MVC\Model\ItemModel::addIncludePath(JPATH_ADMINISTRATOR . '/components/com_actionlogs/models', 'ActionlogsModelActionlog');
            $fmodel = \Joomla\CMS\MVC\Model\ItemModel::getInstance($name, $prefix, $config);

            return $fmodel;
        }
```
### Formulaire de transaction côté utilisateur

Maintenant que les fondations sont posées, nous devons juste déclencher le processus. Nous capturons des informations sur une transaction qui est créée ou mise à jour et nous avons un modèle appelé `transactionform.php`. C'est dans la méthode Save que nous voulons capturer un journal.
```php
       // Donc, le code précédent ce point vérifie et fait ce qu'il doit faire, puis après l'enregistrement réussi de l'enregistrement, nous vérifions le paramètre de configuration pour voir si la journalisation est nécessaire, nous transmettons les éléments clés à recordActionLog.
            $table = $this->getTable();

            if ($table->save($data) === true) {

                /* ---------------------------------------------------------------- */
                // déclencher le journal de transaction si nécessaire
                $act_log = $params->get('act_log', 0);
                if ($act_log && $table->id) {
                    // rassembler des informations et enregistrer dans une nouvelle entrée de journal d'action
                    MycomponentHelper::recordActionLog($user, $table->id, $data['id']);
                }
                /* ---------------------------------------------------------------- */

                return $table->id;
            } else {
                return false;
            }
```
### Fichier de langue

Enfin, pour aider à la liste des journaux d'actions dans l'administration de Joomla, nous souhaitons définir certains éléments clés de données à afficher dans le fichier de langue en-GB/com_mycomponent.ini.
```ini
    COM_MYCOMPONENT_TRANSACTION_LINK="Utilisateur {username} a créé une transaction ( {type} )"
```

*Traduit par openai.com*

