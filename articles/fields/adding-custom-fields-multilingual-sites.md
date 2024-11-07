<!-- Filename: J3.x:Adding_custom_fields/Multilingual_Sites / Display title: # Sites Multilingues -->

## Introduction

Si vous avez un site multilingue, vous pouvez afficher les étiquettes et les descriptions des champs et des groupes de champs dans la langue de l'utilisateur. Pour ce faire :

1. Définissez le titre et la description de votre groupe de champs comme des constantes de langue.
2. Définissez l'étiquette et la description de votre champ comme des constantes de langue.
3. Configurez ces constantes de langue comme des remplacements pour chacune de vos langues.

Dans l'exemple suivant, un groupe de champs et un champ de contact sont créés pour les préférences personnelles d'un contact. Le groupe de champs est nommé Favoris et le champ d'exemple est nommé Voiture. Bien entendu, d'autres champs peuvent être ajoutés pour d'autres éléments favoris, tels que la nourriture ou les films.

Pour suivre cet exemple, il est supposé que vous avez configuré un site multilingue comme décrit dans le tutoriel [Sites Multilingues](jdocmanual?article=user/languages/setup-a-multilingual-site "Sites Multilingues").

## Constantes de Langue

Les constantes de langue sont des espaces réservés qui sont remplacés par des valeurs de langue lorsqu'une page est rendue. Les constantes et leurs valeurs sont stockées dans des fichiers de langue tels que JPATH_SITE/languages/en-GB/com_contact.ini et JPATH_SITE/administrator/languages/en-GB/com_contact.ini, respectivement pour le frontend et le backend. Par convention, la plupart des constantes de langue commencent par le nom de l'extension en majuscules, par exemple COM_CONTACT_...

Les substitutions de langue sont des remplacements définis par l'utilisateur pour les constantes et valeurs de langue existantes ou des constantes et valeurs entièrement nouvelles, comme dans cet exemple. Elles sont toutes stockées dans des fichiers uniques, un pour les pages du Site et un autre pour les pages de l'Administrateur :
```
SITE_ROOT/language/overrides/en-GB.override.ini
SITE_ROOT/administrator/language/overrides/en-GB.override.ini
```
Il est important de rendre les nouvelles constantes de langue définies par l'utilisateur uniques pour éviter de remplacer des constantes existantes. Par exemple :

COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES="Favoris"
COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES_DESCRIPTION="Voiture préférée, film, etc."
COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR="Voiture Préférée"
COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR_DESCRIPTION="Parfois utilisé comme question de sécurité"

Si une erreur de syntaxe se trouve dans un fichier de langue, celui-ci ne sera pas chargé et toutes les constantes qu'il contient peuvent apparaître dans les pages de sortie. Notez qu'un fichier est trié par ordre alphabétique.

## Définir les Remplacements

Il est important de créer des remplacements pour l’anglais (GB). Joomla charge d'abord les fichiers de traduction en-GB, puis remplace les valeurs par un fichier de langue sélectionné. Cela garantit que les utilisateurs ne verront jamais une constante textuelle. Si une valeur traduite manque, l'anglais apparaîtra dans la sortie. Cela peut sembler étrange, mais c'est mieux que de voir une constante assez longue qui perturbe généralement l'agencement.

Depuis le menu de l'Administrateur :

* Sélectionnez **Système / Gérer le panneau / Remplacements de langue**
* Sélectionnez **Anglais (Royaume-Uni) - Site** dans la liste *Sélectionner la langue et le client*
* Sélectionnez le bouton **Nouveau** dans la barre d'outils.
* Dans le champ **Constante de langue**, entrez *COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES*
* Dans le champ **Texte**, entrez la valeur *Favourites*
* Cochez la case **Pour les deux emplacements**. Cela créera des remplacements pour les pages du site et de l'administrateur.
* Sélectionnez **Enregistrer & Nouveau** dans la liste déroulante *Enregistrer * Fermer*.
* Répétez pour chacune des autres constantes requises.
* Sélectionnez **Fermer** après que la dernière entrée a été enregistrée.
* Répétez pour chacune des langues installées.

La capture d'écran suivante montre un exemple de création de remplacement pour une constante de langue allemande.

![Création de remplacement en allemand](../../../en/images/fields/fields-overrides-creation-de.png "Création de remplacement en allemand")

## Définir le Groupe de Champs

Depuis le menu Administrateur :

* Sélectionnez l'élément de menu **Composants / Contacts / Groupes de Champs**.
* Sélectionnez le bouton **Nouveau** dans la barre d'outils.
* Dans le champ Titre, entrez la constante COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES
* Dans le champ Description, entrez la constante COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES_DESCRIPTION
* Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

## Définir le Champ

Pour sélectionner une voiture préférée, vous pouvez fournir une liste déroulante de voitures que vous définissez, ou une liste déroulante de voitures obtenues à partir d'une table de base de données, ou une liste de boutons radio avec des étiquettes que vous définissez. Dans ce cas, un simple champ de saisie de texte permettra d'entrer n'importe quelle marque et modèle de voiture de toute l'histoire mondiale de l'industrie automobile.

Depuis le menu Administrateur :

* Sélectionnez l'élément de menu **Composants / Contacts / Champs**.
* Sélectionnez le bouton **Nouveau** dans la barre d'outils.
* Dans le champ Titre, entrez la constante COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR.
* Dans le champ Type, sélectionnez **Texte (texte)** si ce n'est pas déjà sélectionné.
* Dans le champ Description, entrez la constante COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR_DESCRIPTION.
* Dans le champ **Groupe de Champs** (à droite), sélectionnez le Groupe de Champs que vous avez créé.
* Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

## Modifier un contact

Avec l'anglais sélectionné avant la connexion Administrateur, le formulaire de saisie des contacts doit contenir un onglet avec le nom anglais de votre groupe de champs et des champs de ce groupe également avec des valeurs en anglais.

![Saisie de données en anglais](../../../en/images/fields/fields-overrides-entry.png "Saisie de données en anglais")

Avec l'allemand sélectionné avant la connexion Administrateur, vous devriez voir les traductions allemandes de vos constantes de langue :

![Saisie de données en allemand](../../../en/images/fields/fields-overrides-entry-de.png "Saisie de données en allemand")

Avertissement : traduction par translate.google.co.uk !

## Afficher un contact

En anglais :

![Affichage des données en anglais](../../../en/images/fields/fields-overrides-display.png "Affichage des données en anglais")

Et en allemand :

![Affichage des données en allemand](../../../en/images/fields/fields-overrides-display-de.png "Affichage des données en allemand")
