# Follower counts for CKAN objects

Report follower totals for datasets, groups, organizations, or users.

See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.organization_follower_count>
for the official API contract.

## Usage

``` r
dataset_follower_count(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

group_follower_count(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

user_follower_count(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

organization_follower_count(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character or `ckan_*`) Identifier for the object to inspect. For
  datasets, pass an id/slug or `ckan_package`. For groups, pass the
  corresponding identifier or `ckan_group`. For organizations, pass the
  corresponding identifier or `ckan_organization`. For users, pass a
  username or `ckan_user`.

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
dataset_follower_count("my-dataset")
group_follower_count("my-group")
organization_follower_count("my-organization")
user_follower_count("demo-user")
} # }
```
