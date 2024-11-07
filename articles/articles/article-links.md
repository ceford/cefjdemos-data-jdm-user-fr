<!-- Filename: J4.x:Article_Links / Display title: Article : Édition - Liens  -->

## Liens Accessibles

Sélectionnez un lien dans un document et votre navigateur ouvre le document lié, soit dans la même fenêtre, soit dans une nouvelle fenêtre ou un nouvel onglet. Une personne utilisant un lecteur d'écran peut naviguer uniquement par les liens, donc le texte du lien doit être significatif.

Voici un exemple de **bonne pratique** car il indique où mène le lien :

- Pour en savoir plus, lisez notre [Manifeste](#)

Voici un exemple de **mauvaise pratique** car il ne donne aucune indication sur la nature de la destination et peut être l'un de plusieurs liens similaires sur la même page :

- Pour en savoir plus, cliquez [ici](#)

Pour en savoir plus sur les liens accessibles, lisez cet article sur la [Création de liens valides et accessibles](https://www.a11yproject.com/posts/creating-valid-and-accessible-links/).

## Liens Intégrés

Cet article porte sur les liens intégrés dans le contenu d'un article. Il existe un article distinct sur l'utilisation de l'onglet [Images et Liens](jdocmanual?article=user/articles/article-images-and-links) pour inclure des liens associés à un article.

Les liens intégrés dans un article peuvent renvoyer à d'autres pages au sein du site (liens internes) ou à d'autres sites (liens externes). La procédure pour insérer ces deux types de liens diffère. Elles sont chacune décrites ci-dessous.

## Insérer un Lien Interne

Le processus pour insérer un lien vers un article du même site web est simple :
- Tapez la phrase contenant le texte du lien. Par exemple :

  *Pour plus d'informations, veuillez consulter la page sur les Grenouilles.*
- Sélectionnez le texte du lien : *Grenouilles*

Le lien peut être vers un seul article ou vers un élément de menu pour un blog de catégorie, une liste de catégories ou des articles en vedette.

### Un Lien vers un Article Unique

- Sélectionnez *Article* dans la liste déroulante *Contenu CMS*.
- Sélectionnez le titre de l'article requis dans la boîte de dialogue Article.
- Enregistrez l'article et essayez-le en utilisant le bouton Aperçu dans la barre d'outils.

### Un Lien vers un Élément de Menu

- Sélectionnez *Menu* dans la liste déroulante *Contenu CMS*.
- Sélectionnez l'élément de menu requis dans la boîte de dialogue Menu.
- Enregistrez l'article et essayez-le en utilisant le bouton Aperçu dans la barre d'outils.

## Insérer un lien externe

Pour un lien externe, il est préférable de copier le lien depuis la barre d'URL du navigateur. Pour cela, il est utile d'avoir des fenêtres ou des onglets séparés ouverts pour votre formulaire *Articles : Modifier* et le site distant vers lequel vous créez un lien.

Procédure :

- Trouvez ou créez une phrase contenant le texte à utiliser pour le texte du lien. Par exemple :

  *Pour plus d'informations, consultez l'article Wikipédia sur les Rainettes vertes.*
- Sélectionnez le ou les mots à lier, dans ce cas *Rainettes vertes*.
- Utilisez alors l'une des méthodes suivantes :
  - Sélectionnez **Insérer → Lien** dans le menu Texte de l'article (la première barre d'outils en haut de l'onglet Contenu).
  - Double-cliquez sur le texte sélectionné pour ouvrir un petit menu contextuel contenant une icône de lien à sélectionner.

L'une ou l'autre méthode ouvrira une boîte de dialogue Insérer/Modifier le lien à remplir comme suit :

- Dans le champ *URL*, collez le lien copié depuis la barre d'URL de la fenêtre de destination.
- Le champ *Texte à afficher* doit contenir le texte que vous avez sélectionné avant d'ouvrir la boîte de dialogue. Sinon, tout texte que vous tapez ici sera inséré dans l'article et doit donc avoir un sens contextuel. Rappel : évitez *Cliquez ici* ou *En savoir plus*.
- Le champ *Titre* crée un attribut de titre pour le lien, mais son utilisation par les navigateurs est incohérente et controversée pour des raisons d'accessibilité. En cas de doute, laissez-le vide.
- Le champ *Rel* propose plusieurs options. En cas de doute, laissez-le sur *Aucun*. Il existe une liste d'options disponibles dans l'article *mdn web docs* sur [l'attribut HTML : rel](https://developer.mozilla.org/fr/docs/Web/HTML/Attributes/rel).
- Le champ *Ouvrir le lien dans...* offre un choix simple entre *Fenêtre actuelle* et *Nouvelle fenêtre*. Les paramètres du navigateur contrôlent si cela entraîne l'ouverture d'une nouvelle fenêtre distincte ou d'un nouvel onglet.
- Enregistrez l'article et essayez-le en utilisant le bouton Aperçu dans la barre d'outils.

## Vérification des liens

Dans l'affichage du site de la page, vérifiez que le lien est esthétique et fonctionne correctement. 
Essayez-le également avec un lecteur d'écran !

## Supprimer un lien

Il existe plusieurs façons de supprimer un lien. Méthode 1 :
- Cliquez sur le lien.
- Sélectionnez l’icône des points de suspension (...) pour ouvrir le menu étendu de l'éditeur.
- Sélectionnez l’icône *Supprimer le lien*.
- Enregistrez. Le texte reste mais le lien a disparu.

Méthode 2 :
- Double-cliquez sur le lien.
- Sélectionnez l’icône de lien dans la petite fenêtre contextuelle.
- Dans la boîte de dialogue Insérer/Modifier le lien, supprimez le contenu du champ URL.
- Enregistrez. Le texte reste mais le lien a disparu.

Méthode 3 :
- Supprimez le texte contenant le lien. Le lien et le texte disparaissent tous les deux.

Méthode 4 :
- Sélectionnez le lien.
- Sélectionnez le bouton TinyMCE Édition / Lien.
- Dans la boîte de dialogue Insérer/Modifier le lien, supprimez le contenu du champ URL.
- Enregistrez. Le texte reste mais le lien a disparu.

## Modifier un lien

En utilisant l'une des méthodes décrites ci-dessus pour ouvrir la boîte de dialogue Insérer/Modifier un lien, collez une nouvelle URL de lien. N'oubliez pas : il est toujours préférable de copier l'URL depuis la barre d'URL d'une fenêtre ou d'un onglet de navigateur affichant la page de destination et de la coller dans le champ URL du formulaire Insérer/Modifier un lien.

*Traduit par openai.com*

