# Coaster CMS Documentation
- [Overview](#overview)
- [Server Setup](#server-setup)
  - [Server Requirements](#server-requirements)
  - [Linux / Mac](#unix)
  - [Windows](#windows)
  - [Webserver Config](#webserver-config)
  - [Using Docker](#using-docker)
- [Install](#install)
  - [Download via Composer (recommended)](#download-via-composer)
  - [Download via Zip](#download-via-zip)
  - [Completing the Install](#completing-the-install)
  - [Install State](#install-state)

## Overview

The developer documentation will guide you through the process of installing Coaster CMS on the hosting platform of your choice. Use the links to the right to find specific detailed documentation on an area of interest.

## Server Setup

### Server Requirements

- Web Server (Apache/Nginx recommended)
- PHP (>5.6)
- MySQL (>5.5) or MariaDB Database
- Composer (required for updates)

Also the following PHP extensions are required:

- OpenSSL PHP Extension
- PDO PHP Extension
- MySQLi PHP Extension (If using MySQL)
- Mbstring PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension
- GD2 PHP Extension
- Zip PHP Extension

### Server Setup

#### Unix

To install Apache, PHP, MySQL on Linux or macOS we recommend using package management software such as homebrew. There are lots of tutorials out there to help with this process.

### Windows

To install on Windows we recommend using an all in one solution such as WAMP/XAMPP, or preferably Docker or Laravel Homestead. If you do decide to use WAMP, you may have to make some changes to PHP's ini file to prevent SSL errors with cURL.

Download the cacert.pem certificate file from http://curl.haxx.se/ca/cacert.pem and save it to C:\xampp\php\extras\ssl\cacert.pem or your server's equivalent. Find the correct php.ini file for your PHP version and append the following line:

`curl.cainfo = "C:\xampp\php\extras\ssl\cacert.pem"`

Ensure this line is not duplicated anywhere else within the file, and remove any semi-colons present at the beginning of the line. Finally, restart WAMP or XAMPP to reload changes made to the php.ini file.

To access the database, we recommend using a program such as HeidiSQL. From here you can create new databases, edit tables, truncate tables and change the structure of tables. Go ahead and create a new table called "coastercms".

## Webserver Config

Here some some example webserver config files for setting up Coaster with Nginx or Apache.

#### Example Nginx Config

```
server {
    listen 127.0.0.1:80;

    root /var/www/yoursite/public;
    index index.html index.php;

    server_name www.yoursite.com;
    client_max_body_size 20M;
    rewrite ^/index.php/(.*) /$1  permanent;

    location / {
        index index.html index.php;
        try_files $uri $uri/ /index.php$is_args$args;
    }

    location ~ /\. {
        deny all;
    }

    location ~ \.php$ {
        try_files $uri =404;
        expires off;
        fastcgi_pass unix:/run/php/php7.1-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

}
```

#### Example Apache Config

```
<VirtualHost *:80>
  ServerName www.yoursite.com
  DocumentRoot "/var/www/yoursite/public"
  <Directory "/var/www/yoursite/public">
    AllowOverride all
  </Directory>
</VirtualHost>
```

### Using Docker

If you don't want to install MySQL Server onto your host machine, you can now put it in it's own container. This is made possible using Docker. Go ahead and install Docker. If unfamiliar with Docker it can be a bit intimidating at first, but what we aim to do is quite simple. 

Run the following command from a Powershell or Command Prompt window:

`docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=secret -d mysql:5.7`

In the above command, we are creating a new MySQL container with the appropriate name "mysql" and forwarding the port 3306 from the container. This allows us to access MySQL from the host machine. The final part of the command, "mysql:5.7" will download the latest MySQL 5.7 image from Docker. This is done automatically and won't require any intervention. The image measures about 400mb, so depending on your connection it could take awhile to download. We are then setting the root MySQL password as "secret", this can of course be changed to anything you like. The final -d parameter daemonises the container to run in the background.

## Install

### Download via Composer

First make sure you have composer installed, it's relatively simple, but not entirely obvious for those who haven’t done it before. A simple guide can be found at https://getcomposer.org/download/ or if you are on Windows here is a good post on [installing PHP 7 with Composer on Windows 10](https://www.webtechgadgetry.com/install-php-7-windows/).

Once composer is setup just run the following command:

`composer create-project web-feet/coastercms [project-name]`

This will download the latest version of coastercms and any packages it requires (it may take a while depending on your internet connection).

#### Adding Coaster CMS to an existing laravel project

The steps are as follows:

1. Add "web-feet/coasterframework": "5.4.*" to the composer.json file and run composer update
2. Go to the root directory of your project. 
3. Add the folders /coaster and /uploads to your public folder.
4. Run the updateAssets script
`php vendor/web-feet/coasterframework/updateAssets`
5. Add the service providers CoasterCms\CmsServiceProvider::class and CoasterCms\Providers\CoasterRoutesProvider::class, to your config/app.php file. The routes service provider has some catch all routes so it recommended to put that one last.

### Download via Zip

Just download and extract this [file](https://github.com/Web-Feet/coastercms/releases/download/v5.4.0/full-dist.zip). The zip contains v5.4.9 of the coaster framework.

### Completing the Install

Once you have downloaded all the files you will need to open the site in a web browser.

If you do not have a webserver like Nginx or Apache installed that's not a problem. Thankfully, Laravel has a built-in web server for running projects. Type the following command from within the directory you installed Coaster:

`php artisan serve`

Now that the web server is running hopefully you’ll be greeted with a Coaster CMS install page in your web browser. 

There will be a quick permissions check first.

Next at the database section enter your database details. If using MySQL the default host is normally 127.0.0.1, root as the user, then your database password as the password, and you database name ie. coastercms. Also feel free to choose your own prefix or leave it blank.

Then setup the admin account, enter a username, preferably an email address, and a password.

Finally you can select the theme, for new developers or designers it probably best to install the default Coaster2017 theme with the page data. This will give you a good example of how the themes work.

### Install State

If you every need to go back a setup in the install process or re-run the whole thing you can.

The install state is held in the storage file `/storage/app/coaster/install.txt`

States:

- Missing or blank file will set you back to the beginning of the install process.
- coaster.install.database (database connection configuration)
- coaster.install.databaseMigrate (just about to run the database table setup)
- coaster.install.admin (add admin user step)
- coaster.install.theme (theme select / install step)
- complete-welcome (installed with new welcome message on first login)
- complete (installed)

#### Other storage files

There are two other files in the same folder, which are both used when running the updateAssets script.

 - `/storage/app/coaster/assets.json` 
 
 This stores what version of the assets have been downloaded (ie. jQuery, filemanager).
 If you want to redownload these asset files again you can just delete this file.
 
 - `/storage/app/coaster/updates.json`
 
This stores the version of database migrations applied and if updates outside the vendor folder have been applied.
