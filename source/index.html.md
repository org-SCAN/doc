---
title: API Reference

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation pour N4P
---

# Introduction

Hello, voici la doc dev de N4P. Dans un premier temps on revient sur les outils utiles pour le projet.
Ensuite on décrit la base du projet et enfin vous pouvez retrouver une doc de l'API.

# Outils
lorem ipsum dolor sit ...

## Serveur

## Using docker

### Using portainer on your machine

You can go to [https://portainer.netw4ppl.tech](https://portainer.netw4ppl.tech) to manage the docker server but also your machine locally, provided you register your machine.

To do so: 

- Connect to the portainer space with the credentials present in the keepass
- Go to *Environments*.
  - Add an environment
  - Choose *Edge Agent* and enter a name, choose the group *Local Machine* and leave the other parameters as default
  - Click on *Add environment*.

<!-- <%= add_edge "images/portainer_add_edge.png" %> -->

Depending on your configuration, choose the right deployment script. For mac and wsl, it is possible to choose Linux and docker standalone.

- Copy the script and run it on your machine.
- Finish by clicking on *Update environment*.

You should find your machine in *Home*.

<!-- <%= portainer_home "images/portainer_home.png" %> -->

### How to deploy the project?

- Clone the github project
- With portainer, create a new *stack*. 
- Choose *custom template* and choose the *n4p-website* template
- Adapt the compose according to the deployment environment

**IMPORTANT** :

1. It is necessary to add the environment variables which define the identifiers of the database.
2. Correctly create and associate the volumes:
   - `/var/N4P/sql-volume` : stores the data of the database
   - `/var/www/website/` : path to the website source code (if cloned from github, be careful to point to the `src` folder)
   - `/srv/www/web_apps/website/ssl`: not necessary if ssl is not required
   - `/etc/apache2/sites-available/docker_config.conf` points to an apache configuration file (see below)

Then deploy the stack.

#### Apache configuration file

Here is an appache `docker_config.conf` configuration file example:

```apache
      # conf/vhost.conf
      <VirtualHost *:80>
          DocumentRoot /var/www/html/public

          <Directory "/var/www/html">
              AllowOverride all
              Require all granted
          </Directory>

          ErrorLog ${APACHE_LOG_DIR}/error.log
          CustomLog ${APACHE_LOG_DIR}/access.log combined
      </VirtualHost>

      # Delete the lines below if you don't use ssl 
      <IfModule mod_ssl.c>
      <VirtualHost *:443>
          DocumentRoot /var/www/html/public

          <Directory "/var/www/html">
              AllowOverride all
              Require all granted
          </Directory>

          SSLCertificateFile /var/imported/ssl/fullchain.pem
          SSLCertificateKeyFile /var/imported/ssl/privkey.pem
          SSLEngine on
      </VirtualHost>
      </IfModule>
```

### Finalize the configuration:

Make sure the `.env.example` file is present and run this from the application container.

```bash
      cp .env.example .env
      npm update
      cd /var/www/html
      composer update
      php artisan cache:clear
      composer dump-autoload
      php artisan key:generate
      chmod -R 777 storage/
      php artisan migrate:refresh --seed
```

#### `.env.example` file


Here is a .env.example file. Make sure you edit the database information (`DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`) properly. It is also important to fill in `DEFAULT_EMAIL`, `DEFAULT_PASSWORD` and `DEFAULT_TEAM`.

Note that during development it is recommended to have `APP_DEBUG=true`. In case of production, `APP_DEBUG` should be `false`.

```
      APP_NAME=Laravel
      APP_ENV=local
      APP_KEY=
      APP_DEBUG=true
      APP_URL=

      LOG_CHANNEL=stack
      LOG_LEVEL=debug

      DB_CONNECTION=mysql
      DB_HOST=sql_container_name
      DB_PORT=3306
      DB_DATABASE='database_name'
      DB_USERNAME=USER
      DB_PASSWORD='PASSWORD'

      BROADCAST_DRIVER=log
      CACHE_DRIVER=file
      QUEUE_CONNECTION=sync
      SESSION_DRIVER=database
      SESSION_LIFETIME=120

      MEMCACHED_HOST=127.0.0.1

      REDIS_HOST=127.0.0.1
      REDIS_PASSWORD=null
      REDIS_PORT=6379

      MAIL_MAILER=smtp
      MAIL_HOST=mailhog
      MAIL_PORT=1025
      MAIL_USERNAME=null
      MAIL_PASSWORD=null
      MAIL_ENCRYPTION=null
      MAIL_FROM_ADDRESS=null
      MAIL_FROM_NAME="${APP_NAME}"

      AWS_ACCESS_KEY_ID=
      AWS_SECRET_ACCESS_KEY=
      AWS_DEFAULT_REGION=us-east-1
      AWS_BUCKET=

      PUSHER_APP_ID=
      PUSHER_APP_KEY=
      PUSHER_APP_SECRET=
      PUSHER_APP_CLUSTER=mt1

      MIX_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
      MIX_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"

      DEFAULT_EMAIL="default user email"
      DEFAULT_PASSWORD="default user password"
      DEFAULT_TEAM="default user team"
```

# N4P - Documentation

N4P website est développé en Laravel. La doc de Laravel est plutôt bien faite et vous pouvez la retrouver [ici](https://laravel.com/docs/9.x). Pour comprendre le fonctionnement du projet, il est important de se familiariser avec le framework et notamment avec les concepts de MVC (Model, View, Controller) et les [ORM](https://laravel.com/docs/9.x/eloquent).
En complément de Laravel, nous utilisons [Jetstream](https://jetstream.laravel.com/2.x/introduction.html) pour la gestion de l’authentification.


La base de données est en SQL mais Laravel utilise des ORM pour gérer les requêtes. Les requêtes sont donc écrites en PHP et non en SQL. Pour plus d'informations sur les ORM, vous pouvez consulter la doc de Laravel [ici](https://laravel.com/docs/9.x/eloquent).

## La philosophie de Teams

La récente refonte de N4P avec Teams rend le projet plus modulaire mais bien plus complexe. Il est donc important de bien comprendre le fonctionnement du projet pour pouvoir le maintenir.
Pour comprendre comment tout fonctionne, il est intéressant de suivre le chemin de la donnée.

L'idée est la suivante : un administrateur peut créer une équipe et y associer des champs d'un formulaire. Les utilisateurs d'une équipe voient donc le formulaire associé à leur équipe. Ils peuvent remplir le formulaire et le soumettre. On peut ensuite consulter les réponses et les analyser.

Ce court paragraphe permet de comprendre qu'on a besoin de référencer des équipes et de leur associer des champs. Les réponses au formulaire sont stockées dans une table qui associe la réponse à un champ du formulaire. Une autre table contient le détail des champ des formulaires.

## Models


## Controller

## Routes

# API


