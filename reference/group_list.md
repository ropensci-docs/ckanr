# List groups.

List groups.

## Usage

``` r
group_list(
  offset = 0,
  limit = 31,
  sort = NULL,
  groups = NULL,
  all_fields = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- offset:

  (numeric) Where to start getting activity items from (optional,
  default: 0)

- limit:

  (numeric) The maximum number of activities to return (optional,
  default: 31)

- sort:

  Field to sort on. You can specify ascending (e.g., score desc) or
  descending (e.g., score asc), sort by two fields (e.g., score desc,
  price asc), or sort by a function (e.g., sum(x_f, y_f) desc, which
  sorts by the sum of x_f and y_f in a descending order).

- groups:

  (character) A list of names of the groups to return, if given only
  groups whose names are in this list will be returned

- all_fields:

  (logical) Return full group dictionaries instead of just names.
  Default: `FALSE`

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
group_list(limit = 3)
group_list(limit = 3, as = "json")
group_list(limit = 3, as = "table")
} # }
```
