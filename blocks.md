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

```// Vanilla PHP
<?php PageBuilder::block('block_name') ?>

// Blade (escaped)
{{ PageBuilder::block('block_name') }}

// Blade (unescaped)
{!! PageBuilder::block('block_name') !!}```

This will instantiate an unspecified block within the theme builder. Once logged into the dashboard, select the block type, and whether you want it to appear within pages, site-wide content, or both.

###String blocks

###Text blocks

The text block is used for larger amounts of text that do not require the WYSIWYG editor. Additional formatting can be added manually through the admin.

###Date blocks

The date block allows the end-user to select a date from an interactive calendar. This is useful for making changes to the date on an article, or event.

###Link blocks

Link blocks are primarily used to store URLs, this is useful for managing social media links and "read more" buttons.

##Gallery

The gallery block is great for showing off work to your audience.

##Images

##Videos
