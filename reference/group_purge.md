# Purge a group

IMPORTANT: You must be a sysadmin to purge a group. Purging a group
cannot be undone: it completely removes the group from the CKAN
database, whereas deleting a group only marks it as deleted. Datasets in
the group remain, just no longer in the purged group. See
<https://docs.ckan.org/en/2.11/api/#ckan.logic.action.delete.group_purge>
for the official API contract.

## Usage

``` r
group_purge(
  id,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character or `ckan_group`) The name or id of the group to purge, or a
  `ckan_group` object.

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

The function returns an empty list on success

## References

https://docs.ckan.org/en/2.11/api/#ckan.logic.action.delete.group_purge

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

# create a group
(res <- group_create("foobar-group",
  title = "Foo bars",
  description = "love foo bars"
))

# delete the group just created
res$id
group_delete(id = res$id)

# purge the group just deleted
res$id
group_purge(id = res$id)
} # }
```
