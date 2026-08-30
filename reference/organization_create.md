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

  (character) the name of the organization, a string between 2 and 100
  characters long, containing only lowercase alphanumeric characters,

  - and \_

- id:

  the id of the organization (optional)

- title:

  (character) the title of the organization (optional)

- description:

  (character) the description of the organization (optional)

- image_url:

  (character) the URL to an image to be displayed on the organization's
  page (optional)

- state:

  (character) the current state of the organization, e.g. 'active' or
  'deleted', only active organization show up in search results and
  other lists of organization, this parameter will be ignored if you are
  not authorized to change the state of the organization (optional).
  Default: 'active'

- approval_status:

  (character) Approval status

- extras:

  The organization's extras (optional), extras are arbitrary (key:
  value) metadata items that can be added to organizations, each extra
  dictionary should have keys 'key' (a string), 'value' (a string)
  `package_relationship_create` for the format of relationship
  dictionaries (optional)

- packages:

  (list of dictionaries) the datasets (packages) that belong to the
  organization, a list of dictionaries each with keys 'name' (string,
  the id or name of the dataset) and optionally 'title' (string, the
  title of the dataset)

- users:

  (character) the users that belong to the organization, a list of
  dictionaries each with key 'name' (string, the id or name of the user)
  and optionally 'capacity' (string, the capacity in which the user is a
  member of the organization)

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
