# Connect to CKAN with dplyr

Use `src_ckan` to connect to an existing CKAN instance and `tbl` to
connect to tables within that CKAN based on the DataStore Data API.

## Usage

``` r
src_ckan(url)
```

## Arguments

- url, :

  the url of the CKAN instance

## Examples

``` r
if (FALSE) { # \dontrun{
library("dplyr")

# To connect to a CKAN instance first create a src:
my_ckan <- src_ckan("http://demo.ckan.org")

# List all tables in the CKAN instance
db_list_tables(my_ckan$con)

# Then reference a tbl within that src
my_tbl <- tbl(src = my_ckan, name = "44d7de5f-7029-4f3a-a812-d7a70895da7d")

# You can use the dplyr verbs with my_tbl. For example:
dplyr::filter(my_tbl, GABARITO == "C")
} # }
```
