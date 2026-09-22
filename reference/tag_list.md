# List tags.

List tags.

## Usage

``` r
tag_list(
  query = NULL,
  vocabulary_id = NULL,
  all_fields = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- query:

  (character) Tag name query to search for. If you give a query, the
  function returns only tags whose names contain this string.

- vocabulary_id:

  (character) ID or name of a vocabulary. If you give a vocabulary, the
  function returns only tags that belong to this vocabulary.

- all_fields:

  (logical) The function returns full tag dictionaries instead of names.
  Default is `FALSE`.

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
# list all tags
tag_list()

# search for a specific tag
tag_list(query = "aviation")

# all fields
tag_list(all_fields = TRUE)

# give back different data formats
tag_list("aviation", as = "json")
tag_list("aviation", as = "table")
} # }
```
