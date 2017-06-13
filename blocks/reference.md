# Blocks
- [Syntax](#syntax)
  - [Options](#options)
- [Block types](#block-types)
- [Image block](#image-block)
  - [Parameters](#parameters-2)

## Syntax

All string, date, link, and image blocks use the same template syntax. An example of this can be seen below:

```php
// Vanilla PHP
<?php PageBuilder::block('block_name') ?>

// Blade (escaped)
{{ PageBuilder::block('block_name') }}

// Blade (unescaped)
{!! PageBuilder::block('block_name') !!}
```

Any file with the blade extension can use the blade syntax, or the PHP syntax. For blocks that rely on HTML formatting we recommend using the unescaped syntax.

This will instantiate an unspecified block within the theme builder. Once logged into the dashboard, select the block type, and whether you want it to appear within pages, site-wide content, or both.

### Options

By default, some block types accept the use of attributes through the options parameter, example syntax can be seen below:

`PageBuilder::block('block_name', ['attribute_name' => 'attribute_value'])`

As you can see, the attribute name is followed by the attribute value, for example `'class' => 'my_class'` would add the 'my_class' class to the block.

If you wish to add an options parameter to a block that doesn't support it by default you can create a default view. strings
It is possible to make changes to a block type through the use of [different views](#).

#### Default Options

There are a number of options available to every block, these are:

| Key                 | Type          | Default             |
| ------------------- | ------------- | ------------------- |
| 'page_id'           | int           | current page ID     |
| 'version'           | int           | current version     |
| 'force_query'       | boolean       | null                |
| 'raw'               | boolean       | null                |
| 'ignoreOnImport'    | boolean       | null                |
| 'reviewReturnValue' | mixed         | null                |

## Block types

### String

The string block is used for smaller amounts of text - perfect for titles and bylines.

### Text

The text block is used for larger amounts of text that do not require the WYSIWYG editor. Additional HTML formatting can be added manually through the admin.

### Richtext

The rich text block will render as a WYSIWYG editor in the admin. This is often used for larger portions of content where a lot of formatting may be required. If using blade, be sure to unescape the string e.g. `{!! PageBuilder::block('my_block') !!}` to ensure the HTML is rendered correctly on the front-end.

#### Parameters

| Parameter | Type    | Example             |
| --------- | ------- | ------------------- |
| $name     | string  | 'richtext'          |
| $options  | array   | ['length' => '200'] |

### Date

The date block allows the end-user to select a date from an interactive calendar. This is useful for time sensitive content such as blog posts and news articles.

#### Parameters

| Parameter | Type    | Example                |
| --------- | ------- | ---------------------- |
| $name     | string  | 'date'                 |
| $options  | array   | ['format' => 'F j, Y'] |

### Link

Link blocks are primarily used for URLs, this is useful for managing links to social media profiles and "read more" buttons.

## Image block

The image block is used to display images on the front-end. Image blocks integrate with the file manager to allow users to select images from their library.

### Parameters

| Parameter | Type    | Example                 |
| --------- | ------- | ----------------------- |
| $name     | string  | 'image'                 |
| $options  | array   | ['class' => 'my_class'] |

## Select block

The select block is used to select a value in the admin for display on the frontend, the options of a select block can be defined in Coaster's admin system under "Theme" >> "Manage block slect options".

### Parameters

| Parameter | Type    | Example                 |
| --------- | ------- | ----------------------- |
| $name     | string  | 'image_class'           |
