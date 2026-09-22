# ckan_tag class helpers

ckan_tag class helpers

## Usage

``` r
as.ckan_tag(x, ...)

is.ckan_tag(x)
```

## Arguments

- x:

  One of character, list, or ckan_tag class object

- ...:

  Extra arguments. If `x` is character, the function passes them on to
  [`tag_show()`](https://docs.ropensci.org/ckanr/reference/tag_show.md)

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

(tags <- tag_search(query = "ta"))
tags[[3]]

# create item class from only an item ID
as.ckan_tag(tags[[3]]$id)

# gives back itself
(x <- as.ckan_tag(tags[[3]]$id))
as.ckan_tag(x)
} # }
```
