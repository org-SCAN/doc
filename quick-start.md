# 🏁 Quick Start

{% hint style="info" %}
**Good to know:** SCAN works entirely with Docker! No need to worry about different software versions, Docker handles everything.
{% endhint %}

Install SCAN in only few steps :

1. [Clone the github project](quick-start.md#clone-the-github-project)
2. [Install Docker](quick-start.md#install-docker)
3. [Install SCAN requirements with docker Compose](quick-start.md#docker-compose)
4. [Add the required configuration files required](quick-start.md#required-configuration-files)
5. Run few command lines

## Clone the github project

You may clone the github project. The required files are located in the `src` directory.

{% tabs %}
{% tab title="HTTPS" %}
```bash
git clone https://github.com/TC-netw4ppl/website.git
```
{% endtab %}

{% tab title="SSH" %}
```bash
git clone git@github.com:TC-netw4ppl/doc.git
```
{% endtab %}

{% tab title="Github CLI" %}
```bash
gh repo clone TC-netw4ppl/doc
```
{% endtab %}
{% endtabs %}

## Install Docker

The best way to install our software is with Docker:

{% hint style="info" %}
[https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)
{% endhint %}

You can use [https://www.portainer.io](https://www.portainer.io) to manage your different docker containers easily.

## Docker compose

Here is an example of a docker-compose used :

```docker
version: '3.7'

services:
 sql:
  image: mysql:5.7
  container_name : sql
  restart : unless-stopped
  environment:
   MYSQL_DATABASE: ${DATABASE_NAME}
   MYSQL_ROOT_PASSWORD: ${DATABASE_PASSWORD}
   MYSQL_PASSWORD: ${DATABASE_PASSWORD}
   MYSQL_USER: ${DATABASE_USERNAME}
  volumes:
   - ${LOCAL_DB_STORAGE_PATH}:/var/lib/mysql
  ports:
   - '3306:3306'

 app:
  image: netw4ppl/website:latest
  container_name: app
  restart: unless-stopped
  volumes :
   - ${LOCAL_WEBSITE_PATH}:/var/www/html/
   - ${LOCAL_SSL_PATH}:/var/imported/ssl/
   - ${LOCAL_APACHE_CONFIGURATION_FILE}/etc/apache2/sites-available/000-default.conf
  ports:
   - '2080:80'
   - '2443:443'
```

{% hint style="danger" %}
**Warning :** Please, make sure to correctly fill the following variables
{% endhint %}

| Variable                                                | Value                                                                                                                                                                                                                                               |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <pre><code>DATABASE_NAME</code></pre>                   | The name of the database                                                                                                                                                                                                                            |
| <pre><code>DATABASE_PASSWORD</code></pre>               | The master password of the database                                                                                                                                                                                                                 |
| <pre><code>DATABASE_USERNAME</code></pre>               | The username used to connect to the database                                                                                                                                                                                                        |
| <pre><code>LOCAL_DB_STORAGE_PATH</code></pre>           | A folder in which the contents of your database will be stored                                                                                                                                                                                      |
| <pre><code>LOCAL_WEBSITE_PATH</code></pre>              | <p>The path where the website code is stored. <br><span data-gb-custom-inline data-tag="emoji" data-code="26a0">⚠</span> <mark style="color:orange;">If you clone the project from github, make sure the path points to <code>src</code></mark></p> |
| <pre><code>LOCAL_SSL_PATH</code></pre>                  | <p>The path to your SSL certificate. Can be ignored if you don't want to use https.</p><p><mark style="color:orange;">Recommended <mark style="color:yellow;"></mark> to secure access to the API.</mark></p>                                       |
| <pre><code>LOCAL_APACHE_CONFIGURATION_FILE</code></pre> | The path to an apache configuration file, an example of which is given [here](quick-start.md#apache-configuration-file).                                                                                                                            |

## Required configuration

### Apache Configuration file

{% hint style="info" %}
You can delete the lines concerning the ssl certificate if you do not use https
{% endhint %}

```apacheconf
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

### A Deepl Account

SCAN automatically translates the created fields and lists. To use the automatic translation feature, you need to create an account on DeepL and fill in your Token API. The free version offers 500,000 characters per month, which is more than enough for the application's needs.

{% hint style="info" %}
You can find the information needed to create an account here: [https://www.deepl.com/en/pro-api?cta=header-pro-api/](https://www.deepl.com/en/pro-api?cta=header-pro-api/)
{% endhint %}

### .env file

This `.env` file ** **<mark style="color:orange;">**MUST be completed**</mark>** ** and placed at the root of `src`&#x20;

```
APP_NAME=SCAN
APP_ENV=local
APP_KEY=
APP_DEBUG=false
APP_URL=localhost

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

MAIL_MAILER=smtp
MAIL_HOST=mailhog
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS=null
MAIL_FROM_NAME="${APP_NAME}"

DEFAULT_EMAIL="default user email"
DEFAULT_PASSWORD="default user password"
DEFAULT_TEAM="default user team"

TRANSLATION_API_URL="https://api-free.deepl.com/v2/translate"
TRANSLATION_API_TOKEN="YOUR API TOKEN"
```

{% hint style="danger" %}
**Warning :** Please, make sure to correctly fill the following variables
{% endhint %}

| Variable                                      | Value                                                                                                                              |
| --------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| <pre><code>APP_KEY</code></pre>               | Must be leaft blank                                                                                                                |
| <pre><code>APP_DEBUG</code></pre>             | Set `false` in case of production                                                                                                  |
| <pre><code>DB_HOST</code></pre>               | You must put the docker sql container name. If you used the [docker configuration above](quick-start.md#docker-compose), put `sql` |
| <pre><code>DB_DATABASE</code></pre>           | You must put the same name as the one used during the docker configuration.                                                        |
| <pre><code>DB_USERNAME</code></pre>           | You must put the same username as the one used during the docker configuration.                                                    |
| <pre><code>DB_PASSWORD</code></pre>           | You must put the same password as the one used during the docker configuration.                                                    |
| <pre><code>DEFAULT_EMAIL</code></pre>         | Set the default user's email. This information will be used to create the first account on the application.                        |
| <pre><code>DEFAULT_PASSWORD</code></pre>      | Set the default user's password. This information will be used to create the first account on the application.                     |
| <pre><code>DEFAULT_TEAM</code></pre>          | Set the default team name. This information will be used to create the first team. You can put_`DEFAULT ICRC TEAM`_ for example.   |
| <pre><code>TRANSLATION_API_URL</code></pre>   | The translation API URL. If you use the free version of deepL, the preset URL is the right one.                                    |
| <pre><code>TRANSLATION_API_TOKEN</code></pre> | Your DeepL API Token                                                                                                               |

## Finalize the installation

Only a few seconds left and you'll be there. Run these commands in your docker to finish!

To execute in your docker container run :

{% hint style="info" %}
If you used the [docker configuration example above](quick-start.md#docker-compose), the `<APPLICATION_CONTAINER_NAME>` should be `app`
{% endhint %}

```bash
docker exec -it <APPLICATION_CONTAINER_NAME> /bin/bash
```

{% hint style="warning" %}
**Make sure you are in the docker** before executing the commands.
{% endhint %}

```bash
npm update
cd /var/www/html
composer update
php artisan cache:clear
composer dump-autoload
chmod -R 777 storage/
chmod 777 app/Models
chmod 777 -R database/migrations
chmod -R 777 bootstrap
php artisan key:generate
php artisan migrate:refresh --seed
```

## Real last step

Visit `http://localhost:<PORT>` and you're in!

{% hint style="info" %}
`<PORT>` must be the one filled in for the docker's app container (2080 by default)
{% endhint %}

Congratulations, it's all over, you've earned a little beer.

<figure><img src="https://images.unsplash.com/photo-1436076863939-06870fe779c2?crop=entropy&#x26;cs=tinysrgb&#x26;fm=jpg&#x26;ixid=MnwxOTcwMjR8MHwxfHNlYXJjaHw4fHxjb25ncmF0dWxhdGlvbnxlbnwwfHx8fDE2NjY3NzYxNDA&#x26;ixlib=rb-4.0.3&#x26;q=80" alt=""><figcaption><p>Take a break</p></figcaption></figure>
