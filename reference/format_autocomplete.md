# Autocomplete resource formats.

Return a list of resource formats whose names contain a query string.
See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.format_autocomplete>
for the official API contract.

## Usage

``` r
format_autocomplete(
  q,
  limit = 5,
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

  (numeric) The maximum number of resource formats to return. Default: 5
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

A character vector of matching format names. With `as = "table"`, a
data.frame; with `as = "json"`, the raw JSON response.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.format_autocomplete

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

format_autocomplete(q = "csv")
} # }
```
