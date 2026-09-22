# Background job helpers

Manage the RQ/Redis job queue of CKAN. You must have sysadmin access.

## Usage

``` r
job_list(
  queues = NULL,
  limit = NULL,
  ids_only = FALSE,
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

- limit:

  (numeric) Maximum number of jobs to return. CKAN 2.12 returns 200 jobs
  by default; use `limit` or the `ckan.jobs.default_list_limit` config
  option to change it (<https://github.com/ckan/ckan/pull/8070>).

- ids_only:

  (logical) Return only job IDs. Default: `FALSE`.

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

- id:

  (character) Job identifier.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = "my-ckan-key")
job_list()
} # }
```
