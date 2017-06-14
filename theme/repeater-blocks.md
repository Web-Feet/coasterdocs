# Repeater Blocks

One very useful block that Coaster has is called a "repeater". With these blocks you can repeat sections of HMTL but with different content. This content can be pulled from multiple blocks of any type. You could use this to easily create banner sliders or team member profiles.

## Block View Templates

The block template locations for the repeater blocks are standard so they should go in:

`blocks/repeater/`

However the main difference is these templates will be rendered multiple times. The number of times rendered will depend on how many rows of data for the repeater are entered into the admin.

The `$data` variable will contain an array of block content for the current repeater row being rendered. The keys are block id's and the contents are the raw block content.

However in the repeater block there is an extra bit of code that loads this data ready into the PageBuilder block function. So not only do you just need the name of the block now content will be rendered and returned as a string. This makes it easy to have repeaters inside other repeaters if you wished to do something more complicated.

For example, assuming it an image block, the following code will use the block content from the current repeater row and render it using the image blocks display function:

`PageBuilder::block('slide_image')` 

Note: This will override any page data with the same block name, however if you still need to get the current page data in these templates rather than the repeater data you can pass the page_id option through the block function:

`PageBuilder::block('slide_image', ['page_id' => PageBuilder::pageId()])` 

## Additonal Variables

If you need to alter the template based on the current row being rendered there are a few extra variables provided:

- $is_first (is true on the first row rendered otherwise false) 
- $is_last (is true on the first row rendered) 
- $count (starts at 1 and increaments for each row rendered in the current repeater)
- $total (total number of rows that will be rendered)
- $data_id (the array key of the data being rendered, it's the repeater block_repeater_rows id for repeaters)
- $links / $pagination (return pagination links if using "per_page" option [repeater block only])
- $block (retuns array of block data used in the current repeater [repeater block only])

## Example

Here is a how the repeater block can be used to create a banner slider. 

```
@if ($is_first)
<div id="carousel-example" class="carousel slide" data-ride="carousel">
    <!-- Indicators -->
    <ol class="carousel-indicators">
        @for ($i = 0; $i < $total; $i++)
        <li data-target="#carousel-example" data-slide-to="{!! $i !!}" {!! ($i==0)?' class="active"':'' !!}></li>
        @endfor
    </ol>
    
    <!-- Wrapper for slides -->
    <div class="carousel-inner">
@endif

        <div class="item {!! $is_first?'active':'' !!} car{!! $count !!}">
            <div class="carousel-caption">
                <h1>{!! PageBuilder::block('slide_title') !!}</h1>
                <a href="{!! PageBuilder::block('slide_link') !!}">Find out more</a>
            </div>
        </div>

@if ($is_last)
    </div>

    <!-- Controls -->
    <a class="left carousel-control" href="#carousel-example" role="button" data-slide="prev">
        <span class="glyphicon glyphicon-chevron-left"></span>
    </a>
    <a class="right carousel-control" href="#carousel-example" role="button" data-slide="next">
        <span class="glyphicon glyphicon-chevron-right"></span>
    </a>
    
</div>
@endif
```

## Repeater Forms

In Coaster 5.3, we introduced a feature for creating forms for frontend users to submit content to repeaters (like the comments form in the Coaster 2016 and 2017 themes).

To do this, first create a repeater block. Then create an additonal form file like so: 

`blocks/repeaters/[block_name]-form.blade.php`

Then inside this file create a form with the field names from your repeater block and users can submit their form to the repeater. The theme comments repeater uses this feature - so that's a good place to start when trying this out.

## Repeated View On Other Blocks

Any block type can take advantage of using these repeated views if it has iterable content.

When calling the block function just set the option `repeated_view` to true and the blocks template will be rendered multiple times depeedning on the the size of the content. 
