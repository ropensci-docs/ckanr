# Configure default CKAN settings

Configure default CKAN settings

## Usage

``` r
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = NULL,
  test_url = NULL,
  test_key = NULL,
  test_did = NULL,
  test_rid = NULL,
  test_gid = NULL,
  test_oid = NULL,
  test_behaviour = NULL,
  proxy = NULL
)
```

## Arguments

- url:

  A CKAN URL (optional), default: https://demo.ckan.org/

- key:

  A CKAN API key (optional, character)

- test_url:

  (optional, character) A valid CKAN URL for testing purposes

- test_key:

  (optional, character) A valid CKAN API key privileged to create
  datasets at `test_url`

- test_did:

  (optional, character) A valid CKAN dataset ID, existing at `test_url`

- test_rid:

  (optional, character) A valid CKAN resource ID, attached to `did`

- test_gid:

  (optional, character) A valid CKAN group name at `test_url`

- test_oid:

  (optional, character) A valid CKAN organization name at `test_url`

- test_behaviour:

  (optional, character) Whether to fail ("FAIL") or skip ("SKIP")
  writing tests in case of problems with the configured test CKAN.

- proxy:

  an object of class `request` from a call to
  [`crul::proxy()`](https://docs.ropensci.org/crul/reference/proxies.html)

## Details

`ckanr_setup()` sets CKAN connection details. If you do not specify a
URL or key, the functions use the default URL and API key.

ckanr automated tests require a valid CKAN URL, a privileged API key for
that URL, and the IDs of an existing dataset and an existing resource.

The writing tests (create, update, delete) can fail for two reasons. One
reason is failures in ckanr code. The tests aim to detect these
failures. The other reason is failures in the configured CKAN. These
failures are not necessarily a problem with ckanr code, but they stop
the tests from proving otherwise.

If you set `test_behaviour` to `"SKIP"`, writing tests skip when the
configured test CKAN fails. This helps you test the other functions even
when you have no write access to a CKAN instance.

If you set `test_behaviour` to `"FAIL"`, the tester finds problems with
both the configured test CKAN and the writing functions.

## Examples

``` r
# CKAN users without admin/editor privileges could run:
ckanr_setup(url = "https://demo.ckan.org/")

# Privileged CKAN editor/admin users can run:
ckanr_setup(url = "https://demo.ckan.org/", key = "some-CKAN-API-key")

# ckanR developers/testers can either use the Codespaces/devcontainer test suite
# which automatically sets up all test credentials, or run:
ckanr_setup(
  url = "https://demo.ckan.org/", key = "some-CKAN-API-key",
  test_url = "http://test-ckan.gov/", test_key = "test-ckan-API-key",
  test_did = "test-ckan-dataset-id", test_rid = "test-ckan-resource-id",
  test_gid = "test-group-name", test_oid = "test-organzation-name",
  test_behaviour = "FAIL"
)

# Not specifying the default CKAN URL will reset the CKAN URL to its default
# "https://demo.ckan.org/":
ckanr_setup()

# set a proxy
ckanr_setup(proxy = crul::proxy("64.251.21.73:8080"))
ckanr_settings()
#> <ckanr settings>
#>   Base URL:  https://demo.ckan.org/ 
#>   API key:  show with ckanr::get_default_key() 
#>   Test CKAN URL: http://test-ckan.gov/ 
#>   Test CKAN API key: show with ckanr::get_test_key() 
#>   Test CKAN dataset ID: test-ckan-dataset-id 
#>   Test CKAN resource ID: test-ckan-resource-id 
#>   Test CKAN group ID: test-group-name 
#>   Test CKAN organization ID: test-organzation-name 
#>   Test behaviour if CKAN offline: FAIL 
#>   Proxy: 
## run without setting proxy to reset to no proxy
ckanr_setup()
ckanr_settings()
#> <ckanr settings>
#>   Base URL:  https://demo.ckan.org/ 
#>   API key:  show with ckanr::get_default_key() 
#>   Test CKAN URL: http://test-ckan.gov/ 
#>   Test CKAN API key: show with ckanr::get_test_key() 
#>   Test CKAN dataset ID: test-ckan-dataset-id 
#>   Test CKAN resource ID: test-ckan-resource-id 
#>   Test CKAN group ID: test-group-name 
#>   Test CKAN organization ID: test-organzation-name 
#>   Test behaviour if CKAN offline: FAIL 
#>   Proxy:
```
