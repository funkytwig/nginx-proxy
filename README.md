# nginx-proxy
Nginx proxy for virtual hosts with lets-encrips.  To use this put the folowing Envirment varables on the web servace (i.e. apachie).

e.g.

wordpress:<br>
&nbsp;&nbsp;&nbsp;&nbsp;depends_on:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- db_uls<br>    
&nbsp;&nbsp;&nbsp;&nbsp;image: wordpress:latest<br>
&nbsp;&nbsp;&nbsp;&nbsp;container_name: ${WP_CONTAINER}<br>
&nbsp;&nbsp;&nbsp;&nbsp;hostname: ${WP_CONTAINER}<br>
&nbsp;&nbsp;&nbsp;&nbsp;restart: always<br>
&nbsp;&nbsp;&nbsp;&nbsp;volumes:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ./html:/var/www/html<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ./php.ini:/usr/local/etc/php/conf.d/php.ini<br>
&nbsp;&nbsp;&nbsp;&nbsp;expose:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 80<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;restart: always<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;environment:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;VIRTUAL_HOST: ${DOMAINS}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LETSENCRYPT_HOST: ${DOMAINS}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LETSENCRYPT_EMAIL: ${EMAIL}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WORDPRESS_DB_HOST: db_uls:3306<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WORDPRESS_DB_USER: wordpress<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WORDPRESS_DB_PASSWORD: ${DB_WP_PASSWORD}<br>
