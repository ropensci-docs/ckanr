# Clear resource views

Clear resource views

## Usage

``` r
resource_view_clear(
  view_types = NULL,
  url = get_default_url(),
  key = get_default_key(),
  ...
)
```

## Arguments

- view_types:

  (character vector) Optional subset of view types to delete. When
  `NULL`, all views are removed.

- url:

  Base url to use. Default: https://demo.ckan.org/ See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key, Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- ...:

  Curl args passed on to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)
