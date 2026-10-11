# Get information on a CKAN server

Get information on a CKAN server

## Usage

``` r
ckan_info(url = get_default_url(), ...)

ckan_version(url = get_default_url(), ...)
```

## Arguments

- url:

  Base URL to use. Default: <https://demo.ckan.org/>. See also
  [`ckanr_setup()`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url()`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).
  (required)

- ...:

  Extra curl arguments. The function passes them on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  (optional)

## Value

For `ckan_info`, the function returns a list with many slots with
various info. For `ckan_version`, the function returns a list of length
two, with the actual version as character. The second item converts the
version to numeric (any dots or letters removed)

## Examples

``` r
if (FALSE) { # \dontrun{
ckan_info()
ckan_info(servers()[5])

ckan_version(servers()[5])
} # }
```
