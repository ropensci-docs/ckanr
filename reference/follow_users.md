# Follow or unfollow users

Manage user-to-user follower relationships.

## Usage

``` r
follow_user(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

unfollow_user(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

am_following_user(id, url = get_default_url(), key = get_default_key(), ...)
```

## Arguments

- id:

  (character or `ckan_user`) The user to follow or inspect.

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
follow_user("demo-user")
am_following_user("demo-user")
unfollow_user("demo-user")
} # }
```
