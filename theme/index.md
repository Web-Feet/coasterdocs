# Creating a Theme

- [New Themes](#new-themes)
- [Existing Themes](#existing-themes)

## New Themes

In order to create a Coaster CMS theme you will need two folders named the same.
One folder goes in resource views and the other goes in public themes, for example a them named "mytheme":

```
/resources/views/mytheme
/public/themes/mytheme
```

The required structure of the theme views can be found on the [Theme Structure](http://coastercms.org/docs/latest/theme/structure) page.
Once the structure is created, you can then create your theme templates, blocks, menus and sections using the instructions found in these documentation pages.

The structure of the public themes folder is largely up to you.
However if you want to use the PageBuilder `img`, `css` and `js` functions you will need to use the same folder names.

Finally to add the new theme to the database you will need to login to the admin and go to the Themes section and click install on your new theme.

## Existing Themes

Alternatively you can install and edit an existing theme. These come uploaded by default if you install the coastercms project.
To manually add a theme just upload the zip file to the /resources/themes/ folder in the root of your project or through the admin.

The default themes are:
- Coaster2017
- Coaster2016
- Default (minimal theme)

The Coaster themes have good implementaion examples of most of the stuff in the documentation and are worth taking a look at.

