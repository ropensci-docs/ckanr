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

## Details

By default the function drops the help and success slots, and it returns
only the result slot. If you want raw json, pass `as = 'json'`. Then you
parse the result to get the help slot.

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# create a package and a related item
res <- package_create("hello-pluto2") |>
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
