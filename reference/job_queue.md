# Background job helpers

Manage CKAN's RQ/Redis job queue (requires sysadmin access).

## Usage

``` r
job_list(
  queues = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

job_show(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

job_clear(
  queues = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

job_cancel(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- queues:

  (character) Queue names to target.

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

- id:

  (character) Job identifier.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = "my-ckan-key")
job_list()
} # }
```
