# Datastore write helpers (CKAN 2.12+ parameters from the start)

Wrappers for `datastore_upsert`, `datastore_delete`,
`datastore_records_delete`, `datastore_info`,
`datastore_function_create`, `datastore_function_delete`, and
`datastore_run_triggers`.
[`ds_search()`](https://docs.ropensci.org/ckanr/reference/ds_search.md)
and
[`ds_create()`](https://docs.ropensci.org/ckanr/reference/ds_create.md)
cover read/create; these helpers complete the write/info coverage with
the CKAN 2.12 parameters (`include_records`, `include_meta`,
`include_fields_schema`, `argmode`) available from the start. See
<https://docs.ckan.org/en/2.12/maintaining/datastore.html#the-data-api>.

## Usage

``` r
ds_upsert(
  resource_id,
  records = NULL,
  method = "upsert",
  force = FALSE,
  include_records = FALSE,
  calculate_record_count = "background",
  dry_run = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

ds_delete(
  resource_id = NULL,
  filters = NULL,
  force = FALSE,
  include_deleted_records = FALSE,
  calculate_record_count = "background",
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

ds_records_delete(
  resource_id,
  filters,
  force = FALSE,
  include_deleted_records = FALSE,
  calculate_record_count = "background",
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

ds_info(
  resource_id,
  include_meta = TRUE,
  include_fields_schema = TRUE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

ds_function_create(
  name,
  rettype = "trigger",
  definition,
  or_replace = FALSE,
  argmode = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

ds_function_delete(
  name,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

ds_run_triggers(
  resource_id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- resource_id:

  (character) Resource id that the data is stored against.

- records:

  (list\|data.frame) The data, e.g. `list(list(a = 1, b = "xyz"))`.

- method:

  (character) Upsert method: `"upsert"` (default), `"insert"`, or
  `"update"`. `upsert`/`update` require a unique key or `_id` field.

- force:

  (logical) Edit a read-only table. Default: `FALSE`.

- include_records:

  (logical) If `TRUE`, return the actual affected rows in the response
  (CKAN 2.12+). Default: `FALSE`.

- calculate_record_count:

  (logical\|character) `FALSE` skips the count update, `TRUE` updates
  immediately, `"background"` schedules a background job (default).

- dry_run:

  (logical) Abort the transaction instead of committing, e.g. to check
  validation errors. Default: `FALSE`.

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

- filters:

  (list\|character) Matching conditions to select, e.g.
  `list(name = "fred")`. CKAN 2.12+ accepts advanced syntax (ranges,
  nested AND/OR); the argument passes through untouched.

- include_deleted_records:

  (logical) If `TRUE`, return the full values of deleted records (CKAN
  2.12+). Default: `FALSE`.

- include_meta:

  (logical) For `ds_info()`, return table size, index size, row count
  and aliases (CKAN 2.12+). Default: `TRUE`.

- include_fields_schema:

  (logical) For `ds_info()`, return per-field index/unique/notnull
  status (CKAN 2.12+). Default: `TRUE`.

- name:

  (character) Trigger function name for `ds_function_create()` /
  `ds_function_delete()`.

- rettype:

  (character) Set to `"trigger"` (only trigger functions may be created
  at this time).

- definition:

  (character) PL/pgSQL function body for the trigger.

- or_replace:

  (logical) Replace the function if it exists. Default: `FALSE`.

- argmode:

  (character) Argument mode for custom DataStore SQL function
  parameters, e.g. `"in"`, `"inout"`, `"out"` (CKAN 2.12+,
  <https://github.com/ckan/ckan/pull/8279>). Optional.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))
ds_info(resource_id = "my-resource-id")
ds_upsert(resource_id = "my-resource-id",
  records = list(list(a = 1, b = "xyz")), method = "upsert")
} # }
```
