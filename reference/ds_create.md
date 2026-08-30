# Add a new table to a datastore

BEWARE: This function still doesn't quite work yet.

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
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- resource_id:

  (string) Resource id that the data is going to be stored against.

- resource:

  (dictionary) Resource dictionary that is passed to
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md).
  Use instead of `resource_id` (optional)

- force:

  (logical) Set to `TRUE` to edit a read-only resource. Default: `FALSE`

- aliases:

  (character) Names for read only aliases of the resource. (optional)

- fields:

  (list) Fields/columns and their extra metadata. (optional)

- records:

  (list) The data, eg: `[{"dob": "2005", "some_stuff": ["a", "b"]}]`
  (optional)

- primary_key:

  (character) Fields that represent a unique key (optional)

- indexes:

  (character) Indexes on table (optional)

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
