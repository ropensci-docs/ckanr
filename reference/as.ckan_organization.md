# ckan_organization class helpers

ckan_organization class helpers

## Usage

``` r
as.ckan_organization(x, ...)

is.ckan_organization(x)
```

## Arguments

- x:

  Variety of things, character, list, or ckan_organization class object

- ...:

  Further args passed on to
  [`organization_show()`](https://docs.ropensci.org/ckanr/reference/organization_show.md)
  if character given

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

(orgs <- organization_list(limit = 3))
orgs[[3]]

# create item class from only an item ID
as.ckan_organization(orgs[[3]]$id)

# gives back itself
(x <- as.ckan_organization(orgs[[3]]$id))
as.ckan_organization(x)
} # }
```
