<!-- Filename: J6.x:_Article_Publishing / Display title: Article : Edition - Publication  -->

## Introduction

Une partie essentielle d'un système de gestion de contenu (CMS) est sa capacité à fournir du contenu à des utilisateurs sélectionnés pendant des périodes déterminées. Joomla! le fait avec des niveaux d'accès et des dates de début et de fin de publication.

Les dates de début et de fin peuvent être définies pour les articles *Mis en avant* et les articles *Non mis en avant* de la même manière. Par exemple, un nouvel article pourrait être mis en avant pendant une période déterminée, disons 30 jours, après quoi il deviendrait un article ordinaire non mis en avant. Il disparaîtrait des mises en page des articles en avant, mais apparaîtrait toujours dans d'autres mises en page de blog ou d'article unique.

La plupart du temps, les articles sont publiés le jour de leur création et le restent jusqu'à ce qu'ils soient dépubliés, archivés ou supprimés.

## Capture d'écran

![Onglet de publication du formulaire d'édition d'article](../../../en/images/articles/articles-edit-publishing-tab.png)

Le panneau *Méta-données* est expliqué dans un article distinct. Cet article traite du panneau *Publication*.

## Panneau de publication

Certains champs du formulaire sont destinés à l'information et ne peuvent pas être modifiés directement dans le formulaire. Ils sont affichés avec des arrière-plans gris. D'autres champs peuvent être modifiés si nécessaire.

### Début de publication

Ce champ est défini à la date et l'heure actuelles lorsque l'article est enregistré pour la première fois. Si vous souhaitez que l'article soit en embargo jusqu'à une date et une heure futures, vous pouvez définir sa valeur à l'aide de l'outil Calendrier ou en modifiant directement les valeurs du champ.

### Fin de publication

Par défaut, ce champ est vide. Si vous souhaitez que l'article disparaisse après une date et une heure spécifiées, utilisez l'outil Calendrier ou tapez directement une date et une heure futures dans le champ. À ce moment-là, l'article disparaîtra du site. Dans la liste des articles, il sera marqué comme *Publié, mais expiré*.

### Début en vedette

Si l'article est marqué comme un *Article en vedette*, ce champ peut être défini pour qu'il apparaisse dans une mise en page *Articles en vedette* à la date spécifiée. Notez que la date ne sera pas enregistrée si l'article n'est pas marqué comme *Article en vedette*.

### Fin en vedette

Si l'article est marqué comme un Article en vedette, ce champ peut être défini pour qu'il disparaisse d'une mise en page *Articles en vedette* à la date spécifiée. L'article reste publié et peut encore apparaître dans d'autres mises en page. Dans la liste des articles, il sera marqué comme *En vedette, mais expiré*.

### Date de création

Cette date est définie lorsque l'article est enregistré pour la première fois. Vous souhaiterez peut-être la modifier si vous avez créé une série d'articles dans un ordre aléatoire et que vous souhaitez les trier dans un ordre de date de création.

### Créé par

L'identifiant de l'utilisateur qui a créé l'article est enregistré au moment de sa création et le nom de cet utilisateur apparaît dans ce champ. Vous pouvez changer le créateur en sélectionnant l'icône de personne pour afficher une boîte de dialogue popup *Sélectionner un utilisateur*, à partir de laquelle vous pouvez trouver et sélectionner un utilisateur différent.

### Alias de l'auteur

Si vous ne souhaitez pas que le nom d'utilisateur du créateur apparaisse dans le bloc d'information de l'article, vous pouvez insérer un alias ici. Entrez votre alias, enregistrez l'article et consultez-le avec le bouton Aperçu dans la barre d'outils.

## Planification de la Publication d'un Article

Par défaut, les articles sont définis comme **Publiés** dès qu'ils sont enregistrés. La première sauvegarde de l'article crée la **Date de Création** et les dates de **Début de Publication**.

La planification d'un article implique de définir manuellement une date et une heure de **Début de Publication** pour retarder la publication. Vous pouvez également définir des dates et des heures pour **Fin de Publication**.

**Remarque :** Pour que la planification fonctionne, le **Statut** de l'article doit être défini sur **Publié**.

Avant la date de Début de Publication, les articles sont considérés comme **En Attente** et après la date de Fin de Publication, ils sont considérés comme **Expirés**. Bien que l'article lui-même soit défini pour être publié, Joomla utilise les paramètres de début et de fin pour remplacer l'état publié par défaut.

Les valeurs de date et d'heure peuvent être tapées dans les champs de date ou sélectionnées avec l'outil Calendrier, ouvert en sélectionnant l'icône du calendrier à la fin de chaque champ de date.

![Dates de publication](../../../en/images/articles-access/article-schedule-publishing.png)

Le calendrier navigue entre les jours, mois et années à l'aide des flèches avant, arrière, haut et bas du clavier. Le bouton **Aujourd'hui** fixe la date actuelle. Le bouton **Effacer** efface la date et l'heure.

* Sélectionnez la date requise.
* Réglez l'heure à l'aide des cases déroulantes.
* Sélectionnez le bouton **Fermer** du Calendrier pour définir la date et l'heure sélectionnées.
* Sélectionnez **Enregistrer** ou **Enregistrer & Fermer** dans la barre d'outils pour sauvegarder les modifications.

## Icônes de vue de liste

Dans la liste des articles, l'icône *À la une* est généralement soit un cercle gris, soit une étoile jaune. De même, l'icône *Statut* est généralement une coche verte ou une croix grise. Chacune a une info-bulle, et l'action habituelle est de basculer l'état.

- Publié et est actuel : <span class="icon-publish" aria-hidden="true"></span>
- Non publié : <span class="icon-unpublish" aria-hidden="true"></span>
- À la une : <span class="icon-featured" aria-hidden="true"></span>
- Non à la une : <span class="icon-unfeatured" aria-hidden="true"></span>

Les icônes pour les articles avec des dates de début et de fin programmées sont différentes.

- Publié mais en attente : <span class="icon-pending" aria-hidden="true"></span>
- Publié mais expiré : <span class="icon-expired" aria-hidden="true"></span>
- À la une mais en attente : <span class="icon-pending" aria-hidden="true"></span>
- À la une mais expiré : <span class="icon-expired" aria-hidden="true"></span>

Dans chaque cas, une info-bulle montre des informations supplémentaires sur les dates programmées.  

## Conseils

- Vous pouvez également programmer la publication des articles depuis l'interface utilisateur.
- Il est également possible de programmer via l'élément de menu pour l'article.
- La programmation est également disponible pour les Contacts et les Modules.

*Traduit par openai.com*

