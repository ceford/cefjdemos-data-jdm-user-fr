<!-- Filename: Entering_raw_HTML_in_editors / Display title: Filtres HTML  -->

## Balise Textarea en HTML

En HTML, un champ de saisie multi-lignes est connu sous le nom de textarea. Tout texte entre les balises ouvrantes et fermantes est affiché comme du texte pouvant contenir des balises HTML. Exemple : 
```
<textarea><p class="poem">Le vif renard brun<br>
saute par-dessus le chien paresseux.</textarea>
```
Les éditeurs, tels que TinyMCE ou Code Mirror, utilisent JavaScript pour superposer la textarea avec un affichage différent permettant une saisie WYSIWYG des données ou une colorisation syntaxique. Le bouton Toggle sous un champ de l'éditeur bascule entre la vue textarea et la vue WYSIWYG.

Les vues des éditeurs sont utilisées pour le contenu des Articles et certains Modules. Cependant, vous devez être conscient que tous les utilisateurs ne sont pas autorisés à utiliser toutes les balises et attributs HTML (comme class="xyz"). Certains ou tous peuvent disparaître lorsque vous enregistrez le contenu d'une textarea ou d'un champ d'édition.

Cela est causé par des mécanismes de filtrage, soit dans la Configuration Globale de Joomla!, soit dans la configuration de l'éditeur. Un filtre d'éditeur peut être contourné en sélectionnant *Aucun Éditeur* dans vos paramètres de *Profil Utilisateur*. Vous ne pouvez pas contourner les filtres globaux, mais vous pouvez les modifier selon les besoins de votre site.

## Sélection de l'Éditeur d'Utilisateur

Vous pouvez sélectionner l'un des éditeurs disponibles, y compris Aucun, depuis votre Profil Utilisateur accessible via le menu Compte Utilisateur / Modifier le Profil en haut à droite de l'écran Administrateur. Le formulaire Modifier : Profil contient un onglet Paramètres de base avec un champ pour sélectionner un Éditeur. Il est normalement réglé sur *- Utiliser la valeur par défaut -*, qui est généralement TinyMCE. Vous pouvez sélectionner *Éditeur Aucun*. Cela contournera tout filtrage des balises et attributs HTML non autorisés par les paramètres de configuration de TinyMCE.

**Avertissement :** si vous sélectionnez *Éditeur - Aucun* pour créer du contenu contenant des balises HTML non autorisées par un filtre d'éditeur et que vous revenez ensuite à l'éditeur par défaut, vous devez faire attention à ne pas modifier et enregistrer ce contenu à nouveau ou vous perdrez toutes les balises et attributs filtrés. Il est facile de faire cela par erreur et il n'y a pas d'avertissement.

## Configuration Globale : Filtres de Texte

Depuis le Tableau de Bord Principal, sélectionnez Configuration Globale puis l'onglet Filtres de Texte. Les paramètres par défaut ont *Aucun HTML* sélectionné pour les groupes d'utilisateurs Invité, Public et Enregistré. Chacun de ces groupes pourrait avoir l'opportunité de remplir un champ de zone de texte, par exemple dans un formulaire de contact qui recherche des informations supplémentaires sur un problème, il est donc généralement approprié de supprimer automatiquement toutes les balises HTML. Les autres groupes, à l'exception des Super Utilisateurs, sont restreints par la Liste Interdite par Défaut. Les Super Utilisateurs ne sont soumis à aucun filtrage.

![configuration globale des filtres de texte](../../../en/images/configuration/global-configuration-filters-tab.png)

Les notes expliquent ce qui est inclus dans la liste interdite par défaut et comment utiliser les autres listes.

## Configuration de TinyMCE pour les filtres de texte

Les éditeurs sont implémentés sous forme de plugins dans Joomla. L'éditeur CodeMirror n'a pas de paramètres de filtre de texte. Pour personnaliser l'éditeur TinyMCE, trouvez-le et sélectionnez-le dans la liste des plugins. À mi-chemin de la longue liste de paramètres, vous verrez un champ intitulé *Utiliser le filtre de texte Joomla* qui est désactivé (**Off**) par défaut. Les trois champs suivants sont :
* **Éléments interdits** : une liste de balises qui seront toujours supprimées. La liste par défaut *script, applet, iframe* présente toutes des préoccupations de sécurité.
* **Éléments valides** : utilisez cette liste pour limiter les balises valides à un sous-ensemble de toutes les balises HTML courantes. Exemple : `a[href|target=_blank],strong/b,div[align],br`
* **Éléments valides étendus** : utilisez cette liste pour ajouter un élément au jeu de règles par défaut existant ou pour modifier un élément dans le jeu de règles par défaut. Exemple : `img[class|src|border=0|alt|title|hspace|vspace|width|height|align|onmouseover|onmouseout|name]`

Consultez la documentation de TinyMCE pour plus d'explications.

Pour contourner les filtres de texte de TinyMCE et utiliser les filtres de texte Joomla, réglez *Utiliser le filtre de texte Joomla* sur activé (**On**). Les trois champs supplémentaires décrits ci-dessus disparaissent car ils ne sont pas utilisés.

*Traduit par openai.com*

