#Blocks
- [Strings, dates and links](#strings_dates_links)
  - [Text blocks](#text)
  - [Date block](#date)
  - [Link block](#link)
- [Gallery](#gallery)
  - [Options](#galleryoptions)
- [Image block](#image)
  - [Options](#imageoptions)
- [Videos](#videos)
  - [Options](#videooptions)

##Strings, dates and links

All string, date, link, and image blocks use the same template syntax. An example of this can be found below:

```php
// Vanilla PHP
<?php PageBuilder::block('block_name') ?>

// Blade (escaped)
{{ PageBuilder::block('block_name') }}

// Blade (unescaped)
{!! PageBuilder::block('block_name') !!}
```

Any file with the blade extension can use the blade syntax, or the PHP syntax. For blocks that use rely on HTML formatting we recommend using the unescaped syntax.

This will instantiate an unspecified block within the theme builder. Once logged into the dashboard, select the block type, and whether you want it to appear within pages, site-wide content, or both.

###String blocks

The string block is used for smaller amounts of text - perfect for titles and bylines.

###Text blocks

The text block is used for larger amounts of text that do not require the WYSIWYG editor. Additional HTML formatting can be added manually through the admin.

###Richtext blocks

The rich text block will render as a WYSIWYG editor in the admin. This is often used for larger portions of content where a lot of formatting may be required. If using blade, be sure to unescape the string e.g. `{!! PageBuilder::block('my_block') !!}` to ensure the HTML is rendered correctly on the front-end.

###Date blocks

The date block allows the end-user to select a date from an interactive calendar. This is useful for time sensitive content such as blog posts and news articles.

###Link blocks

Link blocks are primarily used for URLs, this is useful for managing links to social media profiles and "read more" buttons.

###Options

Additional attributes can be appended to the link block through the options paramater.

##Gallery

The gallery block is used to manage a collection of images.

##Images

The image block is used to display images on the front-end. Image blocks integrate with the file manager to allow users to select images from their library.

###Options

Occassionally you may find you want to add some additional attributes to an image such as a class. Attributes can be passed through using the options parameter:

`PageBuilder::block('image', ['attribute_name' => 'attribute_value'])`

As you can see the attribute name is followed by the attribute value, for example `'class' => 'my_class'` would add the 'my_class' class to the image.

##Videos
