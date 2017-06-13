# Page Templates / Sections

Every page in Coaster uses a template which is set in the admin, the options will depend one the avaliable templates in the current. This section will explain how to create those templates.

Coaster makes use of the blade templating engine from Laravel 5. For every template file you created should use the .blade.php extension. This will enable all of the blade templating features [here](https://laravel.com/docs/5.4/blade). If you wish to use pure .php files or have another templating language installed with laravel you can use that instead.

## Page Templates

First open the `templates` folder in your theme and create a new template file, for example `home.blade.php`.

Next, you will need to decide on the layout of your page template, will it inherit sections from a past template (commonly a header and footer), or will it have a completely new layout? Other things to take into account when creating a new template are what blocks are required and how they are to be composed.

### Example

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

## Section

Sections are good for reusing large chunks of HTML. Sections may be called from a page template or even other templates such as menus or even breadcrumbs.

These template files should be placed in the `sections` folder.

For example `PageBuilder::section('footer')` will load the `sections/footer.blade.php`.

You can also pass custom view data through `PageBuilder::section('footer', ['withSocial' => true])`

### Example

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
