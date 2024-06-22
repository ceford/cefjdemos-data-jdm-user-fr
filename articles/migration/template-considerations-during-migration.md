<!-- Filename: Template_Considerations_During_Migration / Display title: Considérations en matière de template lors d'une migration -->

<img
src="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/25px-Copyedit.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/38px-Copyedit.png 1.5x, https://docs.joomla.org/images/thumb/4/47/Copyedit.png/50px-Copyedit.png 2x"
data-file-width="200" data-file-height="200" width="25" height="25"
alt="Copyedit.png" />This Article Needs Your Help

*This article is tagged because it* **NEEDS UPDATING***. You can help
the Joomla! Documentation Wiki by <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Template_Considerations_During_Migration/fr&amp;action=edit"
class="external text" target="_blank"
rel="noreferrer noopener">contributing to it</a>.
<span class="small">More pages that need help similar to this one are
here.</span>
<span class="small">**NOTE-If you feel the need is satistified, please
remove this notice.**</span>*
**Reason:** See section 3.4 and 4

Les templates peuvent parfois être source de confusion lors d'une
migration. Cela ne devrait pourtant pas être le cas. Avec quelques
explications, les choses peuvent devenir claires quant aux options qui
s'offrent à vous.

## Introduction

Les Templates sont une extension. De même que les composants, modules et
plugins sont des extensions, le template en est également une.

Lors du paramétrage d'une migration, il vous faudra décider du devenir
de votre template actuel (qui détermine l'actuel “look and feel” de
votre site).

Pour la plupart, le scénario pour votre template devrait s'inscrire dans
l'une des options suivantes :

- Vous utilisez un template qui a été acheté dans un club de template.
- Vous utilisez un template qui a été acheté une seule fois auprès d'un
  fournisseur de templates.
- Vous avez fait concevoir un template personnalisé pour vous.
- Vous utilisez un template par défaut fourni avec votre installation de
  Joomla qui peut avoir été personnalisé de manière significative ou pas
  du tout :
  - Les templates par défaut de Joomla ! 1.5 sont Rhuk_milkyway, JA
    Purity, Beez.
  - Les templates par défaut de Joomla ! 2.5 sont Atomic, Beez3, et
    Beez25.
  - Les templates par défaut de Joomla ! 3 sont Protostar et Beez3.
  - Le template par défaut de Joomla ! 4 est Cassiopeia uniquement.

## Évaluez votre scénario

Avant de décider de ce qu'il convient de faire, vous devez déterminer si
vous souhaitez conserver l'aspect actuel de votre site Web. Si vous
souhaitez un changement, c'est le moment de le décider. La raison la
plus importante pour laquelle vous souhaitez changer de template est
peut-être l'utilisation de technologies plus récentes que l'on trouve
dans les templates actuels. Les templates réactifs n'étaient pas
disponibles dans la version 1.5 au début du cycle de vie de la version
2.5.

Prenons ces scénarios un par un :

### Vous utilisez Protostar

Protostar n'est pas compatible avec Joomla 4.x. La migration
fonctionnera en un clic de Joomla 3.10.x à 4.x mais le template
disparaîtra et sera remplacé par Cassiopeia lors de la migration. Vous
devrez prévoir d'utiliser Cassiopeia ou un autre template dans Joomla 4.

#### Pourquoi ne pouvez-vous pas faire évoluer Protostar vers Joomla 4 ?

Protostar est basé sur une ancienne version de Bootstrap (Bootstrap 2)
et de jQuery (1.x). Les versions de ces composants sont dépassées et
présentent des problèmes de sécurité connus (Joomla 3 a maintenu des
versions bifurquées de ces bibliothèques avec des correctifs de sécurité
appliqués) - et Joomla 4 les a mises à jour vers la dernière version -
Bootstrap 5. Cependant, cela signifie que les templates doivent être mis
à jour pour utiliser la nouvelle syntaxe HTML requise par Bootstrap 5.

### Vous utilisez un template acheté auprès d'un template club

C'est le plus facile - la plupart du temps. Si vous avez acheté un
template dans un club de template, retournez à l'entreprise et voyez si
elle dispose d'une version de votre template pour Joomla 4.x. Si c'est
le cas, c'est excellent, avec quelques points à prendre en compte. Si
vous passez de la version 1.5 à la version 4.x, vérifiez si la version
pour Joomla 4 est réactive, si c'est important pour vous. Si vous passez
de la 1.5 à la 4, il y a de fortes chances qu'il y ait des différences
entre la version 1.5 du template et la version 4 du template.
Préparez-vous à personnaliser le template si vous voulez qu'il ait
"exactement" le même aspect. Si vous passez de la version 1.5 à la
version 4.x, il est probable que vous deviez commencer par un nouveau
template.

Si vous passez de 2.5 à 4.x ou de 3.10.x à 4.x, vérifiez si les versions
2.5 et 4.x ou 3.10.x et 4.x sont emballées dans le même paquet du
développeur. Si ce n'est pas le cas, consultez le développeur pour
connaître les étapes de la mise à niveau de Joomla 2.5 vers 3.x, puis de
3.10.x vers 4.x. Si 2.5 et 3.x, ou 3.10.x et 4.x sont dans le même
paquet, c'est bon. Si ce n'est pas le cas, vous pouvez quand même être
tranquille. Cela dépend simplement du chemin de mise à jour du
développeur.

### Vous utilisez un template acheté à l'unité auprès d'un fournisseur de template

Si vous avez acheté un template auprès d'un concepteur de template qui
était un achat unique, retournez auprès de la société et voyez s'il
existe une version disponible pour Joomla 3.x ou 4.x (selon la migration
que vous faites). Si ce n'est pas le cas, vous n'avez probablement pas
de chance. Vous pouvez néanmoins essayer de contacter quelqu'un de la
société pour voir s'il peut le mettre à jour pour vous et le rendre
compatible avec Joomla 3.x ou 4.x.

Si cela ne se fait pas, alors vous devrez soit :

1.  Choisissez un nouveau template.
2.  Convertissez le template pour qu'il soit compatible avec Joomla 4.x.
    (Note : peut ne pas être responsive.)

Le *point 1* est explicite. Vous pouvez obtenir un template
commercialisé par un concepteur ou personnaliser le template par défaut
de Cassiopeia (voir plus loin sur Cassiopeia) qui s'installe avec Joomla
4.x.
*Le point 2* n'est pas aussi simple. Afin de convertir votre template
existant pour qu'il soit compatible avec Joomla 3 (et à terme Joomla 4),
consultez la section suivante.

## Conversions ou migrations de templates

### Conversion de templates 1.5 vers 3

-  Migration d'un template Joomla! 1.5 vers
  3.x

### Conversion de templates 1.5 vers 2.5

-  Migration d'un template Joomla! 1.5 vers
  2.5
- <a
  href="http://magazine.joomla.org/issues/issue-may-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25"
  class="external free" target="_blank"
  rel="noreferrer noopener">http://magazine.joomla.org/issues/issue-may-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25</a>

### Conversion de templates 2.5 vers 3

-  Conversion d'un ancien template
  Joomla!
- <a
  href="http://stackoverflow.com/questions/16055707/convert-joomla-2-5-template-to-3-0"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">http://stackoverflow.com/questions/16055707/convert-joomla-2-5-template-to-3-0</a>
- <a href="https://www.youtube.com/watch?v=E13QMWgvwlA"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">https://www.youtube.com/watch?v=E13QMWgvwlA</a>

### Conversions de templates de 3.10.x à 4

Cette section a besoin de contenu. Si vous avez des connaissances sur la
conversion des templates construits pour Joomla 3 pour les rendre
compatibles avec Joomla 4, veuillez écrire un article de magazine ou
poster un YouTube ou quelque chose qui peut être lié à partir de cette
zone. Merci d'avance.

### Vous utilisez un template personnalisé et conçu pour répondre à vos besoins propres

Si vous avez eu un template personnalisé conçu pour votre site 1.5, 2.5
ou 3.x, il devra être converti pour être compatible avec Joomla 4. Voir
les liens dans la section précédente. Si vous avez besoin d'engager
quelqu'un pour convertir votre template existant afin qu'il soit
compatible avec Joomla 4.x, consultez le portail de la communauté
Joomla !
<a href="https://community.joomla.org/service-providers-directory/"
class="external text" target="_blank" rel="noreferrer noopener">Service
Providers Directory</a> pour les catégories <a
href="https://community.joomla.org/service-providers-directory/listings/category/view/124-template-development.html"
class="external text" target="_blank" rel="noreferrer noopener">Template
Development</a> ou <a
href="https://community.joomla.org/service-providers-directory/listings/category/view/119-migrations-upgrades.html"
class="external text" target="_blank"
rel="noreferrer noopener">Migrations &amp; Upgrades</a>.

### Vous utilisez un des templates par défaut fourni avec votre installation Joomla!

Les templates par défaut de Joomla ! 1.5 sont Rhuk_milkyway, JA Purity
et Beez. Les templates par défaut de Joomla ! 2.5 sont Atomic et deux
versions différentes de Beez. Les templates par défaut de Joomla ! 3
sont Beez3 et Protostar. Il peut avoir été personnalisé de manière
significative ou pas du tout. Si vous utilisez un modèle par défaut 2.5
et que vous passez à Joomla 3.x, vous pourrez effectuer une mise à jour
en un clic. Si vous utilisez un template par défaut 1.5, vous devrez
passer par l'une des étapes ci-dessus pour le mettre à jour pour Joomla
3.x. (Si quelqu'un trouve ces informations incorrectes, veuillez
contribuer et les corriger). Les templates par défaut de Joomla 3 ne
sont **pas** compatibles avec Joomla 4. Vous ne serez pas en mesure
d'utiliser Protostar ou Beez3 dans Joomla 4.

Avant de décider si vous souhaitez convertir votre template 1.5 en
Joomla 4, vous pouvez envisager sérieusement de trouver un nouveau
template présentant des similitudes avec votre template existant. Il est
probable qu'il sera moins cher et plus rapide d'utiliser un nouveau
template que de convertir l'ancien. Si vous souhaitez convertir l'ancien
template et que vous n'avez pas les compétences nécessaires pour le
faire vous-même, visitez le répertoire des prestataires de services du
portail communautaire de Joomla ! dans la catégorie "Migrations et mises
à niveau" <a
href="https://community.joomla.org/service-providers-directory/listings/category/view/119-migrations-upgrades.html"
class="external autonumber" target="_blank"
rel="noreferrer noopener">[1]</a>.

Protostar, le modèle qui est livré avec Joomla 3.x n'est **pas**
compatible avec Joomla 4.x. Vous devrez passer par l'une des étapes
ci-dessus pour le mettre à jour pour Joomla 4.x.

### Au moment de choisir son template

- Concentrez-vous sur un seul fournisseur de template à la fois ou cela
  devient rapidement ingérable.
- Si vous commencez à être submergé, faites une pause, même si cela vous
  retarde d'une journée.
- Essayez de regarder au-delà des très animées et attrayantes démos.
  Vous allez devoir intégrer votre contenu dans ce template et ne pas
  forcément utiliser tout ce qu'il propose de faire.
- Inspectez bien les positions et les variations de modules des
  différents templates.
- Buvez beaucoup d'eau pendant votre recherche de template et
  étirez-vous toutes les heures en cas de besoin.

## Utiliser le template par défaut Cassiopeia dans Joomla! 4.x

À ce stade, cette section est incomplète. Si vous avez des connaissances
sur le sujet, nous vous invitons à participer en complétant cette page.
Dans l'intervalle, une recherche Google sur comment personnaliser le
template Cassiopeia devrait vous proposer de nombreux résultats en
dehors de la documentation Joomla.
