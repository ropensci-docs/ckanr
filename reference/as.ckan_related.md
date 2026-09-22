# ckan_related class helpers

ckan_related class helpers

## Usage

``` r
as.ckan_related(x, ...)

is.ckan_related(x)
```

## Arguments

- x:

  One of character, list, or ckan_related class object

- ...:

  Extra arguments. If `x` is character, the function passes them on to
  [`related_show()`](https://docs.ropensci.org/ckanr/reference/related_show.md)

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

(x <- package_create("foobbbbbarrrrr") |>
  related_create(
    title = "my resource",
    type = "visualization"
  ))

# create item class from only an item ID
as.ckan_related(x$id)

# gives back itself
(x <- as.ckan_related(x$id))
as.ckan_related(x)
} # }
```
