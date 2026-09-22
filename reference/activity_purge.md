# Activity purge helpers (CKAN 2.12+)

These helpers wrap the CKAN 2.12 activity purge feature
(<https://github.com/ckan/ckan/pull/8189>). You must have sysadmin
rights and the target instance must enable the `activity` plugin with
CKAN 2.12 or later. Each wrapper calls `ensure_action_available()` so it
fails clearly on older instances.

## Usage

``` r
activity_delete(
  id = NULL,
  start_date = NULL,
  end_date = NULL,
  offset_days = NULL,
  keep = NULL,
  batch_size = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

activity_delete_all(
  batch_size = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

activity_delete_counts(
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) Activity identifier to delete via `activity_delete()`.
  Alternatively provide `start_date` + `end_date` or `offset_days`.

- start_date:

  (character) Start of the deletion range (ISO 8601).

- end_date:

  (character) End of the deletion range (ISO 8601).

- offset_days:

  (numeric) Delete activities older than this many days.

- keep:

  (numeric) Optional. Keep this many most recent activities per item;
  delete only older ones in the range.

- batch_size:

  (numeric) Optional batch size for large tables.

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

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))
activity_delete_counts()
activity_delete(offset_days = 365)
} # }
```
