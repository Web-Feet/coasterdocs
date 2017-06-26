# Feeds / Sitemap

Any page template can have a corresponding template to be used as a feed. This makes it simple to grab any page data in what ever format is needed.

## Feeds (rss, xml, json, ...)

Any template can have a corresponding feed template which can be rendered just by appending the type: .[type]

For example a page with the url /about can have a feed on the url /about.json or /about.rss
The only exception is the homepage feed which is at /root.[type]

The feed templates are located here, Coaster looks for matching template name first then default:

 - /feed/[type]/[page template].blade.php
 - /feed/[type]/default.blade.php

By default Coaster will only look for rss, xml and json feed templates, to change this you will need to edit the config value:

`coaster.frontend.enabled_feed_extensions`

## Simple Json API Example

To get all block data on every page you can just create this one file:

/feed/json/default.blade.php

```
{!! Pagebuilder::blockJson('', ['returnAll' => true]) !!}
```

blockJson is a handy function that can be used to return all block data on a page.

## Sitemap

To return a rendered view of all webiste pages (can exclude specific pages in the admin):

`{!! Pagebuilder::sitemap($options) !!}`

$options - same as options/variables as category function

Note: you will need to call the category function in the category template file to make this recursive so it goes through subpages as well. Also you will need to have the special sitemap option set so the exclusion works.

### Example

/categories/sitemap/pages.blade.php

```
<li>
    <a href="{{ $page->url }}" title="{{ $page->name }}">{!! $page->name !!}</a>
    {!! PageBuilder::category(['view' => 'sitemap', 'sitemap' => 1]) !!}
</li>

```

## XML Sitemap Example

To create an XML as well as the HTML sitemap you can use the feed functionality.

If you have a sitemap template named 'sitemap', you just need to create the following for an XML one:

/feed/xml/sitemap.blade.php

```
<?php echo '<?xml version="1.0" encoding="UTF-8"?>' ?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    {!! PageBuilder::sitemap(['view' => 'sitemap_xml']) !!}
</urlset>
```

/categories/sitemap_xml/pages_wrap.blade.php

```
{!! $pages !!}
```

/categories/sitemap_xml/pages.blade.php

```
<url>
    <loc>{!! URL::to(PageBuilder::page_url()) !!}</loc>
    <priority>{!! (PageBuilder::page_template()==1)?'1':'0.5' !!}</priority>
</url>
{!! PageBuilder::category(['page_id' => $page->page->id, 'view' => 'sitemap_xml']) !!}
```

Then to access the sitemap make sure you have a page in Coaster with the url sitemap and go to /sitemap.xml
