# Block Templates

The block function will render CMS content depending on the blocks type, the current page and any options passed through:

`PageBuilder::block('block_name', $options = [])`

## Block Types

Blocks can have different types, the most standard block is a simple string. Any new block you add will get picked up by the [Block Review](#review.md) system and you can set the type as well as any other details before they're saved.

Once they are saved you can start putting your editable content in through the admin.

## Block Page Data

If block has content for the current page that will be used, if not then the site-wide content will be checked, if that still fails it will just use a null value.

For a string block the text entered into the admin will simply be saved as a string. For other more complicated blocks like  the image block it gets stored as an object beacuse it has multiple parts, an images source field and an image title field.

Coaster has around 20 different block types currently.

## Block Views

For any block that saves just string data the PageBuilder block function will simply return it. The block libraries "display" function manages what is return for each block type.

However for blocks which return arrays or object data, like images, the "display" function requires an additonal template to be created. You can either create a default template for that block type, or a name specific one. If both exists the name specifc one will be used.

The files should be created at the following location in your theme:

`blocks/[block_type]/default.php`
`blocks/[block_type]/[block_name].php`

Then in these templates the block data will be passed through to the `$data` vairiable. For example with the image block you can then use the source or file in the blocks template file.

```
<img src="{!! $data->file !!}" title="{!! $image->title !!}" alt="{!! $data->title !!}" />
```

These rendered block templates are then passed back to the PageBuilder block function as a string.

For details on the varaibles an objects avaliable in these templates you can check the [Block Reference](../blocks/type.md) page. 

As of 5.4 all blocks can make use of these template views, this adds consistency to the block behaviour and also greatly enhances the flexibility of displaying certain block types such as string blocks.


## Block Data

There is also a blockData function, it will retrieve the data before it gets put through the block's display function should you need it. With some blocks there are options to fetch different data, for the select block it's possible fetch all the drop down items with the "returnAll" option. 

`Pagebuilder::blockData('block_name', $options = [])`

A blockJson function is also availaible which returns the data in a json format. 

`Pagebuilder::blockJson('block_name')`

This will return the data in the format:

`{block_name : {'data' : $data, 'block' : $blockData}}`

# Custom Block Types 

Custom block types can be added fairly easily.

Coaster will look for custom Block classes in the projects `app/Blocks/` folder. These should extend the base block class `CoasterCms\Libraries\Blocks\AbstractBlock`.

The admin view for the block should go in `resources/views/coaster/blocks/[lower case block name]/main.php`.
