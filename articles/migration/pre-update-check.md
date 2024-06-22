<!-- Filename: Pre-Update_Check / Display title: Vérification préalable à la mise à jour -->

Le composant de pré-vérification de mise à jour est la nouveauté de
Joomla! 3.10.x. Ce composant affiche les spécifications techniques du
serveur sur lequel le site est installé, ainsi que les extensions
centrales et de tierces parties qui utilisent le serveur de mise à jour
sous forme de liste.

**To navigate to the Update-screen:**

- Click the 'Live Update' tab.

**Pour aller à l'écran du Pré-vérificateur de mise à jour:**

- Cliquez sur l'élément de menu **Components **→** Joomla! Update** de
  la barre du haut.
- Si vous ne voyez pas l'écran du Pré-vérificateur de mise à jour
  cliquez sur le bouton "Vérifiez les mises à jour" ou effacez le cache
  et actualisez la page.
- Vérifiez également que le site est sur le canal de mise à jour du
  prochain joomla. **Administrator **→** Composants **→** Mise à jour de
  Joomla **→** Options **→** Update Channel**. Sélectionnez *Joomla
  Next*, puis *sauvegarder et fermer*.

## Spécifications techniques

La partie supérieure de la vérification avant mise à jour indique si
votre environnement de serveur actuel est compatible avec la version
cible actuelle de Joomla pour les paramètres PHP et de base de données
requis. Les données de la page
<a href="https://downloads.joomla.org/technical-requirements"
class="external text" target="_blank"
rel="noreferrer noopener">Pré-requis techniques</a> montrent les
spécifications que nous vérifions.

<img
src="https://docs.joomla.org/images/thumb/b/b0/Php_and_database_settings-en.png/800px-Php_and_database_settings-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/b/b0/Php_and_database_settings-en.png/1200px-Php_and_database_settings-en.png 1.5x, https://docs.joomla.org/images/thumb/b/b0/Php_and_database_settings-en.png/1600px-Php_and_database_settings-en.png 2x"
data-file-width="1890" data-file-height="996" width="800" height="422"
alt="Partie du composant de vérification préalable à la mise à jour concernant le PHP et les paramètres de la base de données" />
<img
src="https://docs.joomla.org/images/thumb/d/d1/Recommended_php_settings-en.png/800px-Recommended_php_settings-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/d/d1/Recommended_php_settings-en.png/1200px-Recommended_php_settings-en.png 1.5x, https://docs.joomla.org/images/thumb/d/d1/Recommended_php_settings-en.png/1600px-Recommended_php_settings-en.png 2x"
data-file-width="1869" data-file-height="733" width="800" height="314"
alt="Partie paramètres PHP recommandés du composant de Pré-vérification de mise à jour" />

L'important est de vérifier si quelque chose est rouge et n'est pas
compatible avec Joomla 4.x. Si ce n'est pas le cas, vous devrez en
parler à votre hébergeur ou changer d'hébergement avant de migrer vers
Joomla 4.x. Pendant une migration, c'est le moment idéal pour changer
d'hôte. Voir l' entonnoir de la
migration
pour plus d'informations sur la planification et les instructions étape
par étape.

## Vérification préalable des extensions

La partie extension du composant de vérification des mises à jour
extrait des extensions tierces.

La liste est divisée en sections basées sur la balise *targetplatform*,
les extensions que vous utilisez ou non. Pour les développeurs, voirpour plus d'informations sur ces balises et sur la manière de déployer
un serveur de mise à jour. Pour plus d'informations sur le système de
mise à jour Joomla, voir les pages <a
href="https://extensions.joomla.org/support/knowledgebase/submission-requirements/joomla-update-system-requirement/"
class="external text" target="_blank"
rel="noreferrer noopener">Pré-requis pour la mise à jour du système
Joomla !</a> et <a
href="https://docs.joomla.org/Help39:Extensions_Extension_Manager_Update"
class="external text" target="_blank"
rel="noreferrer noopener">Extensions Gestion des mises à jour
d'extensions</a>.

En cliquant sur le lien **Plus de détails** à droite dans chaque en-tête
de couleur, vous pouvez voir des informations supplémentaires sur les
extensions installées sur votre site.

<img
src="https://docs.joomla.org/images/thumb/4/40/Pre_upgrade_checker_error-en.png/800px-Pre_upgrade_checker_error-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/40/Pre_upgrade_checker_error-en.png/1200px-Pre_upgrade_checker_error-en.png 1.5x, https://docs.joomla.org/images/thumb/4/40/Pre_upgrade_checker_error-en.png/1600px-Pre_upgrade_checker_error-en.png 2x"
data-file-width="1850" data-file-height="648" width="800" height="280"
alt="Mise à jour des informations non disponibles" />

Les extensions listées ici ne supportent pas encore le système de mise à
jour de Joomla ou du moins n'ont pas de balise targetplatform qui
indique le support de la version cible de Joomla sélectionnée. (voirVeuillez contacter le développeur des extensions listées pour vous
assurer qu'elles sont compatibles avec la version 4.x.

<img
src="https://docs.joomla.org/images/thumb/1/12/Pre_upgrade_checker_warning-en.png/800px-Pre_upgrade_checker_warning-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/1/12/Pre_upgrade_checker_warning-en.png/1200px-Pre_upgrade_checker_warning-en.png 1.5x, https://docs.joomla.org/images/thumb/1/12/Pre_upgrade_checker_warning-en.png/1600px-Pre_upgrade_checker_warning-en.png 2x"
data-file-width="1874" data-file-height="434" width="800" height="185"
alt="Mise à jour requise" />

Les extensions listées ici nécessitent une mise à jour pour fonctionner
correctement sur 4.x. Veuillez contacter le développeur des extensions
listées pour vous assurer que vous devez mettre à jour le composant
avant ou après la mise à jour.

<img
src="https://docs.joomla.org/images/thumb/1/19/Pre_upgrade_checker_ok-en.png/800px-Pre_upgrade_checker_ok-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/1/19/Pre_upgrade_checker_ok-en.png/1200px-Pre_upgrade_checker_ok-en.png 1.5x, https://docs.joomla.org/images/thumb/1/19/Pre_upgrade_checker_ok-en.png/1600px-Pre_upgrade_checker_ok-en.png 2x"
data-file-width="2038" data-file-height="600" width="800" height="236"
alt="Aucune mise à jour nécessaire" />

Les extensions énumérées ici se déclarent compatibles 4.x et aucune mise
à jour n'est nécessaire.

## Qu'en est-il de ce *potentiel problème de mise à niveau*

Les plugins avec le type ('system', 'user', 'authentication',
'actionlog', 'twofactorauth') pourraient être déclenchés pendant que
nous traitons la mise à jour. S'il se produit un problème critique dans
ces plugins cela pourrait entraîner une interruption de la mise à jour
rendant le site inutilisable. Pour cette raison, tout plugin de ce type
qui n'est pas explicitement répertorié comme compatible doit être
examiné encore plus attentivement avant d'appuyer sur le bouton de mise
à jour. Il est **fortement** recommandé de désactiver les plugins en
question et de vérifier auprès du développeur d'origine.

<img
src="https://docs.joomla.org/images/thumb/1/1e/Pre_upgrade_checker_popup-en.png/200px-Pre_upgrade_checker_popup-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/1/1e/Pre_upgrade_checker_popup-en.png/300px-Pre_upgrade_checker_popup-en.png 1.5x, https://docs.joomla.org/images/thumb/1/1e/Pre_upgrade_checker_popup-en.png/400px-Pre_upgrade_checker_popup-en.png 2x"
data-file-width="492" data-file-height="446" width="200" height="181"
alt="The popup warning for potencial upgrade issue" />

Sur l'onglet *Mise à jour en direct* on vous présentera à nouveau la
liste complète des extensions pouvant interrompre la mise à jour.

<img
src="https://docs.joomla.org/images/thumb/b/b1/Live_upgrade_tab_errors-en.png/800px-Live_upgrade_tab_errors-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/b/b1/Live_upgrade_tab_errors-en.png/1200px-Live_upgrade_tab_errors-en.png 1.5x, https://docs.joomla.org/images/thumb/b/b1/Live_upgrade_tab_errors-en.png/1600px-Live_upgrade_tab_errors-en.png 2x"
data-file-width="2042" data-file-height="787" width="800" height="308"
alt="The Live Update message on potential breaking extensions" />

Il est **fortement** recommandé de désactiver toutes les extensions, y
compris les plugins répertoriés ici avant d'exécuter la mise à niveau,
car les extensions répertoriées ici ne semblent pas être compatibles
avec votre version cible mais pourraient interrompre votre mise à
niveau.

Savez vous ce que vous faites ? Vous voulez choisir d'ignorer les
avertissements et d'exécuter la mise à niveau de toute façon, vous
pouvez le faire en cochant la case. Comme cela risque de casser votre
site sans récupération facile, c'est la dernière fois pour vous rappeler
de faire une sauvegarde !

## Questions et réponses

Décomposons cela en quelques questions et réponses.

**Q : Que signifient les balises ?**

R : La balise verte *Pas de mise à jour nécessaire* signifie que
l'extension a été marquée par le développeur comme étant prête pour
Joomla 4. Elle *devrait* migrer en un clic de 3.10.x à 4.x. Il est
suggéré de vérifier cela avec le développeur.

La balise rouge *Mise à jour des informations non disponibles* signifie
que l'extension n'a pas ajouté d'informations compatibles avec
l'extension. Vérifiez avec le développeur sur le processus de migration
de 3.10.x à 4.x.

La balise jaune/orange **Oui (x.x.x)** signifie que l'extension a été
identifiée par le développeur comme pouvant nécessiter une mise à jour
pour être compatible avec Joomla 4. Mettez à jour l'extension et voyez
si elle devient un Oui vert. Si ce n'est pas le cas, vérifiez avec le
développeur sur le processus de migration de 3.10.x à 4.x.

La balise grise **Compatibilité manquante** signifie que l'extension n'a
pas de balise **ou** n'utilise pas le serveur de mise à jour. Le
développeur n'a pas dit oui ou non ou a besoin d'une mise à jour. Dans
certains cas, un paquet peut avoir été installé et la partie composant a
une balise mais les plugins ou modules supplémentaires sont des balises
manquantes. Comme toujours, vous devrez vérifier avec chaque développeur
d'extension le processus de migration de la version 3.10.x à la version
4.x.

Q : Qu'en est-il des composants principaux de Joomla ?

R : Les extensions de base de Joomla migreront de 3.10.x à 4.x en un
seul clic, avec ces exceptions :

Les packs linguistiques ne sont pas encore prêts pour Joomla 4 (en
septembre 2020). Avec le temps, ils le seront. Si votre site dépend
d'autres packs linguistiques, attendez que tous les packs linguistiques
soient prêts avant de migrer.

Le composant Weblinks n'est pas encore prêt pour Joomla 4 (à partir de
septembre 2020). Si vous comptez continuer à utiliser Weblinks sur votre
site Joomla 4, attendez que le composant Weblinks soit prêt pour migrer.

Q : Qu'en est-il des templates ?

R : En raison des changements apportés à Joomla 4, votre template peut
ou non être compatible avec Joomla 4. Les templates de base comme
Protostar, Beez3, Beez5, etc. seront "convertis" en un clic au nouveau
template Cassiopeia et les anciens templates seront complètement
supprimés. Si vous utilisez un template de club d'un développeur tiers
qui n'est pas compatible avec Joomla 4, vous devrez changer votre
template par défaut en Protostar (ou Beez3) avant de faire le one-click.
Si vous avez des templates d'administrateur ou des templates de base
plus anciens, il est recommandé de les désinstaller tous sauf celui que
vous définirez comme template de base par défaut. Cela inclut Bluestork,
Hathor et les autres templates beez. Vous conserverez Isis comme
template d'administrateur. Vous conserverez par défaut votre template
tiers compatible, Protostar ou Beez3. Vous désinstallerez le reste.

Q : Puis-je désinstaller plg_content_geshi ?

R : Oui. Il s'agit d'un reliquat du cycle de vie de Joomla! 2.5 qui
**doit** être désinstallé.

Q : Qu'en est-il de tous ces FOF, fef, etc.

R : De nombreuses extensions dans les rubriques rouge ou jaune/orange
*seront / pourront* passer le cap d'un seul clic et migrer sans
problème. Il est recommandé d'aller sur Extensions→Gestion→Gestion et de
vérifier toutes les extensions. En général, celles qui ont été créées
par Joomla migrent en un seul clic. Les extensions Akeeba le feront
également. Encore une fois, vérifiez avec les développeurs d'extensions
le chemin de migration sur *toutes* les extensions tierces.

Q : Le contrôle de pré-mise à jour des extensions montre-t-il toutes les
extensions installées sur mon site ?

R : La vérification préalable à la mise à jour affichera toutes les
extensions. Seules les extensions qui utilisent le serveur de mise à
jour reçoivent des informations de compatibilité. Les extensions qui
n'utilisent pas le serveur de mise à jour s'afficheront dans la liste
avec **l'étiquette compatibilité manquante**.

## Résumé

Du point de vue de la migration, je pense que la vérification préalable
devrait servir de guide. Vous voudrez avoir un deuxième onglet ouvert
avec *Extensions→Gestion→Gestion* afin de désinstaller les extensions ou
de vérifier par qui elles ont été créées afin que vous puissiez
contacter les développeurs d'extensions tiers sur la voie de migration
qu'ils ont établie pour migrer leurs extensions.
