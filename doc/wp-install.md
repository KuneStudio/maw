<p>Ce guide a pour but de mettre en place un environnement de démarage pour Wordpress. Avant toute installation, il est bon de relire ce guide pour ne rien oublié. <br>
Chaque étape est importante et ne doit pas être oubliée.</p>

<p>Le guide est découpé en plusieurs parties, allant de l’installation propre de Wordpress à l’activation de plusieurs plugins, jusqu’à la configuration de certain de ces derniers.</p>



<h2 id="installation-de-wordpress">Installation de Wordpress</h2>



<h3 id="environnement-de-développement">Environnement de développement</h3>

<p>Tout développement doit d’abord passer par un environnement de développement. Cette étape nous permettra, même pour les “petits” sites, de maintenir à jour le code proprement.</p>

<p>Plusieurs options sont possibles :  <br>
* Télécharger l’archive par <a href="http://fr.wordpress.org/">le site officiel</a> <br>
* Téléchargement par GIT sur <a href="https://github.com/WordPress/WordPress">le repo officiel</a></p>



<h3 id="installation">Installation</h3>

<p>Une fois l’installation de WP lancée, il convient de respecter ces quelques consignes :</p>

<ul>
<li>Utiliser un nom d’utilisateur différent de admin. Les attaques de masse sur les installations WP partent du principe que beaucoup d’installations utilisent ce nom d’utilisateur.</li>
<li>Utiliser un mot de passe fort. Il doit contenir des caractères alphanumériques ainsi que des caractères spéciaux (-, _, !, $, € …). Un minimum de 8/10 caractères est plus que recommandé.</li>
<li>Utiliser un préfixe de table <strong>différent</strong> de wp_ . La raison est la même que pour le premier point, wp_ est utilisé par la majorité des sites, il convient d’en utiliser une autre, distincte.</li>
</ul>



<h4 id="1-supprimer-les-fichiers-inutiles">1) Supprimer les fichiers inutiles</h4>

<p>Cette étape va nous permettre de supprimer les informations sur notre installation qui pourraient être utile à un tiers pour accéder à notre site. <br>
Les fichiers et dossiers à supprimer sont donc :</p>

<ul>
<li>licence.txt</li>
<li>readme.html</li>
<li>wp-content/plugins/hello.php</li>
</ul>

<p>Si le site n’est pas prévu pour recevoir de commentaires, supprimer aussi <strong>wp-content/plugins/akismet</strong>.</p>



<h4 id="2-génération-des-permaliens">2) Génération des permaliens</h4>

<p>Une fois les permaliens générés, nous pourrons passer à la modification du fichier <strong>.htaccess</strong>.  <br>
Il n’y a pas vraiment de meilleur choix pour les permaliens. La seule recommandation, d’un point de vue SEO serait :</p>

<ul>
<li>Format “jour et nom de l’article” si le site est plutôt tourné vers l’actualité : <code>/%year%/%monthnum%/%day%/%postname%/</code></li>
<li>Pour tout le reste, juste le nom de l’article <code>/%postname%/</code> ou catégorie et nom de l’article `/%category%/%postname%/“</li>
</ul>



<h3 id="plugins-à-installer-par-défaut">Plugins à installer par défaut</h3>

<p>Vous pourrez trouver les plugins décrits plus bas en vous rendant dans votre espace d’administration : Plugins &gt; Ajouter &gt; Favorites. <br>
Vous pouvez alors rechercher l’utilisateur MawMat et installer tous les plugins présents dans la liste, en commençant par :</p>



<h4 id="ithemes-security">iThemes Security</h4>

<p>Ce plugin important va nous permettre de réaliser quelques opérations simples pour augmenter la sécurité de notre installation.</p>



<h5 id="1-une-fois-le-plugin-activé-cliquez-sur-secure-your-site-now-une-fenêtre-va-souvrir-procédez-aux-3-opérations">1) Une fois le plugin activé, cliquez sur <em>Secure your site now</em>. Une fenêtre va s’ouvrir, procédez aux 3 opérations.</h5>

<ul>
<li>Backup du site</li>
<li>Allow file update</li>
<li>One click secure</li>
</ul>

<p>Après avoir effectué cette dernière opération, plusieurs points sont encore à résoudre, mais nous reviendrons dessus lorsque le site sera prêt à être mis en production. Pour le moment, seuls ces points sont important :</p>

<ul>
<li><em>A user with id 1 still exists.</em> : Vous devrez vous reconnecter après avoir réalisé cette opération, c’est normal. Même login, même mot-de-passe.</li>
<li><em>Hide login area</em> : cela changera l’adresse permettant de se logguer.</li>
</ul>

<p>Passez ensuite à la partie <em>Settings</em> et défilez jusqu’à la section <em>Banned Users</em>. Activez la blacklist <em>Hackrepairs.com</em> et enregistrez.</p>

<p>Rendez-vous ensuite dans la partie “Advanced” du menu, et changez le nom du dossier content. Il est <strong>IMPORTANT</strong> de faire ça des l’installation de Wordpress pour ne pas avoir à réécrire les liens vers les fichiers à posteriori.</p>

<p>Activez enfin les protections .htaccess, cela empèchera les modifications de fichiers et autres actes malveillants.</p>



<h4 id="plugin-de-sauvegarde">Plugin de sauvegarde</h4>

<p>Le plugin recommandé est BackupBuddy. Payant mais très pratique. Il regroupe de nombreuses fonctions supplémentaires comme un outil de migration dev/prod.</p>

<p>Quelque soit le plugin que vous choisissez, pensez à régler les sauvegardes pour qu’elles travaillent tous les jours (pendant la nuit) pour la BDD, et toute les semaines pour les fichiers. Si votre plugin vous permet de ne sauvegarder que ce qui a été créé depuis la dernière sauvegarde, faites le tous les jours.</p>



<h4 id="wordpress-seo-by-yoast">WordPress SEO by Yoast</h4>

<p>Plugin qui permettra de bien gérer le SEO du site. Il est VIVEMENT recommandé de ne pas utiliser les outils de SEO des thèmes. Lorsque le thème change, le risque est trop grand de perdre tout le travail effectué pour le SEO.</p>



<h4 id="wp-super-cache">WP Super Cache</h4>

<p>Plugin qui permet une meilleure mise en cache du site. </p>



<h4 id="google-analytics-for-wordpress">Google Analytics for WordPress</h4>

<p>De même que pour le SEO, il est recommandé de ne pas utiliser les fonctions du thème pour Google Analytics, en cas de changement de thème.</p>



<h4 id="wp-smushit">WP Smush.it</h4>

<p>Plugin d’optimisation des images.</p>



<h4 id="wp-sync-db-fork-de-wp-migrate-pro">WP Sync DB (Fork de WP Migrate Pro)</h4>

<p>Ce plugin nous aidera lors de la migration de la BDD. <br>
Il faut le télécharger sur <a href="https://github.com/wp-sync-db/wp-sync-db">le github du projet</a>.</p>



<h4 id="iwp-client">IWP Client</h4>

<p>Ce plugin va nous servir à manager le site, pour les mises à jour notamment. <a href="https://wordpress.org/plugins/iwp-client/">https://wordpress.org/plugins/iwp-client/</a></p>



<h2 id="gestion-du-thème">Gestion du thème</h2>

<p>Il faut bien faire attention aux thèmes que l’on installe sur un site, même en version de test. Je déconseille fortement toute utilisation de thème téléchargé hors de la plateforme d’achat ou du site officiel.  <br>
Il est fort probable qu’ils aient été modifié pour y ajouter du code malicieux qui permettrait de pirater le site ou effectuer des actions négative pour le site.</p>



<h3 id="ajout-de-contenu-de-test">Ajout de contenu de test</h3>

<p>Avant l’installation du thème, une bonne pratique est d’installer du contenu de test afin de vérifier que toutes les fonctions typographiques et graphiques (images, vidéos …) sont bien prises en compte par le thème.  <br>
Pour cela, télécharger l’archive présente ici : <a href="http://wptest.io">wptest.io</a> et suivez les instructions dans le readme.</p>



<h3 id="développement-et-modifications">Développement et modifications</h3>

<p>Une fois le thème sélectionné est installé, si une modification est souhaitée, il est FORTEMENT recommandé de créer un thème enfant.</p>

<p>Pour cela, il faut créer un dossier avec le nom du thème enfant dans <em>wp-content/themes/</em> et y ajouter un fichier <em>style.css</em>. <br>
Dans ce dernier, ajoutez les lignes suivantes au début du fichier :</p>

<pre><code>/*
 Theme Name:   Nom du thème enfant
 Theme URI:    http://www.marsatwork.fr
 Description:  Description du thème
 Author:       Marsatwork
 Author URI:   http://marsatwork.fr
 Template:     nom_du_theme_parent
 Version:      1.0.0
 Text Domain:  nom-theme-enfant
*/


@import url("../nom_du_theme_parent/style.css");


/* Commencez les modifications ci-dessous
----------------------------------------------- */
</code></pre>

<p>Si vous souhaitez modifier un fichier, copiez l’original dans ce dossier et modifiez le. Il sera utilisé automatiquement par WP au lieu du fichier principal.</p>



<h4 id="modifications-ultérieures">Modifications ultérieures</h4>

<p>Si vous souhaitez de nouveau modifier un fichier, lors de la phase de recette par exemple, si vous n’utilisez pas de versionning, pensez à bien dupliquer le fichier de cette manière : <em>nom_fichier-DATEDUJOUR.php.back</em>. <br>
Si vous avez accès à BackupBuddy, faites une sauvegarde du thème et le plugin vous permettra de faire un rollback sur ce fichier en particulier.</p>



<h2 id="mise-en-ligne">Mise en ligne</h2>

<p>Pour mettre le site en ligne, voilà quelques conseils et méthodes.</p>



<h3 id="1-nettoyage">1) Nettoyage</h3>

<p>Si vous ne l’avez pas encore fait, pensez à supprimer tout le contenu de test (et celui la uniquement) que vous avez ajouté au site. Cela allègera la BDD et simplifiera l’utilisation au client.</p>



<h3 id="2-archive-des-fichiers">2) Archive des fichiers</h3>

<p>Commencez par faire une archive avec les fichiers contenus dans la partie <em>wp-content</em> du site que vous enverrez sur le nouveau serveur. </p>



<h3 id="3-installation-prod">3) Installation PROD</h3>

<ol>
<li>Faites une installation propre de WP sur le serveur de PROD. </li>
<li>Supprimez le dossier wp-content par l’archive que vous avez récupérez dans le point 2.</li>
</ol>



<h3 id="4-htaccess">4) .htaccess</h3>

<p>Téléchargez le fichier .htaccess et ouvez le dans votre éditeur de texte. Vérifiez bien qu’il n’y a pas d’URL dans celui-ci et s’il y en a une, modifiez la par la nouvelle. <br>
Une fois terminé, transférez le fichier.</p>



<h3 id="5-bdd">5) BDD</h3>

<p>Il existe de nombreuses manières de transférer la BDD d’un site à l’autre, mais voilà celle que je conseille, surtout pour les thèmes achetés en ligne. <br>
Vous avez installé le plugin WP Sync DB, il est temps de l’utiliser. <br>
Sur le <strong>serveur de production</strong>, rendez vous sur Outils &gt; Migrate DB. <br>
Sélectionnez “Pull”. <br>
Sur le serveur de test, rendez vous sur Outils &gt; Migrate DB &gt; Settings, et cochez la case “Accept Pull requests”. Copiez les informations du champ (fig1) et collez les dans le champ le champ <em>Connection info</em>.</p>

<p><strong>fig1</strong> : <br>
<img src="http://goo.gl/SD49Gx" alt="fig1" title=""></p>

<p>Vous pouvez maintenant lancer la migration. Patientez quelques minutes, selon la taille de la BDD. <br>
Toutes les options du thème devraient être présentes également sur le site de prod !</p>



<h3 id="6-configuration-finale">6) Configuration finale</h3>

<p>Vous pouvez maintenant terminer la configuration du site. </p>



<h4 id="cache">Cache</h4>

<p>Activez le plugin de cache en veillant à bien utiliser les options recommandées.</p>



<h4 id="ithemes-security-1">iThemes Security</h4>

<p>Rendez-vous sur la page de configuration de iThemes Security, et configurez ces quelques points si ils sont toujours présents :</p>

<ol>
<li>Your website is not protected against bots looking for known vulnerabilities. Consider turning on 404 protection.</li>
<li><em>Your WordPress Dashboard is available 24/7. Do you really update 24 hours a day? Consider using Away Mode</em>. Si votre client le souhaite, configurez le mode away afin que le site ne soit accessible que sur certaines plages horaire. <strong>Attention</strong>, une fois configurez, le back-office ne sera accessible par <strong>personne</strong> hors des plages horaires autorisées.</li>
<li><em>Your WordPress installation is allowing users without a user agent to post comments. Fix this to reduce comment spam.</em> Si le site accepte les commentaires, configurez cette partie.</li>
</ol>



<h4 id="désactivez-wp-sync-db">Désactivez WP Sync DB</h4>

<p>Désactivez bien WP Sync DB sur les 2 sites, mais ne les supprimez pas, nous en aurons surement besoin plus tard. </p>



<h4 id="iwp">IWP</h4>

<p>Activez le plugin client InfiniteWP. Vous aurez besoin de clés. <br>
Pour la configuration, envoyer un mail à mbasili@marsatwork.fr avec comme sujet [IWP Activation], et dans le corps du mail : <br>
- L’URL de l’administration WP (attention, vous avez normalement du la changer dans les configurations de IThemes Security). <br>
- Le nom d’utilisateur principal (attention, si vous avez bien suivi le guide, il ne doit pas exister d’utilisateur <em>admin</em> sur le site, si c’est le cas,  créez en un nouveau avec les droits d’administration et supprimez le login admin). <br>
- <em>L’activation key</em> que vous obtenez en activant le plugin IWP.</p>



<h4 id="désactivez-les-backups-sur-le-site-de-dev">Désactivez les backups sur le site de DEV !!!</h4>

<p>Pensez à bien desactiver les backup automatique du site de dev pour ne pas encombrer le serveur.</p>



<h2 id="maintenance-du-code">Maintenance du code</h2>

<p>Quelque soit la mise à jour que vous effectuez, il faut s’assurer de les faire sur le site de développement. Sauf cas de force majeure, il ne faut <strong>jamais</strong> les faire directement sur le site de production.</p>

<p>Les quelques étapes pour remettre à jour ce dernier :</p>

<ol>
<li><strong>Assurez vous que les 2 sites sont sauvegardés !!!</strong></li>
<li>Téléchargez le dossier wp-content du site de prod ou demandez le au chef de projet et envoyez le sur le site de dev.</li>
<li>Activez WP Sync DB et faites une synchronisation du site de prod vers le site de dev. Vérifiez bien 2 ou 3 fois que vous le faites bien dans ce sens.</li>
<li>Lorsque vous modifiez un fichier, pensez à en faire la sauvegarde et à noter quelque part que ce fichier est à transférer sur le site de prod une fois la maintenance terminée.</li>
</ol>

<p><strong>Attention, pour que le plugin fonctionne correctement, les 2 sites doivent avoir la même version de WP d’installée.</strong></p>

<p>Lorsque vous avez terminé et que la recette a été faite, si vous n’avez pas modifié la BDD, transférez les fichiers sur le serveur de prod après avoir effectué une backup du site de prod (de toutes les parties que vous avez modifié, theme, plugin…). Si vous avez modifié la base de données, effectuez une synchronisation (encore une fois, vérifiez bien 2 ou 3 fois si c’est le bon sens).</p>