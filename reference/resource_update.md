# Update a resource

You call this function to update a resource file attachment and "extra"
metadata fields. Each update sets the metadata key "last_updated".

On CKAN \< 2.12 omitted metadata fields could be overwritten; on CKAN
2.12+ unchanged resources are no longer revalidated and
[`package_update()`](https://docs.ropensci.org/ckanr/reference/package_update.md)
without `resources` keeps existing resources
(<https://github.com/ckan/ckan/pull/8155>,
<https://github.com/ckan/ckan/pull/5713>). To update selected metadata
fields and keep all other fields unchanged, first retrieve the full
resource metadata with `resource_show`. Then update this metadata as
required. Then update the resource with `resource_update` with the
locally updated metadata.

If you update a resource file, the new file must exist on a local path.
You cannot use R objects directly to update a resource file. Instead,
write them to a file. For example, use
[`tempfile()`](https://rdrr.io/r/base/tempfile.html). See the example.

To point an existing resource at a new external URL, pass the link
through `rcurl`. Do not put the link in `extras`.

The CKAN base URL and API key default to the global options.
`ckanr_setup` sets the global options.

## Usage

``` r
resource_update(
  id,
  path = NULL,
  extras = list(),
  rcurl = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) Resource ID to update. Required.

- path:

  (character) Local path of the file to upload. Optional.

- extras:

  (list) Extra metadata fields of the resource. Optional.

- rcurl:

  (character) New external URL of the resource, for example an ArcGIS
  link. The function sends it as the resource `url` and sets `url_type`
  to `link`, so CKAN stores a true external link. Use this without
  `path` to point an existing resource at a new external URL. If you
  also pass `path`, the uploaded file wins on the server. Optional.

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

The function returns the HTTP response from CKAN as a list (default),
table, or JSON.

## References

http://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.create.resource_create

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# Get file
path <- system.file("examples", "actinidiaceae.csv", package = "ckanr")

# Create package, then a resource within that package
(res <- package_create("newpackage10"))
(xx <- resource_create(
  package_id = res$id,
  description = "my resource",
  name = "bears",
  upload = path,
  rcurl = "http://google.com"
))

# Modify dataset, here lowercase strings in one column
dat <- read.csv(path, stringsAsFactors = FALSE)
dat$Family <- tolower(dat$Family)
newpath <- tempfile(fileext = ".csv")
write.csv(dat, file = newpath, row.names = FALSE)

# Upload modified dataset
## Directly from output of resource_create
resource_update(xx, path = newpath)

## or from the resource id
resource_update(xx$id, path = newpath)

## optionally include extra tags
resource_update(xx$id,
  path = newpath,
  extras = list(some = "metadata")
)

# Update a resource's extra tags
## add extra tags without uploading a new file
resource_update(id,
  extras = list(some = "metadata")
)

# Point an existing resource at a new external URL
resource_update(xx$id, rcurl = "https://example.com/data.geojson")

## or remove all extra tags
resource_update(id, extras = list())

#######
# Using default settings
ckanr_setup(url = "http://demo.ckan.org/", key = "my-demo-ckan-org-api-key")
path <- system.file("examples", "actinidiaceae.csv", package = "ckanr")
resource_update(id = "an-existing-resource-id", path = path)

# Using an R object written to a tempfile, and implicit CKAN URL and API key
write.csv(data <- installed.packages(), path <- tempfile(fileext = ".csv"))
ckanr_setup(url = "http://demo.ckan.org/", key = "my-demo-ckan-org-api-key")
resource_update(id = "an-existing-resource-id", path = path)

# Testing: see ?ckanr_setup to set default test CKAN url, key, package id
ckanr_setup(
  test_url = "http://my-ckan.org/",
  test_key = "my-ckan-api-key",
  test_did = "an-existing-package-id",
  test_rid = "an-existing-resource-id"
)
resource_update(
  id = get_test_rid(),
  path = system.file("examples",
    "actinidiaceae.csv",
    package = "ckanr"
  ),
  key = get_test_key(),
  url = get_test_url()
)

# other file formats
## html
path <- system.file("examples", "mapbox.html", package = "ckanr")

# Create package, then a resource within that package
(res <- package_create("mappkg"))
(xx <- resource_create(
  package_id = res$id,
  description = "a map, yay",
  name = "mapyay",
  upload = path,
  rcurl = "http://google.com"
))
browseURL(xx$url)

# Modify dataset, here lowercase strings in one column
dat <- readLines(path)
dat <- sub("-111.06", "-115.06", dat)
newpath <- tempfile(fileext = ".html")
cat(dat, file = newpath, sep = "\n")

# Upload modified dataset
## Directly from output of resource_create
(xxx <- resource_update(xx, path = newpath))
browseURL(xxx$url)
} # }
```
