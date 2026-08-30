# Term translation helpers

Manage localized UI strings stored in CKAN's term translation table.

## Usage

``` r
term_translation_show(
  terms,
  lang_codes = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

term_translation_update(
  term,
  term_translation,
  lang_code,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

term_translation_update_many(
  data,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- terms:

  (character) Vector of source terms.

- lang_codes:

  (character) Language codes to include.

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

- term:

  (character) Source term.

- term_translation:

  (character) Translation value.

- lang_code:

  (character) Target language code.

- data:

  (list) List of translation dictionaries with `term`,
  `term_translation`, and `lang_code` entries.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = "my-ckan-key")
term_translation_show(c("License", "Dataset"), lang_codes = "fr")
term_translation_update(term = "License", term_translation = "Licence", lang_code = "fr")
} # }
```
