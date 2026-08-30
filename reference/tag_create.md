# Create a tag

IMPORTANT: You must be a sysadmin to create vocabulary tags.

## Usage

``` r
tag_create(
  name,
  vocabulary_id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- name:

  (character) The name for the new tag, a string between 2 and 100
  characters long containing only alphanumeric characters and -, \_ and
  ., e.g. 'Jazz'

- vocabulary_id:

  (character) The id of the vocabulary that the new tag should be added
  to, e.g. the id of vocabulary 'Genre'

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
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = Sys.getenv("CKAN_DEMO_KEY")
)
tag_create(name = "TestTag1", vocabulary_id = "Testing1")
} # }
```
