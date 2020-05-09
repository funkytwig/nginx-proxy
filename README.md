# nginx-proxy
Nginx proxy for virtual hosts with lets-encrips.  To use this put the folowing Envirment varables on the web servace (i.e. apachie).

e.g.

  wordpress:
    depends_on:
      - db_uls
    image: wordpress:latest
    container_name: ${WP_CONTAINER}      
    hostname: ${WP_CONTAINER}
    restart: always
    volumes:
      - ./html:/var/www/html
      - ./php.ini:/usr/local/etc/php/conf.d/php.ini
    expose:
      - 80
    restart: always
    environment:
      VIRTUAL_HOST: ${DOMAINS}
      LETSENCRYPT_HOST: ${DOMAINS}
      LETSENCRYPT_EMAIL: ${EMAIL}
      WORDPRESS_DB_HOST: db_uls:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: ${DB_WP_PASSWORD}
