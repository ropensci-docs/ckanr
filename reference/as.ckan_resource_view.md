# ckan_resource_view class helpers

ckan_resource_view class helpers

## Usage

``` r
as.ckan_resource_view(x, ...)

is.ckan_resource_view(x)
```

## Arguments

- x:

  Variety of things: character, list, or `ckan_resource_view` object

- ...:

  Further arguments passed to
  [`resource_view_show()`](https://docs.ropensci.org/ckanr/reference/resource_view_show.md)
  when `x` is an identifier.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = Sys.getenv("CKAN_DEMO_KEY")
)

res <- package_show("sample-dataset")
views <- resource_view_list(res$resources[[1]]$id)

# Coerce from ID
as.ckan_resource_view(views[[1]]$id)

# Pass through existing objects
as.ckan_resource_view(views[[1]])
} # }
```
