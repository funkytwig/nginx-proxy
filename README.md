# nginx-proxy
Nginx proxy for virtual hosts with lets-encrips.  To use this put the folowing Envirment varables on the web servace (i.e. apachie).

e.g.

wordpress:<br>
    depends_on:<br>
      - db_uls<br>    
    image: wordpress:latest<br>
    container_name: ${WP_CONTAINER}      <br>
    hostname: ${WP_CONTAINER}<br>
    restart: always<br>
    volumes:<br>
      - ./html:/var/www/html<br>
      - ./php.ini:/usr/local/etc/php/conf.d/php.ini<br>
    expose:<br>
      - 80<br>
    restart: always<br>
    environment:<br>
      VIRTUAL_HOST: ${DOMAINS}<br>
      LETSENCRYPT_HOST: ${DOMAINS}<br>
      LETSENCRYPT_EMAIL: ${EMAIL}<br>
      WORDPRESS_DB_HOST: db_uls:3306<br>
      WORDPRESS_DB_USER: wordpress<br>
      WORDPRESS_DB_PASSWORD: ${DB_WP_PASSWORD}<br>
