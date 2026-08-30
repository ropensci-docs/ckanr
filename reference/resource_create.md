# Create a resource

Create a resource

## Usage

``` r
resource_create(
  package_id = NULL,
  rcurl = NULL,
  revision_id = NULL,
  description = NULL,
  format = NULL,
  hash = NULL,
  name = NULL,
  resource_type = NULL,
  mimetype = NULL,
  mimetype_inner = NULL,
  webstore_url = NULL,
  cache_url = NULL,
  size = NULL,
  created = NULL,
  last_modified = NULL,
  cache_last_updated = NULL,
  webstore_last_updated = NULL,
  upload = NULL,
  extras = NULL,
  http_method = "GET",
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- package_id:

  (character) id of package that the resource should be added to. This
  should be an alphanumeric string. Required.

- rcurl:

  (character) url of resource. Required.

- revision_id:

  (character) revision id (optional)

- description:

  (character) description (optional). Required.

- format:

  (character) format (optional)

- hash:

  (character) hash (optional)

- name:

  (character) name (optional). Required.

- resource_type:

  (character) resource type (optional)

- mimetype:

  (character) mime type (optional)

- mimetype_inner:

  (character) mime type inner (optional)

- webstore_url:

  (character) webstore url (optional)

- cache_url:

  (character) cache url(optional)

- size:

  (integer) size (optional)

- created:

  (character) iso date string (optional)

- last_modified:

  (character) iso date string (optional)

- cache_last_updated:

  (character) iso date string (optional)

- webstore_last_updated:

  (character) iso date string (optional)

- upload:

  (character) A path to a local file (optional)

- extras:

  (list) - the resources' extra metadata fields (optional)

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
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

# create a package
(res <- package_create("foobarrrr", author = "Jane Doe"))

# then create a resource
file <- system.file("examples", "actinidiaceae.csv", package = "ckanr")
(xx <- resource_create(
  package_id = res$id,
  description = "my resource",
  name = "bears",
  upload = file,
  extras = list(species = "grizzly"),
  rcurl = "http://google.com"
))

package_create("foobbbbbarrrr") %>%
  resource_create(
    description = "my resource",
    name = "bearsareus",
    upload = file,
    extras = list(my_extra = "some value"),
    rcurl = "http://google.com"
  )
} # }
```
