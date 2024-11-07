<!-- Filename: J4.x:Language_Overrides / Display title: Remplacements de Langue -->

## Emplacements des Fichiers de Langue

La plupart des fichiers de langue Joomla! se trouvent dans des dossiers de langue, l'un à la racine du site et l'autre dans le dossier de l'administrateur. Chaque langue possède son propre sous-dossier basé sur les codes de langue standard RFC3066. Chaque extension stocke ses traductions avec un nom dérivé du nom de l'extension. Quelques exemples :

    siteroot/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.sys.ini

Les fichiers contiennent des lignes composées d'une clé et de sa traduction :

    COM_CONTENT="Articles"
    COM_CONTENT_ADD_NEW_MENU_ITEM="Nouvel Élément de Menu"
    COM_CONTENT_ARTICLE_CONTENT="Contenu"
    COM_CONTENT_ARTICLES_TABLE_CAPTION="Tableau des Articles"
    COM_CONTENT_ARTICLES_TITLE="Articles"

Le code PHP de Joomla utilise la clé. Elle est remplacée par la traduction en texte au moment de l'exécution. Le fichier .ini contient les traductions utilisées par l'extension. Les fichiers sys.ini contiennent les traductions utilisées par Joomla pour gérer l'extension. Il peut y avoir des centaines de lignes dans un fichier de langue.

Les extensions tierces sont conseillées de stocker leurs fichiers de langue dans des dossiers de langue au sein de l'extension. Là, ils sont protégés contre la suppression si un administrateur décide de désinstaller une langue. Exemple :

    siteroot/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.sys.ini

**Ne modifiez jamais un fichier de langue de base de Joomla! ou de tiers ! Toute modification que vous effectuez sera perdue lors de la prochaine mise à jour. Si vous souhaitez changer la formulation de n'importe quel élément de langue, utilisez le composant formel Language Override.**

Les surcharges de langue sont vos remplacements pour les traductions de clés de langue de base ou d'extensions. Ce sont des traductions individuelles, une ou deux, pas un fichier complet ! Les surcharges de langue pour une langue donnée sont toutes stockées dans un seul fichier :

    siteroot/language/overrides/en-GB.override.ini
    siteroot/language/overrides/fr-FR.override.ini
    siteroot/language/overrides/de-DE.override.ini

    siteroot/administrator/language/overrides/en-GB.override.ini
    siteroot/administrator/language/overrides/fr-FR.override.ini
    siteroot/administrator/language/overrides/de-DE.override.ini

### Ordre de Chargement des Langues

À chaque chargement de page, les traductions de langue en-GB sont chargées en premier. Cela garantit qu'aucune clé n'est visible par les utilisateurs du site. Si une autre langue est utilisée, les traductions pour cette langue sont chargées ensuite, remplaçant les traductions en-GB. Les autres langues ont tendance à être en retard par rapport à en-GB dans la création des traductions, de sorte que les utilisateurs peuvent occasionnellement voir des mots ou des phrases en anglais parmi ceux de leur propre langue.

Enfin, les traductions sont chargées à partir du fichier de surcharge de langue. Cela permet au site d'utiliser des mots ou des phrases alternatives pour s'adapter aux circonstances locales. 

## Remplacements de Langue

Parfois, vous pouvez souhaiter remplacer un élément de langue traduit par quelque chose de plus adapté aux circonstances locales. Un cas courant est lorsque vous créez une substitution de modèle ou de disposition et souhaitez ajouter du contenu utilisant une nouvelle clé de langue. L'exemple suivant illustre un cas où du texte a été ajouté à la disposition de déconnexion du module de connexion, décrit dans l'article sur les Dispositions de Modèle. La disposition alternative a ce code :

```html
<p class="text-center">
Votre session expirera à <br><?php echo $endTime; ?>
</p>
```

Pour un site multilingue utilisant l'anglais, le français et l'allemand, le code doit changer :

```html
<p class="text-center">
<?php echo Text::_('TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT')?><br><?php echo $endTime; ?>
</p>
```

Note : si vous avez suivi le tutoriel de Disposition de Modèle, vous avez peut-être déjà une clé TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES qui se traduit par Expire. Mais celle-ci est utilisée dans siteroot/administrator/language/overrides.

La nouvelle clé peut maintenant être traduite dans chaque langue. Les traductions seront enregistrées dans siteroot/language/overrides.

- Sélectionnez **Système**→**Panneau de gestion**→**Substitutions de langue**
- Sélectionnez votre langue et l'emplacement du site.
- Sélectionnez le bouton **Nouveau** et remplissez le formulaire. Dans cet exemple, la clé de langue est **TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT** et le texte pourrait être **Votre session expirera à**
- Enregistrez & Fermez le formulaire.
- Répétez le processus de traduction pour chaque langue.

![formulaire d'édition des substitutions de langue](../../../en/images/languages/language-overrides-edit.png)

Enfin, vérifiez que la traduction a été mise en œuvre.

![Résultat de substitution dans le formulaire de connexion du site](../../../en/images/languages/language-overrides-custom-logout.png)

*Traduit par openai.com*

