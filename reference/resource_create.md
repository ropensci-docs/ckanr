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

  (character) ID of the package. You add the resource to this package.
  The value must be an alphanumeric string. Required.

- rcurl:

  (character) URL of the resource. Required.

- revision_id:

  (character) Revision ID. Optional.

- description:

  (character) Description of the resource. Optional. Required.

- format:

  (character) Format. Optional.

- hash:

  (character) Hash. Optional.

- name:

  (character) Name of the resource. Optional. Required.

- resource_type:

  (character) Resource type. Optional.

- mimetype:

  (character) MIME type. Optional.

- mimetype_inner:

  (character) Inner MIME type. Optional.

- webstore_url:

  (character) Webstore URL. Optional.

- cache_url:

  (character) Cache URL. Optional.

- size:

  (integer) Size. Optional.

- created:

  (character) ISO date string. Optional.

- last_modified:

  (character) ISO date string. Optional.

- cache_last_updated:

  (character) ISO date string. Optional.

- webstore_last_updated:

  (character) ISO date string. Optional.

- upload:

  (character) Path to a local file. Optional.

- extras:

  (list) Extra metadata fields of the resource. Optional.

- http_method:

  (character) HTTP method (verb) to use. The value is one of "GET" or
  "POST". Default is "GET".

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

package_create("foobbbbbarrrr") |>
  resource_create(
    description = "my resource",
    name = "bearsareus",
    upload = file,
    extras = list(my_extra = "some value"),
    rcurl = "http://google.com"
  )
} # }
```
