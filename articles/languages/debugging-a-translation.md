<!-- Filename: Debugging_a_translation / Display title: Débogage d'une traduction -->

<img
src="https://docs.joomla.org/images/thumb/6/69/Split-icon.png/25px-Split-icon.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/6/69/Split-icon.png/38px-Split-icon.png 1.5x, https://docs.joomla.org/images/thumb/6/69/Split-icon.png/50px-Split-icon.png 2x"
data-file-width="200" data-file-height="67" width="25" height="8"
alt="Split-icon.png" />Split Page into Specific Joomla! Versions - J2.5
and 3.x

It has been suggested that this article or section be split into
specific version
*Namespaces*.
(<a
href="https://docs.joomla.org/index.php?title=Talk:Debugging_a_translation/fr&amp;action=edit&amp;redlink=1"
class="new"
title="Talk:Debugging a translation/fr (page does not exist)">Discuss</a>).
If version split is not obvious, please allow split request to remain
for 1 week pending discussions. <span class="small">*Proposed since **2
years ago***.</span>


Joomla! prend en charge certains mécanismes de débogage très utiles et
qui permettent notamment de localiser les chaînes non traduites et de
diagnostiquer des problèmes avec les traductions de langues dans les
extensions installées.

#### Débogage de langue

<img
src="https://docs.joomla.org/images/b/bf/Global-config-language-debug-fr.png"
decoding="async" data-file-width="200" data-file-height="76" width="250"
height="95" alt="Global-config-language-debug-fr.png" />

Vous activez le système de débogage de langue via le backend en allant
dans Configuration et en cliquant sur l'onglet Système. Trouvez le
Débogage de la langue et modifiez la valeur par "Oui", puis enregistrez
vos modifications.

Avec cette option activée, toutes les chaînes traduisibles sont
représentées entourées de caractères spéciaux qui indiquent leur statut.

|                    |                                                                                                                                                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code               | Statut                                                                                                                                                                                  |
| \*\*Joomla CMS\*\* | *(texte entouré par des ronds)* indique qu'une correspondance a été trouvée dans le fichier de définition de langue et que la chaîne a été traduite.                                    |
| ??Joomla CMS??     | *(texte entouré par des paires de points d'interrogation)* indique que la chaîne est traduisible mais qu'aucune correspondance n'a été trouvée dans le fichier de définition de langue. |
| Joomla CMS         | *(texte sans caractères autour)* indique que la chaîne n'est pas traduisible.                                                                                                           |

#### Débogage système

Les Informations de débogage des langues supplémentaires peuvent être
obtenues en activant le débogage du système. Allez dans Configuration et
cliquez sur l'onglet Système. Trouvez le champ Débogage système et
modifiez la valeur par "Oui", puis enregistrez vos modifications.

Avec cette option activée, des informations de débogage supplémentaires
s'affichent en bas de chaque page. Ce qui inclut actuellement :

- **Profil d'information.** C'est le temps nécessaire pour exécuter du
  code dans divers points de repère du code.
- **Occupation de la mémoire.** La quantité de RAM utilisée.
- **Requêtes de bases de données.** Toutes les requêtes SQL exécutées
  lors du processus de construction de la page.
- **Fichiers de langue chargés.** Une liste de tous les fichiers de
  langue chargés lors du processus de création de la page, y compris
  informations du chemin d'accès. Ceci peut être utile pour vérifier que
  les fichiers attendus ont bien été chargés. Le nombre situé après
  chaque chemin d'accès de fichier correspond au nombre de fois où le
  fichier a été référencé.
- **Diagnostic des Chaînes non traduites.** Une liste de toutes les
  chaînes non traduites trouvées et l'emplacement probable du fichier
  dans lequel l'appel **JText** a été effectué.
- **Style des chaînes non traduites.** Une liste de toutes les chaînes
  non traduites trouvées mais listées au format CLE=Valeur pouvant ainsi
  être copiées-collées directement dans un fichier de définition de
  langue (INI).

#### Plugin de débogage

<img src="https://docs.joomla.org/images/7/79/Debug-plugin-fr.png"
decoding="async" data-file-width="400" data-file-height="399"
width="400" height="399" alt="Debug-plugin-fr.png" />

Ce plugin système contrôle ce qui est affiché lorsque le dégogage est
activé dans **Configuration**. Il est activé par défaut. Pour accéder
aux paramètres de ce plugin, allez dans **Extensions → Gestion des
plug-ins**. Localisez le plugin “Système - Débogage” et ouvrez-le et
cliquez sur l'onglet **Paramètres de langue**. Vous y trouverez trois
paramètres intéressants pour les traducteurs.

- **Affiche les chaînes de langue chargés**. Si paramétré sur “Oui”,
  alors les informations de dégogage incluront une liste des fichiers de
  langue demandés par la page en cours de chargement.
- **Affiche les chaînes de langues indéfinies.** Si paramétré sur “Mode
  diagnostic”, alors une liste des chaînes non traduites et
  l'emplacement du fichier contenant l'appel à **JText** sont inclus aux
  informations de débogage. Si paramétré sur “Mode concepteur”, alors
  une liste des chaînes non traduites sera inclus aux informations de
  débogage dans un format pouvant être copié/collé directement dans un
  fichier de définition de langue. C'est à dire que la liste sera
  affichée au format CLE=Chaîne. Si paramétré sur “Tous les modes”,
  alors les listes des deux modes diagnostic et concepteur seront
  incluses aux informations de débogage.
- **Exclure le préfixe de clé**. Utilisé uniquement lorsque **Affiche
  les chaînes de langues indéfinies** est paramétré sur “Mode
  concepteur” ou "Tous les modes". Cela vous permet d'exclure un préfixe
  de la chaîne pour former la clé. C'est utile si le concepteur utilise
  un préfixe commun pour ses extensions lors de l'utilisation de
  méthodes **JText**. Voir l'exemple ci-dessous.

Notez que l'affichage des chaînes non traduites n'afficheront que les
valeurs transmises par la méthode appropriée **JText**. Par exemple,
dans le code suivant :

    echo JText::_( 'Reports Import Configuration' );

Si non traduite, le Mode concepteur affichera cela comme suit :

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Reports Import Configuration

Si Exclure le préfixe de clé est paramétré sur "Rapports", alors
l'affichage sera légèrement modifié en :

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Import Configuration

Notez que le chemin indiqué est seulement la meilleure estimation basée
sur un appel à la fonction PHP *debug_backtrace*. Parfois, le résultat
est précis, parfois il ne l'est pas et parfois aucun fichier ne peut
être déterminé. Dans ces cas, il vous faudra juger par vous-même.
