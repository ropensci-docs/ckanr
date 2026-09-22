# ckan_package class helpers

ckan_package class helpers

## Usage

``` r
as.ckan_package(x, ...)

is.ckan_package(x)
```

## Arguments

- x:

  One of character, list, or ckan_package class object

- ...:

  Extra arguments. If `x` is character, the function passes them on to
  [`package_show()`](https://docs.ropensci.org/ckanr/reference/package_show.md).
  If GET is not supported, use the `http_method` parameter to set a
  different HTTP verb

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
