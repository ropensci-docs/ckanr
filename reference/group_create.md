# Create a group

Create a group

## Usage

``` r
group_create(
  name = NULL,
  id = NULL,
  title = NULL,
  description = NULL,
  image_url = NULL,
  type = NULL,
  state = "active",
  approval_status = NULL,
  extras = NULL,
  packages = NULL,
  groups = NULL,
  users = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- name:

  (character) the name of the new dataset, must be between 2 and 100
  characters long and contain only lowercase alphanumeric characters,

  - and \_, e.g. 'warandpeace'

- id:

  (character) The id of the group (optional)

- title:

  (character) The title of the dataset (optional, default: same as name)

- description:

  (character) The description of the group (optional)

- image_url:

  (character) The URL to an image to be displayed on the group's page
  (optional)

- type:

  (character) The type of the dataset (optional), IDatasetForm plugins
  associate themselves with different dataset types and provide custom
  dataset handling behaviour for these types

- state:

  (character) The current state of the dataset, e.g. 'active' or
  'deleted', only active datasets show up in search results and other
  lists of datasets, this parameter will be ignored if you are not
  authorized to change the state of the dataset (optional, default:
  'active')

- approval_status:

  (character) Approval status (optional)

- extras:

  (list of dataset extra dictionaries) The dataset's extras (optional),
  extras are arbitrary (key: value) metadata items that can be added to
  datasets, each extra dictionary should have keys 'key' (a string),
  'value' (a string)

- packages:

  (data.frame) The datasets (packages) that belong to the group, a
  data.frame, where each row has column 'name' (string, the id or name
  of the dataset) and optionally 'title' (string, the title of the
  dataset)

- groups:

  (data.frame) The groups to which the dataset belongs (optional), each
  data.frame row should have one or more of the following columns which
  identify an existing group: 'id' (the id of the group, string), or
  'name' (the name of the group, string), to see which groups exist call
  [`group_list()`](https://docs.ropensci.org/ckanr/reference/group_list.md)

- users:

  (list of dictionaries) The users that belong to the group, a list of
  dictionaries each with key 'name' (string, the id or name of the user)
  and optionally 'capacity' (string, the capacity in which the user is a
  member of the group)

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
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# create a group
(res <- group_create("fruitloops2", description = "A group about fruitloops"))
res$users
res$num_followers
} # }
```
