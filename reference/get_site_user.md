# Show the CKAN site user.

Return the CKAN site user. The site user is a special internal user that
the web interface and background jobs use for internal operations. You
must be a sysadmin to call this endpoint. See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.get_site_user>
for the official API contract.

## Usage

``` r
get_site_user(
  defer_commit = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- defer_commit:

  (logical) By default (`FALSE`), `get_site_user` commits and cleans up
  the current transaction. If `TRUE`, the caller is responsible for
  committing the transaction after the call. Leaving open connections
  can cause CLI commands to hang (optional).

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

## Value

A `ckan_user` object. With `as = "table"`, a data.frame; with
`as = "json"`, the raw JSON response.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.get_site_user

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

get_site_user()
} # }
```
