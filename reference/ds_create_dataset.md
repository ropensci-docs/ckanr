# Datastore - create a new resource on an existing dataset

Datastore - create a new resource on an existing dataset

## Usage

``` r
ds_create_dataset(
  package_id,
  name,
  path,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- package_id:

  (character) Existing package ID (required)

- name:

  (character) Name of the new resource (required)

- path:

  (character) Path of the file to add (required)

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

## Details

This function is deprecated - will be defunct in the next version of
this package

## References

http://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.create.resource_create

## Examples

``` r
if (FALSE) { # \dontrun{
path <- system.file("examples", "actinidiaceae.csv", package = "ckanr")
ckanr_setup(url = "https://demo.ckan.org/", key = "my-demo-ckan-org-api-key")
ds_create_dataset(package_id = "testingagain", name = "mydata", path = path)

# Testing: see ?ckanr_setup to set test settings
ckanr_setup(
  test_url = "http://my-ckan.org/",
  test_key = "my-ckan-api-key",
  test_did = "an-existing-package-id",
  test_rid = "an-existing-resource-id"
)
ds_create_dataset(
  package_id = get_test_pid(), name = "mydata",
  path = system.file("examples",
    "actinidiaceae.csv",
    package = "ckanr"
  ),
  key = get_test_key(),
  url = get_test_url()
)
} # }
```
