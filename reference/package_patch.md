# Update a package's metadata

Update a package's metadata

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

  (list) A list with key-value pairs

- id:

  (character) Resource ID to update (optional, required if x does not
  have an "id" field)

- extras:

  (character vector) - the dataset's extras (optional), extras are
  arbitrary (key: value) metadata items that can be added to datasets,
  each extra dictionary should have keys 'key' (a string), 'value' (a
  string)

- http_method:

  (character) which HTTP method (verb) to use; one of "GET" or "POST".
  Default: "GET"

- key:

  A privileged CKAN API key, Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- url:

  Base url to use. Default: https://demo.ckan.org/ See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

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
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# Create a package
(res <- package_create("hello-world13", author = "Jane Doe"))

# Get a resource
res <- package_show(res$id)
res$title

# patch
package_patch(res, extras = list(list(key = "foo", value = "bar")))
unclass(package_show(res))
} # }
```
