# ckan_group class helpers

ckan_group class helpers

## Usage

``` r
as.ckan_group(x, ...)

is.ckan_group(x)
```

## Arguments

- x:

  Variety of things, character, list, or ckan_group class object

- ...:

  Further args passed on to
  [`group_show()`](https://docs.ropensci.org/ckanr/reference/group_show.md)
  if character given

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

(grps <- group_list())
grps[[3]]

# create item class from only an item ID
as.ckan_group(grps[[3]]$id)

# gives back itself
(x <- as.ckan_group(grps[[3]]$id))
as.ckan_group(x)
} # }
```
