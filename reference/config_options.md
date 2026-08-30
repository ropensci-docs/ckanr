# Runtime configuration helpers

Inspect and update CKAN's runtime-editable configuration keys.

## Usage

``` r
config_option_list(
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

config_option_show(
  option_key,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

config_option_update(
  options,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

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

- option_key:

  (character) Configuration option identifier.

- options:

  (list) Named list of configuration options to update.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = "my-ckan-key")
config_option_list()
config_option_update(list("ckan.site_title" = "My Portal"))
} # }
```
