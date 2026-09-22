# Move a dataset to another organization

On CKAN 2.12 `package_owner_org_update` may report success without
moving the dataset; when the verification shows the dataset is still
owned by the previous organization, the function falls back to
[`package_patch()`](https://docs.ropensci.org/ckanr/reference/package_patch.md)
with `owner_org`, which moves the dataset reliably on all supported
versions.

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

  Base URL to use. Default: https://demo.ckan.org/. See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key. Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- ...:

  Extra curl arguments. The function passes them to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)

## Examples

``` r
if (FALSE) { # \dontrun{
package_owner_org_update("dataset-id", organization_id = "target-org")
} # }
```
