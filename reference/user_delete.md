# Delete a user.

Delete a user.

## Usage

``` r
user_delete(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) the id of the new user (required)

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

## Value

(logical) TRUE when the user is successfully deleted

## References

http://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.delete.user_delete

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(
  url = "https://data-demo.dpaw.wa.gov.au",
  key = "824e7c50-9577-4bfa-bf32-246ebed1a8a2"
)

# create a user
res <- user_delete(
  name = "stacy", email = "stacy@aaaaa.com",
  password = "helloworld"
)

# then, delete a user
user_delete(id = "stacy")
} # }
```
