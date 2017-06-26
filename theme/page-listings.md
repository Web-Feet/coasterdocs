# Page Listings / Categories

## Display Method

Return and format a subpage list using the category templates:

`{!! PageBuilder::category($options) !!}`

$options - array of options
 - page_id - (int, default: current page id)
 - view - (string, default: default)
 - type - can be set to 'pages' or 'categories', categories being pages with sub pages (string, default: all)
 - per_page - number of pages to display per page (int, default: 20 [0 or less than 20 pages = no pagination])
 - limit - max pages to return (int, default: 0 [0 = no limit])
 - content - can pass text through to view (string, default: null) 
 - render - if false will return page models (bool, default: true)
 - renderIfEmpty - if false and no pages in category will return null (bool, default: true)
 - canonicals - if pages have multiple urls will use canonical regardless of current path (default: ture)
 - fromPageIds - only render selected pages (array of page ids, default: [])
 - templates - only render pages with specific templates (array of template ids, default: [])
 - groups - only render pages in specific groups (array of group ids, default: [])
 
### Other Methods
 
Return the url for the next or previous page in the same page level : 

`{{ Pagebuilder::categoryLink($direction) }}`

$direction - 'next' goes down the page list, 'prev' goes up

Get Category Pages (with filtered results):

`{!! Pagebuilder::categoryFilter($blockName, $search, $options) !!}`

$blockName - block name

$search - search string or array (ie. between array on dates) and must be array for multiple searches

$options - same as category but with some extra filtering options
- 'match' - 'in' will return all pages where the search term is in the block, '=' is exact match (string, default: '=')
- operand - result operand on multplie search matches (string, default: AND)
- multiFilter - if true will treat each element in the search array as a seprate search query (bool, default: false)
 
## Template Files

- /categories/[category_view]/pages_wrap.blade.php (main template wrapper)  
- /categories/[category_view]/page.blade.php (template for each subpage)

[category_view] is the template set

## Template Varaibles

$category_id (int - page id of the category being displayed)

$total (int - total number of subpages)

### Wrapper file only (pages_wrap):

$pages (string - returns the formatted pages)

$pagination or $links (string - returns the pagination links)

$content (string - returns the content option value / formatted search text)

$search_query (string - returns search query if used in a search)

### Page file only (page):

$page (object - PageDetails)

- $page->id (int - page id)
- $page->name (string - page name)
- $page->url (string - page full url)
- $page->fullName (string - full page name including category path)
- $page->urlSegment (string - page url segment)
- $page->page (object - page model)
- $page->pageLang (object - page lang model)

$is_first (bool - check if page is first in category)

$is_last (bool - check if page is last in category)

$count (int - gets page position in category)

