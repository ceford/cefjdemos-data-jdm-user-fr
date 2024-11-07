<!-- Filename: How_do_you_block_direct_hot_linking_to_image_files_using_htaccess%3F / Display title: Interdire le Hotlinking d'Images  -->

## Définition

Le hotlinking est la pratique qui consiste à lier une image d'un site à partir d'un article sur un autre site. Cela peut être une pratique très utile. Ce site utilise de nombreuses images qui sont en réalité situées sur le site docs.joomla.org. Cela permet d'économiser le temps et l'effort nécessaires pour créer des captures d'écran ainsi que la bande passante de ce site. Cependant, cela peut poser des problèmes de droits d'auteur et vous pourriez souhaiter empêcher que vos images soient utilisées de cette manière.

La méthode décrite ici utilise un fichier *.htaccess*, qui est une fonction du serveur Apache. D'autres serveurs web peuvent proposer d'autres méthodes pour empêcher le hotlinking.

## Instructions

Placez le code suivant dans le fichier *.htaccess* de votre répertoire racine.
```
<IfModule mod_rewrite.c>
    RewriteEngine on
    RewriteCond %{HTTP_REFERER} !^$
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?votredomaine.com [NC]
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?google.com [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```

### Explication

* La première RewriteCond permet les demandes directes en utilisant une URL - pas de referer.
* La deuxième RewriteCond permet les demandes depuis votre propre domaine. Le flag *\[NC\]*
  signifie *Pas de Casse*, c’est-à-dire correspondance indifférente à la casse.
* La troisième RewriteCond permet les demandes depuis Google, de sorte que vos images
  peuvent encore apparaître dans les résultats de recherche. Vous pouvez ajouter des lignes similaires pour n'importe
  quels autres sites que vous souhaitez autoriser.
* La RewriteRule bloque les demandes de fichiers image provenant de tous les domaines
  non préalablement autorisés. Le flag F dit au navigateur de renvoyer un en-tête Interdit (403). L signifie Dernière règle.

### Bloquer le Hot Linking de Domaines Spécifiques

Pour arrêter le hotlinking depuis des domaines spécifiques uniquement, tels que *myspace.com*,
*blogspot.com* et *livejournal.com*, tout en permettant à d'autres sites de
faire du hotlinking vers vos images, utilisez le code suivant :

```
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?myspace\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?blogspot\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?livejournal\.com/ [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```

Vous pouvez ajouter autant de domaines différents que vous le souhaitez. Chaque ligne *RewriteCond* sauf la dernière doit se terminer par les flags *\[NC,OR\]*. *NC* signifie ignorer la casse. *OR* signifie "Ou Suivant", c'est-à-dire, correspondre cette ligne **ou** la ligne suivante. La dernière *RewriteCond* omet le flag *OR* pour arrêter de correspondre après la dernière *RewriteCond*.

