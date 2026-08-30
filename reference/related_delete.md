# Delete a related item.

Delete a related item.

## Usage

``` r
related_delete(id, url = get_default_url(), key = get_default_key(), ...)
```

## Arguments

- id:

  (character) Resource identifier.

- url:

  Base url to use. Default: https://data.ontario.ca See also
  [`ckanr_setup()`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url()`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key, Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- ...:

  Curl args passed on to
  [crul::verb-POST](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# create a package and a related item
res <- package_create("hello-venus2") %>%
  related_create(
    title = "my resource",
    type = "visualization"
  )

# show the related item
related_delete(res)
## or with id itself:
## related_delete(res$id)
} # }
```
