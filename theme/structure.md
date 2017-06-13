# Theme Structure

In this sections we will look at the structure of view and templates within Coaster CMS.

There are 2 locations to be aware of for themes currently:

- [Template Files](#template-files) - resources/views/themes
- [Public Assests](#public-assets) - public/themes

The default theme has all the top level folders necessary to use Coaster CMS. If you want to get started quickly you can copy these folders.

## Template Files

The template files should be located under `resources/views/themes/[yourtheme]`

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
