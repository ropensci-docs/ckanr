# Datastore - search or get a dataset from CKAN datastore

Datastore - search or get a dataset from CKAN datastore

## Usage

``` r
ds_search_sql(
  sql,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- sql:

  (character) A single SQL select statement. (required)

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
ckanr_setup(url = "https://data.gov.au/")
sql <- 'SELECT * from "eef6a84b-ad44-446f-9cf9-fb5d135e3123" LIMIT 2'
ds_search_sql(sql, as = "table")
sql2 <- 'SELECT "Dog","TRI" from "eef6a84b-ad44-446f-9cf9-fb5d135e3123" LIMIT 2'
ds_search_sql(sql2, as = "table")
} # }
```
