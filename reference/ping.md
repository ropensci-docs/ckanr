# Ping a CKAN server to test if it is up or down.

Ping a CKAN server to test if it is up or down.

## Usage

``` r
ping(url = get_default_url(), key = get_default_key(), as = "logical", ...)
```

## Arguments

- url:

  Base URL to use. Default: https://demo.ckan.org/. See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key. Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- as:

  (character) One of "logical" (default) or "json". With
  `as = "logical"` failures return `FALSE`. With `as = "json"` failures
  signal an error instead of returning a non-JSON logical.

- ...:

  Extra curl arguments. The function passes them to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)

## Examples

``` r
if (FALSE) { # \dontrun{
ping()
ping(as = "json")
} # }
```
