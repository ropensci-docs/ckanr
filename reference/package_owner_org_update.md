# Move a dataset to another organization

Move a dataset to another organization

## Usage

``` r
package_owner_org_update(
  id,
  organization_id,
  url = get_default_url(),
  key = get_default_key(),
  ...
)
```

## Arguments

- id:

  (character or `ckan_package`) Dataset identifier.

- organization_id:

  (character or `ckan_organization`) Owning organization identifier.

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
package_owner_org_update("dataset-id", organization_id = "target-org")
} # }
```
