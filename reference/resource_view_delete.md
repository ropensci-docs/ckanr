# Delete a resource view

Delete a resource view

## Usage

``` r
resource_view_delete(id, url = get_default_url(), key = get_default_key(), ...)
```

## Arguments

- id:

  (character or `ckan_resource_view`) View identifier.

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

## Value

(bool) The result of the deletion, TRUE if the resource view was deleted
sucessfully, FALSE if not.
