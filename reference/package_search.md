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

  Filter query, this does not affect the search, only what gets returned

- sort:

  Field to sort on. You can specify ascending (e.g., score desc) or
  descending (e.g., score asc), sort by two fields (e.g., score desc,
  price asc), or sort by a function (e.g., sum(x_f, y_f) desc, which
  sorts by the sum of x_f and y_f in a descending order).

- rows:

  Number of records to return. Defaults to 10.

- start:

  Record to start at, default to beginning.

- facet:

  (logical) Whether to return facet results or not. Default: `FALSE`

- facet.limit:

  (numeric) This param indicates the maximum number of constraint counts
  that should be returned for the facet fields. A negative value means
  unlimited. Default: 100. Can be specified on a per field basis.

- facet.field:

  (character) This param allows you to specify a field which should be
  treated as a facet. It will iterate over each Term in the field and
  generate a facet count using that Term as the constraint. This
  parameter can be specified multiple times to indicate multiple facet
  fields. None of the other params in this section will have any effect
  without specifying at least one field name using this param.

- facet.mincount:

  (integer) the minimum counts for facet fields should be included in
  the results

- include_drafts:

  (logical) if `TRUE` draft datasets will be included. A user will only
  be returned their own draft datasets, and a sysadmin will be returned
  all draft datasets. default: `FALSE`. first CKAN version: 2.6.1;
  dropped from request if CKAN version is older or if CKAN version isn't
  available via
  [`ckan_version()`](https://docs.ropensci.org/ckanr/reference/ckan_info.md)

- include_private:

  (logical) if `TRUE` private datasets will be included. Only private
  datasets from the user’s organizations will be returned and sysadmins
  will be returned all private datasets. default: `FALSE` first CKAN
  version: 2.6.1; dropped from request if CKAN version is older or if
  CKAN version isn't available via
  [`ckan_version()`](https://docs.ropensci.org/ckanr/reference/ckan_info.md)

- use_default_schema:

  (logical) use default package schema instead of a custom schema
  defined with an IDatasetForm plugin. default: `FALSE` first CKAN
  version: 2.3.5; dropped from request if CKAN version is older or if
  CKAN version isn't available via
  [`ckan_version()`](https://docs.ropensci.org/ckanr/reference/ckan_info.md)

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
