# Bulk update dataset visibility.

Make a list of datasets private, public, or deleted in a single call.
You must be authorized to edit the datasets (for example, an editor or
admin of the owning organization). See the official API contracts:
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.update.bulk_update_private>,
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.update.bulk_update_public>,
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.update.bulk_update_delete>.

## Usage

``` r
bulk_update_private(
  datasets,
  org_id,
  url = get_default_url(),
  key = get_default_key(),
  ...
)

bulk_update_public(
  datasets,
  org_id,
  url = get_default_url(),
  key = get_default_key(),
  ...
)

bulk_update_delete(
  datasets,
  org_id,
  url = get_default_url(),
  key = get_default_key(),
  ...
)
```

## Arguments

- datasets:

  (character or list) The datasets to update: a character vector of
  dataset ids or names, a list of `ckan_package` objects, or a list with
  an `id` entry per dataset.

- org_id:

  (character or `ckan_organization`) The id or name of the owning
  organization, or a `ckan_organization` object.

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

## Value

(logical) `TRUE` when CKAN applies the bulk update successfully.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.update.bulk_update_private

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

org <- organization_create("bulk-org")
ds1 <- package_create("bulk-dataset-1", owner_org = org$id)
ds2 <- package_create("bulk-dataset-2", owner_org = org$id)

bulk_update_private(c(ds1$id, ds2$id), org_id = org$id)
bulk_update_public(c(ds1$id, ds2$id), org_id = org$id)
bulk_update_delete(c(ds1$id, ds2$id), org_id = org$id)
} # }
```
