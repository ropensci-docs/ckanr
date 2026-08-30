# Update an existing resource view

Update an existing resource view

## Usage

``` r
resource_view_update(
  id,
  resource = NULL,
  title = NULL,
  description = NULL,
  config = NULL,
  filter_fields = NULL,
  filter_values = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character or `ckan_resource_view`) View identifier.

- resource:

  (character or `ckan_resource`) Parent resource identifier.

- title:

  (character) Title assigned to the view.

- description:

  (character) Optional description.

- config:

  (list) Arbitrary configuration list passed to the plugin.

- filter_fields, filter_values:

  Optional filter parameters for filterable views.

- url:

  Base url to use. Default: https://demo.ckan.org/ See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key, Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- as:

  (character) One of list (default), table, or json. Parsing with table
  option uses `jsonlite::fromJSON(..., simplifyDataFrame = TRUE)`, which
  attempts to parse data to data.frame's when possible, so the result
  can vary from a vector, list or data.frame. (required)

- ...:

  Curl args passed on to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)
