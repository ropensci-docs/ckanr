# Get or set ckanr CKAN settings

Get or set ckanr CKAN settings

## Usage

``` r
ckanr_settings()

get_default_url()

get_default_key()

get_test_url()

get_test_key()

get_test_did()

get_test_rid()

get_test_gid()

get_test_oid()

get_test_behaviour()
```

## Value

`ckanr_settings` prints your base url, API key (if used), and optional
test server settings (URL, API key, a dataset ID and a resource ID).
`ckanr_setup` sets your production and test settings, while `get_test_*`
get each of those respective settings. `test_behaviour` indicates
whether the CKANR test suite will skip ("SKIP") or fail ("FAIL") writing
tests in case the configured test CKAN settings don't work.

## See also

[`ckanr_setup()`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md),
`get_default_url()`, `get_default_key()`, `get_test_url()`,
`get_test_key()`, `get_test_did()`, `get_test_rid()`, `get_test_gid()`,
`get_test_oid`, `get_test_behaviour`

## Examples

``` r
ckanr_settings()
#> <ckanr settings>
#>   Base URL:  https://demo.ckan.org/ 
#>   API key:  show with ckanr::get_default_key() 
#>   Test CKAN URL:  
#>   Test CKAN API key: show with ckanr::get_test_key() 
#>   Test CKAN dataset ID:  
#>   Test CKAN resource ID:  
#>   Test CKAN group ID:  
#>   Test CKAN organization ID:  
#>   Test behaviour if CKAN offline: SKIP 
#>   Proxy:
```
