<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_IIS/IIS7 / Display title: Autoriser les réécriture d'URL en clair  (SEF) avec IIS/IIS7 -->

Si votre serveur utilise IIS 7 et PHP, vous pouvez bénéficier de la
réécriture d'URL propre à IIS en utilisant un fichier web.config
similaire à celui décrit ci-dessous.

Vous pouvez soit créer le fichier vous-même ou bien à travers l'IHM du
gestionnaire IIS7. Vous pouvez importer les règles .htaccess en
utilisant le GUI/wizard.

L'utilisation de cette fonctionnalité dépend de la présence du module
**IIS URL Rewrite Module**, qui n'est pas installé par défaut avec
Windows. C'est un téléchargement gratuit d'un produit Microsoft.

### IHM

Si le module IIS "URL Rewrite module" est installé, votre gestionnaire
de site mettra à disposition un outil "URL Rewrite", visible dans
l'interface du gestionnaire d'IIS dans les modules IIS de la
configuration de votre site. L'interface est largement intiutive. Les
expressions régulières, les caractères spéciaux et les correspondances
exactes sont tous supportés.

Dans la configuration de Joomla, activez à la fois SEF et Apache
mod_rewrite. Ensuite, créer une règle dans IIS URL Rewrite :

Pattern field: **^(\[^/\]+)/?\$**

Ignore case **ON**

Action type: **Rewrite**

Rewrite URL: **index.php/**

### web.config

Ceci a été testé avec Joomla 1.5 et IIS 7 sous Windows Server 2008 sans
rencontrer de problèmes. Pour plus d'information sur la conversion de
.htaccess en web.config, reportez-vous à <a
href="http://learn.iis.net/page.aspx/557/translate-htaccess-content-to-iis-webconfig/"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">http://learn.iis.net/page.aspx/557/translate-htaccess-content-to-iis-webconfig/</a>


        
            
                
                    
                    
                        
                        
                            
                            
                            
                            
                            
                        
                        
                    
                    
                        
                        
                            
                        
                        
                    
                    
                        
                        
                            
                            
                            
                        
                        
                    
                
            
            
                
                    
                
            
        
