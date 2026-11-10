# Patch a user account.

This function partially updates a user account: it updates only the
provided parameters and leaves all other parameters unchanged (unlike
[`user_update()`](https://docs.ropensci.org/ckanr/reference/user_update.md),
which may delete parameters not explicitly provided). Normal users can
only patch their own user accounts; sysadmins can patch any user
account. See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.patch.user_patch>
for the official API contract.

## Usage

``` r
user_patch(
  x,
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- x:

  (list) A list with key-value pairs

- id:

  (character or `ckan_user`) The id or name of the user to patch, or a
  `ckan_user` object.

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

The patched user account as a `ckan_user` object. With `as = "table"`, a
data.frame; with `as = "json"`, the raw JSON response.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.patch.user_patch

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# Create a user, then patch it
usr <- user_create(
  name = "stacy-patch", email = "stacy-patch@example.com",
  password = "helloworld"
)
user_patch(list(about = "patched via ckanr"), id = usr)

# Clean up
user_delete(usr$id)
} # }
```
