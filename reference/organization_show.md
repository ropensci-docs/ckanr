# Show an organization

Show an organization

## Usage

``` r
organization_show(
  id,
  include_datasets = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) Organization id or name.

- include_datasets:

  (logical). Whether to include a list of the organization datasets

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

## Details

By default the help and success slots are dropped, and only the result
slot is returned. You can request raw json with `as = 'json'` then parse
yourself to get the help slot.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

res <- organization_create("stuffthings2")
organization_show(res$id)
} # }
```
