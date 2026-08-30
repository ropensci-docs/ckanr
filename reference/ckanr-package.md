# R client for the CKAN API

ckanr is a full client for the CKAN API, wrapping all APIs, including
for reading and writing data. Please get in touch
(<https://github.com/ropensci/ckanr/issues> or
<https://discuss.ropensci.org/>) if you have problems, or have use cases
that we don't cover yet.

## CKAN API

Documentation for the CKAN API is at
<https://docs.ckan.org/en/latest/api/index.html>. We'll always be
following the latest version of the API.

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

We are also working on supporting the Datastore extension
(<https://docs.ckan.org/en/latest/maintaining/datastore.html>). We
currently have these functions:

- [`ds_create()`](https://docs.ropensci.org/ckanr/reference/ds_create.md)

- [`ds_create_dataset()`](https://docs.ropensci.org/ckanr/reference/ds_create_dataset.md)

- [`ds_search()`](https://docs.ropensci.org/ckanr/reference/ds_search.md)

- [`ds_search_sql()`](https://docs.ropensci.org/ckanr/reference/ds_search_sql.md)

## Fetch

Data can come back in a huge variety of formats. We've attempted a
function to help you fetch not just metadata but the actual data for a
link to a file on a CKAN instance. Though if you know what you're doing,
you can easily use whatever is your preferred tool for the job (e.g.,
maybe you like [`read.csv()`](https://rdrr.io/r/utils/read.table.html)
for reading csv files).

## CKAN Instances

We have a helper function
([`servers()`](https://docs.ropensci.org/ckanr/reference/servers.md))
that spits out the current CKAN instances we know about, with URLs to
their base URLs that should work using this package. That is, not
necessarily landing pages of each instance, although, the URL may be the
landing page and the base API URL.

## See also

Useful links:

- [https://docs.ropensci.org/ckanr/ (website)
  https://github.com/ropensci/ckanr
  (devel)](https://docs.ropensci.org/ckanr/%20(website)%20https://github.com/ropensci/ckanr%20(devel))

- Report bugs at <https://github.com/ropensci/ckanr/issues>

## Author

Scott Chamberlain <myrmecocystus@gmail.com>

Florian Mayer <florian.wendelin.mayer@gmail.com>

Wush Wu

Imanuel Costigan <i.costigan@me.com>

Sharla Gelfand

Francisco Alves <fjunior.alves.oliveira@gmail.com>
