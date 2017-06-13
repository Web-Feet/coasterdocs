# Block Templates

The block function will render CMS content depending on the blocks type, the current page and any options passed through:

`PageBuilder::block('block_name', $options)`

## Block Types

Blocks can have different types, the most standard type is a "string". Any new block you add will get picked up by the [Block Review](review.md) system and you can set the type as well as any other details before they're saved.

Once they are saved you can start putting your editable content in through the admin.

## Block Page Data

If the current page has content for a particular block that will be used, if not then the site-wide content will be checked, if that still fails it will just use a null value.

In the admin a string block will be show as text input and when saved it will be saved as a string. For other more complicated blocks like an image block it gets stored as an object beacuse it has multiple parts, an images source field and an image title field.

Currently coaster has around 20 different block types. This can make it very easy to edit different types of content.

## Block Views

The block libraries "display" function manages the return value for each block type. For every single block type the return value should always be a string.

Any block that saves just string data the PageBuilder block function will simply return it.

However for blocks have arrays or object data, like images, the "display" function requires an additonal template to be created. You can either create a default template for that block type, or a name specific one. If both exists the name specific one will be used.

The files should be created at the following location in your theme:

`blocks/[block_type]/default.php`
`blocks/[block_type]/[block_name].php`

Then in these templates the block data will be passed through to the `$data` vairiable. For example with the image block you can then use the source or file in the blocks template file.

```
<img src="{!! $data->file !!}" title="{!! $image->title !!}" alt="{!! $data->title !!}" />
```

These rendered block templates are then passed back to the PageBuilder block function as a string. For details on the varaibles an objects avaliable in these templates you can check the [Block Reference](../blocks/type.md) page. 

As of 5.4 all blocks can make use of these template views, this adds consistency to the block behaviour and also greatly enhances the flexibility of displaying certain block types such as string blocks.

## Block Data

There is also a blockData function, it will retrieve the data before it gets put through the block's display function should you need it. With some blocks there are options to fetch different data, for the select block it's possible fetch all the drop down items with the "returnAll" option. 

`Pagebuilder::blockData('block_name', $options)`

A blockJson function is also availaible which returns the data in a json format. 

`Pagebuilder::blockJson('block_name')`

This will return the data in the format:

`{block_name : {'data' : $data, 'block' : $blockData}}`

## Custom Block Types 

Custom block types can be added fairly easily as shown [here](../blocks/custom.md).
