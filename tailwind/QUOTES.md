## _quotes.scss

``` (scss)
main.main > blockquote.wp-block-quote,
main.main > blockquote.wp-block-quote.is-large,
main.main > blockquote.wp-block-quote.is-style-large {
  @apply my-4 mx-auto px-8 py-8;
}

main.main > figure.wp-block-pullquote {
  @apply mx-auto;
}

main.main > figure.wp-block-pullquote.alignfull {
  @apply px-4;
}

main.main > blockquote.wp-block-quote > cite,
main.main > figure.wp-block-pullquote > blockquote > cite {
  @apply
    inline-block pt-4
    font-sans uppercase roman font-semibold tracking-tight;

  &::before {
    content: "\2014 ";
  }
}

main.main > figure.wp-block-pullquote.alignleft,
main.main > figure.wp-block-pullquote.alignright {
  @apply pt-4 max-w-full;

  > blockquote {
    @apply max-w-xs mt-12 mb-4 mx-8;
  }
}

main.main > figure.wp-block-pullquote.alignleft {
  > blockquote {
    @apply ml-0;
  }
}

main.main > figure.wp-block-pullquote.alignright {
  > blockquote {
    @apply mr-0;
  }
}

main.main > figure.wp-block-pullquote[class*="align"] cite {
  @apply mt-4;
}
```