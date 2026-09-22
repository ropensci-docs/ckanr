# Search for packages.

Search for packages.

## Usage

``` r
package_search(
  q = "*:*",
  fq = NULL,
  sort = NULL,
  rows = NULL,
  start = NULL,
  facet = FALSE,
  facet.limit = NULL,
  facet.field = NULL,
  facet.mincount = NULL,
  include_drafts = FALSE,
  include_private = FALSE,
  use_default_schema = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- q:

  Query terms, defaults to '*:*', or everything.

- fq:

  Filter query. It does not affect the search. It only controls what the
  function returns.

- sort:

  Field to sort on. You can specify ascending order, for example score
  desc. You can specify descending order, for example score asc. You can
  sort by two fields, for example score desc, price asc. You can sort by
  a function, for example sum(x_f, y_f) desc. The function then sorts by
  the sum of x_f and y_f in descending order.

- rows:

  Number of records to return. Defaults to 10.

- start:

  Record to start with. It defaults to the beginning.

- facet:

  (logical) Whether to return facet results or not. Default: `FALSE`

- facet.limit:

  (numeric) The maximum number of constraint counts for the facet
  fields. A negative value means unlimited. Default: 100. You can set it
  for each field.

- facet.field:

  (character) This parameter sets a field to treat as a facet. It
  iterates over each Term in the field. It generates a facet count with
  that Term as the constraint. You can give this parameter multiple
  times for multiple facet fields. If you omit all field names for this
  parameter, the other parameters in this section have no effect.

- facet.mincount:

  (integer) the minimum counts for facet fields. The results include
  only fields that meet this count.

- include_drafts:

  (logical) If `TRUE`, the function includes draft datasets. A user gets
  only their own draft datasets. A sysadmin gets all draft datasets.
  Default: `FALSE`. First CKAN version: 2.6.1. If the CKAN version is
  older, or if the version is not available through
  [`ckan_version()`](https://docs.ropensci.org/ckanr/reference/ckan_info.md),
  the function drops it from the request.

- include_private:

  (logical) If `TRUE`, the function includes private datasets. It
  returns only private datasets from the user organizations. Sysadmins
  get all private datasets. Default: `FALSE`. First CKAN version: 2.6.1.
  If the CKAN version is older, or if the version is not available
  through
  [`ckan_version()`](https://docs.ropensci.org/ckanr/reference/ckan_info.md),
  the function drops it from the request.

- use_default_schema:

  (logical) Use default package schema instead of a custom schema from
  an IDatasetForm plugin. Default: `FALSE`. First CKAN version: 2.3.5.
  If the CKAN version is older, or if the version is not available
  through
  [`ckan_version()`](https://docs.ropensci.org/ckanr/reference/ckan_info.md),
  the function drops it from the request.

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
ckanr_setup(url = "https://demo.ckan.org", key = getOption("ckan_demo_key"))

package_search(q = "*:*")
package_search(q = "*:*", rows = 2, as = "json")
package_search(q = "*:*", rows = 2, as = "table")

package_search(q = "*:*", sort = "score asc")
package_search(q = "*:*", fq = "num_tags:[3 TO *]")$count
package_search(q = "*:*", fq = "num_tags:[2 TO *]")$count
package_search(q = "*:*", fq = "num_tags:[1 TO *]")$count
} # }
```
