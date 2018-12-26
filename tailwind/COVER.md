## _cover.scss

``` (scss)
main.main {
  > * + .wp-block-cover.alignfull,
  > * + .wp-block-cover.alignwide,
  > * + .wp-block-image.alignfull,
  > * + .wp-block-image.alignwide {
    @apply mb-4 mt-8;
  }

  > .wp-block-cover.alignfull,
  > .wp-block-cover.alignwide,
  > .wp-block-image.alignfull,
  > .wp-block-image.alignwide {
    @apply py-4;
  }
}
```