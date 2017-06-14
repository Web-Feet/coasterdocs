# Theme Structure

- [Creating A Theme](#creating-a-theme)
- [Template Files](#template-files)
- [Public Assests](#public-assets)
- [Existing Themes](#existing-themes)

## Creating A Theme

In order to create a Coaster CMS theme you will need to create two folders with the name of your new theme. One folder goes into resource views which will contain the template files and the other goes in public themes which will contains your themes assets. 

For example you would need to create the following folders for a theme named "mytheme":

```
/resources/views/mytheme
/public/themes/mytheme
```

Then to add the new theme to the database you will need to login to the admin and go to the Themes section and click install on your new theme.

## Template Files

For any Coaster theme the template files should be located under `resources/views/themes/[yourtheme]`

The general folder structure is like this:

- blocks
- breadcrumbs
- categories
- emails
- errors
- externals
- feeds
- menus
- sections
- templates

All the folders aren't requied, for example if your theme doesn't use breadcrumbs you can leave that folder out. Also feel free to add an assets folder and use gulp / laravel-elixir / grunt to combine/minify js/css into the public themes folder if you wish to do so.

## Public Assets

The public assets for your theme should be located under `public/themes/[yourtheme]`

The structure of this folder is largely up to you, though there are helper functions in the PageBuilder class that use the css, img and js folders so it would be easier to use them for the assets.

As an example the folder structure for the default theme is like this:

- css
- fonts
- img
- js

## Existing Themes

Alternatively you can install and edit an existing theme. These come uploaded by default if you install the coastercms project. To import a theme upload the zip file to the /resources/themes/ folder in the root of your project or use the upload in the admin, then you should be able to install it.

The default themes in the are:
- Coaster2017
- Coaster2016
- Default (minimal theme)

The "default" theme has all the top level folders necessary to use Coaster CMS but is very minimal in terms of templates and actual HTML. The Coaster themes have lots of different theme building functions implemented and contain serveral different templates with a lot more HTML. If you want to get started on your own theme quickly you can copy one these themes and start editing it, just remember to copy both the template files and public assets.
