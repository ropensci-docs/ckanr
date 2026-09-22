# Update a package's metadata

If the portal uses the `ckanext-scheming` extension for custom schema
fields, put each custom field directly in `x`. Do not pass custom fields
through `extras`. CKAN rejects custom fields in `extras` with an error.

## Usage

``` r
package_patch(
  x,
  id = NULL,
  extras = NULL,
  http_method = "GET",
  key = get_default_key(),
  url = get_default_url(),
  as = "list",
  ...
)
```

## Arguments

- x:

  (list) A list with key-value pairs. Put `ckanext-scheming` custom
  fields here as named items.

- id:

  (character) Resource ID to update (optional). If x lacks an "id"
  field, this parameter is required.

- extras:

  (list) The dataset's extras (optional). Extras are arbitrary (key:
  value) metadata items for datasets. Each extra dictionary must have
  keys 'key' (a string) and 'value' (a string). Use this only for plain
  CKAN extras, not for `ckanext-scheming` custom fields.

- http_method:

  (character) Which HTTP method (verb) to use. Use one of "GET" or
  "POST". Default: "GET"

- key:

  A privileged CKAN API key. Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- url:

  Base URL to use. Default: https://demo.ckan.org/. See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

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
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# Create a package
(res <- package_create("hello-world13", author = "Jane Doe"))

# Get a resource
res <- package_show(res$id)
res$title

# patch
package_patch(res, extras = list(list(key = "foo", value = "bar")))
unclass(package_show(res))

# Update a ckanext-scheming custom field: put the field in `x`
package_patch(list(id = res$id, internal_notes = "New internal notes"))
} # }
```
