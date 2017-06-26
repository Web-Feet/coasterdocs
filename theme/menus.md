# Menus

Menus are an integral part of any website and Coaster's flexibility allows you to have as many as you want.

The default template files are in `/menus/default` and you can add other folders in the same place as the default folder for additional layouts, for example `/menu/footer`.

## Display Method

To return the constructed menu with all menu items added from within the admin (excluding hidden pages):

`{!! Pagebuilder::menu($menuName, $options)  !!}`

- $menuName is the name of the menu that is stored in the database

- $options is an array of options
  - view - use a custom template set (exmaple: 'view' => 'sidebar', default: 'default')
  - canonicals - if pages have multiple urls will use canonical regardless of path used (default: ture)
  - addtional options will be passed as view Data to all the menu templeates

## Template Files

Menus are composed of two required files with extra optional files if you wish the menu to have further dropdown functionality.

- /menus/[menu_view]/menu.blade.php (main menu template wrapper) 
- /menus/[menu_view]/item.blade.php   (basic item template) 

Optional (for dropdowns):
- /menus/[menu_view]/submenu_1.blade.php (item template with a sub menu)   
- /menus/[menu_view]/submenu_2.blade.php (2nd sublevel menu … and so on)  

Additional submenu files can be created each with an incrementing integer, for example submenu_4.blade.php.

[menu_view] is the template set

## Template Variables

$item (object - MenuItemDetails)

- $item->name (string - item/page name)
- $item->url (string - item/page full url)
- $item->active (bool - if item/page is currently active)
- $item->parentPageId (int - page parent in menu)
- $item->page (object - page model)
- $item->item (object - menu item model)

$level (int - current submenu depth, starts at 1 , then in first submenu 2, ...)

$further_levels (int - based on the item sublevel setting in the admin, then -1 for each level down)

$items (string - returns formatted items for submenus)

$is_first (bool - check if item is first in menu)

$is_last (bool - check if item is last in menu)

$count (int - get item position in menu)

$total (int - total number of items in the menu)  

## Example

An example of a basic menu.blade.php file can be seen below:

```
<nav class="navbar navbar-inverse ">
    <div class="container">

        <div class="navbar-header">
            <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar">
                <span class="sr-only">Toggle navigation</span>
                <span class="hamburger">
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </span>
                <span class="navig">Menu</span> </button>
        </div>

        <div id="navbar" class="collapse navbar-collapse">
            <ul class="nav navbar-nav">
                {!! $items !!}
            </ul>
        </div>
        <!--/.nav-collapse -->
    </div>
</nav>
```

Much of the above is the HTML forming the layout of the menu, this will of course differ depending on how your theme has been designed. The integral part of any menu in Coaster revolves around {!! $items !!}, as this is where the links are rendered.

An example of an item.blade.php can be found below:

```
<?php $class = ($item->active) ? 'active' : ''?>
<li class="{!! $class !!}">{!! HTML::link($item->url, $item->name) !!}</li>
```

The above code renders an li element for each link in a menu. It will also append an active class to the link of the current page a user is on.

Many top level menus now have some sort of dropdown functionality, if your site requires such a feature the code you can have a look at the template example below.

An example of an submenu_1.blade.php can be found below:

```
<?php $class = ($item->active) ? 'active' : ''?>
<li class="dropdown {!! $class !!}">
    <a href="{!! $item->url !!}" class="dropdown-toggle" data-toggle="dropdown">
        {!! $item->name !!} <b class="caret"></b>
    </a>
    <ul class="dropdown-menu">
        {!! $items !!}
    </ul>
</li>
```

The HTML above is an example layout of how a submenu may look, this will of course differ from theme to theme as with the menu above. The submenu file uses the same principles as the main menu file in that the {!! $items !!} code handles the menu linking logic. As was said originally as many submenu files can be made as you require, providing your HTML supports it.
