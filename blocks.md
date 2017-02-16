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

The text block is used for larger amounts of text that do not require the WYSIWYG editor. Additional formatting can be added manually through the admin.

###Date blocks

The date block allows the end-user to select a date from an interactive calendar. This is useful for time sensitive content such as blog posts and news articles.

###Link blocks

Link blocks are primarily used for URLs, this is useful for managing social media links and "read more" buttons.

##Gallery

The gallery block is great for showing off your work to visitors. This block is slightly more 

##Images

##Videos
