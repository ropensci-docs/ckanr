# Patch an organization.

This function partially updates an organization: it updates only the
provided parameters and leaves all other parameters unchanged (unlike
[`organization_update()`](https://docs.ropensci.org/ckanr/reference/organization_update.md),
which may delete parameters not explicitly provided). See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.patch.organization_patch>
for the official API contract.

## Usage

``` r
organization_patch(
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

  (character or `ckan_organization`) The id or name of the organization
  to patch, or a `ckan_organization` object.

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

The patched organization as a `ckan_organization` object. With
`as = "table"`, a data.frame; with `as = "json"`, the raw JSON response.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.patch.organization_patch

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# Create an organization
(res <- organization_create("hello-my-org2"))

# Get the organization
org <- organization_show(res$id)

# Make some changes
x <- list(title = "!hello world!", description = "hello world org")
organization_patch(x, id = org)
} # }
```
