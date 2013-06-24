SASS Flexible Media Queries Mixin-Andres Gallo
=================================

There are many sass mixins to make media queries all over the internet but all of them seem to support only one media query at a time.  It is for this reason I wrote this mixin. For more complex layouts for example there are cases where the same css is needed in two different media queries.  While it is possible to call the current media query mixins twice (once for each of the two different media queries), the duplicate output is undesireable as it creates unecessary duplicate code.

Using the script
---------------

* First import the mixin....
* Should you want to skip the instructions there are some examples below ...oh yeee!
* To use the script simply call the sass mixing 'media' and pass it a single or multiple lists followed by an empty list to tell sass to iterate through them 2 level list. The syntax for the lists is ().  
* Each list corresponds to each media query. 

### Parameters for each media query- in order in which they may be passed. NONE ARE REQUIRED.

* min (int)
* max (int)
* format (String) - Defaults to screen
* orientation (String)

Examples
--------

### SCSS for devices with a width greater than or equal to 600px AS WELL AS devices with a width of lesser or equal to 599 in portrait mode

    .TEST {//Multiple media query example
      @include media( (600)(null 599 null portrait)() ){
        color: green;
      }
    }

#### CSS output
    @media only screen and (min-width: 600px), only screen and (max-width: 599px) and (orientation: portrait) {
      .TEST {
        color: green;
      }
    } 


### SCSS for print devices

    @include media( (null null print null)() ){
      .TESTB {
        color: red;//Not that color matters in most printer stylesheets
      }
    }

#### CSS output

    @media only print {
      .TESTB {
        color: red;
      }
    }

### Good example showing using multiple lists and their merged media query

    @include media( (600)(600 1000)(600 1000 print)(600 1000 print landscape) ){
      .TESTB {
        color: orange;
      }
    }

#### CSS output

    @media only screen and (min-width: 600px), only screen and (min-width: 600px) and (max-width: 1000px), only print and (min-width: 600px) and (max-width: 1000px) {
      .TESTB {
        color: orange;
      }
    }



    