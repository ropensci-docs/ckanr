# Remove a membership via member\_\* endpoints

Remove a membership via member\_\* endpoints

## Usage

``` r
member_delete(
  id,
  object,
  object_type,
  url = get_default_url(),
  key = get_default_key(),
  ...
)
```

## Arguments

- id:

  (character, `ckan_group`, or `ckan_organization`) Identifier for the
  container.

- object:

  (character) The object to add (dataset id, user name, etc.).

- object_type:

  (character) Type of object being added (`"user"`, `"package"`, ...).

- url:

  Base url to use. Default: https://demo.ckan.org/ See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key, Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- ...:

  Curl args passed on to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)
