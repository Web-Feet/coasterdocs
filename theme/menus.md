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
- ...

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


