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
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- name:

  (character) the name of the new user, a string between 2 and 100
  characters in length, containing only lowercase alphanumeric
  characters, - and \_ (required)

- email:

  (character) the email address for the new user (required)

- password:

  (character) the password of the new user, a string of at least 4
  characters (required)

- id:

  (character) the id of the new user (optional)

- fullname:

  (character) user full name

- about:

  (character) a description of the new user (optional)

- openid:

  (character) an openid (optional)

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
