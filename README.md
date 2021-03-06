# Anatomi

## A configurable, equal width, SCSS grid generator for structuring your layout

This is another grid generator for building grid systems. Using it is fairly straigfhtforward, just add your own values to the <pre>sass/modules/_config.scss</pre> and recompile the styles.scss.

## Usage 

Out of the box, you can have a sweet, mobile first repsonsive grid. Below is a quick example of a standard main column and a sidebar layout:

### Your markup

    <!-- Your grid row -->
    <div class="grid">
    
      <!-- "mobile" or "phablet" (eugh) screen = Full width --> 
      <!-- "laptop" screen = 5/6 --> 
      <!-- "desktop" screen = 3/4 --> 
      <div class="grid__unit m-5-6 w-8-12 main" role="main">
      
        <!-- Your awesome important content goes here -->
      
      </div>
      
      <!-- "mobile" or "phablet" (eugh) screen = Full width --> 
      <!-- "laptop" screen = 1/6 --> 
      <!-- "desktop" screen = 1/4 -->
      <div class="grid__unit m-1-6 w-4-12 sidebar">
        
        <!-- Your sidebar crap goes here -->
        
      </div>
    
    </div>
    <!-- / row ends -->  

## OK, but what can I configure

### Ghost Grids Usage

This will enable the use of Sass' silent classes. This basically means you can have all the sexy grid-ness without all the dirty class names in your HTML.
Mr [CSS Wizardry](http://csswizardry.com/2013/02/responsive-grid-systems-a-solution/) can explain this much better than me

#### Sass

    $ghost-grids : true; //default = false

    .wrap {
      @extend %grid;
    }
    .sidebar {
      @extend %grid__unit;
      @extend %w-3-12;
    }

#### Compiled CSS

    .wrap {
      width: 102.5%;
      margin-left: -2.5%
    }
    .sidebar {
      float: left;
      margin-left: 2.5%;
      width: 22.5%;
    }
    
    
### Column Counts

These will set the number of available columns at various breakpoints (set up below)
    
    // Standard (eg: no media qs)
    $grid-units-sml  : 1;   // default 4
    
    // First breakpoint to second breakpoint
    $grid-units-med  : 5;   // default 6
    
    // Second BP to third
    $grid-units-wide : 9;   // default 12


### Grid Gutter
    
Sets the gutter width. This needs to be a percentage. You can make it 0% and use padding instead though (config coming soon)

    $grid-gutter : 3%;      // default 2.5%

### breakpoints

These don't have to be your overall breakpoints (although they probably will be). Just breakpoints for your columns.  
    
    // Handheld (but bigger than a phone)
    $bp-s : 40em;
    // Lap
    $bp-m : 50em;
    // Desk
    $bp-w : 60em;
    // Jumbotron (What is the media query support for those..?)
    $bp-xw : 100em;
    
    
## To do

- The grid generators aren't too DRY so I wanna redo those. 
- I need to add some config to be able to use padding as a gutter instead of the margin. I don't support IE7 anyway (the grids won't work even with a mediaQ polyfill. I don't even care. I might fix it)

## Thanks

This is basically a configurable version of the original Bootstrap scaffolding (although maybe that is configurable) and also to [innuit.css](https://github.com/csswizardry/inuit.css/). Also Chris Coyier's [naming media queries post](http://css-tricks.com/naming-media-queries) for the mq generator. Thanks.

## Disclaimer 
Mostly this is an experiment for me to try out some intermediate Sass stuff and for use in my personal projects, mostly. I may update it. I may not. Its provided as is. If it breaks your Boss's computer, you never even heard of me, ok? 
