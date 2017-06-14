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

`PageBuilder::block($name, $options)`

$name is the block name

$options


| Key                 | Type          | Default             |
| ------------------- | ------------- | ------------------- |
| 'page_id'           | int           | current page ID     |
| 'version'           | int           | current version     |
| 'force_query'       | boolean       | null                |
| 'raw'               | boolean       | null                |
| 'ignoreOnImport'    | boolean       | null                |
| 'reviewReturnValue' | mixed         | null                |

