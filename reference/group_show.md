# Show a group

Show a group

## Usage

``` r
group_show(
  id,
  include_datasets = TRUE,
  include_users = TRUE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) Package identifier.

- include_datasets:

  (logical) Include a list of the group's datasets. Default: `TRUE`

- include_users:

  (logical) Include the group's users. CKAN 2.12 changed the server
  default to `FALSE` regardless of the `ckan.auth.public_user_details`
  setting (<https://github.com/ckan/ckan/pull/9232>); ckanr defaults to
  `TRUE` to preserve the historical behavior. The parameter is accepted
  on all supported CKAN versions (2.9, 2.10, 2.11, 2.12).

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

## Details

By default the function drops the help and success slots. It returns
only the result slot. If you want raw json, request `as = 'json'`. Then
you parse the result yourself to get the help slot.

## Examples

``` r
if (FALSE) { # \dontrun{
res <- group_list()

# via a group name/id
group_show(res[[1]]$name)

# or via an object of class ckan_group
group_show(res[[1]])

# return different data formats
group_show(res[[1]]$name, as = "json")
group_show(res[[1]]$name, as = "table")
} # }
```
