# File management

These helpers wrap CKAN 2.12 `file_*` endpoints. Files are first-class
entities in CKAN 2.12 (see
<https://docs.ckan.org/en/2.12/api/#ckan-logic-action-file> and
<https://github.com/ckan/ckan/pull/9026>). The target CKAN instance must
run CKAN 2.12 or later; each wrapper calls `ensure_action_available()`
so it fails clearly on older instances.

## Usage

``` r
file_create(
  upload,
  name = NULL,
  storage = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

file_register(
  location = NULL,
  storage = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

file_show(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

file_delete(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

file_rename(
  id,
  name,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

file_pin(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

file_unpin(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

file_ownership_transfer(
  id,
  owner_id,
  owner_type,
  force = FALSE,
  pin = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

file_owner_scan(
  owner_id,
  owner_type,
  start = NULL,
  rows = NULL,
  sort = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- upload:

  (character) Local path of the file to upload for `file_create()`.
  Required.

- name:

  (character) Human-readable file name. For `file_create()`, defaults to
  the uploaded file's name when `upload` is a local path.

- storage:

  (character) Name of the storage handling the upload. Defaults to the
  configured `default` storage.

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

- location:

  (character) Location of the file in the storage for `file_register()`.
  Required.

- id:

  (character or `ckan_file`) File identifier.

- owner_id:

  (character) ID of the new owner for `file_ownership_transfer()` and
  `file_owner_scan()`.

- owner_type:

  (character) Type of the new owner (for example `"package"`, `"user"`,
  `"group"`, `"organization"`).

- force:

  (logical) For `file_ownership_transfer()`, move the file even if it is
  pinned. Default: `FALSE`.

- pin:

  (logical) For `file_ownership_transfer()`, pin the file after transfer
  to stop future transfers. Default: `FALSE`.

- start:

  (numeric) Index of the first row for `file_owner_scan()`.

- rows:

  (numeric) Number of rows to return for `file_owner_scan()`.

- sort:

  (character) `File` column used for sorting in `file_owner_scan()`.
  Optional; when `NULL` the server default (`"name"`) applies.

## Details

By default only sysadmins may call `file_create()`; see
`ckan.files.authenticated_uploads.allow` in the CKAN docs for granting
access to registered users.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))
f <- file_create(upload = "path/to/file.csv")
file_show(f$id)
} # }
```
