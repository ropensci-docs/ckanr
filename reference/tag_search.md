# Search tags.

Search tags.

## Usage

``` r
tag_search(
  query = NULL,
  vocabulary_id = NULL,
  offset = 0,
  limit = 31,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- query:

  (character) A tag name query to search for, if given only tags whose
  names contain this string will be returned; one or more search strings

- vocabulary_id:

  (character) The id or name of a vocabulary, if give only tags that
  belong to this vocabulary will be returned

- offset:

  (numeric) Where to start getting activity items from (optional,
  default: 0)

- limit:

  (numeric) The maximum number of activities to return (optional,
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
tag_search(query = "ta")
tag_search(query = c("ta", "al"))

# different formats back
tag_search(query = "ta", as = "json")
tag_search(query = "ta", as = "table")
} # }
```
