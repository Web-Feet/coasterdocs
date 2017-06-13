# Block Templates

The block function will render CMS content depending on the current page and the blocks type as well as any options passed to it:

`PageBuilder::block('[blockName]', $options = [])`

If there is has been any block content entered into the current page from the admin that will be used, if not then the site-wide content will be checked, if that still fails it will just use a null value.

## Block Types

Blocks can have different types, the most standard block is a simple string. Any new block you add will get picked up by the [Block Review](#review.md) system and you can set the type as well as any other details before they're saved.

Once they are saved you can start putting your editable content in through the admin.

## Block Data

For a string block the text entered into the admin will simply be saved as a string. For other more complicated blocks like  the image block it gets stored as an object beacuse it has multiple parts, an images source field and an image title field.

Coaster has around 20 different block types currently for a full list can be found [here](../blocks/type.md)

## Block View

For any block that saves just string data the `PageBuilder::block` function will simply return it by default.

However for blocks which return objects data like images an additonal tempalte needs to be created.


All blocks can have multiple views in the themes/[theme_name]/blocks/[block_type] folder - this adds consistency to the block behaviour and also greatly enhances the flexibility of displaying certain block types such as string blocks. In addition, all block libraries "display" function will return strings and an additional PageBuilder function "blockData" will retrieve the data before it gets put through the block's display function should you need it.

{{ Pagebuilder::block('block_name', $options) }}

# Custom Block Types 

Custom block types can be added fairly easily.

Coaster will look for custom Block classes in the projects `app/Blocks/` folder. These should extend the base block class `CoasterCms\Libraries\Blocks\AbstractBlock`.

The admin view for the block should go in `resources/views/coaster/blocks/[lower case block name]/main.php`.
