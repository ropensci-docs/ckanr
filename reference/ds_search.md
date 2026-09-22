# Datastore - search or get a dataset from CKAN datastore

Datastore - search or get a dataset from CKAN datastore

## Usage

``` r
ds_search(
  resource_id = NULL,
  filters = NULL,
  q = NULL,
  plain = NULL,
  language = NULL,
  fields = NULL,
  offset = NULL,
  limit = NULL,
  sort = NULL,
  include_next_page = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- resource_id:

  (character) id or alias of the resource to be searched against

- filters:

  (character) Matching conditions to select, for example
  `{"key1": "a", "key2": "b"}` (optional)

- q:

  (character) full text query (optional)

- plain:

  (character) treat as plain text query (optional, default: `TRUE`)

- language:

  (character) language of the full text query (optional, default:
  english)

- fields:

  (character) fields to return (optional, default: all fields in
  original order)

- offset:

  (numeric) Where to start getting activity items from (optional,
  default: 0)

- limit:

  (numeric) The maximum number of activities to return (optional,
  default: 100)

- sort:

  Field to sort on. You can specify ascending, for example score desc,
  or descending, for example score asc. You can sort by two fields, for
  example score desc, price asc. You can sort by a function, for example
  sum(x_f, y_f) desc, which sorts by the sum of x_f and y_f in
  descending order. (optional)

- include_next_page:

  (logical) If `TRUE`, CKAN 2.12+ returns a `next_page` value with
  filters for fast keyset pagination. Ignored unless records are sorted
  by the `_id` field (optional, default: `FALSE`). See
  <https://docs.ckan.org/en/2.12/maintaining/datastore.html#search-pagination>.

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

## Details

From the help for this method "The datastore_search action allows you to
search data in a resource." If a DataStore resource belongs to a private
CKAN resource, you can read it only with access to that resource. You
must send the appropriate authorization.

CKAN 2.12+ `filters` accept advanced syntax: range operations (`lt`,
`lte`, `gt`, `gte`, `eq`), lists mixing values and ranges, nested AND/OR
via lists, and `$or` groups (see
<https://docs.ckan.org/en/2.12/maintaining/datastore.html#filters>). The
`filters` argument passes through untouched, so both classic
(`{"key1": "a"}`) and advanced filters work. For large tables prefer
keyset pagination (`include_next_page = TRUE` with `sort = "_id asc"`)
over large `offset` values.

If you set `plain=FALSE`, you enable the entire PostgreSQL *full text
search query language*. You can find a listing of all available
resources at the alias *table_metadata* full text search query language:
http://www.postgresql.org/docs/9.1/static/datatype-textsearch.html#DATATYPE-TSQUERY

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://data.gov.au/")
rid <- "eef6a84b-ad44-446f-9cf9-fb5d135e3123"

ds_search(resource_id = rid)
ds_search(resource_id = rid, as = "table")
ds_search(resource_id = rid, as = "json")

ds_search(resource_id = rid, limit = 1, as = "table")
ds_search(resource_id = rid, q = "S*")

# Return selected fields
ds_search(
  resource_id = rid,
  fields = c("name", "amount"),
  as = "table"
)

# Match more than one field. CKAN applies the conditions together.
ds_search(
  resource_id = rid,
  filters = list(status = "active", category = "water"),
  fields = c("name", "status", "category"),
  as = "table"
)
} # }
```
