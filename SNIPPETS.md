# SCSS Snippets

## `.alignfull` & `.alignwide` without a container

``` (lang=scss)
main { 
    > [class*="wp-block-"]:not(.alignwide,.alignfull),
    > :not(h1,h2,h3,h4,h5,h6,p,li):not(.alignwide,.alignfull) {
        /**
        *  Set a max-width, margin & padding here
        *  which conforms to your desired measure.
        *
        *  This takes the place of a container/wrapper element.
        **/
    }

    > [class*="wp-block-"].alignwide {
        /**
        *  Allow for wideset elements to be wider
        *  than our generic measure. Set a small amount of 
        *  horizontal padding so that content doesn't bump
        *  against viewport at lower resolutions.
        **/
    }

    > [class*="wp-block-"].alignfull {
        /**
         * Set max-width to be 100%. Text elements may still require 
         * padding to prevent the above viewport issue. This can be 
         * set on those elements directly.
         **/
    }
}
```