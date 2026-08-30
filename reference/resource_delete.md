# Delete a resource.

Delete a resource.

## Usage

``` r
resource_delete(id, url = get_default_url(), key = get_default_key(), ...)
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
ckanr_setup(url = "https://demo.ckan.org/", key = Sys.getenv("CKAN_DEMO_KEY"))

# create a package
(res <- package_create("yellow9"))

# then create a resource
file <- system.file("examples", "actinidiaceae.csv", package = "ckanr")
(xx <- resource_create(res,
  description = "my resource",
  name = "bears",
  upload = file,
  rcurl = "http://google.com"
))

# delete the resource
resource_delete(xx)
} # }
```
