# Update an organization.

This function updates all organization metadata fields. You must be
authorized to edit the organization. Update methods may delete
parameters not explicitly provided: if you want to edit only specific
attributes, use
[`organization_patch()`](https://docs.ropensci.org/ckanr/reference/organization_patch.md)
instead. For the full list of accepted fields, see
[`organization_create()`](https://docs.ropensci.org/ckanr/reference/organization_create.md)
and
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.update.organization_update>.

## Usage

``` r
organization_update(
  x,
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- x:

  (list) A list with key-value pairs

- id:

  (character or `ckan_organization`) The name or id of the organization
  to update, or a `ckan_organization` object.

- url:

  Base URL to use. Default: https://demo.ckan.org/. See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key. Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- as:

  (character) One of list (default), table, or json. Parsing with the
  table option uses `jsonlite::fromJSON(..., simplifyDataFrame = TRUE)`,
  which attempts to parse data to data.frame's when possible. The result
  can vary from a vector, list or data.frame. (required)

- ...:

  Extra curl arguments. The function passes them to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)

## Value

The updated organization as a `ckan_organization` object. With
`as = "table"`, a data.frame; with `as = "json"`, the raw JSON response.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.update.organization_update

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# First, create an organization
org <- organization_create("water-bears2")
organization_show(org)

# Make some changes
x <- list(description = "An organization about water bears")

# Then update the organization
organization_update(x, id = org)
} # }
```
