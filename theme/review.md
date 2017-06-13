# Review Block Changes

- [Overview](#overview)
- [Table Colour Key](#table-colour-key)
- [Block Data](#block-data)
  - [From Csv](#from-csv)
  - [From Theme Files](#from-theme-files)
  - [Fallback Guesses](#fallback-guesses)
- [Block Templates](#block-templates)
- [Ignoring Block](#ignoring-blocks)
- [Setting Return Values](#setting-return-values)
- [Saving Changes](#saving-changes)

# Overview

Coaster has a special "ThemeBuilder" class that will go through your theme looking for any block changes that may need to be saved to the database.

When the ThemeBuilder runs it uses only blank block and page data to retain consitency on each run, because of this anything relying on spefic page data such as ids, may not be autmatically picked up.  

The results of the ThemeBuilder can be reviewed in the admin of your site under "Themes", just select your theme (mytheme) and click 'Review Block Changes'. You should then see a table with all the blocks in your theme. If you click on the info icon you can get more detailed info for each block.

## Table Colour Key

There is a basic colour key on the table to make any changes found stand out: green for new blocks, yellow for updated blocks, and red for deleted blocks.
There is also a blue which means there was not sufficient data to determine all the blocks templates.

## Block Data

The ThemeBuilder will load data for a block in a specific order. It will work down the following list for each column in the block data table and stop when the information is found.

1. From an Import CSV File
2. Your theme files
3. Any existing database data if the block already exists
4. Finally a guess will be made

### From CSV

This file is used for importing and exporting block data for a theme, however it can be used to fix any block data or even add templates.
More information can be found [here](review-csv.md)

### From Theme Files

You may set any data by passing it through the block function:

```
PageBuilder::block('myblock', [
  'label' => 'My Block!!!',
  'category_id' => 5,
  'type' => 'richtext',
  'order' => 10,
  'note' => 'Info about the block ...',
  'search_weight' => 2,
  'active' => 1,
]);
```

In addition you may set the type by adding a suffix to the block function (this has priority over the method above):

`PageBuilder::block_richtext('myblock')`

### Fallback Guesses

If all other methods fail the ThemeBuilder will make a "guess" or use a default value. Here's a list of what happens for each block data column:

- Label: Capitilized version of the block name.
- Category: Array based match
- Type: Array based match
- Order: Will try to find a number between the order values of blocks above and below
- Note: Defaults to null
- Search Weight: Defaults to 1
- Active: Default to 1

#### Category Guess

If a repeater block has no set category it will get put in it's own block category. A repeater block named "banner" for example would go into the "Banners" category, if this category doesn't exist it will be created.

Most of the time a other blocks will be placed in the main category, however if it does happen to match any of the strings below it will be place into the respective category.

```
$defaultCategorySearchStrings = [
    'header' => ['head'],
    'main' => ['main', 'default'],
    'banner' => ['banner', 'carousel'],
    'footer' => ['foot'],
    'seo' => ['seo']
];
```
For example "Footer HTML" will be matched by "foot" and thus gets put into the "Footer" Category.

#### Type Guess

For repeater blocks there is also an inital check in the `blocks/repeater` folder for any matching template names, then it will use the array below to try and match the block name. If that still fails the block will default to a string.

```
$typesArr = [
    'video' => ['vid'],
    'text' => ['text', 'desc', 'keywords', 'intro', 'address', 'html', 'lead'],
    'richtext' => ['richtext', 'content'],
    'image' => ['image', 'img', 'banner', 'logo'],
    'link' => ['link', 'url'],
    'datetime' => ['date', 'datetime'],
    'string' => ['link_text', 'caption', 'title'],
    'form' => ['form', 'contact'],
    'select' => ['select'],
    'selectmultiple' => ['selectmultiple', 'multipleselect'],
    'selectpage' => ['selectpage'],
    'selectpages' => ['selectpages']
];
```

## Block Templates

For each block, there is infomation on what templates the block is currently on the left.
Then on the right the changes are listed if it's found in a new template or removed from an existing one.

The information for repeater templates and changes are also listed ie. if a block has child blocks or is part of a rpeater block.

### Updating Templates

Template changes will only save if the "Update Templates" column has been checked. This means you can just update block data on specific blocks.

The last two columns on the right determine if the block is a site-wide block. Site-wide blocks can be shown in either the site-wide content section, in pages or both.

The main difference with a site-wide block is how the data is stored in the database. Rather than having a row for each template a blocks in in the theme_template_blocks table, a single row will be created in the themes_blocks table. There is a column for excluding certain templates in this table.

Note: Blocks not on any page templates will not have this option, ie. blocks only used inside repeaters

## Ignoring Blocks

If you wish for any blocks not to be picked up you can set the reviewIgnore option.

`PageBuilder::block('myblock', ['reviewIgnore' => true]);`

## Setting Return Values

If you wish for any blocks to return a specific value when being run by the ThemeBuilder you can use the reviewReturnValue option.
It may be used in conjunction with the ignore method above.

`PageBuilder::block('myblock', ['reviewReturnValue' => true]);`

## Saving Changes

After you are happy with the block types and labels (for the admin fields), click Update at the bottom of the table and your templates and blocks will be saved to Coaster.

You can review/change update the block types from here at any time.
