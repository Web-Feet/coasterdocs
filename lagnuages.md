# Lanugages

## Different Content For Different Lagnuages

Coaster has support for different language content. First of all you will need to add an additonal row for your new language in the database table "languages".

Once this is done you will be able to start editing the content in the back end for your new language. Just go to an existing page and put in the content.

## Language Switcher

### Template Modification

After you have added the addtional lanuages to the database you will need to add a language switcher to your template. Here is some exmaple code for creating a drop-down selector.

```
{!! Form::open() !!}
{!! Form::select('lang', [1 => 'English', 2 => 'French'], \CoasterCms\Models\Language::current()) !!}
{!! Form::submit() !!}
{!! Form::close() !!}
```

### Middleware

The final part is to create some middleware to make the language change. Here is an example which includes a redirect to the new page url.

app/Http/Middleware/LanguageSwitch.php
```
namespace App\Http\Middleware;

use CoasterCms\Models\Language;
use PageBuilder;

class LanguageSwitch
{
    public function handle($r, $n) {
        if ($l = $r->input('lang')) {
            $pageId = PageBuilder::pageId();
            Language::set($l);
            return redirect(PageBuilder::pageUrl($pageId));
        }
        return $n($r);
    }
}
```

Then either add this middleware to the web middleware group so it runs the language switch check on each request.

app/Http/Kernel.php
```
protected $middlewareGroups = [
    'web' => [
        ...,
        \App\Http\Middleware\LanguageSwitch::class,
    ],

];
```

Or you just want to do the switch on a specific route you will need to specify the route in your routes file and add the middleware to it, ie.

`Route::any('/my-route', ['middleware' => 'lang', 'uses' => '\CoasterCms\Http\Controllers\CmsController@generatePage']);`

app/Http/Kernel.php
```
protected $routeMiddleware = [
    ...,
    'lang' => \App\Http\Middleware\LanguageSwitch::class
];
```
