# Create a package

Create a package

## Usage

``` r
package_create(
  name = NULL,
  title = NULL,
  private = FALSE,
  author = NULL,
  author_email = NULL,
  maintainer = NULL,
  maintainer_email = NULL,
  license_id = NULL,
  notes = NULL,
  package_url = NULL,
  version = NULL,
  state = "active",
  type = NULL,
  resources = NULL,
  tags = NULL,
  extras = NULL,
  relationships_as_object = NULL,
  relationships_as_subject = NULL,
  groups = NULL,
  owner_org = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- name:

  (character) the name of the new dataset, must be between 2 and 100
  characters long and contain only lowercase alphanumeric characters, -
  and \_, e.g. 'warandpeace'

- title:

  (character) the title of the dataset (optional, default: same as name)

- private:

  (logical) whether the dataset should be private (optional, default:
  `FALSE`), requires a value for `owner_org` if `TRUE`

- author:

  (character) the name of the dataset's author (optional)

- author_email:

  (character) the email address of the dataset's author (optional)

- maintainer:

  (character) the name of the dataset's maintainer (optional)

- maintainer_email:

  (character) the email address of the dataset's maintainer (optional)

- license_id:

  (license id string) - the id of the dataset's license, see
  license_list() for available values (optional)

- notes:

  (character) a description of the dataset (optional)

- package_url:

  (character) a URL for the dataset's source (optional)

- version:

  (string, no longer than 100 characters) - (optional)

- state:

  (character) the current state of the dataset, e.g. 'active' or
  'deleted', only active datasets show up in search results and other
  lists of datasets, this parameter will be ignored if you are not
  authorized to change the state of the dataset (optional, default:
  'active')

- type:

  (character) the type of the dataset (optional), IDatasetForm plugins
  associate themselves with different dataset types and provide custom
  dataset handling behaviour for these types

- resources:

  (list of resource dictionaries) - the dataset's resources, see
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md)
  for the format of resource dictionaries (optional)

- tags:

  (list of tag dictionaries) - the dataset's tags, see
  [`tag_create()`](https://docs.ropensci.org/ckanr/reference/tag_create.md)
  for the format of tag dictionaries (optional)

- extras:

  (list of dataset extra dictionaries) - the dataset's extras
  (optional), extras are arbitrary (key: value) metadata items that can
  be added to datasets, each extra dictionary should have keys 'key' (a
  string), 'value' (a string)

- relationships_as_object:

  (list of relationship dictionaries) - see
  `package_relationship_create` for the format of relationship
  dictionaries (optional)

- relationships_as_subject:

  (list of relationship dictionaries) - see
  `package_relationship_create` for the format of relationship
  dictionaries (optional)

- groups:

  (data.frame) the groups to which the dataset belongs, each row should
  have one or more of the following columns which identify an existing
  group: 'id' (the id of the group, string), or 'name' (the name of the
  group, string), to see which groups exist call
  [`group_list()`](https://docs.ropensci.org/ckanr/reference/group_list.md).
  see example (optional)

- owner_org:

  (character) the id of the dataset's owning organization, see
  [`organization_list()`](https://docs.ropensci.org/ckanr/reference/organization_list.md)
  or `organization_list_for_user` for available values (optional)

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

# create a package
## Example 1
(res <- package_create("foobar4", author = "Jane Doe"))
res$author

## Example 2 - create package, add a resource
(res <- package_create("helloworld", author = "Jane DOe"))

# include a group
# package_create("brownbear", groups = data.frame(id = "some-id"))
} # }
```
