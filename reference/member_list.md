# List members for a group or organization

List members for a group or organization

## Usage

``` r
member_list(
  id,
  object_type = NULL,
  capacity = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character, `ckan_group`, or `ckan_organization`) Identifier for the
  container.

- object_type:

  (character) Optional object type filter (`"user"`, `"package"`, etc.).

- capacity:

  (character) Optional capacity filter (`"member"`, `"editor"`,
  `"admin"`).

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
# ckanr_setup(url = "https://demo.ckan.org/", key = "my-key")
# member_list("my-group", object_type = "user")
```
