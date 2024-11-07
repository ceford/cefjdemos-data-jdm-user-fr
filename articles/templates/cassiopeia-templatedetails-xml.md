<!-- Filename: J4.x:Cassiopeia_templateDetails.xml / Display title: Cassiopeia templateDetails.xml -->

## Emplacement et Objectif

Vous pouvez voir un exemple de fichier `templateDetails.xml` répertorié dans **Système → Modèles de site → Détails et fichiers de Cassiopeia**. Vous pouvez également le modifier à cet endroit si vous avez une bonne raison de le faire. Sinon, laissez-le tel quel ! Chaque modèle possède un tel fichier et un modèle enfant se compose initialement d'une structure de fichiers contenant seulement ce fichier.

Le fichier `templateDetails.xml` contient les données dont Joomla! a besoin pour gérer et afficher le modèle. Cela inclut les métadonnées utilisées pour fournir des informations sur le modèle, les emplacements des dossiers et des fichiers, les positions des modules du modèle et les options de configuration sélectionnables par l'utilisateur. Le contenu du fichier templateDetails.xml variera d'un modèle à l'autre.

## Cassiopeia templateDetails.xml

Les fichiers au format XML ont une structure bien définie. Un fichier XML doit avoir la syntaxe correcte, sinon il ne fonctionnera pas !

### Format XML

La première ligne de chaque `templateDetails.xml` doit commencer par la définition du doctype XML.

La ligne suivante indique à Joomla! que les données contenues dans ce fichier concernent une extension de modèle de site. Toutes les données du modèle sont contenues entre les balises d'ouverture et de fermeture.

```xml
<extension type="template" client="site">
...
</extension>
```

### Métadonnées

La première section des données du modèle définit généralement les informations relatives au modèle, par exemple : noms, dates, informations de contact, droits d'auteur, numéro de version et description.

```xml
<extension version="3.1" type="template" client="site">
	<name>cassiopeia</name>
	<version>1.0</version>
	<creationDate>2017-02</creationDate>
	<author>Joomla! Project</author>
	<authorEmail>admin@joomla.org</authorEmail>
	<copyright>(C) 2017 Open Source Matters, Inc.</copyright>
	<description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
	<inheritable>1</inheritable>
```

Notez qu'un modèle pouvant avoir des modèles enfants a la valeur héritable fixée à 1. Les modèles enfants ont cette valeur fixée à 0. Ces données sont utilisées dans la liste des modèles : Modèles (Site) comme illustré ci-dessous.

![liste des modèles de site](../../../en/images/templates/templates-list.png)

La description contient une clé de langue et non la chaîne de texte de description réelle. La clé est remplacée par le texte obtenu à partir d'un fichier de langue lors de l'exécution. Les fichiers de langue sont définis dans la section langue de `templateDetails.xml`.

![formulaire de modification du style des modèles](../../../en/images/templates/templates-edit-style.png)

### Répertoires et fichiers

Les dossiers et fichiers pour le modèle Cassiopeia sont stockés à deux endroits distincts. Les fichiers php et associés sont stockés dans le dossier site/templates. Les fichiers médias (css, images, js et scss) sont stockés dans le dossier site/media. Ces emplacements sont définis dans le fichier XML comme suit :

```xml
	<files>
		<filename>component.php</filename>
		<filename>error.php</filename>
		<filename>index.php</filename>
		<filename>joomla.asset.json</filename>
		<filename>offline.php</filename>
		<filename>templateDetails.xml</filename>
		<folder>html</folder>
	</files>
	<media destination="templates/site/cassiopeia" folder="media">
		<folder>js</folder>
		<folder>css</folder>
		<folder>scss</folder>
		<folder>images</folder>
	</media>
```

C'est le schéma observé dans tous les modèles modernes Joomla 4 et 5. La structure peut être vue dans le formulaire Modèles : Personnaliser (Cassiopeia) :

![page de personnalisation du modèle Cassiopeia](../../../en/images/templates/templates-customise-cassiopeia.png)

### Positions des modules

Les positions des modules disponibles sont définies comme suit :

```xml
	<positions>
		<position>topbar</position>
		<position>below-top</position>
		<position>menu</position>
		<position>search</position>
		<position>banner</position>
		<position>top-a</position>
		<position>top-b</position>
		<position>main-top</position>
		<position>main-bottom</position>
		<position>breadcrumbs</position>
		<position>sidebar-left</position>
		<position>sidebar-right</position>
		<position>bottom-a</position>
		<position>bottom-b</position>
		<position>footer</position>
		<position>debug</position>
	</positions>
```

Chaque balise crée une position de module disponible dans la liste des positions dans un formulaire de modification de module. Le format simple de la liste des positions signifie qu'elle peut être facilement personnalisée. Par exemple, pour ajouter une nouvelle position de module à la liste **dans un modèle enfant**, ajoutez simplement une nouvelle balise à l'intérieur de la balise avec un nom unique en utilisant toutes les lettres minuscules sans espaces. Gardez à l'esprit que cela n'ajoute la position que dans les formulaires de modification des modules et qu'un développement supplémentaire dans d'autres fichiers de modèle est nécessaire pour afficher la nouvelle position sur l'interface.

Cassiopeia a suffisamment de positions de modèle ! Si vous pensez en avoir besoin d'une supplémentaire, vous avez probablement tort. Souvenez-vous que tout nombre de modules peut être attribué à une seule position et trié dans l'ordre sur la page de liste des Modules. Positions disponibles :

![schéma des positions des modèles Cassiopeia](../../../en/images/templates/cassiopeia-template-positions.png)

Vous pouvez également voir les positions des modules dans n'importe quel modèle : depuis **Système → Modèles de site**, sélectionnez le bouton Options dans la barre d'outils. Dans le formulaire Options, définissez le champ Présentation des positions des modules sur Activé. Enregistrez et Fermez. Accédez à votre site et ajoutez ?tp=1 à la fin de n'importe quel URL (ou &tp=1 s'il y a déjà un ? dans l'URL). Joomla affichera toutes les positions des modèles disponibles, même celles qui n'ont pas été utilisées :

![positions des modèles Cassiopeia](../../../en/images/templates/templates-template-positions-by-tp.png)

### Langues

Les fichiers de langue permettent la traduction de texte statique dans le modèle. Le fichier tpl_cassiopeia.ini contient les traductions clé de texte pour le texte consulté par l'Utilisateur. Le fichier tpl_cassiopeia.sys.ini contient les traductions clé de texte pour le texte consulté par l'Administrateur.

```xml
	<languages folder="language">
		<language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
		<language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
	</languages>
```

Les fichiers de langue pour la langue par défaut anglaise GB sont stockés dans site/language/en-GB/. D'autres langues seraient stockées de la même manière dans des fichiers avec le code de langue ISO approprié, par exemple fr-FR pour le français en France ou de-DE pour l'allemand en Allemagne (qui pourrait être différent de l'allemand suisse et de l'allemand autrichien).

### Options

Un modèle peut offrir des options d'affichage pouvant être choisies par l'Administrateur dans le formulaire Modèle : Modifier le style. Par exemple, l'onglet Avancé du modèle Cassiopeia permet à un Administrateur de changer la Marque, d'ajouter un Logo, de sélectionner un Schéma de Polices, et plus encore.

![formulaire de modification du style des modèles onglet avancé](../../../en/images/templates/templates-edit-style-advanced.png)

Les options du modèle sont définies dans une structure qui crée des champs dans des groupes de champs. Chaque groupe de champs apparaît comme un onglet dans le formulaire de modification. Voici la structure qui crée l'onglet Avancé vu ci-dessus.

```xml
	<config>
		<fields name="params">
			<fieldset name="advanced">
				<field
					name="brand"
					type="radio"
					label="TPL_CASSIOPEIA_BRAND_LABEL"
					default="1"
					layout="joomla.form.field.radio.switcher"
					filter="boolean"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>
				...
			</fieldset>
		</fields>
	</config>
```

Les options individuelles sont définies avec la balise `<field>`. Chaque `<fieldset>`, et chaque paramètre `<field>` dans un `<fieldset>`, nécessite un nom unique défini par un attribut **name**. Ce nom définit le paramètre lui-même et est utilisé pour passer des paramètres aux fichiers de l'interface. Chaque paramètre contient également un attribut **label** et un attribut **description**. Le texte de l'étiquette apparaît avec le paramètre dans l'écran des paramètres pour identifier à quoi sert le paramètre et des informations plus détaillées peuvent être incluses dans la description.

Un champ de paramètre peut être pratiquement n'importe quel type d'entrée de formulaire avec les options correspondantes. Cela est sélectionné par l'attribut **type**. Les options nécessaires, telles que les choix de bouton radio ou de sélection, sont définies dans les balises `<option>`. Les noms de classes CSS peuvent être définis avec l'attribut **class** et une valeur par défaut peut être définie à l'aide de l'attribut **default**.

Voici les définitions des options dans le modèle Cassiopeia par défaut. Dans cet exemple, toutes les étiquettes, descriptions et options utilisent des définitions de chaîne de langue des fichiers de langue définis dans la section précédente, ainsi que certaines du noyau de Joomla!, pour qu'elles puissent être traduites dans différentes langues au besoin.

```xml
	<config>
		<fields name="params">
			<fieldset name="advanced">
				<field
					name="brand"
					type="radio"
					label="TPL_CASSIOPEIA_BRAND_LABEL"
					default="1"
					layout="joomla.form.field.radio.switcher"
					filter="boolean"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>

				<field
					name="logoFile"
					type="media"
					default=""
					label="TPL_CASSIOPEIA_LOGO_LABEL"
					showon="brand:1"
				/>

				<field
					name="siteTitle"
					type="text"
					default=""
					label="TPL_CASSIOPEIA_TITLE"
					filter="string"
					showon="brand:1"
				/>

				<field
					name="siteDescription"
					type="text"
					default=""
					label="TPL_CASSIOPEIA_TAGLINE_LABEL"
					description="TPL_CASSIOPEIA_TAGLINE_DESC"
					filter="string"
					showon="brand:1"
				/>

				<field
					name="useFontScheme"
					type="groupedlist"
					label="TPL_CASSIOPEIA_FONT_LABEL"
					default="0"
					>
					<option value="0">JNONE</option>
					<group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
						<option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (local)</option>
					</group>
					<group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
						<option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
						<option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
					</group>
				</field>

				<field
					name="noteFontScheme"
					type="note"
					description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
					class="alert alert-warning"
				/>

				<field
					name="colorName"
					type="filelist"
					label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
					default="colors_standard"
					fileFilter="^custom.+[^min]\.css$"
					exclude="^colors.+"
					stripext="true"
					hide_none="true"
					hide_default="true"
					directory="media/templates/site/cassiopeia/css/global/"
					validate="options"
					>
					<option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
					<option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
				</field>

				<field
					name="fluidContainer"
					type="radio"
					layout="joomla.form.field.radio.switcher"
					default="0"
					label="TPL_CASSIOPEIA_FLUID_LABEL"
					>
					<option value="0">TPL_CASSIOPEIA_STATIC</option>
					<option value="1">TPL_CASSIOPEIA_FLUID</option>
				</field>

				<field
					name="stickyHeader"
					type="radio"
					label="TPL_CASSIOPEIA_STICKY_LABEL"
					layout="joomla.form.field.radio.switcher"
					default="0"
					filter="integer"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>

				<field
					name="backTop"
					type="radio"
					label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
					layout="joomla.form.field.radio.switcher"
					default="0"
					filter="integer"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>
			</fieldset>
		</fields>
	</config>
```

Dans cet exemple, la balise `<fieldset name="advanced">` enveloppe tous les paramètres et utilise l'attribut **name** pour créer l'onglet *Avancé* dans l'interface. Tout ce qui est nécessaire pour créer un autre onglet dans l'interface est une autre balise `<fieldset>` avec un attribut **name** différent. Avec cela en tête, il est relativement simple de créer autant d'onglets et de paramètres supplémentaires que nécessaire dans un modèle.

Une utilisation potentielle de paramètres supplémentaires est dans les overrides ou les mises en page pour les modèles parents ou enfants.

## Résumé

Ceci est le fichier templateDetails.xml utilisé par Cassiopeia :

```xml
<?xml version="1.0" encoding="utf-8"?>
<extension type="template" client="site">
	<name>cassiopeia</name>
	<version>1.0</version>
	<creationDate>2017-02</creationDate>
	<author>Joomla! Project</author>
	<authorEmail>admin@joomla.org</authorEmail>
	<copyright>(C) 2017 Open Source Matters, Inc.</copyright>
	<description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
	<inheritable>1</inheritable>
	<files>
		<filename>component.php</filename>
		<filename>error.php</filename>
		<filename>index.php</filename>
		<filename>joomla.asset.json</filename>
		<filename>offline.php</filename>
		<filename>templateDetails.xml</filename>
		<folder>html</folder>
	</files>
	<media destination="templates/site/cassiopeia" folder="media">
		<folder>js</folder>
		<folder>css</folder>
		<folder>scss</folder>
		<folder>images</folder>
	</media>
	<positions>
		<position>topbar</position>
		<position>below-top</position>
		<position>menu</position>
		<position>search</position>
		<position>banner</position>
		<position>top-a</position>
		<position>top-b</position>
		<position>main-top</position>
		<position>main-bottom</position>
		<position>breadcrumbs</position>
		<position>sidebar-left</position>
		<position>sidebar-right</position>
		<position>bottom-a</position>
		<position>bottom-b</position>
		<position>footer</position>
		<position>debug</position>
	</positions>
	<languages folder="language">
		<language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
		<language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
	</languages>
	<config>
		<fields name="params">
			<fieldset name="advanced">
				<field
					name="brand"
					type="radio"
					label="TPL_CASSIOPEIA_BRAND_LABEL"
					default="1"
					layout="joomla.form.field.radio.switcher"
					filter="boolean"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>

				<field
					name="logoFile"
					type="media"
					default=""
					label="TPL_CASSIOPEIA_LOGO_LABEL"
					showon="brand:1"
				/>

				<field
					name="siteTitle"
					type="text"
					default=""
					label="TPL_CASSIOPEIA_TITLE"
					filter="string"
					showon="brand:1"
				/>

				<field
					name="siteDescription"
					type="text"
					default=""
					label="TPL_CASSIOPEIA_TAGLINE_LABEL"
					description="TPL_CASSIOPEIA_TAGLINE_DESC"
					filter="string"
					showon="brand:1"
				/>

				<field
					name="useFontScheme"
					type="groupedlist"
					label="TPL_CASSIOPEIA_FONT_LABEL"
					default="0"
					>
					<option value="0">JNONE</option>
					<group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
						<option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (local)</option>
					</group>
					<group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
						<option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
						<option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
					</group>
				</field>

				<field
					name="noteFontScheme"
					type="note"
					description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
					class="alert alert-warning"
				/>

				<field
					name="colorName"
					type="filelist"
					label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
					default="colors_standard"
					fileFilter="^custom.+[^min]\.css$"
					exclude="^colors.+"
					stripext="true"
					hide_none="true"
					hide_default="true"
					directory="media/templates/site/cassiopeia/css/global/"
					validate="options"
					>
					<option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
					<option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
				</field>

				<field
					name="fluidContainer"
					type="radio"
					layout="joomla.form.field.radio.switcher"
					default="0"
					label="TPL_CASSIOPEIA_FLUID_LABEL"
					>
					<option value="0">TPL_CASSIOPEIA_STATIC</option>
					<option value="1">TPL_CASSIOPEIA_FLUID</option>
				</field>

				<field
					name="stickyHeader"
					type="radio"
					label="TPL_CASSIOPEIA_STICKY_LABEL"
					layout="joomla.form.field.radio.switcher"
					default="0"
					filter="integer"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>

				<field
					name="backTop"
					type="radio"
					label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
					layout="joomla.form.field.radio.switcher"
					default="0"
					filter="integer"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>
			</fieldset>
		</fields>
	</config>
</extension>
```

*Traduit par openai.com*

