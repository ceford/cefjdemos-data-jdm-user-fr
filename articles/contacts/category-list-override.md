<!-- Filename: category-list-override.md / Display title: Liste des catégories par défaut -->

## L'élément de menu "Lister les contacts dans une catégorie"

C'est peut-être une opinion personnelle, mais pour moi, la mise en page par défaut de la liste des catégories de contacts n'est pas tout à fait satisfaisante. Mes problèmes :

* Les photos des contacts sont trop grandes avec presque 500 pixels de largeur.
* Le nom du contact n'est pas suffisamment mis en avant.
* La liste à puces des informations personnelles n'a pas de titre et semble isolée.
* La position n'a pas de titre, ce qui peut paraître isolé.
* Les champs d'adresse et de code postal sont absents.
* Les données de localisation sont incomplètes.
* La déclaration personnelle est manquante.
* La liste est présentée dans un tableau qui est un peu mieux sur les écrans étroits mais plutôt serrée.

Alors, comment y remédier à mon goût ?

## Style

L'image a le style CSS `contact-thumbnail img-thumbnail`. Les outils de développement du navigateur indiquent que img-thumbnail est réglé sur `max-width: 100%;` mais contact-thumbnail n'est pas utilisé. La seule occurrence de ce dernier style dans tout le site se trouve à cet endroit, il semble donc sûr de définir un remplacement dans user.css pour restreindre la largeur de l'image. Et la taille de la police du nom de contact peut être augmentée en utilisant sa balise `a` englobante :

```
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
```
La liste à puces des champs personnalisés peut être améliorée en supprimant les puces et le remplissage en sélectionnant uniquement les listes à puces qui apparaissent dans une balise ayant la classe contactList :
```
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
```
![comité d'affaires stylisé](../../../en/images/contacts/contact-business-committee-styled.png)

C'est tout ce qui peut être fait avec le style. Mieux mais toujours pas suffisant. Pour ajouter plus d'éléments et modifier la disposition, un remplacement de disposition sera nécessaire.

## Remplacement de la mise en page du modèle

Le dossier com_contact/tmpl/category contient trois fichiers PHP : default.php, default_children.php et default_items.php. Le dernier de cette liste contient la mise en page du tableau pour la liste.

Les fichiers de remplacement sont créés via Système / Modèles du site / Détails et fichiers Cassiopeia / Créer des Remplacements. Sélectionnez com_contact puis category. Le dossier html contient alors com_contact/category avec les trois fichiers de modèle mentionnés ci-dessus. Le fichier default_items.php est celui à sélectionner pour l'édition. Les lignes 83 à 203 contiennent le tableau utilisé pour la mise en page.

Cela peut ne pas sembler évident mais $this->items est un tableau de membres de catégorie et chaque membre contient en fait toutes les données pour chaque item, pas seulement celles mentionnées dans les paramètres du menu.

Ce qui suit est un remplacement de la section `<table>...</table>` du fichier default_items.php en utilisant une grille Bootstrap. Sur les écrans étroits, les trois colonnes sont empilées. Sur les écrans de plus de 768 pixels, les colonnes sont côte à côte. Plus d'explications suivent le code.

```html
<div class="container-fluid text-center border border-2">
<?php $nrows = 0; foreach ($this->items as $i => $item) : ?>
    <?php if ($item->published !== 1 ||
        (!empty($item->publish_up) && strtotime($item->publish_up) > strtotime(Factory::getDate())) ||
        (!empty($item->publish_down) && strtotime($item->publish_down) < strtotime(Factory::getDate()))) { continue; } ?>
        <div class="row cat-list-row<?php echo $nrows % 2; $nrows += 1; ?> align-items-center">
            <div class="col-12 col-md-3">
                <?php if ($this->params->get('show_image_heading')) : ?>
                    <?php if ($item->image) : ?>
                        <?php echo LayoutHelper::render(
                            'joomla.html.image',
                            [
                                'src'   => $item->image,
                                'alt'   => 'image officielle de ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong>Position</strong><br>
                    <?php echo $item->con_position; ?><br>
                <?php endif; ?>
                <?php if ($this->params->get('show_suburb_headings')) : ?>
                    <?php $location = []; ?>
                    <?php if (!empty($item->address)) : ?>
                        <?php $location[] = $item->address; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->suburb)) : ?>
                        <?php $location[] = $item->suburb; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->state)) : ?>
                        <?php $location[] = $item->state; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->postcode)) : ?>
                        <?php $location[] = $item->postcode; ?>
                    <?php endif; ?>
                        <strong>Adresse</strong><br>
                    <?php echo implode("<br>\n", $location); ?><br>
                <?php endif; ?>
                <?php if (!empty($item->misc)) : ?>
                    <?php echo $item->misc; ?>
                <?php endif; ?>
            </div>
        </div>
    <?php endforeach; ?>
</div>
```
### Explication

La liste de contacts peut contenir des éléments qui ne sont pas publiés, ou qui ont des dates de publication_up et publication_down qui ne sont pas courantes. Ils doivent être exclus de l'affichage et un compteur séparé est nécessaire pour maintenir l'alternance des couleurs de fond dans chaque ligne.

La balise img est rendue comme suit :
```html
<img src="/j51/images/parliament/Official_portrait_of_Liam_Byrne_crop_2.jpg"
alt="image officielle de Liam Byrne" class="contact-thumbnail img-thumbnail"
width="479" height="639" loading="lazy">
```
La classe `<span class="fs-2">...</span>` définit le nom du contact à une taille de police 2, ce qui serait équivalent à un titre de niveau 2.

L'item `show_suburb_headings` est utilisé comme proxy pour afficher l'adresse complète car certains des éléments individuels de l'adresse n'ont pas de sélecteurs Montrer/Masquer dans l'élément du menu.

### Style Supplémentaire

La version en grille de la liste de contacts a besoin de styles supplémentaires dans user.css :
```css
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}

a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}

#contactList ul {
  list-style-type: none;
  padding-left: 0;
}

.cat-list-row0 {
  background-color: #efefef;
}

.cat-list-row0:hover, .cat-list-row1:hover  {
  background-color: #ddd;
}
```

### Résultat

![comité d'entreprise en grille](../../../en/images/contacts/contact-business-committee-grid.png)

*Traduit par openai.com*  

