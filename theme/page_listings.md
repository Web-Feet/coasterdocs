# Page Listings / Categories

## Display Method

{!! PageBuilder::category($options) !!}

Will return and format a subpage list using the category templates.

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
 
