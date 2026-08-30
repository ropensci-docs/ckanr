# Revise a dataset using match/filter/update semantics

Revise a dataset using match/filter/update semantics

## Usage

``` r
package_revise(
  match = NULL,
  filter = NULL,
  update = NULL,
  include = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- match:

  (list) Key/value pairs identifying the dataset to revise. Required
  unless using flattened keys.

- filter:

  (character or list) Patterns describing fields to remove before the
  update runs.

- update:

  (list) Values to set after filtering. Supports flattened keys.

- include:

  (character or list) Optional patterns delimiting which fields are
  returned in the response.

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
package_revise(
  match = list(name = "source-dataset"),
  update = list(notes = "New description")
)
} # }
```
