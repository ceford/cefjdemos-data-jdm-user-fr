<!-- Filename: J6.x:Access_Control / Display title: Article : Modifier - Autorisations  -->

## Introduction

Joomla propose un système sophistiqué de *contrôle d'accès* basé sur les *niveaux d'accès* et les *groupes d'utilisateurs*. Cela est décrit dans l'article sur le [contrôle d'accès](jdocmanal?article=user/users/access-control) dans la section *Utilisateurs* de ce manuel.

La description ici concerne l'onglet *Permissions* du formulaire *Article : Modifier*. Ses paramètres peuvent paraître étranges à moins que vous ne soyez familier avec le système de contrôle d'accès de Joomla.

## Capture d'écran

![L'onglet des autorisations de l'article avec auteur sélectionné](../../../en/images/articles/articles-edit-permissions-tab.png)

Il peut être surprenant qu'un auteur ne semble pas avoir la permission de modifier un article !

## Groupes d'utilisateurs Frontend et Backend

Si vous n'êtes pas familier avec les groupes d'utilisateurs Joomla standards, il est utile de savoir que *Auteur*, *Éditeur* et *Éditeur de publication* sont des groupes d'utilisateurs frontend. Ils ne peuvent pas se connecter au backend. Leur travail de création, d'édition et de publication d'articles est accompli à l'aide des formulaires d'édition d'articles frontend. *Gestionnaire* et *Administrateur* sont des groupes d'utilisateurs ayant accès à la fois au frontend et au backend et peuvent éditer des articles en utilisant soit les formulaires d'édition backend, soit les formulaires d'édition frontend.

## Accès à l'édition par l'auteur

Pourquoi le formulaire des autorisations affiche-t-il *Modifier* comme **Non autorisé (hérité)**
pour le groupe Auteur ?

Il y a une explication simple. Si vous fermez le formulaire d'édition et allez à la
page *Articles : Options* via le bouton *Options* de la liste *Articles* dans la barre d'outils,
l'onglet *Autorisations* montre qu'un membre du groupe Auteur a des
autorisations supplémentaires : *Créer* et *Modifier ses propres*. Ce sont ces autorisations qui
permettent à un auteur de créer des articles et de modifier ses propres articles.

Ainsi, les autorisations dans le formulaire *Articles : Modifier* n'autorisent pas un membre du
groupe Auteur à modifier des articles créés par quelqu'un d'autre.
*Traduit par openai.com*

