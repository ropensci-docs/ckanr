# R client for the CKAN API

ckanr is a client for the CKAN API. It wraps all APIs for reading and
writing data. If you have problems, or have use cases that the package
does not cover yet, get in touch
(<https://github.com/ropensci/ckanr/issues> or
<https://discuss.ropensci.org/>)

## CKAN API

Documentation for the CKAN API is at
<https://docs.ckan.org/en/latest/api/index.html>. The package follows
the latest version of the API.

## ckanr package API

The functions can be grouped into those for setup, packages, resources,
tags, organizations, groups, and users.

- Setup - The main one is
  [`ckanr_setup()`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md) -
  and many related functions, e.g.,
  [`get_default_key()`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md)

- Packages - Create a package with
  [`package_create()`](https://docs.ropensci.org/ckanr/reference/package_create.md),
  and see other functions starting with `package_*`

- Resources - Create a package with
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md),
  and see other functions starting with `resource_*`

- Tags - List tags with
  [`tag_list()`](https://docs.ropensci.org/ckanr/reference/tag_list.md),
  and see other functions starting with `tag_*`

- Organizations - List organizations with
  [`organization_list()`](https://docs.ropensci.org/ckanr/reference/organization_list.md),
  show a specific organization with
  [`organization_show()`](https://docs.ropensci.org/ckanr/reference/organization_show.md),
  and create with
  [`organization_create()`](https://docs.ropensci.org/ckanr/reference/organization_create.md)

- Groups - List groups with
  [`group_list()`](https://docs.ropensci.org/ckanr/reference/group_list.md),
  and see other functions starting with `group_*`

- Users - List users with
  [`user_list()`](https://docs.ropensci.org/ckanr/reference/user_list.md),
  and see other functions starting with `user_*`

- Related items - See functions starting with `related_*`

## Datastore

The package supports the Datastore extension
(<https://docs.ckan.org/en/latest/maintaining/datastore.html>). It
provides these functions:

- [`ds_create()`](https://docs.ropensci.org/ckanr/reference/ds_create.md)

- [`ds_create_dataset()`](https://docs.ropensci.org/ckanr/reference/ds_create_dataset.md)

- [`ds_search()`](https://docs.ropensci.org/ckanr/reference/ds_search.md)

- [`ds_search_sql()`](https://docs.ropensci.org/ckanr/reference/ds_search_sql.md)

## Fetch

Data comes back in a wide range of formats. The package provides a
function to help you fetch metadata. The function also fetches the
actual data for a link to a file on a CKAN instance. If you know what
you are doing, you can use your preferred tool for the job. For example,
you like [`read.csv()`](https://rdrr.io/r/utils/read.table.html) for
reading csv files.

## CKAN Instances

A helper function
([`servers()`](https://docs.ropensci.org/ckanr/reference/servers.md))
lists the current CKAN instances that the package knows about. It gives
the base URLs that work with this package. The URLs are not necessarily
landing pages of each instance, but the URL can be the landing page and
the base API URL.

## See also

Useful links:

- <https://docs.ropensci.org/ckanr/> (website)
  <https://github.com/ropensci/ckanr> (devel)

- Report bugs at <https://github.com/ropensci/ckanr/issues>

## Author

Scott Chamberlain <myrmecocystus@gmail.com>

Florian Mayer <florian.wendelin.mayer@gmail.com>

Wush Wu

Imanuel Costigan <i.costigan@me.com>

Sharla Gelfand

Francisco Alves <fjunior.alves.oliveira@gmail.com>
