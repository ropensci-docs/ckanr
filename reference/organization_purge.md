# Purge an organization

IMPORTANT: You must be a sysadmin to purge an organization. Once an
organization is purged, it is permanently removed from the system.

## Usage

``` r
organization_purge(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) name or id of the organization

- url:

  Base url to use. Default: https://demo.ckan.org/ See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key, Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- as:

  (character) One of list (default), table, or json. Parsing with table
  option uses `jsonlite::fromJSON(..., simplifyDataFrame = TRUE)`, which
  attempts to parse data to data.frame's when possible, so the result
  can vary from a vector, list or data.frame. (required)

- ...:

  Curl args passed on to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)

## Value

an empty list on success

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# create an organization
(res <- organization_create("foobar",
  title = "Foo bars",
  description = "love foo bars"
))

# delete the organization just created
res$id
organization_delete(id = res$id)

# purge the organization just deleted
res$id
organization_purge(id = res$id)
} # }
```
