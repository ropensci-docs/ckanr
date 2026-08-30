# Delete a dataset relationship

Delete a dataset relationship

## Usage

``` r
package_relationship_delete(
  subject,
  object,
  relationship_type,
  url = get_default_url(),
  key = get_default_key(),
  ...
)
```

## Arguments

- subject:

  (character or `ckan_package`) Dataset acting as the subject in the
  relationship.

- object:

  (character or `ckan_package`) Dataset acting as the object in the
  relationship.

- relationship_type:

  (character) Relationship type (`"depends_on"`, `"derives_from"`,
  etc.).

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
