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

  Query terms. It is a string of the form `field:term` or a vector/list
  of strings, each of the same form. Within each string, `field` is a
  field or extra field on the Resource domain object. If `field` is
  hash, then an attempt is made to match the `term` as a *prefix* of the
  Resource.hash field. If `field` is an extra field, then an attempt is
  made to match against the extra fields stored against the Resource.

- sort:

  Field to sort on. You can specify ascending (e.g., score desc) or
  descending (e.g., score asc), sort by two fields (e.g., score desc,
  price asc), or sort by a function (e.g., sum(x_f, y_f) desc, which
  sorts by the sum of x_f and y_f in a descending order).

- offset:

  Record to start at, default to beginning.

- limit:

  Number of records to return.

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
resource_search(q = "name:data")
resource_search(q = "name:data", as = "json")
resource_search(q = "name:data", as = "table")
resource_search(q = "name:data", limit = 2, as = "table")
resource_search(q = c("description:encoded", "name:No.2"), url = "demo.ckan.org")
} # }
```
