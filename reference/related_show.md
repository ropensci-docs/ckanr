# Show a related item

Show a related item

## Usage

``` r
related_show(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) Related item identifier.

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
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# create a package and a related item
res <- package_create("hello-pluto2") %>%
  related_create(
    title = "my resource",
    type = "visualization"
  )

# show the related item
related_show(res)
related_show(res$id)

# get data back in different formats
related_show(res, as = "json")
related_show(res, as = "table")
} # }
```
