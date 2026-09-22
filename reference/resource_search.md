# Search for resources.

Search for resources.

## Usage

``` r
resource_search(
  q,
  sort = NULL,
  offset = NULL,
  limit = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- q:

  Query terms. The value is a string of the form `field:term` or a
  vector or list of strings. Each string uses the same form. `field` is
  a field or extra field on the Resource domain object. If `field` is
  hash, the function matches the `term` as a prefix of the Resource.hash
  field. If `field` is an extra field, the function matches against the
  extra fields stored against the Resource.

- sort:

  Field to sort on. You can specify ascending (for example, score desc)
  or descending (for example, score asc). You can sort by two fields
  (for example, score desc, price asc). You can sort by a function (for
  example, sum(x_f, y_f) desc). The function sorts by the sum of x_f and
  y_f in descending order.

- offset:

  Record to start at. The default is the beginning.

- limit:

  Number of records to return.

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
resource_search(q = "name:data")
resource_search(q = "name:data", as = "json")
resource_search(q = "name:data", as = "table")
resource_search(q = "name:data", limit = 2, as = "table")
resource_search(q = c("description:encoded", "name:No.2"), url = "demo.ckan.org")
} # }
```
