# Update a package

This function updates all package metadata fields. Any update will also
set the metadata key "last_updated". Any omitted metadata fields will be
overwritten.

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

  (character) which HTTP method (verb) to use; one of "GET" or "POST".
  Default: "GET"

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

# Step 3b: Possible or intended data loss
# Any metadata fields missing from `ds` will be deleted in the package
del(ds$description)
result_with_deleted_description <- ckanr::package_update(ds, ds_id)
} # }
```
