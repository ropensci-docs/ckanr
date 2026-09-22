# Create a user.

Create a user.

## Usage

``` r
user_create(
  name,
  email,
  password,
  id = NULL,
  fullname = NULL,
  about = NULL,
  openid = NULL,
  image_url = NULL,
  plugin_extras = NULL,
  with_apitoken = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- name:

  (character) Name of the new user. The name is a string between 2 and
  100 characters in length. The name contains only lowercase
  alphanumeric characters, - and \_. Required.

- email:

  (character) Email address for the new user. Required.

- password:

  (character) Password of the new user. The password is a string of at
  least 4 characters. Required.

- id:

  (character) ID of the new user. Optional. Plugins may set user IDs at
  creation (CKAN 2.12+, <https://github.com/ckan/ckan/pull/8609>).

- fullname:

  (character) Full name of the user. Optional.

- about:

  (character) Description of the new user. Optional.

- openid:

  (character) OpenID of the new user. Optional.

- image_url:

  (character) URL to an image displayed on the user's page. Optional.

- plugin_extras:

  (list) Private extra user data for plugins. Only sysadmins may set
  this. Plugins should namespace extras with the plugin name. Optional.

- with_apitoken:

  (logical) Create an API token for the user. Optional.

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

## References

http://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.create.user_create

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(
  url = "https://data-demo.dpaw.wa.gov.au",
  key = "824e7c50-9577-4bfa-bf32-246ebed1a8a2"
)

# create a user
user_create(
  name = "stacy", email = "stacy@aaaaa.com",
  password = "helloworld"
)
} # }
```
