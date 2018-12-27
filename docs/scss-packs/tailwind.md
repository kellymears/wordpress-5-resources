## main.scss

``` scss
@import "blocks/align";
@import "blocks/copy";
@import "blocks/quotes";
@import "blocks/unordered_grids.scss";
@import "blocks/table";
@import "blocks/audio";
@import "blocks/cover";
@import "blocks/separator";
```

## _align.scss
``` scss
main.main {
  > *:not(.alignwide,.alignfull,.alignleft,.alignright,.aligncenter) {
    @apply max-w-lg mt-4 mb-4 ml-auto mr-auto pt-4 pb-4;
  }

  > [class*="wp-block-"].alignwide {
    @apply max-w-xl ml-auto mr-auto mt-10 mb-10;
  }

  > [class*="wp-block-"].alignfull {
    @apply max-w-full mx-0 my-12 py-12;
  }

  > [class*="wp-block-"].alignleft > * {
    @apply float-left mr-4 mt-0 mb-0;
  }

  > [class*="wp-block-"].alignright > * {
    @apply float-right ml-4 mt-0 mb-0;
  }

  > [class*="wp-block-"].alignleft,
  > [class*="wp-block-"].alignright,
  > [class*="wp-block-"].aligncenter {
    @apply mx-auto pt-4 pb-4;
  }

  > .wp-block-cover.alignright {
    @apply float-right mt-8 mb-8;
  }

  > .wp-block-cover.alignleft {
    @apply float-left mt-8 mb-8;
  }

  > .wp-block-cover.alignleft,
  > .wp-block-cover.alignright {
    > p {
      @apply mx-0;
    }
  }
}
```

## _copy.scss
``` scss
main.main {
  h1,
  h2,
  h3,
  h4,
  h5,
  h6,
  p,
  ul li,
  ol li,
  > span,
  > a,
  table * {
    @apply font-sans;
  }

  pre,
  .wp-block-code,
  .wp-block-verse,
  code {
    @apply font-mono overflow-hidden;
  }

  > h1,
  > h2,
  > h3,
  > h4,
  > h5,
  > h6 {
    @apply leading-tight;
  }

  > h1 {
    @apply pt-12 pb-8;
  }

  > h2,
  > h3 {
    @apply pt-4 pb-4;
  }

  > h4,
  > h5,
  > h6 {
    @apply my-0 pt-4 pb-0 uppercase;
  }

  > ul {
    @apply list-reset;
  }

  > ul,
  > ol {
    @apply my-0 py-4;
  }

  > ul ul,
  > ol ol {
    @apply my-0 py-0;
  }

  > ul li,
  > ol li {
    @apply mt-4 mb-0 pb-0;
  }

  > p,
  > ul:not([class*="wp-block"]) li,
  > ol:not([class*="wp-block"]) li,
  > pre,
  > span,
  > table * {
    @apply text-base leading-normal;
  }

  p {
    @apply py-4;
  }

  /** axiomatic */
  p + p {
    @apply my-0 pt-0;
  }

  /** buttons */
  a:not(.wp-block-button__link) {
    @apply text-primary no-underline border-b border-transparent;

    transition: 0.2s ease;

    &:hover {
      @apply border-primary;
    }
  }

  pre {
    @apply w-full overflow-x-scroll my-4;
  }
}
```

## _quotes.scss
``` scss
main.main {
  > blockquote.wp-block-quote,
  > blockquote.wp-block-quote.is-large,
  > blockquote.wp-block-quote.is-style-large {
    @apply mt-4 mb-4 ml-auto mr-auto px-8 py-8;
  }

  > figure.wp-block-pullquote {
    @apply mx-auto;
  }

  > figure.wp-block-pullquote.alignfull {
    @apply px-4;
  }

  > blockquote.wp-block-quote > cite,
  > figure.wp-block-pullquote > blockquote > cite {
    @apply
      inline-block pt-4
      font-sans uppercase roman font-semibold tracking-tight;

    &::before {
      content: "\2014 ";
    }
  }
}

main.main > figure.wp-block-pullquote.alignleft,
main.main > figure.wp-block-pullquote.alignright {
  @apply max-w-lg pt-4 pb-0;

  > blockquote {
    @apply max-w-xs mt-4;
  }
}

main.main > figure.wp-block-pullquote.alignleft {
  > blockquote {
    @apply ml-0 mr-8;
  }
}

main.main > figure.wp-block-pullquote.alignright {
  > blockquote {
    @apply mr-0 ml-8;
  }
}

main.main > figure.wp-block-pullquote[class*="align"] cite {
  @apply mt-4;
}
```

## _unordered_grids.scss
``` scss
main.main {
  > ul:not(.wp-block-categories):not(.wp-block-archives) {
    li {
      @apply list-reset;
    }
  }

  > ul:not([class*="columns-"]):not(.is-grid) {
    li::before,
    li ul li::before {
      content: "👉 ";
    }
  }
}
```

## _table.scss
``` scss
main.main table.wp-block-table {
  @apply table-auto w-full max-w-lg mx-auto my-8 px-8;

  tbody tr:first-child {
    @apply mb-4;

    td {
      @apply font-semibold uppercase;
    }
  }

  tbody tr:not:first-child td {
    @apply py-4;
  }
}
```

## _audio.scss
``` scss
main.main .wp-block-audio figcaption {
  @apply mt-1 mb-0;
}
```

## _cover.scss
``` scss
main.main {
  > .wp-block-cover.alignfull,
  > .wp-block-cover.alignwide,
  > .wp-block-image.alignfull,
  > .wp-block-image.alignwide {
    @apply py-4;
  }

  > .wp-block-cover.alignleft,
  > .wp-block-cover.alignright,
  > .wp-block-cover.aligncenter {
    @apply max-w-lg my-12 mx-8 py-0;

    clear: both;

    ::after {
      clear: both;
      content: "";
    }
  }

  > .wp-block-cover.aligncenter {
    @apply mx-auto;

    clear: both;
    content: "";
  }
}
```

## _separator.scss
``` scss
main.main {
  .wp-block-separator {
    @apply
      block h-px mt-12 mb-12 mx-auto py-0
      text-grey bg-grey opacity-75 border-transparent;

    clear: both;

    &.is-style-dots {
      @apply bg-transparent;
    }

    &:not(.is-style-wide):not(.is-style-dots) {
      &::before {
        content: "";
        width: 40px;
      }
    }

    &.is-style-dots::before {
      @apply text-lg;

      letter-spacing: 12px;
      padding-left: 12px;
    }
  }
}
```
