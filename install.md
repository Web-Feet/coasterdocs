# Installing Coaster Cms
- [Server Requirements](#server)
  - [MySQL](#mysql)
  - [PHP](#php)
  - [Using Docker (optional)](#docker)
- [Install](#install)
  - [Install via Composer (recommended)](#composer)
  - [Install via Zip](#zip)
  - [Completing the Install](#completing)
- [Upgrading](#upgrading)
- [Accessing the Database](#database)

## Server Requirements

### MySQL

Version 5.7 of is MySQL recommend, though it will still run on version 5.5+.

### PHP

PHP version 5.6.4+ is required as well as the following extensions:

- OpenSSL PHP Extension
- PDO PHP Extension
- MySQLi PHP Extension (If using MySQL)
- Mbstring PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension
- GD2 PHP Extension
- Zip PHP Extension

### Using Docker

Instead of installing MySQL Server onto your host machine, it's sometimes nice to install this within its own container. This is made possible using Docker. Go ahead and install Docker. If unfamiliar with Docker it can be a bit intimidating at first, but what we aim to do is quite simple. 

Run the following command from a Powershell or Command Prompt window:

`docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=secret -d mysql:5.7`

In the above command, we are creating a new MySQL container with the appropriate name "mysql" and forwarding the port 3306 from the container. This allows us to access MySQL from the host machine. The final part of the command, "mysql:5.7" will download the latest MySQL 5.7 image from Docker. This is done automatically and won't require any intervention. The image measures about 400mb, so depending on your connection it could take awhile to download. We are then setting the root MySQL password as "secret", this can of course be changed to anything you like. The final -d parameter daemonises the container to run in the background.

## Install

### Via Composer (recommended)

First make sure you have composer installed, it's relatively simple, but not entirely obvious for those who haven’t done it before. A simple guide can be found at https://getcomposer.org/download/ or if you are on Windows here is a good post on [installing PHP 7 with Composer on Windows 10](https://www.webtechgadgetry.com/install-php-7-windows/).

Once composer is setup just run the following command:

`composer create-project web-feet/coastercms`

This will download the latest version of coastercms and any packages it requires (it may take a while depending on your internet connection).

### Via Zip

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

## Upgrading

Upgrading is very simple via composer, just go to the command line in the root of your project and type:

`composer update`

If there has been a major versin update, ie. from 5.3 to 5.4 you will need to run this command first:

`composer require web-feet/coasterframework:5.4.* laravel/framework:5.4.*`

If you downloaded the zip file instead you will need to download a new copy and overwrite your existing files. It would be a good idea to export the theme you are using from the admin if you have made any changes.

## Accessing the Database

To access the database, we recommend using a program such as HeidiSQL. From here you can create new databases, edit tables, truncate tables and change the structure of tables. Go ahead and create a new table called “coastercms”.
