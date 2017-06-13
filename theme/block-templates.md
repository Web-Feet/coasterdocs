# Block Templates

## The Block Function

The data returned

## Block View

All blocks can have multiple views in the themes/[theme_name]/blocks/[block_type] folder - this adds consistency to the block behaviour and also greatly enhances the flexibility of displaying certain block types such as string blocks. In addition, all block libraries "display" function will return strings and an additional PageBuilder function "blockData" will retrieve the data before it gets put through the block's display function should you need it.

{{ Pagebuilder::block('block_name', $options) }}

# Custom Block Types 

Custom block types can be added fairly easily.

Coaster will look for custom Block classes in the projects app/Blocks/ folder. These should extend the base block class.

The admin view for the block should go in resources/views/coaster/blocks/[lower case block name]/main.php .
