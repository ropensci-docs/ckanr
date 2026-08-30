# Delete a package

Delete a package

## Usage

``` r
package_delete(id, url = get_default_url(), key = get_default_key(), ...)
```

## Arguments

- id:

  (character) The id of the package. Required.

- url:

  Base url to use. Default: https://data.ontario.ca See also
  [`ckanr_setup()`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url()`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md)

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
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# create a package
(res <- package_create("lions-bears-tigers"))

# show the package
package_show(res)

# delete the package
package_delete(res)
} # }
```
