# Create default views for a single resource

Create default views for a single resource

## Usage

``` r
resource_create_default_resource_views(
  resource,
  package = NULL,
  create_datastore_views = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- resource:

  (character or `ckan_resource`) Resource identifier or object.

- package:

  (optional) Dataset identifier or `ckan_package` object.

- create_datastore_views:

  (logical) When `TRUE`, the function creates only views that require
  DataStore-backed resources. The function uses this option when
  DataPusher finishes ingesting data.

- url:

  Base URL to use. Default: https://demo.ckan.org/. See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key. Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- as:

  (character) One of list (default), table, or json. Parsing with the
  table option uses `jsonlite::fromJSON(..., simplifyDataFrame = TRUE)`,
  which attempts to parse data to data.frame's when possible. The result
  can vary from a vector, list or data.frame. (required)

- ...:

  Extra curl arguments. The function passes them to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)
