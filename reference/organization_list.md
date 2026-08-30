# List organization

List organization

## Usage

``` r
organization_list(
  order_by = c("name", "package"),
  decreasing = FALSE,
  organizations = NULL,
  all_fields = TRUE,
  limit = 31,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- order_by:

  (character, only the first element is used). The field to sort the
  list by, must be `name` or `packages`.

- decreasing:

  (logical). Is the sort-order is decreasing or not.

- organizations:

  (character or `NULL`). A list of names of the organizations to return.
  `NULL` returns all organizations.

- all_fields:

  (logical). Return the name or all fields of the object.

- limit:

  (numeric) The maximum number of organizations to return (optional,
  default: 31)

- url:

  Base url to use. Default: https://demo.ckan.org/ See also
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md).

- key:

  A privileged CKAN API key, Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- as:

  (character) One of list (default), table, or json. Parsing with table
  option uses `jsonlite::fromJSON(..., simplifyDataFrame = TRUE)`, which
  attempts to parse data to data.frame's when possible, so the result
  can vary from a vector, list or data.frame. (required)

- ...:

  Curl args passed on to
  [`verb-POST`](https://docs.ropensci.org/crul/reference/verb-POST.html)
  (optional)

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/")

# list organizations
res <- organization_list()
res[1:2]

# Different data formats
organization_list(as = "json")
organization_list(as = "table")
} # }
```
