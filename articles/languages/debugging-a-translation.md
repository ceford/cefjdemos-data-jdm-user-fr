<!-- Filename: Debugging_a_translation / Display title: Déboguer une Traduction -->

## Fichiers de langue Joomla

Chaque fois qu'un texte doit être affiché à l'écran, les codeurs Joomla insèrent une constante de langue telle que JYES ou JNO. Pendant le processus de rendu, les fichiers de langue sont chargés avec les traductions dans la langue appropriée. Les fichiers de langue se terminent tous par `.ini`. Vous pouvez consulter languages/en-GB/joomla.ini pour quelques exemples de base. Les lignes commençant par un point-virgule sont ignorées. Elles peuvent être utilisées pour des commentaires. Les lignes restantes se composent de paires de clés="valeurs". Chaque langue a le même ensemble de clés, mais les valeurs sont les traductions appropriées.

Chaque extension Joomla a ses propres fichiers de langue, il y en a donc des centaines en tout. Parfois, des problèmes surviennent, tels que des constantes de langue manquantes, des constantes de langue mal orthographiées ou des erreurs de syntaxe dans les chaînes de traduction qui peuvent rendre un fichier de langue entier invalide.

## Langage de débogage

Joomla offre quelques mécanismes de débogage utiles qui peuvent faciliter la localisation des chaînes non traduites et le diagnostic des problèmes liés aux traductions de langue dans les extensions installées. Pour les essayer :

Depuis le tableau de bord d'accueil :

* Sélectionnez le bouton **Configuration globale** dans le panneau *Système*.
* Sélectionnez le panneau *Système* et réglez **Déboguer le langage** sur **Oui**.
* L'**Affichage de la langue** est normalement réglé sur **Valeur**. S'il est réglé sur **Constante**, la mise en page est perturbée par de longues constantes qui ne se coupent pas.

Avec le Débogage de langue actif, toutes les valeurs traduisibles sont affichées entourées de caractères spéciaux indiquant leur statut :

* `**Joomla CMS**` Le texte entouré de deux astérisques indique qu'une correspondance
a été trouvée dans un fichier de langue et que la constante a été traduite.
* `??Joomla CMS??` Le texte entouré de paires de points d'interrogation indique que
la constante est traduisible, mais qu'aucune correspondance n'a été trouvée dans un fichier de langue.
* `Joomla CMS` Le texte sans aucun caractère entourant indique que la valeur n'est
pas traduisible.

## Debugger le Système

Des informations supplémentaires de débogage linguistique peuvent être obtenues en activant le débogage du système.

Depuis le tableau de bord d'accueil :

* Sélectionnez **Extensions**, puis trouvez et activez le plugin **Système - Débogage**.
* Sélectionnez à nouveau le tableau de bord d'accueil, puis...
* Sélectionnez le bouton **Configuration Globale**.
* Sélectionnez le panneau *Système* et réglez **Déboguer le Système** sur **Oui**.

Avec **Débogage du Système** activé, tous les écrans disposent d'informations de débogage supplémentaires au bas de chaque page. Elles peuvent être développées à partir d'une icône Joomla, et la bordure supérieure peut être tirée verticalement pour afficher plus de lignes.

Les informations de débogage sont classées sous plusieurs rubriques :

* **J! Info** Informations de base sur l'installation.
* **Requête** Champs de requête du serveur.
* **Session** Informations de session.
* **Profil** Le temps pris pour exécuter le code jusqu'à divers points de repère dans le code.
* **Requêtes** Les requêtes SQL exécutées au cours de la construction de la page.
* **Chargés** Une liste de tous les fichiers de langue chargés lors de la construction de la page, y compris les informations de chemin complet. Cela peut être utile pour vérifier que les fichiers attendus ont été chargés.
* **Non traduit** Une liste de toutes les constantes non traduites trouvées et la localisation probable du fichier à partir de laquelle l'appel de traduction a été fait.
* **Erreurs**

## Système - Plugin de Débogage

Ce plugin système contrôle ce qui est affiché lorsque le débogage est activé dans la **Configuration Globale**. Il y a trois paramètres d'intérêt pour les traducteurs.

Dans l'onglet **Langue** :

![plugin système debug](../../../en/images/languages/languages-debug-plugin.png "Système - Débogage Langue")

* **Erreurs Lors de l'Analyse des Fichiers de Langue** Afficher une erreur si un fichier de langue ne parvient pas à se charger.

- **Fichiers de Langue**. Si réglé sur *Afficher*, alors ...
- **Chaîne de Langue** Si réglé sur *Afficher*, alors ...
- **Éliminer le Premier Mot**.
- **Éliminer Depuis le Début**
- **Éliminer Depuis la Fin**

**L'explication suivante nécessite une révision !**

Notez que les chaînes non traduites afficheront uniquement la valeur transmise à la méthode **Texte** appropriée. Par exemple, avec le code suivant :

    echo Text::_( 'Reports Import Configuration' );

Si non traduit, il s'affichera comme suit :

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Reports Import Configuration

Si le Préfixe de Clé à Éliminer est réglé sur "Reports", l'affichage changerait légèrement pour :

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Import Configuration

Notez que le chemin affiché est seulement une meilleure estimation basée sur un appel à la fonction PHP *debug_backtrace*. Parfois, il est précis, parfois, il ne l'est pas et il y a aussi des cas où aucun fichier ne pourrait être déterminé. Dans ces cas, vous devez utiliser votre meilleur jugement.

*Traduit par openai.com*

