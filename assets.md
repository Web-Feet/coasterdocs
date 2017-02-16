#Using Public Assets
- [CSS](#css)
  - [Parameters](#parameters)
- [JavaScript](#javascript)
  - [Parameters](#parameters)
- [Images](#images)
  - [Parameters](#parameters)

##CSS

The css method returns the URL of the specified CSS stylesheet. The .css extension is not required, as Coaster will append this automatically. An example of this can be seen below:

`<link rel="stylesheet" href=""{{ PageBuilder::css('mystyles') }}>`

###Parameters

| Parameter | Type    | Example             |
| --------- | ------- | ------------------- |
| `$name`   | string  | 'mystyles'             |

##JavaScript

The js method returns the URL of the specified JavaScript file. As with CSS files, the .js extension is not required. An example of this can be found below:

`<script async defer src="{{ PageBuilder::js('myscript')) }}">`

###Parameters

| Parameter | Type    | Example             |
| --------- | ------- | ------------------- |
| `$name`   | string  | 'myscript'          |

##Images

The img method returns 

###Parameters

| Parameter | Type    | Example             |
| --------- | ------- | ------------------- |
| `$name`   | string  | 'image'             |
| `$options`| array   | ['length' => '200'] |
