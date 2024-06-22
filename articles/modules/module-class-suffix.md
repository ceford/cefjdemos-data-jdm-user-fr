<!-- Filename: Module_Class_Suffix / Display title: Suffixe de Classe de Module -->

Un Suffixe de Classe de Module dans Joomla! est un paramètre de module.
Il est configurable dans le Module : écran \[Modifier\] dans la section
"Paramètres Avancées". Il permet à Joomla! soit d'ajouter une nouvelle
classe CSS soit de modifier la classe CSS `div` existante d'un module
spécifique.

Lorsque Joomla! génère un module, une classe CSS nommée "moduletable"
est automatiquement créée, permettant de personnaliser l'affichage du
module -- par exemple :

Afin de créer une nouvelle classe, entrez le paramètre précédé d'un
espace. Par exemple, en saisissant espace + "maNouvelleClasse", une
nouvelle classe CSS nommée "maNouvelleClasse" est créée. Le HTML sera
alors modifié en

Pour changer le nom d'une classe existante, entrez le paramètre sans
espace. Par exemple, en saisissant "\_monSuffixe" (sans espace), le HTML
sera modifié en :

Généralement, il est recommandé d'utiliser un espace pour créer une
nouvelle classe. Ainsi, les styles CSS de ce module, qui utilise les
noms de classe standards, continueront de fonctionner. Vous pouvez
utiliser un nouveau nom de classe pour ajouter des styles au module sans
avoir besoin de recréer tout le code CSS existant. Attention, si vous
créez un nouveau nom de classe, assurez-vous que son nom soit unique et
n'entre pas en conflit avec un nom de classe existant.

Voir également :  Utilisation des Suffixes de
Classe.

## Utilisation

Si vous saisissez un Suffixe de Classe de Module précédé d'un espace,
une nouvelle classe CSS sera alors créée. Si votre paramètre n'est pas
précédé d'un espace, la classe CSS "moduletable" est alors modifiée. La
première méthode est souvent préférable, car ainsi vous ne cassez aucun
des styles existants du module, et il vous faut seulement ajouter vos
propres codes CSS pour la nouvelle mise en page.

Si vous n'utilisez pas d'espace préalable, il vous faudra copier
l'intégralité des codes de style de la classe "moduletable" et les
dupliquer dans la nouvelle classe CSS avant de commencer vos
modifications de CSS.

Voir  le tutoriel d'utilisation des Suffixes de
Classe
pour un exemple détaillé d'utilisation des Suffixes de Classe de Page et
de Module.
