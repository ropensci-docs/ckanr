# Update a user account.

Normal users can only update their own user accounts. Sysadmins can
update any user account and modify existing usernames. Update methods
may delete parameters not explicitly provided: if you want to edit only
specific attributes, use
[`user_patch()`](https://docs.ropensci.org/ckanr/reference/user_patch.md)
instead. For the full list of accepted fields, see
[`user_create()`](https://docs.ropensci.org/ckanr/reference/user_create.md)
and
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.update.user_update>.

## Usage

``` r
user_update(
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

  (character or `ckan_user`) The name or id of the user to update, or a
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

The updated user account as a `ckan_user` object. With `as = "table"`, a
data.frame; with `as = "json"`, the raw JSON response.

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.update.user_update

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# Create a user, then update it (user_update replaces the whole account,
# so fetch the full object first and modify it)
usr <- user_create(
  name = "stacy-update", email = "stacy-update@example.com",
  password = "helloworld"
)
full <- unclass(user_show(usr$id))
full$fullname <- "Stacy Updated"
user_update(full, id = usr)

# Clean up
user_delete(usr$id)
} # }
```
