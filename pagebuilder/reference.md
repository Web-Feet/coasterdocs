# PageBuilder Reference

- [block](#block)
- blockData
- blockJson
- blockPosts
- breadcrumb
- category
- categoryFilter
- categoryFilters
- categoryLink
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

Usage:

`PageBuilder::block($blockName, $options)` or `PageBuilder::block_[type]($blockName, $options)`

$blockName - is the block name

$options - will depend on the [block types](../blocks/reference.md) display function as well as the additonal options below

| Key                 | Type          | Default             |
| ------------------- | ------------- | ------------------- |
| 'page_id'           | int           | current page ID     |
| 'version'           | int           | current version     |
| 'force_query'       | boolean       | null                |
| 'raw'               | boolean       | null                |

[Review options] (../theme/review.md) can also be set on the block functions.

## Block Data

Usage:

`PageBuilder::blockData($blockName, $options)`

$blockName - is the block name

$options - will depend on the [block types](../blocks/reference.md) data function as well as the standard options above

## Block Json Data

Usage:

`PageBuilder::blockJson($blockName, $options)`

$blockName - is the block name

$options - will depend on the [block types](../blocks/reference.md) toJson function as well as the standard options above


| Key                 | Type          | Default             |
| ------------------- | ------------- | ------------------- |
| 'returnAll'         | boolean       | null                |


