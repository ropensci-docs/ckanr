# Delete a tag.

Delete a tag. You must be a sysadmin to delete tags. See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.delete.tag_delete>
for the official API contract.

## Usage

``` r
tag_delete(
  id,
  vocabulary_id = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character or `ckan_tag`) The id or name of the tag to delete, or a
  `ckan_tag` object.

- vocabulary_id:

  (character) The id or name of the vocabulary that the tag belongs to.
  Omit it (default `NULL`) for free tags (optional).

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

## Value

(logical) `TRUE` when the function deletes the tag successfully.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.delete.tag_delete

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# create a vocabulary and a tag in it
vocab <- vocabulary_create(name = "delete-me-vocab")
tag <- tag_create(name = "delete-me-tag", vocabulary_id = vocab$id)

# delete the tag, then clean up the vocabulary
tag_delete(tag$id, vocabulary_id = vocab$id)
vocabulary_delete(vocab$id)
} # }
```
