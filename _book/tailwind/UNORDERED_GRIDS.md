## _unordered_grids.scss

``` (scss)
main.main > ul:not(.wp-block-categories):not(.wp-block-archives) {
  li {
    @apply list-reset;
  }
}

main.main > ul:not([class*="columns-"]):not(.is-grid) {
  li::before,
  li ul li::before {
    content: "👉 ";
  }
}
```