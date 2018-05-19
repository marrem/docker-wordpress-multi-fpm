= Easily deploy multiple Wordpress sites
== Wordpress alpine-fpm containers behind nginx as reverse proxy

=== Quick start

 * Clone repo
 * Change into repo directory
 * Run: docker stack deploy -c wordpress-multi-fpm.yml <stack_name>


Since fpm only handles php execution, the nginx container has to have access to the same file system as
the wordpress container. This is accomplished by mounting the siteN_html into the nginx container as
/siteN and into the wordpress container as /var/www/html

Wordpress containers normally mount an anonymous volume at /var/www/html. This is done in order to upgrade
to a new version of wp. You change the image tag and restart the container. So it is unfortunate that 
nginx needs to access the volume as well. Now you will have to remove the volume before up- (or down-) grade
the wordpress container. Of course you will want to keep your site content (uploads, plugins, themes, etc), so
I mount this as a seperate volume as siteN/wp-content into the nginx container, and as /var/www/html/wp-content
into the wordpress containers







