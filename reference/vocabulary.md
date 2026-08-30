# Manage CKAN vocabularies.

CKAN restricts vocabulary creation, updates, and deletions to sysadmin
users. Each helper wraps the matching `/api/3/action/vocabulary_*`
endpoint.

## Usage

``` r
vocabulary_list(
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

vocabulary_show(
  id,
  include_datasets = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

vocabulary_create(
  name,
  tags = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

vocabulary_update(
  id,
  name = NULL,
  tags = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

vocabulary_delete(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

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

- id:

  (character or `ckan_vocabulary`) Vocabulary id or name. Can also be an
  existing `ckan_vocabulary` object.

- include_datasets:

  (logical) Return datasets owned by the vocabulary. Only applies to
  `vocabulary_show()`.

- name:

  (character) Unique vocabulary name.

- tags:

  (list) Optional list of tag objects, each containing at least a `name`
  field. See <https://docs.ckan.org/en/latest/api/> for the full
  structure.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

vocab_name <- sprintf("demo_vocab_%s", sample.int(1e6, 1))
vocab <- vocabulary_create(name = vocab_name)

vocabulary_show(vocab$id)
vocabulary_update(vocab, name = paste0(vocab_name, "_updated"))
vocabulary_list()
vocabulary_delete(vocab)
} # }
```
