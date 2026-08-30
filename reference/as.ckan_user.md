# ckan_user class helpers

ckan_user class helpers

## Usage

``` r
as.ckan_user(x, ...)

is.ckan_user(x)
```

## Arguments

- x:

  Variety of things, character, list, or ckan_user class object

- ...:

  Further args passed on to
  [`user_show()`](https://docs.ropensci.org/ckanr/reference/user_show.md)
  if character given

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

(usrs <- user_list())
usrs[1:3]
usrs[[3]]

# create item class from only an item ID
as.ckan_user(usrs[[3]]$id)

# gives back itself
(x <- as.ckan_user(usrs[[3]]$id))
as.ckan_user(x)
} # }
```
