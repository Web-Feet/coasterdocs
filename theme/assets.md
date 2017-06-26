# Using Public Assets
- [CSS](#css)
- [JavaScript](#javascript)
- [Images](#images)

## CSS

The css method returns the URL of the specified CSS stylesheet. The .css extension is not required, as Coaster will append this automatically. An example of this can be seen below:

`<link rel="stylesheet" href="{{ PageBuilder::css('mystyles') }}">`

Remember to encapsulate the method within the `<link>` tag, or else the URL will display as plain text.

### Parameters

| Parameter | Type    | Example             |
| --------- | ------- | ------------------- |
| `$name`   | string  | 'mystyles'          |

## JavaScript

The js method returns the URL of the specified JavaScript file. As with CSS files, the .js extension is not required. An example of this can be found below:

`<script async defer src="{{ PageBuilder::js('myscript')) }}">`

### Parameters

| Parameter | Type    | Example             |
| --------- | ------- | ------------------- |
| `$name`   | string  | 'myscript'          |

## Images

The img method returns the URL of the image complete with the surrounding `<img>` tag using the image blocks display function. An example can be found below:

`{!! PageBuilder::img('myimage.jpg') !!}`

In this instance, you'll notice the file extension is required.

### Parameters

Unlike the CSS and JS methods highlighted above, the img method accepts the `$options` parameter. The available options are the same as the image block plus one extra below.

If you want to use full paths to your images you can set the option 'full_path' to true.

| Parameter | Type    | Example                 |
| --------- | ------- | ----------------------- |
| `$name`   | string  | 'image'                 |
| `$options`| array   | ['class' => 'myclass']  |
