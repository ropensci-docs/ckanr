# ckan_package class helpers

ckan_package class helpers

## Usage

``` r
as.ckan_package(x, ...)

is.ckan_package(x)
```

## Arguments

- x:

  Variety of things, character, list, or ckan_package class object

- ...:

  Further args passed on to
  [`package_show()`](https://docs.ropensci.org/ckanr/reference/package_show.md)
  if character given. In particular, if GET is not supported you can try
  the `http_method` parameter to set a different HTTP verb

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

(pkgs <- package_search())
pkgs$results
pkgs$results[[3]]

# create item class from only an item ID
as.ckan_package(pkgs$results[[3]]$id)

# gives back itself
(x <- as.ckan_package(pkgs$results[[3]]$id))
as.ckan_package(x)
} # }
```
