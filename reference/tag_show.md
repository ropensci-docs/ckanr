# Show a tag.

Show a tag.

## Usage

``` r
tag_show(
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

  (character) Name or ID of the tag.

- include_datasets:

  Include a list of up to 1000 datasets of the tag. The limit is 1000
  datasets. Use
  [`package_search()`](https://docs.ropensci.org/ckanr/reference/package_search.md)
  for more. Optional. Default is `FALSE`.

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

## Examples

``` r
if (FALSE) { # \dontrun{
# get tags with tag_list()
tags <- tag_list()
tags[[30]]$id

# show a tag
(x <- tag_show(tags[[30]]$id))

# give back different data formats
tag_show(tags[[30]]$id, as = "json")
tag_show(tags[[30]]$id, as = "table")
} # }
```
