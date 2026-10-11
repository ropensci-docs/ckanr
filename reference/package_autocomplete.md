# Autocomplete dataset names.

Return a list of datasets (packages) with names or titles that contain a
query string. See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.package_autocomplete>
for the official API contract.

## Usage

``` r
package_autocomplete(
  q,
  limit = 10,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- q:

  (character) Partial string to search for. The function returns entries
  whose name or title contains this string. (required)

- limit:

  (numeric) The maximum number of datasets to return. Default: 10
  (optional)

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

## Value

A list of dataset dictionaries. Each dictionary has at least the keys
`name` and `title`. With `as = "table"`, a data.frame; with
`as = "json"`, the raw JSON response.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.package_autocomplete

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

package_autocomplete(q = "spending")
package_autocomplete(q = "spending", limit = 5, as = "table")
} # }
```
