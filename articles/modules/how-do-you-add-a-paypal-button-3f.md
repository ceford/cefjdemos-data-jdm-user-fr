<!-- Filename: How_do_you_add_a_PayPal_button%3F / Display title: Comment ajouter un bouton PayPal? -->

Joomla!  3.x Joomla!  2.5

PayPal, Google Checkout et d'autres solutions de commerce électronique
fournissent souvent un code HTML que vous pouvez utiliser pour insérer
des liens sur votre site Web tels que les boutons "Ajouter au panier" et
"Acheter maintenant".

Il est généralement préférable de créer un module HTML personnalisé
plutôt que de simplement coller le code dans un article. De cette façon,
vous pouvez placer le lien en position de module sur autant de pages que
vous le souhaitez. Vous pouvez également placer le module à l'intérieur
d'un article en utilisant la commande  {loadposition
myposition}.

## Documentation technique PayPal

Les spécifications et les exemples de code HTML figurent dans le
<a href="https://www.paypal.com/fr/webapps/mpp/standard"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Guide d'intégration standard des
paiements sur site Web PayPal</a>.

## Les pièges de l'éditeur HTML

Vous pouvez insérer ce type de code HTML, y compris les formulaires,
soit à l'intérieur d'un article, soit dans un module de contenu
personnalisé. Toutefois, l'éditeur TinyMCE supprime normalement le code
HTML. Si vous essayez de coller certains types de code HTML en utilisant
cet éditeur, cela ne fonctionnera pas ; l'éditeur supprimera le code
lorsque vous enregistrerez l'article ou le module.

### Solution pour l'éditeur TinyMCE

Pour éviter ce problème lors de l'utilisation de l'éditeur TinyMCE

1.  Allez dans le Gestionnaire des utilisateurs et changez l'éditeur de
    l'utilisateur en *Éditeur - Non WYSIWYG*.
2.  Allez dans l'article ou le module HTML personnalisé et collez le
    code HTML souhaité.
3.  Allez de nouveau dans le gestionnaire d'utilisateurs et changez
    l'éditeur d'utilisateur en TinyMCE.

Notez que vous devrez répéter cette opération chaque fois que vous
voudrez modifier le code (sauf si vous utilisez la solution alternative
ci-dessous).

### Solution pour l'éditeur JCE

1.  Installez l'éditeur JCE à partir de
    <a href="https://extensions.joomla.org/extension/jce/"
    class="external text" target="_blank" rel="noreferrer noopener">le
    répertoire des extensions de Joomla</a>.
2.  Changez l'éditeur par défaut (Configuration globale \> Site \>
    Editeur par défaut) pour JCE à partir de TinyMCE. Vous devrez
    peut-être aussi changer l'éditeur par défaut pour les autres
    utilisateurs.
3.  Allez dans l'article ou le module contenu personnalisé et cliquez
    sur l'onglet *code*, ce qui modifiera la boîte d'édition pour vous
    permettre d'entrer du code HTML au lieu du texte WYSIWYG.
4.  Collez le code HTML dans l'éditeur.

Lorsque vous revenez à l'article ou au module dans le backend, il sera
déjà configuré en HTML ; le code ne sera pas altéré. C'est plus facile
que de devoir modifier les paramètres de l'utilisateur chaque fois que
vous voulez éditer le code pendant que vous testez différents paramètres
de boutons.

## Les pièges du masquage d'e-mails

Le code PayPal comprend une adresse électronique pour votre site Web.
Joomla ! dispose d'un plugin appelé *Contenu - Protection des e-mails*
qui tente de dissimuler les adresses électroniques dans les articles. Si
vous souhaitez coller le code PayPal directement dans un article, vous
devrez peut-être désactiver ce plugin. Naviguez vers Extensions /
Plugins, trouvez le plugin *Contenu - Protection des e-mails'* et
cliquez sur la case verte Statut activé pour le désactiver.

Par défaut, les plugins de contenu ne sont pas actifs dans les modules.
Par conséquent, si vous utilisez un module de contenu personnalisé, vous
serez toujours en mesure de laisser le masquage des e-mails actif.

### Désactivation de masquage d'email spécifique à un article

Vous pouvez désactiver le masquage d'e-mails dans un article en
saisissant *{emailcloak=off}* n'importe où dans l'article avant
l'adresse mail. Avec ce contrôle, vous n'avez pas besoin de désactiver
le masquage d'e-mail de manière générale.

### Sécuriser l'ID du compte marchand à la place de l'adresse e-mail

PayPal propose gratuitement un ID de compte marchand sécurisé (une
chaîne alphanumérique utilisée à la place de l'adresse électronique du
marchand). Il est disponible pour les clients des paiements Web standard
ainsi que dans les plans optionnels. Le masquage d'e-mail n'affecte pas
l'ID de compte marchand sécurisé.

## La fonctionnalité du bouton PayPal invoquée par un élément de menu de Joomla

Vous pouvez utiliser un élément de menu pour faire office de bouton
PayPal. Par exemple, le bouton PayPal Afficher le panier envoie
simplement une chaîne de requête dans le cadre d'une URL (Uniform
Resource Locator) à l'aide d'un formulaire HTML. Vous pouvez créer un
élément de menu Joomla qui remplit la même fonction.

Dans le gestionnaire des éléments de menu, créez un nouvel élément de
menu Liens divers \> URL. Dans la section Détails de l'élément de menu,
allez dans le champ Lien et entrez l'URL du formulaire :

    https://www.paypal.com/us/cgi-bin/webscr&business=myusername@mysite.com&cmd=_cart&display=1

Remplacez *monnomutilisateur@monsite.com* dans l'exemple d'URL ci-dessus
par le nom d'utilisateur unique de **votre** compte PayPal.

Pour tester l'opération dans l'Environnement de test PayPal, il suffit
de modifier légèrement l'URL pour que *www.paypal.com* devienne
*www.sandbox.paypal.com*.

    https://www.sandbox.paypal.com/us/cgi-bin/webscr&business=myusername@mysite.com&cmd=_cart&display=1
