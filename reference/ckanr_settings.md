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
`ckanr_setup` sets your production and test settings. `get_test_*` gets
each of those settings. `test_behaviour` states whether the CKANR test
suite skips ("SKIP") or fails ("FAIL") writing tests when the configured
test CKAN settings do not work.

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
