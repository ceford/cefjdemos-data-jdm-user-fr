<!-- Filename: Multiple_Domains_and_Web_Sites_in_a_single_Joomla!_installation / Display title: Plusieurs domaines et sites web dans une seule installation Joomla! -->

**Remarque :** Cet article a été mis à jour pour la dernière fois en 2012 ! 

Bien qu'il soit recommandé de donner à chaque site web son propre domaine,
installation Joomla! et base de données, il peut exister des conditions particulières où une solution multi-sites sous une seule installation Joomla! est justifiée. 

## Un Exemple d'Application

Une petite entreprise, 'Johnson Candies', possède deux marques distinctes mais liées : *Red Candy* et *Yellow Candy*. Ils nécessitent un site Web basé sur Joomla! où les deux types de bonbons sont visibles, chacun avec sa propre page d'accueil sur le site Joomla! qui correspond aux domaines `www.redjohnsoncandy.com` et `www.yellowjohnsoncandy.com`.

De plus, chaque marque et site **nécessite son propre design** : un modèle jaune pour l'un ; un modèle rouge, pour l'autre.

## Avantages

En incluant les deux marques dans une seule installation web Joomla!, Johnson Candies est capable de réduire le temps d'édition (un seul login), de partager des articles et des données entre les deux marques (ou sites) et d'utiliser une seule fonctionnalité, telle qu'un formulaire de contact, pour les deux marques.

## Procédure de Mise en Œuvre

### Préparez Vos Domaines

Utilisez un seul domaine pour votre compte d'hébergement, comme d'habitude. Créez les domaines supplémentaires nécessaires dans le panneau de contrôle de votre compte d'hébergement. Pour les besoins de ce tutoriel, nous utiliserons `www.redjohnsoncandy.com` en plus du nom de domaine principal `www.yellowjohnsoncandy.com`.

### Installez et Configurez Joomla!

Installez et configurez Joomla! normalement. Ensuite, développez des articles, des menus et des modules pour chaque site.

### Créez des Modèles

Ensuite, développez et installez les modèles nécessaires - un pour chaque site que vous souhaitez avoir. Dans l'exemple ci-dessus, vous créeriez un modèle pour *red candy* nommé *Modèle Rouge* et un modèle pour *yellow candy* nommé *Modèle Jaune*. Une fois les modèles installés, attribuez-les aux éléments de menu pertinents, en utilisant le gestionnaire de modèles de Joomla! dans la zone d'administration de Joomla!.

### Ajoutez une Redirection

#### Option #1 : Créez une redirection .htaccess (Apache)

**Remarque** *Activez les URL SEF dans Joomla! d'abord*

Une option consiste à utiliser .htaccess (Apache) pour rediriger les requêtes vers un domaine donné vers une page spécifique de Joomla!.

Notre objectif est de rediriger les requêtes vers le nom de domaine Red Candy vers une page donnée sur le site Joomla!. Dans cet exemple, nous redirigeons les requêtes vers `www.redjohnsoncandy.com` vers une page de blog de catégorie. Vous auriez précédemment attribué le modèle 'red candy' à cet élément de menu pour créer l'illusion d'un site séparé.

```
#La règle suivante fonctionne, mais elle modifie le nom de domaine affiché.
RewriteCond %{HTTP_HOST} ^(www\.)?redjohnsoncandy\.com$
RewriteRule (.*) http://www.yellowjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12 [R=301,L]
```

Eh bien, cela fonctionne - mais vous pouvez immédiatement voir l'inconvénient. Bien que l'utilisateur voie effectivement le site Red Candy, il verra toujours le nom de domaine Yellow Candy. Malheureusement, si vous utilisez à la fois .htaccess et le stationnement de domaine (techniquement une redirection) - cela est nécessaire pour éviter de créer une BOUCLE.

#### Option #2 : Créez une Redirection d’En-Tête PHP

Cette solution a l'avantage de maintenir l'illusion de domaines/sites Web séparés apparente pour le visiteur. Au lieu d'utiliser .htaccess (Apache) pour notre redirection, nous utilisons l'un des modèles sur le site.

Dans cet exemple, le domaine de base est `www.redjohnsoncandy.com`. Vous avez créé un modèle pour cette zone nommé *Modèle Rouge*. L'astuce consiste à ouvrir le fichier index.php du 'Modèle Rouge' et à ajouter ce qui suit **comme les toutes premières lignes** de l'index.php principal de l'installation.

```php
<?php
$domain = $_SERVER["HTTP_HOST"];
$uri = $_SERVER["REQUEST_URI"];
$url = $domain . $uri;

if (($url == "redjohnsoncandy.com/") ||
   ($url == "www.redjohnsoncandy.com/")) {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.redjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12");
}
?>
```

Voici l'avantage : Le visiteur sera maintenant redirigé vers la page *Red Site* appropriée, à laquelle le *Modèle Rouge* est attribué **uniquement** dans le cas où il arrive sur le nom de domaine 'red site'. Sinon, la règle conditionnelle PHP est ignorée et le site Jaune se charge.

Il est important de se rappeler de demander également l'URI (url qui suit le domaine pur) pour que vous puissiez effectuer des redirections vers le même domaine. Lorsque l'URI est invisible dans l'url, la variable devient un signe "/". C'est pourquoi vous devez comparer votre url pure à un signe "/" à la fin. De cette façon, vous pourrez faire des redirections 301 dans le même domaine. Sinon, vous créerez une boucle infinie dans le processus de redirection.

#### Option #3 : Créez une Redirection d’En-Tête PHP, pour plusieurs domaines avec des redirections de domaine spécifiques pour des modèles personnalisés

Solution pour un espace web unique, avec différents domaines, une seule installation Joomla et, selon le domaine d'arrivée de l'utilisateur, redirige vers une page par défaut différente. Collez le code PHP suivant **comme toute première chose** dans le fichier index.php principal de l'installation. Pour attribuer un autre domaine, copiez/collez simplement la fonction "if" et modifiez-la avec les valeurs de l'autre domaine de la même manière. De plus, pour configurer les vues de modèle, vous devrez attribuer différents alias de lien/élément de module et configurer les vues de modèle dans le gestionnaire de modèles de Joomla!. Le paramètre d'alias est nécessaire lorsque vous utilisez les paramètres SEF.

```php
<?php
$domain = $_SERVER["SERVER_NAME"];
$requri = $_SERVER['REQUEST_URI'];
if (($domain == "www.example.de" && $requri == "/" ||
   $domain == "example.de"))  {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.example.de/index.php?option=com_content&view=article&id=6");
}
?>
```

*Traduit par openai.com*

