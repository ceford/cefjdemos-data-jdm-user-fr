<!-- Filename: Keyboard_Shortcuts / Display title: Raccourcis Clavier  -->

## Introduction

Le clavier peut être utilisé dans l'interface administrateur pour invoquer certaines des actions habituellement effectuées avec une souris ou un pavé tactile. Par exemple, il existe des raccourcis clavier pour enregistrer la page en cours, accéder au *Tableau de bord principal* ou ouvrir un formulaire *Options*.

Il existe un aperçu de tous les raccourcis, ouvert par la sélection séquentielle des touches **J** et **X** (pas en même temps et n'utilisez pas la touche Maj généralement utilisée pour la capitalisation). À moins de modifier les paramètres du plugin, vous devez appuyer sur les touches dans un délai de 2 secondes.

La fonctionnalité est activée par défaut. Elle peut être désactivée ou configurée sous **Administrateur → Système → Plugins → Système - Raccourcis Clavier**. Actuellement, la seule configuration est le délai d'attente : combien de temps le système attendra votre prochaine saisie de touche. Par défaut, il attend 2000 millisecondes (2 secondes).

## Raccourcis par défaut dans Joomla

- J + A - Enregistrer le contenu actuel
- J + S - Pour Enregistrer & Fermer
- J + Q - Annule la page en cours
- J + N - Appuie sur le bouton *Nouveau*
- J + F - Met le focus sur le champ de Recherche
- J + O - Va aux Options
- J + H - La fenêtre d'aide s'ouvre (peut déclencher un avertissement de pop-up du navigateur)
- J + M - Bascule la barre de menu
- J + X - Affiche une liste des raccourcis disponibles
- J + D - Va directement au tableau de bord d'accueil

## Raccourcis tiers - Informations pour les développeurs

D'autres développeurs peuvent également ajouter leurs raccourcis. Le plugin Joomla appelle l'événement *onLoadShortcuts*, qui peut également être utilisé par d'autres plugins. L'événement doit être ajouté à la liste des *getSubscribedEvents* à l'intérieur du plugin. La fonction assignée pourrait ressembler à ceci :

```php
    public function onLoadShortcuts(EventInterface $event): void {
       $shortcuts = $event->getArgument('shortcuts');
       $exampleShortcuts = array('example' => (object)['shortcut' => 'E', 'title' => 'Exemple génial', 'selector' => '#menu-collapse']);
       $event->setArgument('shortcuts',  array_merge($shortcuts, $exampleShortcuts));
    }
```
Faites bien attention à la partie array_merge : lorsque les raccourcis déjà existants ne sont pas fusionnés avec les nouveaux, les anciens sont écrasés.

Les développeurs peuvent fournir un tableau avec des objets raccourcis :

    { shortcut: string, selector: string, title: string }

- Le *Raccourci* doit être une entrée clavier, séparée par un plus, par exemple `Y` ou `ALT + Z + 7` (actuellement, il n'y a pas vraiment de filtrage). Gardez à l'esprit que chaque séquence de raccourcis commencera par **J**.
- Les *Sélecteurs* sont des sélecteurs CSS ou des URL pour spécifier la cible. Lorsqu'il s'agit d'un élément d'entrée, le raccourci donne le focus comme c'est le cas pour le champ de recherche. Sinon, l'élément sera cliqué ou l'URL sera appelée.
- Le *Titre* sera affiché dans l'aperçu. Il pourrait s'agir du nom de la cible par exemple.

## Raisons d'utiliser J + X

Certains se demandent peut-être pourquoi le choix s'est porté sur des raccourcis séquentiels ou le **J** au début, au lieu de Ctrl ou autre chose. Les principales raisons sont l'accessibilité et l'évitement d'interruptions par d'autres logiciels. Par exemple, *Ctrl + S* serait pratique pour enregistrer un article, mais est déjà utilisé par les navigateurs. La même chose peut se produire pour les lecteurs d'écran ou les gestionnaires de mots de passe. Donc, l'option la plus sûre était d'utiliser quelque chose de spécifique à Joomla comme le **J** au début.

L'autre problème est qu'il n'est pas toujours possible d'appuyer sur plus d'une touche à la fois. Windows propose le mode touches rémanentes à cet effet, mais il ne fonctionne que pour les touches de modification comme Shift, Ctrl et Alt. Donc, le plugin utilise une saisie séquentielle dès le début, ce qui le rend utilisable par plus de personnes, même sans l'aide des modes système d'exploitation.

*Traduit par openai.com*

