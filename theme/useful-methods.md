# Useful Methods

## Get Current Page Id

{{ Pagebuilder::pageId($noOverride) }}

Returns null if 404 page or external.

 ## Get Parent Page Id 

{{ Pagebuilder::parentPageId($noOverride) }}

Returns null if no parent exists.

## Get Current Page Name

{{ Pagebuilder::pageName($pageId, $noOverride) }}

Returns page name for a page_id. If no page_id set, returns current page name.

## Get Current Page Full Name

{{ Pagebuilder::pageName($pageId, $noOverride) }}

Returns page name for a page_id. If no page_id set, returns current page name.

## Get Current Page Url

{{ Pagebuilder::pageUrl($pageId, $noOverride) }}

Returns full url for a page_id. If no page_id set, returns current page url.

## Get Current Page Url

{{ Pagebuilder::pageUrlSegment($pageId, $noOverride) }}

Returns url segment for a page_id. If no page_id set, returns current page url.

## Get Current Template Id

{{ Pagebuilder::pageTemplateId($noOverride) }}

Returns the id of the current template, if no template is set (ie. on a 404 page) will return null

## Get Current Theme Path

{{ Pagebuilder::themePath() }}

Returns the id of the current template, if no template is set (ie. on a 404 page) will return null

## Get Current Template Path

{{ Pagebuilder::templatePath($withThemePath) }}

Returns the id of the current template, if no template is set (ie. on a 404 page) will return null

## Render Current or Custom Template

{{ Pagebuilder::templateRender($customTemplate, $viewData) }}

Returns the id of the current template, if no template is set (ie. on a 404 page) will return null
