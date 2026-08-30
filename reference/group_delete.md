# Delete a group

Delete a group

## Usage

``` r
group_delete(id, url = get_default_url(), key = get_default_key(), ...)
```

## Arguments

- id:

  (character) The id of the group. Required.

- url:

  Base url to use. Default: https://data.ontario.ca See also
  [`ckanr_setup()`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url()`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md)

- key:

  A privileged CKAN API key, Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- ...:

  Curl args passed on to
  [crul::verb-POST](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# create a group
(res <- group_create("lions", description = "A group about lions"))

# show the group
group_show(res$id)

# delete the group
group_delete(res)
## or with it's id
# group_delete(res$id)
} # }
```
