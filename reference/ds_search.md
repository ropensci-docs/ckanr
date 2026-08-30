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

  (character) matching conditions to select, e.g
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

  Field to sort on. You can specify ascending (e.g., score desc) or
  descending (e.g., score asc), sort by two fields (e.g., score desc,
  price asc), or sort by a function (e.g., sum(x_f, y_f) desc, which
  sorts by the sum of x_f and y_f in a descending order). (optional)

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

From the help for this method "The datastore_search action allows you to
search data in a resource. DataStore resources that belong to private
CKAN resource can only be read by you if you have access to the CKAN
resource and send the appropriate authorization."

Setting `plain=FALSE` enables the entire PostgreSQL *full text search
query language*. A listing of all available resources can be found at
the alias *table_metadata* full text search query language:
http://www.postgresql.org/docs/9.1/static/datatype-textsearch.html#DATATYPE-TSQUERY

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://data.nhm.ac.uk/")

ds_search(resource_id = "8f0784a6-82dd-44e7-b105-6194e046eb8d")
ds_search(
  resource_id = "8f0784a6-82dd-44e7-b105-6194e046eb8d",
  as = "table"
)
ds_search(
  resource_id = "8f0784a6-82dd-44e7-b105-6194e046eb8d",
  as = "json"
)

ds_search(
  resource_id = "8f0784a6-82dd-44e7-b105-6194e046eb8d", limit = 1,
  as = "table"
)
ds_search(resource_id = "8f0784a6-82dd-44e7-b105-6194e046eb8d", q = "a*")
} # }
```
