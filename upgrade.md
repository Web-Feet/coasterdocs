# Upgrading
 - [Using Composer](#composer)
 - [Using the Zip](#zip)
 - [Major Version Changes](#major)
   - [5.3 to 5.4](#5.3)

## Using Composer

Upgrading is very simple via composer, just go to the command line in the root of your project and type:

`composer update`

## Using the Zip

If you downloaded the zip file instead you will need to download a new copy and overwrite your existing files. It would be a good idea to export the theme you are using from the admin if you have made any changes.

## Major Version Upgrades

If there has been a major versin update, ie. from 5.3 to 5.4 you will need to run this command first:

`composer require web-feet/coasterframework:5.4.* laravel/framework:5.4.*`

There may be breaking changes in these versions if you have any custom code or themes.

## 5.3 to 5.4

The routes have been seperated out into a new service provider: `App\Providers\RouteServiceProvider::class` 

You will need to add this to your `config/app.php` file, usually best at the end as it included some catch all routes.

Also in this update a big change was `PageBuilder::block()` only returns a string now. If you where using any data functions they will now need to be changed to `PageBuilder::blockData()`

