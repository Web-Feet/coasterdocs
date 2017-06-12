# Review Block Changes

- [Colour Key](#colour-key)
- [Block Data](#block-data)
  - [From Csv](#from-csv)
  - [From Theme Files](#from-theme-files)
  - [Fallback Guesses](#fallback-guesses)
- [Block Templates](#block-templates)
- [Saving Changes](#saving-changes)

Coaster has a special "ThemeBuilder" class that will go through your theme looking for any block changes that may need to be saved to the database.
These can be reviewed in the admin of your site under "Themes", just select your theme (mytheme) and click 'Review Block Changes'.

You should then see a table with all the blocks in your theme.

## Colour Key

A basic colour key make the changes found clearer, green for new blocks, yellow for updated blocks, and red for deleted blocks.
There is also a blue which means there was not sufficient data to determine all the blocks templates.

## Block Data

The ThemeBuilder will load data for a block in a specific order. It will work down the following list for each column, stopped when the information is found for that column.

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

Most of the time a block will be placed in the main category, however if it does happen to match any of the strings below it will be place into the respective category.

```
$defaultCategorySearchStrings = [
    'header' => ['head'],
    'main' => ['main', 'default'],
    'banner' => ['banner', 'carousel'],
    'footer' => ['foot'],
    'seo' => ['seo']
];
```
For example "Footer HTML" will be matched by "foot" and thus get put into the "Footer" Category.

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




## Saving Changes

After you are happy with the block types and labels (for the admin fields), click Update at the bottom of the table and your templates and blocks will be saved to Coaster.

You can review/change update the block types from here at any time.
