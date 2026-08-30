# Get information on a CKAN server

Get information on a CKAN server

## Usage

``` r
ckan_info(url = get_default_url(), ...)

ckan_version(url = get_default_url(), ...)
```

## Arguments

- url:

  Base url to use. Default: <https://data.ontario.ca>. See also
  [`ckanr_setup()`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url()`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).
  (required)

- ...:

  Curl args passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  (optional)

## Value

for `ckan_info` a list with many slots with various info. for
`ckan_version`, list of length two, with actual version as character,
and another with version converted to numeric (any dots or letters
removed)

## Examples

``` r
if (FALSE) { # \dontrun{
ckan_info()
ckan_info(servers()[5])

ckan_version(servers()[5])
} # }
```
