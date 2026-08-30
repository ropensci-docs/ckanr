# List groups the current user can edit

List groups the current user can edit

## Usage

``` r
group_list_authz(
  type = "group",
  groups = NULL,
  all_fields = FALSE,
  include_dataset_count = TRUE,
  include_extras = FALSE,
  include_tags = FALSE,
  include_groups = FALSE,
  include_users = FALSE,
  available_only = FALSE,
  am_member = FALSE,
  offset = NULL,
  limit = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- type:

  (character) Group type, defaults to `"group"`.

- groups:

  (character vector) Optional list of group names to filter.

- all_fields:

  (logical) Return full group dictionaries.

- include_dataset_count, include_extras, include_tags, include_groups,
  include_users:

  (logical) Include additional metadata when `all_fields = TRUE`.

- available_only:

  (logical) Remove groups already associated to the context dataset.

- am_member:

  (logical) Only return memberships for the current user.

- offset:

  (numeric) Where to start getting activity items from (optional,
  default: 0)

- limit:

  (numeric) The maximum number of activities to return (optional,
  default: 31)

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
