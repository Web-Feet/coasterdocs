# Repeater Blocks

One very useful block that Coaster has is called a "repeater". With these blocks you can repeat sections of HMTL but with different content. This content can be pulled from multiple blocks of any type. For example you could use this to create banner sliders or team member profiles.

## Block Views

The template locations for the repeater blocks are standard so they should go in:

`blocks/repeater/`

However the main difference is these templates will be call mulitple times. The number of times will depend on how many rows of data are entered into the admin.

The `$data` variable will contain an array of block content for the current repeater row being rendered. The keys are the ids of the block. 

However in the repeater block there is an extra bit of code that loads this data into the PageBuilder block function so you can just use the names of the blocks. This will override any page data with the same block name, however if you still need to get the page data in these templates you can pass the page_id option through the block function.


## Example

Here is a banner slider example. The block data for the "slide_title" and "slide_link" will come from the repeater row data as explain above.


```
@if ($is_first)
<div id="carousel-example-generic" class="carousel slide" data-ride="carousel">
    <!-- Indicators -->
    <ol class="carousel-indicators">
        @for ($i = 0; $i < $total; $i++)
        <li data-target="#carousel-example-generic" data-slide-to="{!! $i !!}"{!! ($i==0)?' class="active"':'' !!}></li>
        @endfor
    </ol>
    
    <!-- Wrapper for slides -->
    <div class="carousel-inner">
@endif

        <div class="item {!! ($count==1)?'active':'' !!} car{!! $count !!}">
            <div class="carousel-caption">
                <h1>{!! PageBuilder::block('slide_title') !!}</h1>
                <a href="{!! PageBuilder::block('slide_link') !!}" class="btn btn-primary" >Find out more</a>
            </div>
        </div>

@if ($is_last)
    </div>

    <!-- Controls -->
    <a class="left carousel-control" href="#carousel-example-generic" role="button" data-slide="prev">
        <span class="glyphicon glyphicon-chevron-left"></span>
    </a>
    <a class="right carousel-control" href="#carousel-example-generic" role="button" data-slide="next">
        <span class="glyphicon glyphicon-chevron-right"></span>
    </a>
    
</div>
@endif
```

## Repeater Forms



## Repeated View On Other Blocks
