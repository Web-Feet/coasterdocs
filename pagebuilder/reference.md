# PageBuilder Reference

- [block](#block)
- [blockData](#block-data)
- [blockJson](#block-json)
- [blogPosts](#blog-posts)
- [breadcrumb](#breadcrumb)
- [category](#category)
- [categoryFilter](#category-filter)
- [categoryFilters](#category-filters)
- [categoryLink](#category-link)
- [css](#css)
- [external](#external)
- [filter](#filter)
- [filters](#filters)
- [getData](#get-data)
- [img](#img)
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

| Key                 | Type          | Default             | Note                                                         |
| ------------------- | ------------- | ------------------- |--------------------------------------------------------------|
| 'page_id'           | int           | current page ID     |                                                              |
| 'version'           | int           | current version     |                                                              |
| 'force_query'       | boolean       | null                |                                                              |
| 'raw'               | boolean       | null                | Returns block content before it reaches the display function |

[Review options](../theme/review.md) can also be set on the block functions.

## Block Data

Returns block content, can be of any type depending on the block.

Usage:

`PageBuilder::blockData($blockName, $options)`

$blockName - is the block name

$options - will depend on the [block types](../blocks/reference.md) "data" function as well as the block options above

## Block Json Data

Returns block data as json with the structure: `{blockName : {'data' : $data, 'block' : $block}}`

Usage:

`PageBuilder::blockJson($blockName, $options)`

$blockName - is the block name

$options - will depend on the [block types](../blocks/reference.md) "toJson" function as well as the block options above and one other

| Key                 | Type          | Default             | Note                                                    |
| ------------------- | ------------- | ------------------- |---------------------------------------------------------|
| 'returnAll'         | boolean       | null                | Function will return a json array of all blocks on page |

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

$options - 

| Key                | Type          | Default             | Note                                                     |
| -------------------| ------------- | ------------------- |----------------------------------------------------------|
| 'view'             | string        | 'default'           |                                                          |
| '404-name'         | string        | ''                  | Can rename the current page used in the breadcrumb       |

## Category

Returns rendered category pages, more details [here](../theme/category.md).

Usage:

`PageBuilder::category($options)`

$options - uses the default [category options](../theme/category.md#options) plus

| Key                | Type          | Default             | Note                                                         |
| -------------------| ------------- | ------------------- |--------------------------------------------------------------|
| 'page_id'          | string        | current page ID     |                                                              |
| 'sitemap'          | boolean       | null                | If true will remove pages that are excluded form the sitemap |

## Category Filter

Returns rendered category pages with content matching a search value.

Usage:

`PageBuilder::categoryFilter($blockName, $search, $options)`

$blockName - is the block name

$search - is the search string or array (variable type would depend on the block type being search)

$options - uses the default [category options](../theme/category.md#options) and [fitler options](#filter)

## Category Filters

Same as above but with the `multiFilter` option set to true by default.

Usage:

`PageBuilder::categoryFilters($blockName, $searches, $options)`

## Category Link

Returns link for the next or previous page at the current category level .

Usage:

`PageBuilder::categoryLink($direction)`

$direction - 'prev' or 'next' (default)

## CSS

Helper function to return relative link for css files in current theme.

Basically converts $fileName to `/themes/[theme]/css/$fileName.css`

Usage:

`PageBuilder::css($fileName)`

$fileName - file name for the css file

## External

Returns a rendered external view.

Usage:

`PageBuilder::external($section)`

$section - name of the external template file

## Filter

Returns rendered pages with content matching a search value.

Usage:

`PageBuilder::filter($blockName, $search, $options)`

$blockName - is the block name

$search - is the search string or array (variable type would depend on the block type being search)

$options - uses the default [category options](../theme/category.md#options)  as well as the follwoing filter options

| Key                | Type          | Default             | Note                                                |
| -------------------| ------------- | ------------------- |-----------------------------------------------------|
| 'match'            | string        | '='                 | depends on the block typeas to possible options     |
| 'operand'          | string        | 'AND'               | 'AND' or 'OR'                                       |
| 'multiFilter'      | boolean       | false               | denotes if one search query or multiple             |

## Filters

Same as above but with the `multiFilter` option set to true by default.

Usage:

`PageBuilder::filters($blockName, $searches, $options)`

## Get Data

Returns PageBuilder object variables.

Usage:

`PageBuilder::getData($value)`

$value - PageBuilder object variable to return 

## Img

Helper function to return relative image files in current theme.

Basically converts $fileName to `/themes/[theme]/img/$fileName` and passes it to the image block display function.

Usage:

`PageBuilder::img($fileName, $options)`

$fileName - file name for the css file

$options - uses the [image block options](../blocks/reference.md#image) plus

| Key                | Type          | Default             | Note                                     |
| -------------------| ------------- | ------------------- |------------------------------------------|
| 'full_path'        | boolean       | null                | If true the $fileName wont be converted  |
