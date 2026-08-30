# Follower counts for CKAN objects

Report follower totals for datasets, groups, or users.

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
```

## Arguments

- id:

  (character or `ckan_*`) Identifier for the object to inspect. For
  datasets pass an id/slug or `ckan_package`, for groups pass the
  corresponding identifier or `ckan_group`, and for users pass a
  username or `ckan_user`.

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

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = "my-key")
dataset_follower_count("my-dataset")
group_follower_count("my-group")
user_follower_count("demo-user")
} # }
```
