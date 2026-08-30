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

  (character) A tag name query to search for, if given only tags whose
  names contain this string will be returned

- vocabulary_id:

  (character) The id or name of a vocabulary, if given, only tags that
  belong to this vocabulary will be returned

- all_fields:

  (logical) Return full tag dictionaries instead of just names. Default:
  `FALSE`

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
