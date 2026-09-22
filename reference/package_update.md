# Update a package

This function updates all package metadata fields. Each update sets the
metadata key "last_updated".

On CKAN \< 2.12 the function overwrites any omitted metadata fields: any
metadata fields missing from `x` are deleted in the package. On CKAN
2.12 and later the internal `allow_partial_update` context was removed
(<https://github.com/ckan/ckan/pull/8155>): calling `package_update()`
without `resources` now keeps existing resources instead of wiping them.
To partially update nested fields on any version, prefer
[`package_patch()`](https://docs.ropensci.org/ckanr/reference/package_patch.md)
or
[`package_revise()`](https://docs.ropensci.org/ckanr/reference/package_revise.md).

CKAN 2.12+ also reports whether the update made a real change via a
`changed_entities` envelope value
(<https://github.com/ckan/ckan/pull/8407>); the value is part of the
returned payload when the server provides it.

## Usage

``` r
package_update(
  x,
  id,
  http_method = "GET",
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

  (character) Package identifier

- http_method:

  (character) Which HTTP method (verb) to use. Use one of "GET" or
  "POST". Default: "GET"

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

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# Step 1: get the dataset details as R list
ds_id <- "my-dataset-id-md5-hash"
ds <- ckanr::package_show(ds_id, as = "table")

# Step 2: update selected fields
ds$title <- "An updated title"
ds$description <- "Only title and description have been updated."
# ds contains all other package data, including tags and resources

# Step 3a: Update the dataset on CKAN with locally modified metadata `ds`
result <- ckanr::package_update(ds, ds_id)
# Replace existing package metadata

# Step 3b: Possible or intended data loss on CKAN < 2.12
# Any metadata fields missing from `ds` will be deleted in the package
# (on CKAN 2.12+ omitted `resources` are kept; use package_patch() or
# package_revise() for partial updates on any version)
del(ds$description)
result_with_deleted_description <- ckanr::package_update(ds, ds_id)
} # }
```
