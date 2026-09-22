# Add a new table to a datastore

BEWARE: This function does not work yet.

## Usage

``` r
ds_create(
  resource_id = NULL,
  resource = NULL,
  force = FALSE,
  aliases = NULL,
  fields = NULL,
  records = NULL,
  primary_key = NULL,
  indexes = NULL,
  include_records = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- resource_id:

  (string) Resource id that stores the data.

- resource:

  (dictionary) Resource dictionary for
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md).
  Use it instead of `resource_id` (optional)

- force:

  (logical) To edit a read-only resource, set to `TRUE`. Default:
  `FALSE`

- aliases:

  (character) Names for read only aliases of the resource. (optional)

- fields:

  (list) Fields/columns and their extra metadata. (optional)

- records:

  (list) The data, for example:
  `[{"dob": "2005", "some_stuff": ["a", "b"]}]` (optional)

- primary_key:

  (character) Fields that represent a unique key (optional)

- indexes:

  (character) Indexes on table (optional)

- include_records:

  (logical) If `TRUE`, CKAN 2.12+ returns the actual inserted records
  (including `_id` values and transformations) in the response. Default:
  `FALSE`. See <https://github.com/ckan/ckan/pull/8684>. Note: bulk
  inserts with `include_records = TRUE` can hit a server-side error on
  CKAN 2.12.0; use a single record or
  [`ds_upsert()`](https://docs.ropensci.org/ckanr/reference/datastore_extra.md)
  with `include_records = TRUE` instead when affected.

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

## References

http://bit.ly/ds_create

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

# create a package
(res <- package_create("foobarrrrr", author = "Jane Doe"))

# then create a resource
file <- system.file("examples", "actinidiaceae.csv", package = "ckanr")
(xx <- resource_create(
  package_id = res$id,
  description = "my resource",
  name = "bears",
  upload = file,
  rcurl = "http://google.com"
))
ds_create(resource_id = xx$id, records = iris, force = TRUE)
resource_show(xx$id)
} # }
```
