# Show a package.

Show a package.

## Usage

``` r
package_show(
  id,
  use_default_schema = FALSE,
  http_method = "GET",
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character/ckan_package) Package identifier, or a `ckan_package`
  object

- use_default_schema:

  (logical) Use default package schema instead of a custom schema
  defined with an IDatasetForm plugin. Default: `FALSE`

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

## Details

By default the help and success slots are dropped, and only the result
slot is returned. You can request raw json with `as = 'json'` then parse
yourself to get the help slot.

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

# create a package
(res <- package_create("purposeful55"))

# show package
## From the output of package_create
package_show(res)
## Or, from the ID
package_show(res$id)

# get data back in different formats
package_show(res$id, as = "json")
package_show(res$id, as = "table")

# use default schema or not
package_show(res$id, TRUE)
} # }
```
