# Delete a dataset collaborator

Delete a dataset collaborator

## Usage

``` r
package_collaborator_delete(
  id,
  user_id,
  url = get_default_url(),
  key = get_default_key(),
  ...
)
```

## Arguments

- id:

  (character or `ckan_package`) Dataset identifier or object.

- user_id:

  (character or `ckan_user`) User identifier or object.

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

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = "my-key")
package_collaborator_delete("my-dataset", "new-user")
} # }
```
