1. create image:
    - source:
    - mig:debian11.1 from ./image/debian
    - mig:mariadb-10.5 from ./image/database/mariadb
    - mig:appbase-1.1 from ./image/appbase
    - mig:nginx-1.1 from ./image/nginx
2. setup docker network from ./_file/network
3. config docker-compose for database
    - setup file /config/conf.d/50-server.cnf: server-id, bind-address
    - setup file /config/root/.my.cnf: root-password
4. config docker-compose for app/web
    - setup file /config/php74/conf.d/10-phpini-overrides.ini: post_max_size, upload_max_filesize
    - setup /config/supervisor/services: create file .conf (optional)
5. config docker-compose for nginx
    - setup /config/sites-enabled: create file .conf
    - setup /config/conf.d: create file .conf (optional)
6. up docker compose ordered by: database, app, webserver
7. additional config:
    - master-slave configuration
    - deploy project from git
    - etc