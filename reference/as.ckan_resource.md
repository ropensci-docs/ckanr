# ckan_resource class helpers

ckan_resource class helpers

## Usage

``` r
as.ckan_resource(x, ...)

is.ckan_resource(x)
```

## Arguments

- x:

  One of character, list, or ckan_package class object

- ...:

  Extra arguments. If `x` is character, the function passes them on to
  [`resource_show()`](https://docs.ropensci.org/ckanr/reference/resource_show.md)

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

(resrcs <- resource_search(q = "name:data"))
resrcs$results
resrcs$results[[3]]

# create item class from only an item ID
as.ckan_resource(resrcs$results[[3]]$id)

# gives back itself
(x <- as.ckan_resource(resrcs$results[[3]]$id))
as.ckan_resource(x)
} # }
```
