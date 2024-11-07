<!-- Filename: J4.x:Article_Check-out_and_Check-in / Display title: Article : Enregistrement  -->

## Introduction

De nombreux sites Joomla ont plusieurs utilisateurs qui ont la permission de modifier des articles. Pour empêcher deux utilisateurs de tenter de modifier le même article en même temps, chaque article a un champ de base de données **checked_out** pour indiquer s'il est utilisé ou non. Ce champ est activé lorsqu'un article est ouvert pour modification et désactivé lorsque le formulaire de modification est fermé en utilisant soit le bouton *Enregistrer & Fermer*, soit le bouton *Fermer*.

Parfois, un formulaire de modification d'article n'est pas fermé correctement, par exemple en utilisant le bouton de retour du navigateur ou en cas d'expiration de la session utilisateur. Dans ce cas, le champ checked_out reste activé. Ceci est marqué dans les listes d'articles par une petite icône de cadenas. L'icône de cadenas est également visible à l'endroit où un lien de modification devrait se trouver lorsqu'on est connecté à l'interface du site.

Pour rétablir le fonctionnement normal, les articles verrouillés doivent être enregistrés.

## Enregistrement de l'article

Il existe plusieurs méthodes pour enregistrer un article.

- Si vous étiez la dernière personne à modifier l'article, vous pourrez
  éditer l'article depuis le backend ou le frontend sans avoir besoin
  de l'enregistrer.
- Contactez la dernière personne qui a modifié l'article pour savoir si
  elle a terminé. Vous pouvez survoler le curseur au-dessus du cadenas,
  et le pop-up d'info-bulle affichera le nom de l'utilisateur qui a
  chargé l'article.
- Si vous êtes un Super Utilisateur ou un Administrateur, vous pouvez
  sélectionner l'icône de cadenas pour enregistrer cet article.
- Vous pouvez également sélectionner plusieurs articles et utiliser
  l'élément *Enregistrement* à partir du bouton *Actions* dans la Barre
  d'outils.
- Si vous ne pouvez pas enregistrer l'article vous-même, demandez à un
  Super Utilisateur ou un Administrateur de le faire.

## Enregistrement Global

Si vous êtes un Super Utilisateur ou Administrateur, vous pouvez utiliser l'utilitaire d'enregistrement global pour sélectionner des éléments à enregistrer.

Cet utilitaire doit être utilisé avec précaution, surtout dans des environnements multi-utilisateurs. Il enregistre tous les éléments précédemment empruntés, qu'ils aient été empruntés par vous ou non. Les effets secondaires indésirables possibles peuvent inclure que plusieurs éditeurs finissent par travailler sur le même document. Dans ce cas, celui qui clique en dernier sur le bouton enregistrer voit sa version enregistrée comme copie finale.

Vous devez également être conscient que de nombreuses autres extensions ont des champs **checked_out**. Par exemple, les modules et les catégories peuvent être empruntés pour édition et accidentellement laissés dans cet état.

Depuis le menu Administrateur :

- Sélectionnez **Tableau de bord d'accueil → Enregistrement global** ou
  **Système → Panneau de maintenance → Enregistrement global**.
- La liste affiche le nombre d'éléments empruntés.

![Page d'enregistrement global](../../../en/images/articles/global-checkin.png)

- Dans la liste des tables de la base de données, sélectionnez la case pour le type d'élément à enregistrer.
- Sélectionnez *Enregistrement* dans la barre d'outils.

Tous les éléments empruntés dans cette table seront enregistrés.

## Tables avec le champ checked_out

Vous pouvez découvrir quelles tables ont une colonne checked_out avec cette requête utilisée dans phpMyAdmin :

```sql
SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('checked_out') AND TABLE_SCHEMA='j423sd';
```

Et le résultat devrait ressembler à ceci :

```
TABLE_NAME
bi2hb_banner_clients
bi2hb_banners
bi2hb_categories
bi2hb_contact_details
bi2hb_content
bi2hb_extensions
bi2hb_fields
bi2hb_fields_groups
bi2hb_finder_filters
bi2hb_menu
bi2hb_modules
bi2hb_newsfeeds
bi2hb_scheduler_tasks
bi2hb_tags
bi2hb_update_sites
bi2hb_user_notes
bi2hb_workflow_stages
bi2hb_workflow_transitions
bi2hb_workflows
```

*Traduit par openai.com*

