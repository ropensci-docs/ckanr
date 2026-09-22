# Connect to CKAN with dplyr

Use `src_ckan` to connect to an existing CKAN instance. Use `tbl` to
connect to tables in that CKAN through the DataStore Data API.

## Usage

``` r
src_ckan(url, key = get_default_key())
```

## Arguments

- url:

  The url of the CKAN instance

- key:

  An optional CKAN API key

## Examples

``` r
if (FALSE) { # \dontrun{
library("dplyr")

# To connect to a CKAN instance first create a src:
my_ckan <- src_ckan("http://demo.ckan.org")

# The primary dbplyr interface uses the DBI connection directly
con <- my_ckan$con
dplyr::tbl(con, "resource-id") |>
  dplyr::filter(status == "active") |>
  dplyr::collect()

# List all tables in the CKAN instance
DBI::dbListTables(con)

# `src_ckan()` remains available for existing code
my_tbl <- dplyr::tbl(
  my_ckan,
  name = "44d7de5f-7029-4f3a-a812-d7a70895da7d"
)

# You can use the dplyr verbs with my_tbl. For example:
dplyr::filter(my_tbl, GABARITO == "C")

# The DataStore interface is read-only. `collect()` retrieves the result
# from CKAN. Filter or limit large tables before collecting them.
} # }
```
