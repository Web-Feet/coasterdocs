# Page Templates / Sections

Every page in Coaster uses a template which is set in the admin, the options will depend one the avaliable page templates in the current theme. This section will explain how to create those page templates.

Coaster makes use of the blade templating engine from Laravel 5. For every template file you created should use the .blade.php extension. This will enable all of the blade templating features [here](https://laravel.com/docs/5.4/blade). If you wish to use pure .php files or have another templating language installed with laravel you can use that instead.

## Blade Templating

Instead of using the conventional PHP opening tags, blade uses double curly braces as a simple way to print out content:

`{{ 'some text' }}` is the same as `<?php echo e('some text'); ?>`

If you don't want to escape the special characters in the string you can use the version with the exclamation marks. This one is quite usefull a lot of the function used in building the theme return HTML which you don't want escaped:

`{!! '<p>some text</p>' !!}` is the same as `<?php echo '<p>some text</p>'; ?>`

However, if you so desire, both classic PHP and blade syntax can be used within any file ending with the .blade.php extension.

## Page Templates

To create a page template, first open the `templates` folder in your theme and create a new template file, for example `home.blade.php`.

Next, you will need to decide on the layout of your page template, will it inherit sections from a past template (commonly a header and footer), or will it have a completely new layout? Other things to take into account when creating a new template are what blocks are required and how they are to be composed.

Now the main class which you will be using in the template files is `PageBuilder`. This is basically a library of functions to return page data and other rendered template files. Some of the most common functions are `section` and `block`. The `block` function is a way of returning some rendered page content and is explained further in the [Block Templates](block-templates.md) section.

### Example Page Template

```
{!! PageBuilder::section('head') !!}

{!! PageBuilder::block('banners') !!}

<div class="container">
    <div class="row">
        <div class="col-sm-12">
            <h2>{!! PageBuilder::block('title') !!}</h2>
            {!! PageBuilder::block('content') !!}
        </div>
    </div>
    <!-- /.row -->
</div>
<!-- /.container -->

{!! PageBuilder::section('footer') !!}
```

## Sections

Sections are good for reusing large chunks of HTML as in the example above with the head and footer. Sections may be called from a page template or even other templates such as menus or even breadcrumbs.

These template files should be placed in the `sections` folder.

For example `PageBuilder::section('footer')` will load the file `sections/footer.blade.php`.

You can also pass custom view data through `PageBuilder::section('footer', ['withSocial' => true])`

### Example Section Template

```
<footer>

  @if ($withSocial)
    <div>
      <a href="https://www.linkedin.com/" target="_blank">LinkedIn</a>
      <a href="https://twitter.com/" target="_blank">Twitter</a>
      <a href="https://www.facebook.com/" target="_blank">Facebook</a>
    </div>
  @endif

  <p><a href="/terms">Terms & Conditions</a> | <a href="/sitemap">Sitemap</a></p>
  <p>© 2017 All rights reserved ...</p>
  
</footer>
```
