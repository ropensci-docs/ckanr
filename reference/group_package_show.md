# Show the datasets of a group.

Return the datasets (packages) that belong to a group. See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.group_package_show>
for the official API contract.

## Usage

``` r
group_package_show(
  id,
  limit = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character or `ckan_group`) The id or name of the group, or a
  `ckan_group` object.

- limit:

  (numeric) The maximum number of datasets to return (optional).

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

## Value

A list of `ckan_package` objects. With `as = "table"`, a data.frame;
with `as = "json"`, the raw JSON response.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.get.group_package_show

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

res <- group_list()
group_package_show(res[[1]]$name)
group_package_show(res[[1]], limit = 5, as = "table")
} # }
```
