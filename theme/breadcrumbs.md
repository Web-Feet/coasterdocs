# Breadcrumbs

Template files for breadcrumbs are located in the /breadcrumbs folder in theme.

## Display Method

Return and format the page path using the templates:

`{!! PageBuilder::breadcrumb($options)) !!}`

$options -
 - view - specify which template set to use (string, default: default)

## Template Locations

/breadcrumbs/[view_name]/link_element.blade.php (used for all crumbs)

/breadcrumbs/[view_name]/separator.blade.php (separator html used between all crumbs)

/breadcrumbs/[view_name]/wrap.blade.php (html to wrap around the rendered crumbs)

### Deprecated File

/breadcrumbs/[view_name]/active_element.blade.php (last item in breadcrumb trail ie. current page)

If it exists it will be used instead of link_element for the active crumb.

## Template Variables

For the wrap template:

$crumbs - (string - contiaing HTML for rendered crumbs)

For the link_element / active_element template:

$crumb - (object - BreadCrumb)
 - $crumb->url (string - crumb full url)
 - $crumb->name (string - crumb name)
 - $crumb->active (bool - is crumb active)
 - $crumb->pageLang (object - the pageLang model)

 
