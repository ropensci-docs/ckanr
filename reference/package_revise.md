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

  (list) Key/value pairs that identify the dataset to revise. Unless you
  use flattened keys, this parameter is required.

- filter:

  (character or list) Patterns that describe fields to remove before the
  update runs.

- update:

  (list) Values to set after filtering. The values support flattened
  keys.

- include:

  (character or list) Optional patterns that delimit which fields the
  response returns.

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

## Examples

``` r
if (FALSE) { # \dontrun{
package_revise(
  match = list(name = "source-dataset"),
  update = list(notes = "New description")
)
} # }
```
