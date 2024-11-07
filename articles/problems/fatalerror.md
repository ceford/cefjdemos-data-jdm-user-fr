<!-- Filename: J4.x:FatalError / Display title: ErreurFatale -->

## Introduction

De temps en temps, Joomla peut afficher une page d'erreur au lieu de la page que vous attendiez. Il existe deux types de pages d'erreur :

- La page d'erreur système a un fond rouge. Elle est invoquée s'il y a une erreur grave avant que le modèle du site ou de l'administrateur ne soit rendu.
- La page d'erreur de modèle ressemble au modèle normal du site ou de l'administrateur, mais la zone de contenu est remplacée par un message d'erreur. Ceci est invoqué lorsque l'erreur se produit dans le code de contenu.

### Page d'erreur système

![Page d'erreur fatale du système](../../../en/images/problems/fatal-error.png)

### Page d'erreur de modèle

![Page d'erreur de modèle](../../../en/images/problems/template-error.png)

## Comment Résoudre

Il existe plusieurs raisons possibles pour que des erreurs fatales surviennent. En voici quelques-unes :

- Une modification chez votre hébergeur, par exemple une mise à jour de la version PHP qui n'est pas compatible avec Joomla ou avec une de vos Extensions.
- Un problème d'espace disque, d'utilisation de la mémoire ou de dépassement du temps d'exécution des scripts.
- Une Extension nouvellement installée ou activée qui n'est pas compatible avec Joomla. Un mauvais plugin peut désactiver la connexion à l'administrateur !

### Activer le Débogage

Si votre interface d'administration **fonctionne** encore :
- Allez dans **Tableau de bord d'accueil → Panneau Système → Configuration Globale**. 
- Dans l'onglet Système, réglez *Débogage Système* sur *Oui*.
- Dans l'onglet Serveur, réglez *Rapport d'erreurs* sur *Maximum*. 
- Puis *Enregistrez & Fermez*.

Si votre interface d'administration **ne fonctionne pas**, modifiez le fichier *configuration.php* dans le dossier racine de votre site Joomla.

1. Changez les permissions de *444* ou *-r--r--r--* (personne n'a la permission d'écrire dans le fichier) à *644* ou *-rw-r--r--* (seul le Propriétaire a la permission d'écrire).
2. Éditez le fichier avec un éditeur de texte et réglez `$debug` sur `true` et `$error_reporting` sur `'maximum'`.
3. *Enregistrez* le fichier.

Avec les modifications effectuées, rechargez la page qui causait l'erreur. Vous devriez maintenant voir une trace de pile. Exemple :

![Page d'erreur de modèle](../../../en/images/problems/template-error-stack-trace.png)

Le premier élément de la trace de pile indique où l'erreur a été déclenchée. Parfois, cela suffit pour identifier l'Extension défaillante. Parfois, l'Extension défaillante se trouve plus bas dans la trace de pile. Cela peut ne pas signifier grand-chose pour vous, mais la trace de pile est inestimable pour les experts qui répondent aux questions dans les Forums Joomla.

Si vous pouvez identifier l'Extension défaillante, désactivez-la. Vous pouvez le faire en utilisant l'interface d'administration si elle fonctionne. Sinon, utilisez phpMyAdmin pour trouver l'Extension dans la table de la base de données `#__extensions` et réglez sa valeur `enabled` sur `0`. Vous ne devriez pas avoir besoin de désactiver aucune Extension principale de Joomla.

## Assistant de publication sur le forum

Pour aider à résoudre les problèmes, vous devriez télécharger le [Assistant de publication sur le forum (FPA)](https://forumpostassistant.github.io/docs/) et le charger à la racine de votre site Joomla. Le lien pour le trouver se situe également près du haut de chaque page du forum Joomla. Le FPA est un script PHP autonome qui analyse votre installation Joomla et vous indique ce qui pourrait poser problème. Encore une fois, cela ne signifiera peut-être pas grand-chose pour vous, mais les experts qui répondent aux questions dans les forums peuvent demander à le voir.

## Nettoyage

Lorsque votre problème est résolu :

1. Allez à **Tableau de bord d'accueil → Panneau système → Configuration globale**
2. Sélectionnez l'onglet Système et réglez *Système de débogage* sur *Non*.
3. Sélectionnez l'onglet Serveur et réglez *Rapport d'erreurs* sur *Par défaut du système*.
4. *Enregistrer & Fermer*.
5. Supprimez l'Assistant de publication sur le forum.

Les permissions du fichier `configuration.php` sont définies en lecture seule (444 ou *r--r--r--*) lors de l'enregistrement du formulaire de Configuration globale. Il n'est pas nécessaire de le faire manuellement.

*Traduit par openai.com*

