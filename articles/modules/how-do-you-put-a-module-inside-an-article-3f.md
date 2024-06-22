<!-- Filename: How_do_you_put_a_module_inside_an_article%3F / Display title: Comment placer un module dans un article ? -->

Joomla!  <span class="small">≥ </span>2.5 série

Habituellement vous souhaiterez associer des modules à des articles
d'une certaine façon. Les modules sont assignés à des positions de
module et la position de module permet de le faire apparaître sur la
page Web en fonction des possibilités proposées par le template.
Cependant, il est parfois utile qu'un module soit directement intégré au
sein de l'article. Joomla! propose nativement deux façons de le faire :
**loadposition** et **loadmodule**.

Syntaxe :

- {loadposition position,\[style\]}
- {loadmodule mod_type,the title,\[style\]}
- {loadmoduleid moduleId}

## loadposition

Pour insérer un module dans un article, vous devez publier le module en
lui assignant une position et charger cette position dans l'article
comme suit :

1.  Créez un module et définir sa position comme étant ***myposition***.
    ***myposition*** peut être n'importe quelle valeur qui n'entre pas
    en conflit avec une position de module déjà existante dans le
    template. Au lieu de sélectionner une position dans la liste
    déroulante, renseignez dans le champ position ***myposition*** et
    appuyez sur entrer.
2.  Assignez le module à **Tous** les éléments de menu. Cela permettra
    de s'assurer qu'il apparaît toujours quelque soit la façon dont le
    visiteur aura atteint l'article. Le module n’apparaîtra pas tant que
    vous n'aurez pas placé la commande permettant de charger le module
    dans un
    article.
3.  Modifiez les articles sur lesquels vous souhaitez voir apparaître le
    module et insérez le texte ***{loadposition myposition}*** dans
    l'article, à l'endroit où vous voulez que le module soit placé.

\*Notez que cela ne fonctionne que lorsque le [plugin "Contenu -
Chargement de module" est
activé](https://docs.joomla.org/Help25:Extensions_Plugin_Manager_Edit#Content_-_Load_Modules "Special:MyLanguage/Help25:Extensions Plugin Manager Edit").
Si ce plugin est désactivé, le texte "{loadposition myposition}"
s'affichera tel quel dans l'article. Veuillez noter également que la
position doit être définie en minuscules. La CamelCapitalization
échouera.

## loadmodule

Une alternative à la technique "{loadposition xx}" est la variante
"{loadmodule yyy}" qui est gérée par le même plugin.

Dans ce cas, le plugin va rechercher le premier module dont le **type**
correspondra à la chaîne de caractères : 'yyy'. Ainsi, vous pouvez
charger un module "mod_login" en plaçant {loadmodule mod_login} dans
votre texte. Si vous souhaitez charger une instance spécifique d'un
module, parce que vous avez, par exemple, différents modules de
connexion comme Login 1, Login 2, etc. vous devez alors utiliser
{loadmodule mod_modType,modTitle} avec **mod_modType** égal à mod_login
et **modTitle** le nom/titre de votre instance de ce module. Dans
l'exemple ci-dessus, vous insérez **{loadmodule mod_login, Login 2}**
pour que le module intitulé Login 2 soit affiché. Vous pouvez également
ajouter un style de rendu du module. Pour ce faire, ajoutez le style
comme troisième paramètre comme dans {loadmodule login,Login 2,xhtml}.
Si vous n'ajoutez aucun paramètre, le style "none" sera utilisé.

## loadmoduleid

Since Joomla! version 3.9.0 an alternative to `{loadposition xx}` and
`{loadmodule yyy}` is the variation `{loadmoduleid z}` which is handled
by the same plugin.

In this case the plugin looks for the module who's `id` matches the
number `z`. So you could load the module with id 200 by placing
`{loadmoduleid 200}` in your text. This variant does not "understand"
additional parameters like the `style` parameter.

## Editor Button (since Joomla! version 3.5)

If the editor-xtd plugin "Button - Module" is activated you can use the
editor button "Module" to insert above described tags more easily into
the editor text. Since Joomla! 3.9 also the `loadmouleid` variant.

### Les modules dans les modules

Il est possible dans Joomla! 2.5+ et
Joomla! 3.x+ d'inclure un module à l'intérieur même d'un module "Contenu
personnalisé" en utilisant la même technique des plugins de contenu pour
l'intégration dans un article.

Pour ce faire, l'option **Plug-ins de contenu** doit être activée comme
le montre cette capture d'écran.

<img
src="https://docs.joomla.org/images/a/a8/J3x_custom_html_prepare_content_option-fr.png"
decoding="async" data-file-width="634" data-file-height="304"
width="634" height="304"
alt="Afficher l&#39;option de Plug-ins de contenu d&#39;un module de Contenu personnalisé." />

Vous devez vous rappeler que lorsque vous faites ceci, vous pouvez
rencontrer des problèmes de mise en forme car le "chrome" de votre
module "Contenu personnalisé" se superposera au "chrome" du module
intégré, engendrant des effets indésirables quant à la mise en forme ou
la mise en page.
