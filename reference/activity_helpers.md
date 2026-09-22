# Activity stream helpers

These helpers wrap CKAN's `ckanext.activity` endpoints. The target CKAN
instance must enable the `activity` core plugin.

## Usage

``` r
group_activity_list(
  id,
  offset = 0,
  limit = 31,
  include_hidden_activity = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

organization_activity_list(
  id,
  offset = 0,
  limit = 31,
  include_hidden_activity = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

recently_changed_packages_activity_list(
  offset = 0,
  limit = 31,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

dashboard_new_activities_count(
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

dashboard_mark_activities_old(
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

activity_show(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

activity_data_show(
  id,
  object_type,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

activity_diff(
  id,
  object_type,
  diff_type = "unified",
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

activity_create(
  user_id,
  object_id,
  activity_type,
  data = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

send_email_notifications(
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) Identifier of the target object (group, organization,
  activity, etc.).

- offset:

  (numeric) Where to start getting activity items from (optional,
  default: 0)

- limit:

  (numeric) The maximum number of activities to return (optional,
  default: 31)

- include_hidden_activity:

  (logical) If `TRUE`, include private activity entries. You must have
  sysadmin rights.

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

- object_type:

  (character) Domain object that the activity affects, for example
  "package", "resource", or a plugin-defined type.

- diff_type:

  (character) Diff format that `activity_diff()` returns, typically
  "unified".

- user_id:

  (character) User identifier associated with a custom
  `activity_create()` entry.

- object_id:

  (character) Target object identifier for `activity_create()`.

- activity_type:

  (character) Activity type string to emit via `activity_create()`.

- data:

  (list\|character) Optional structured payload that describes the
  activity body. The function encodes lists as JSON automatically.
