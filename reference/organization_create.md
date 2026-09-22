# Create an organization

Create an organization

## Usage

``` r
organization_create(
  name = NULL,
  id = NULL,
  title = NULL,
  description = NULL,
  image_url = NULL,
  state = "active",
  approval_status = NULL,
  extras = NULL,
  packages = NULL,
  users = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- name:

  (character) the name of the organization. It is a string between 2 and
  100 characters long. It contains only lowercase alphanumeric
  characters,

  - and \_

- id:

  the id of the organization (optional)

- title:

  (character) the title of the organization (optional)

- description:

  (character) the description of the organization (optional)

- image_url:

  (character) the URL of an image for the organization's page (optional)

- state:

  (character) the current state of the organization, for example
  'active' or 'deleted' (optional). Only active organizations appear in
  search results and other lists of organizations. If you lack
  permission to change the state of the organization, the function
  ignores this parameter. Default: 'active'

- approval_status:

  (character) Approval status

- extras:

  The organization's extras (optional). Extras are arbitrary (key:
  value) metadata items for organizations. Each extra dictionary must
  have keys 'key' (a string) and 'value' (a string). See
  `package_relationship_create` for the format of relationship
  dictionaries (optional)

- packages:

  (list of dictionaries) the datasets (packages) that belong to the
  organization. It is a list of dictionaries. Each dictionary has keys
  'name' (string, the id or name of the dataset) and optionally 'title'
  (string, the title of the dataset)

- users:

  (character) the users that belong to the organization. It is a list of
  dictionaries. Each dictionary has key 'name' (string, the id or name
  of the user) and optionally 'capacity' (string, the capacity in which
  the user is a member of the organization)

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

## Examples

``` r
if (FALSE) { # \dontrun{
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# create an organization
(res <- organization_create("foobar",
  title = "Foo bars",
  description = "love foo bars"
))
res$name
} # }
```
