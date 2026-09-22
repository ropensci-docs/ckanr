# Follow and unfollow CKAN datasets or groups

Create or remove follower relationships for a CKAN object. You must
authenticate as a user with an API key. The key represents the follower.

## Usage

``` r
dataset_follow(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

dataset_unfollow(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

dataset_am_following(id, url = get_default_url(), key = get_default_key(), ...)

group_follow(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

group_unfollow(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

group_am_following(id, url = get_default_url(), key = get_default_key(), ...)
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
dataset_follow("my-dataset")
dataset_am_following("my-dataset")
dataset_unfollow("my-dataset")
} # }
```
