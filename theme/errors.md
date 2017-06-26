# Error Pages

You can have custom error 404 and 500 pages for any Coaster CMS theme.

The error templates are under /errors.

## 404 Error

Whenever a user accesses a page that does not exist, this template will be returned. The `$error` variable will return a short description of the error in question. The layout of this page can be changed as you wish and will work much the same as a normal template.

All the default PageBuilder functions can be used, a dummy 404 page is just loaded instead of a real CMS one.

One thing to note is if you want to use the breadcrumb function on this page you use the '404-name' option to set a name ie.

`{!! PageBuilder::breadcrumb(['404-name' => '404 Page']) !!}`

## 500 Error

The exception is passed through as `$e` to the view as well as the `$error` variable which just contains the message. This page curretly ignores the debug level, if you wish to hide the errors you will need to use an if statement in this template.

If an exception is thrown even when rendering this template the default Laravel error will be shown.

## Example 404

```
{!! PageBuilder::section('head') !!}

<div class="container">

<div class="row">
    <div class="col-sm-12">
        {!! PageBuilder::img('404.jpg') !!}
    </div>
</div>

<div class="row">
    <div class="col-sm-12">
        <p class="errorpage_1">oops, {!! $error !!} ...</p>
        <p class="errorpage_2">Error: 404</p>
        <p>
        We couldn't find the page you requested on our servers. <br />
        We're really sorry about that. <br />
        It's our fault, not yours. We'll work hard to get this page back online as soon as possible.
        </p>
    </div>
</div>

</div>

{!! PageBuilder::section('footer') !!}
```
