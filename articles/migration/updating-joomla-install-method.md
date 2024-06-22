<!-- Filename: J3.x:Updating_Joomla_(Install_Method) / Display title: Mise à jour de Joomla! (méthode d'installation) -->

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Warning!

From Joomla 3.5 you can no longer use this to update Joomla, useinstead.

In some cases it may not be possible to use the Extension Manager:
Update method to update your site. One reason for this might be that you
are using a non-standard distribution (for example, a distribution with
a different default language installed). Another reason might be that
you don't have a reliable Internet connection to support automatic
installation.

In this case, you can still do an easy installation using the Extension
Manager: Install screen. Like the Update screen, this method will do the
database updates automatically and will completely update your system
without any further steps.

## Étape 1 : assurez-vous d'avoir une sauvegarde de votre site actuel

Dans la plupart ces cas, votre hébergeur fait périodiquement des
sauvegardes de votre site.

## Étape 2 : localisez le fichier de mise à jour

Locate the required archive file (for example, .zip, .tag.gz, or tar.bz2
archive) for your version. If you are updating to an x.x.0 release (for
example, from 1.7.3 to 2.5.0), this will normally be a file like
Joomla_2.5.0-Stable-Update_Package.zip. If you are updating within the
same release series (for example, 2.5.0 to 2.5.1), then the file will be
named something like Joomla_2.5.0_to_2.5.1-Stable-Patch_Package.zip.

À ce stade, vous disposez de trois options :

1.  Installer depuis une adresse URL
2.  Installer depuis un dossier
3.  Archive à envoyer

Install from URL is the easiest to do. With this option, the upgrade
archive is loaded directly by the server, so it works well even if your
local computer has a slow or unreliable Internet connection.

Install from Directory is the safest method if the server itself has a
slow Internet connection. With this method, you use FTP to load the
unpacked update files into a temporary folder on the server. Then you
point to that directory on the server for the installation.

Upload Package File is fairly simple, but it requires that you have a
good connection between your local computer and the server.

The screen below shows the Extension Manager: Install screen with the
three options labeled.

<img
src="https://docs.joomla.org/images/9/93/Update-screenshot-20120124-03-en.png"
class="thumbimage" decoding="async" data-file-width="809"
data-file-height="365" width="809" height="365"
alt="Update-screenshot-20120124-03-en.png" />

### Installer depuis une adresse URL

This option is the easiest if the archive file is available on a
Website.

1.  In the Extension Manager: Install screen, enter the URL for the
    archive file in the Install URL field.
2.  Cliquez sur le bouton Installer.

The system will work for a period of time - up to two minutes or more
for a full version update. Then a message indicating a successful
installation will display.

### Installer depuis un dossier

This option requires that you unpack the archive file in a directory on
your server. This is the best method if you have a slow Internet
connection or you are experiencing timeouts during the update process.

1.  Unpack the archive file in a temporary directory on your local
    machine.
2.  Upload all the files in this directory (for example, using FTP) to a
    temporary directory that is visible to the Web server. For example,
    you can create a sub-directory under the tmp directory in your
    Joomla root. For this example, let's say the directory on the server
    is `/home/myuser/myjoomla/tmp/upgrade250`).
3.  In the Extension Manager: Install screen, enter the full path of the
    temporary directory (on the server) from step 2 (for example,
    `/home/myuser/myjoomla/tmp/upgrade250`).
4.  Cliquez sur le bouton Installer.

The system will work for a short time (perhaps a minute or less,
depending on your server). Then a message indicating a successful
installation will display.

### Archive à envoyer

This option requires that you first download the archive file to your
local machine.

1.  Téléchargez le fichier sur votre ordinateur.
2.  In the Extension Manager: Install screen, click the Browse button
    next to the Package File field and browse to the archive file.
3.  Cliquez sur le bouton Installer.

The system will work for a period of time - up to two minutes or more
for a full version update. Then a message indicating a successful
installation will display.

1.  Félicitations ! À ce stade, votre site est mis à jour.

**Important:** Clear your browser cache and check that your site is
working correctly. See below Checking Your Site.
