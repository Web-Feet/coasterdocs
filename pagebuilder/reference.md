# PageBuilder Reference

- [block](#block)
- [blockData](#blockData)
- [blockJson](#blockJson)
- [blogPosts](#blogPosts)
- [breadcrumb](#breadcrumb)
- [category](#category)
- [categoryFilter](#categoryFilter)
- [categoryFilters](#categoryFilters)
- [categoryLink](#category-link)
- css
- external
- filter
- filters
- getData
- img
- js
- menu
- pageFullName
- pageId
- pageLiveVersionId
- pageName
- pageTemplateId
- pageUrl
- pageUrlSegment
- pageVersion
- parentPageId
- search
- section
- setCustomBlockData
- setData
- sitemap
- templatePath
- themePath


## Block

Returns rendered block content as a string.

Usage:

`PageBuilder::block($blockName, $options)` or `PageBuilder::block_[type]($blockName, $options)`

$blockName - is the block name

$options - will depend on the [block types](../blocks/reference.md) "display" function as well as the additonal options below

| Key                 | Type          | Default             |
| ------------------- | ------------- | ------------------- |
| 'page_id'           | int           | current page ID     |
| 'version'           | int           | current version     |
| 'force_query'       | boolean       | null                |
| 'raw'               | boolean       | null                |

[Review options](../theme/review.md) can also be set on the block functions.

## Block Data

Returns block content, can be of any type depending on the block.

Usage:

`PageBuilder::blockData($blockName, $options)`

$blockName - is the block name

$options - will depend on the [block types](../blocks/reference.md) "data" function as well as the standard options above

## Block Json Data

Returns block data as json with the structure: `{blockName : {'data' : $data, 'block' : $block}}`

Usage:

`PageBuilder::blockJson($blockName, $options)`

$blockName - is the block name

$options - will depend on the [block types](../blocks/reference.md) "toJson" function as well as the standard options above

| Key                 | Type          | Default             |
| ------------------- | ------------- | ------------------- |
| 'returnAll'         | boolean       | null                |

## Blog Posts

Gets the latest posts from a WordPress blog database as a PDOStatement object.

Usage:

`PageBuilder::blogPosts($getPosts, $where)`

$getPosts - number of posts to fetch

$where - alter the raw SQL where query

## Breadcrumb

Returns rendered breadcrumb as string, more details [here](../theme/breacrumb.md).

Usage:

`PageBuilder::breadcrumb($options)`

$options - can set the view used or the current page name

| Key                | Type          | Default             |
| -------------------| ------------- | ------------------- |
| 'view'             | string        | 'default'           |
| '404-name'         | string        | ''                  |

## Category

Returns rendered category pages, more details [here](../theme/category.md).

Usage:

`PageBuilder::category($options)`

$options - uses the default [category options](../theme/category.md#options) plus

| Key                | Type          | Default             |
| -------------------| ------------- | ------------------- |
| 'page_id'          | string        | null                |
| 'sitemap'          | boolean       | null                |

## Category Filter

Returns rendered category pages with content matching a search value.

Usage:

`PageBuilder::categoryFilter($blockName, $search, $options)`

$blockName - is the block name

$search - is the search string or array (variable type would depend on the block type being search)

$options - uses the default [category options](../theme/category.md#options) and [fitler options](#filter)

## Category Filters

Same as above but with the `multiFilter` option set to true by default 

Usage:

`PageBuilder::categoryFilters($blockName, $searches, $options)`

## Category Link

Returns link for the next or previous page at the current category level 

Usage:

`PageBuilder::categoryLink($direction)`

$direction - 'prev' or 'next' (default)


