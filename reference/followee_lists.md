# Followee lists for CKAN users

The function returns the objects that a user follows.

See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.organization_followee_list>
for the official API contract.

## Usage

``` r
followee_list(
  id,
  q = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

user_followee_list(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

dataset_followee_list(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

group_followee_list(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

organization_followee_list(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character or `ckan_user`) User identifier.

- q:

  (character) Optional prefix filter for `followee_list()`.

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
ckanr_setup(url = "https://demo.ckan.org/", key = "my-key")
followee_list("demo-user", q = "ckan")
dataset_followee_list("demo-user")
organization_followee_list("demo-user")
} # }
```
