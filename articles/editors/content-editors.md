<!-- Filename: Content_editors / Display title: Les éditeurs de contenu -->

Les éditeurs nativement disponibles dans
<img src="https://docs.joomla.org/images/7/7b/Compat_icon_CMS.png"
decoding="async" data-file-width="87" data-file-height="17" width="87"
height="17" alt="Joomla multi" />

## L'éditeur TinyMCE

**TinyMCE** is the default editor for both Frontend and Backend users.
TinyMCE is a **WYSIWYG** (what you see is what you get) editor that
allows users a familiar word-processing interface to use when editing
Articles and other content.

TinyMCE can be configured with 3 different sets of toolbar buttons

- **Set 2** is assigned to 'Public'.
- **Set 1** is assigned to the 'Manager' and 'Registered'.
- **Set 0** is the most extended toolbar and is by default assigned to
  the 'Administrator', 'Editor' and 'Super Users'.

<img
src="https://docs.joomla.org/images/thumb/f/fb/Help30-editor-tinymce-advanced-en.png/600px-Help30-editor-tinymce-advanced-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/f/fb/Help30-editor-tinymce-advanced-en.png 1.5x"
data-file-width="669" data-file-height="114" width="600" height="102"
alt="Help30-editor-tinymce-advanced-en.png" />

Learn about Toolbars, Editor Buttons and Accessibility of
TinyMCE.

## CodeMirror

The CodeMirror editor is designed to make it easy to enter HTML code in
an article or description. CodeMirror supports syntax highlighting and
auto-completion, as shown in this screenshot.

<img
src="https://docs.joomla.org/images/thumb/e/e2/Help25-screenshot-editor-codemirror-example-en.png/320px-Help25-screenshot-editor-codemirror-example-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/e/e2/Help25-screenshot-editor-codemirror-example-en.png 1.5x"
data-file-width="326" data-file-height="165" width="320" height="162"
alt="Help25-screenshot-editor-codemirror-example-en.png" />

CodeMirror offers some of the same advantages of using No Editor, but
makes it somewhat easier to work with raw HTML code.

To set options:  CodeMirror Editor
Plugin

## Aucun éditeur

Si 'Aucun éditeur' est sélectionné pour un utilisateur, alors un simple
éditeur de texte s'affichera. Cela vous permet d'entrer un texte brut
sans mise en forme HTML. Vous pouvez utiliser le bouton **Aperçu** afin
de prévisualiser le HTML qui sera affiché.

Notez que l'option 'Aucun éditeur' peut s'avérer très utile pour
intégrer un code HTML personnalisé comme par exemple pour la création
d'un lien PayPal. TinyMCE va automatiquement re-formater certains HTML
lorsqu'un fichier est enregistré. De ce fait, en cas de code HTML
complexe, le code pourrait ne pas fonctionner correctement.

Si cela se produit, vous pouvez changer temporairement d'éditeur de
texte en sélectionnant **Aucun éditeur** et créer le contenu souhaité.
Veuillez noter que si vous souhaitez modifier ce contenu à l'avenir,
vous devrez être prudent et ne pas oublier de changer votre éditeur en
'Aucun éditeur'. Sinon, si vous ouvrez et enregistrez le contenu avec
TinyMCE, vous risquez de perdre votre code HTML personnalisé.
