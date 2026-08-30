# API token helpers

Inspect, create, and revoke API tokens for a user.

## Usage

``` r
api_token_list(
  user_id = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

api_token_create(
  user,
  name,
  extra_fields = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

api_token_revoke(
  token = NULL,
  jti = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- user_id:

  (character) User identifier to filter tokens.

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

- user:

  (character) Name or id of the token owner.

- name:

  (character) Friendly token name.

- extra_fields:

  (list) Optional named list of additional fields accepted by CKAN or
  extensions.

- token:

  (character) Encoded API token value.

- jti:

  (character) Token identifier (overrides `token` when provided).

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = "my-ckan-key")
api_token_list(user_id = "my-user-id")
} # }
```
