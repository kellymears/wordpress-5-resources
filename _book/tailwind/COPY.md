## _copy.scss

``` (scss)
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
    @apply pt-8 pb-4;
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
    @apply my-0 ml-4 py-4;
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