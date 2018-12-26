## _align.scss

``` (scss)
main.main > [class*="wp-block-"]:not(.alignwide,.alignfull),
main.main > :not(h1,h2,h3,h4,h5,h6,p,li):not(.alignwide,.alignfull) {
  @apply max-w-lg mx-auto px-8 py-8;
}

main.main > [class*="wp-block-"]:not(.alignwide,.alignfull),
main.main > :not(.alignwide,.alignfull) {
  @extend .container;
}

main.main > [class*="wp-block-"].alignwide {
  @apply max-w-xl mx-auto my-10;
}

main.main > [class*="wp-block-"].alignfull {
  @apply max-w-full mx-0 my-12 py-12;
}

main.main > [class*="wp-block-"].alignleft > * {
  @apply float-left mr-4;
}

main.main > [class*="wp-block-"].alignright > * {
  @apply float-right ml-4;
}

main.main > [class*="wp-block-"]:not(.wp-block-cover).alignleft,
main.main > [class*="wp-block-"]:not(.wp-block-cover).alignright,
main.main > [class*="wp-block-"]:not(.wp-block-cover).aligncenter {
  @apply mx-auto pt-4;
}

main.main > .wp-block-cover.alignleft,
main.main > .wp-block-cover.alignright {
  ::after {
    content: "";
    display: table;
    clear: both;
  }
}

main.main > div.wp-block-cover.alignleft {
  @apply float-left mx-8 mr-8 my-8;
}

main.main > div.wp-block-cover.alignright {
  @apply float-right mx-8 ml-8 my-8;
}
```