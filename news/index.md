# Changelog

## ckanr (development version)

## ckanr 0.8.1

#### MAINTENANCE

- Change the default CKAN URL to <https://demo.ckan.org/>
- Update servers(), thanks [@nn-at](https://github.com/nn-at)
  ([\#176](https://github.com/ropensci/ckanr/issues/176))
- Replace the deprecated `lazyeval` dependency with `rlang`, update
  dplyr tests and development tooling accordingly so contributors only
  need the modern tidy-eval stack
  ([\#93](https://github.com/ropensci/ckanr/issues/93))

## ckanr 0.8.0

#### NEW FEATURES

Remaining endpoints of the CKAN 2.11 API have been implemented.

- Add dataset collaborator helpers
  [`package_collaborator_list()`](https://docs.ropensci.org/ckanr/reference/package_collaborator_list.md),
  [`package_collaborator_list_for_user()`](https://docs.ropensci.org/ckanr/reference/package_collaborator_list_for_user.md),
  [`package_collaborator_create()`](https://docs.ropensci.org/ckanr/reference/package_collaborator_create.md),
  and
  [`package_collaborator_delete()`](https://docs.ropensci.org/ckanr/reference/package_collaborator_delete.md).
- Expose membership utilities
  [`member_list()`](https://docs.ropensci.org/ckanr/reference/member_list.md),
  [`member_create()`](https://docs.ropensci.org/ckanr/reference/member_create.md),
  [`member_delete()`](https://docs.ropensci.org/ckanr/reference/member_delete.md),
  [`member_roles_list()`](https://docs.ropensci.org/ckanr/reference/member_roles_list.md),
  [`group_member_create()`](https://docs.ropensci.org/ckanr/reference/group_member_create.md),
  [`group_member_delete()`](https://docs.ropensci.org/ckanr/reference/group_member_delete.md),
  [`organization_member_create()`](https://docs.ropensci.org/ckanr/reference/organization_member_create.md),
  [`organization_member_delete()`](https://docs.ropensci.org/ckanr/reference/organization_member_delete.md),
  [`user_invite()`](https://docs.ropensci.org/ckanr/reference/user_invite.md),
  [`group_list_authz()`](https://docs.ropensci.org/ckanr/reference/group_list_authz.md),
  and
  [`organization_list_for_user()`](https://docs.ropensci.org/ckanr/reference/organization_list_for_user.md)
  to manage user access consistently across groups and organizations.
- Add relationship management wrappers
  [`package_relationships_list()`](https://docs.ropensci.org/ckanr/reference/package_relationships_list.md),
  [`package_relationship_create()`](https://docs.ropensci.org/ckanr/reference/package_relationship_create.md),
  [`package_relationship_update()`](https://docs.ropensci.org/ckanr/reference/package_relationship_update.md),
  and
  [`package_relationship_delete()`](https://docs.ropensci.org/ckanr/reference/package_relationship_delete.md)
  with S3-friendly inputs.
- Provide dataset maintenance helpers
  [`package_revise()`](https://docs.ropensci.org/ckanr/reference/package_revise.md),
  [`package_resource_reorder()`](https://docs.ropensci.org/ckanr/reference/package_resource_reorder.md),
  [`package_owner_org_update()`](https://docs.ropensci.org/ckanr/reference/package_owner_org_update.md),
  and
  [`dataset_purge()`](https://docs.ropensci.org/ckanr/reference/dataset_purge.md)
  for advanced automation workflows.
- Introduce the `ckan_resource_view` S3 class along with wrappers for
  [`resource_view_list()`](https://docs.ropensci.org/ckanr/reference/resource_view_list.md),
  [`resource_view_show()`](https://docs.ropensci.org/ckanr/reference/resource_view_show.md),
  [`resource_view_create()`](https://docs.ropensci.org/ckanr/reference/resource_view_create.md),
  [`resource_view_update()`](https://docs.ropensci.org/ckanr/reference/resource_view_update.md),
  [`resource_view_reorder()`](https://docs.ropensci.org/ckanr/reference/resource_view_reorder.md),
  [`resource_view_delete()`](https://docs.ropensci.org/ckanr/reference/resource_view_delete.md),
  [`resource_view_clear()`](https://docs.ropensci.org/ckanr/reference/resource_view_clear.md),
  [`resource_create_default_resource_views()`](https://docs.ropensci.org/ckanr/reference/resource_create_default_resource_views.md),
  and
  [`package_create_default_resource_views()`](https://docs.ropensci.org/ckanr/reference/package_create_default_resource_views.md)
  to manage CKAN previews from R.
- Refresh the follower/followee helpers: `dataset_*`, `group_*`, and
  `user_*` functions now expose counts, lists, follow/unfollow flows,
  and “am I following” probes, plus followee dashboards
  ([`followee_count()`](https://docs.ropensci.org/ckanr/reference/followee_counts.md),
  [`followee_list()`](https://docs.ropensci.org/ckanr/reference/followee_lists.md),
  `dataset_followee_*()`, `group_followee_*()`, `user_followee_*()`).
  Organization-specific helpers remain unavailable because CKAN 2.11+ no
  longer exposes those endpoints.
- Add activity-stream helpers covering
  [`group_activity_list()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  [`organization_activity_list()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  [`recently_changed_packages_activity_list()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  [`dashboard_new_activities_count()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  [`dashboard_mark_activities_old()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  [`activity_show()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  [`activity_data_show()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  [`activity_diff()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  [`activity_create()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md),
  and
  [`send_email_notifications()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md)
  (all automatically skip when the `activity` plugin is disabled).
- Add sysadmin-only vocabulary helpers
  ([`vocabulary_list()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md),
  [`vocabulary_show()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md),
  [`vocabulary_create()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md),
  [`vocabulary_update()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md),
  [`vocabulary_delete()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md))
  plus
  [`tag_autocomplete()`](https://docs.ropensci.org/ckanr/reference/tag_autocomplete.md)
  to round out the tag discovery toolkit.
- Implement the admin & operations toolkit: task-status maintenance
  (`task_status_*()`), term translations, runtime config editing,
  Redis/RQ job controls, API token lifecycle helpers, and diagnostic
  wrappers for
  [`status_show()`](https://docs.ropensci.org/ckanr/reference/diagnostics.md)/[`help_show()`](https://docs.ropensci.org/ckanr/reference/diagnostics.md).

#### TESTS

- Add integration coverage for collaborator and membership endpoints
  with dynamic skips when the target CKAN instance lacks the relevant
  feature flags.
- Cover the new relationship and dataset maintenance helpers, including
  opt-in purge coverage behind the `CKANR_ALLOW_PURGE_TESTS` gate.
- Exercise the resource view lifecycle
  (create/list/show/update/reorder/delete) plus default view helpers
  when the `text_view` plugin is available, while skipping gracefully
  otherwise.
- Expand the follower tests to follow/unfollow datasets, groups, and
  users, verifying the followee dashboards while automatically cleaning
  up temporary relationships.
- Add skips keyed off
  [`status_show()`](https://docs.ropensci.org/ckanr/reference/diagnostics.md)
  for all activity and dashboard tests, exercising new helpers whenever
  the `activity` plugin is available.
- Cover the new vocabulary lifecycle and
  [`tag_autocomplete()`](https://docs.ropensci.org/ckanr/reference/tag_autocomplete.md)
  helpers, skipping gracefully when the configured CKAN user lacks
  sysadmin rights.
- Exercise the admin/ops helpers with sysadmin-gated tests that verify
  task-status roundtrips, term translations, config changes, job
  management, API tokens, and diagnostics while skipping when the test
  key lacks sufficient privileges.

#### MAINTENANCE

- Add file `.github/copilot-instructions.md` to allow GenAI to reason
  over the codebase. The file is also a great read for human
  contributors.

## ckanr 0.7.1

#### NEW FEATURES

- Support for parquet files:
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md),
  `read_session()` and `fetch_GET()` now support parquet files, thanks
  [@hannaboe](https://github.com/hannaboe)
  ([\#217](https://github.com/ropensci/ckanr/issues/217))

#### MAINTENANCE

- New developer experience: A devcontainer provides a disposable CKAN
  instance for testing, replacing the need for an external CKAN instance
  and GitHub secrets for testing, and offering the choice of CKAN
  v2.9-2.11 ([\#216](https://github.com/ropensci/ckanr/issues/216)
  [\#212](https://github.com/ropensci/ckanr/issues/212))
- New maintainer [@florianm](https://github.com/florianm)

## ckanr 0.7.0

CRAN release: 2023-03-17

#### NEW FEATURES

- [`resource_update()`](https://docs.ropensci.org/ckanr/reference/resource_update.md)
  allows update of resource extra fields by making the `path` parameter
  optional ([\#175](https://github.com/ropensci/ckanr/issues/175))
  thanks [@nicholsn](https://github.com/nicholsn)

#### MINOR IMPROVEMENTS

- `revision_list` and `package_revision_list` return `NULL` instead of
  error for CKAN 2.9+
  ([\#200](https://github.com/ropensci/ckanr/issues/200))
- fix notes and warnings from CRAN package check results
  ([\#195](https://github.com/ropensci/ckanr/issues/195))

## ckanr 0.6.0

CRAN release: 2021-02-03

#### NEW FEATURES

- parameter `http_method` gained in
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md),
  [`package_update()`](https://docs.ropensci.org/ckanr/reference/package_update.md),
  and
  [`package_patch()`](https://docs.ropensci.org/ckanr/reference/package_patch.md);
  it’s passed to
  [`as.ckan_package()`](https://docs.ropensci.org/ckanr/reference/as.ckan_package.md)
  internally, but does not affect the HTTP request for the main point of
  the function ([\#163](https://github.com/ropensci/ckanr/issues/163))
  thanks [@hannaboe](https://github.com/hannaboe)
- gains new function
  [`organization_purge()`](https://docs.ropensci.org/ckanr/reference/organization_purge.md)
  to purge an organization (which requires sysadmin)
  ([\#166](https://github.com/ropensci/ckanr/issues/166)) thanks
  [@nicholsn](https://github.com/nicholsn)

#### MINOR IMPROVEMENTS

- update URLs for known CKAN instances behind the
  [`servers()`](https://docs.ropensci.org/ckanr/reference/servers.md)
  function ([\#162](https://github.com/ropensci/ckanr/issues/162))
  ([\#167](https://github.com/ropensci/ckanr/issues/167))
  ([\#170](https://github.com/ropensci/ckanr/issues/170))
- .Rbuildignore README.md and vignettes
  ([\#171](https://github.com/ropensci/ckanr/issues/171))
- `extras` now passed in HTTP request in
  [`package_create()`](https://docs.ropensci.org/ckanr/reference/package_create.md)
  as a top level part of the request body rather than as a named
  `extras` element
  ([\#158](https://github.com/ropensci/ckanr/issues/158)) thanks
  [@galaH](https://github.com/galaH)
- change in
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md):
  now when a zip file has a subdirectory an `NA` is returned rather than
  `character(0)` ([\#164](https://github.com/ropensci/ckanr/issues/164))
- change in the `...` parameter in
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md):
  was used to pass through curl options to the http request but now is
  used to pass through additional parameters to either `read.csv`,
  [`xml2::read_xml`](http://xml2.r-lib.org/reference/read_xml.md),
  [`jsonlite::fromJSON`](https://jeroen.r-universe.dev/jsonlite/reference/fromJSON.html),
  [`sf::st_read()`](https://r-spatial.github.io/sf/reference/st_read.html),
  [`read.table()`](https://rdrr.io/r/utils/read.table.html), or
  [`readxl::read_excel`](https://readxl.tidyverse.org/reference/read_excel.html)
  ([\#165](https://github.com/ropensci/ckanr/issues/165))
- updated docs for
  [`package_create()`](https://docs.ropensci.org/ckanr/reference/package_create.md)
  and
  [`group_create()`](https://docs.ropensci.org/ckanr/reference/group_create.md) -
  change `groups` parameter description to explain what kind of input is
  expected ([\#168](https://github.com/ropensci/ckanr/issues/168))
- updated docs for
  [`package_update()`](https://docs.ropensci.org/ckanr/reference/package_update.md)
  and
  [`resource_update()`](https://docs.ropensci.org/ckanr/reference/resource_update.md) -
  illustrate possible data loss when updating with incomplete package
  metadata ([\#108](https://github.com/ropensci/ckanr/issues/108))

## ckanr 0.5.0

CRAN release: 2020-07-30

#### NEW FEATURES

- [`package_create()`](https://docs.ropensci.org/ckanr/reference/package_create.md)
  gains parameter `private` (boolean)
  ([\#145](https://github.com/ropensci/ckanr/issues/145))
- add support for resource extras.
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md)
  and
  [`resource_update()`](https://docs.ropensci.org/ckanr/reference/resource_update.md)
  gain new parameter `extras`, while
  [`resource_patch()`](https://docs.ropensci.org/ckanr/reference/resource_patch.md)
  function doesn’t change but gains an example of adding an extra
  ([\#149](https://github.com/ropensci/ckanr/issues/149))
  ([\#150](https://github.com/ropensci/ckanr/issues/150)) thanks
  [@nicholsn](https://github.com/nicholsn)
- [`package_patch()`](https://docs.ropensci.org/ckanr/reference/package_patch.md)
  gains `extras` parameter
  ([\#94](https://github.com/ropensci/ckanr/issues/94)) see also
  ([\#147](https://github.com/ropensci/ckanr/issues/147))

#### MINOR IMPROVEMENTS

- replace httr with crul throughout package
  ([\#86](https://github.com/ropensci/ckanr/issues/86))
  ([\#151](https://github.com/ropensci/ckanr/issues/151))
- use markdown for docs
  ([\#148](https://github.com/ropensci/ckanr/issues/148))
- [`package_patch()`](https://docs.ropensci.org/ckanr/reference/package_patch.md),
  [`package_show()`](https://docs.ropensci.org/ckanr/reference/package_show.md),
  [`package_activity_list()`](https://docs.ropensci.org/ckanr/reference/package_activity_list.md),
  [`package_delete()`](https://docs.ropensci.org/ckanr/reference/package_delete.md),
  [`package_update()`](https://docs.ropensci.org/ckanr/reference/package_update.md),
  and
  [`related_create()`](https://docs.ropensci.org/ckanr/reference/related_create.md)
  now pass on `key` parameter value to `as.ckan_package` internally;
  same for
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md)
  and
  [`resource_show()`](https://docs.ropensci.org/ckanr/reference/resource_show.md),
  but passed to
  [`as.ckan_resource()`](https://docs.ropensci.org/ckanr/reference/as.ckan_resource.md)
  ([\#145](https://github.com/ropensci/ckanr/issues/145))
  ([\#146](https://github.com/ropensci/ckanr/issues/146))
- [`servers()`](https://docs.ropensci.org/ckanr/reference/servers.md)
  gains two additional CKAN urls
  ([\#155](https://github.com/ropensci/ckanr/issues/155))
- [`package_show()`](https://docs.ropensci.org/ckanr/reference/package_show.md)
  called
  [`as.ckan_package()`](https://docs.ropensci.org/ckanr/reference/as.ckan_package.md)
  within it, which itself calls
  [`package_show()`](https://docs.ropensci.org/ckanr/reference/package_show.md) -
  fixed now ([\#127](https://github.com/ropensci/ckanr/issues/127))

#### BUG FIXES

- fix for
  [`resource_search()`](https://docs.ropensci.org/ckanr/reference/resource_search.md)
  and `tag_search`: both were not allowing a query to be more than
  length 1 ([\#153](https://github.com/ropensci/ckanr/issues/153))
- fix for `print.ckan_package`: wasn’t handling well results from
  [`package_search()`](https://docs.ropensci.org/ckanr/reference/package_search.md)
  that had a named list of locale specific results
  ([\#152](https://github.com/ropensci/ckanr/issues/152))

## ckanr 0.4.0

CRAN release: 2019-10-11

#### NEW FEATURES

- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  gains parameter `key` for a CKAN API key; if given the API key is now
  included in the request headers
  ([\#133](https://github.com/ropensci/ckanr/issues/133)) see also
  ([\#122](https://github.com/ropensci/ckanr/issues/122)) by
  [@sharlagelfand](https://github.com/sharlagelfand)
- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  gains ability to read xls/xlsx files with multiple sheets
  ([\#135](https://github.com/ropensci/ckanr/issues/135)) by
  [@sharlagelfand](https://github.com/sharlagelfand)

#### MINOR IMPROVEMENTS

- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  now sets `stringsAsFactors = FALSE` when reading data
  ([\#141](https://github.com/ropensci/ckanr/issues/141))
  ([\#142](https://github.com/ropensci/ckanr/issues/142)) thanks
  [@LVG77](https://github.com/LVG77)
  [@sharlagelfand](https://github.com/sharlagelfand)
- in
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md),
  use `basename(x)` instead of `gsub(paste0(tempdir(), "/"), "", x)`, to
  get file path ([\#140](https://github.com/ropensci/ckanr/issues/140))
  by [@sharlagelfand](https://github.com/sharlagelfand)
- in
  [`package_search()`](https://docs.ropensci.org/ckanr/reference/package_search.md)
  handle better cases where the CKAN version can not be determined
  ([\#139](https://github.com/ropensci/ckanr/issues/139)) && fix logic
  for when `default_schema` and `include_private` parameters are
  included based on the CKAN version
  ([\#137](https://github.com/ropensci/ckanr/issues/137)) by
  [@sharlagelfand](https://github.com/sharlagelfand)
- improve
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md):
  old behavior of the fxn with zip files was that it only worked if the
  zip file contained shp files; works more generally now, e.g., a zip
  file containing a csv file
  ([\#132](https://github.com/ropensci/ckanr/issues/132)) by
  [@sharlagelfand](https://github.com/sharlagelfand)
- fix
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  examples that weren’t working
  ([\#134](https://github.com/ropensci/ckanr/issues/134)) by
  [@sharlagelfand](https://github.com/sharlagelfand)
- fix to parsing CKAN version numbers, new internal fxn
  `parse_version_number()` - now properly parses CKAN version numbers
  that include patch and dev versions
  ([\#136](https://github.com/ropensci/ckanr/issues/136)) by
  [@sharlagelfand](https://github.com/sharlagelfand)

## ckanr 0.3.0

CRAN release: 2019-07-23

#### NEW FEATURES

- new package author Sharla Gelfand !!!
- new functions for users:
  [`user_create()`](https://docs.ropensci.org/ckanr/reference/user_create.md)
  and
  [`user_delete()`](https://docs.ropensci.org/ckanr/reference/user_delete.md)
  ([\#82](https://github.com/ropensci/ckanr/issues/82))
- [`package_show()`](https://docs.ropensci.org/ckanr/reference/package_show.md)
  gains `key` parameter to pass an API key
  ([\#97](https://github.com/ropensci/ckanr/issues/97))
- [`package_search()`](https://docs.ropensci.org/ckanr/reference/package_search.md)
  gains new parameters: `include_drafts`, `include_private`,
  `use_default_schema`, and `facet.mincount`
  ([\#107](https://github.com/ropensci/ckanr/issues/107))
- function [`fetch()`](https://dbi.r-dbi.org/reference/dbFetch.html)
  changed to
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
- gains function `organization_delet()` to delete an organization
  ([\#83](https://github.com/ropensci/ckanr/issues/83))
- gains function
  [`ckan_version()`](https://docs.ropensci.org/ckanr/reference/ckan_info.md)
  to get version info for a CKAN instance
- gains methods for creating a CKAN remote instance as a dplyr backend:
  gains
  [`src_ckan()`](https://docs.ropensci.org/ckanr/reference/src_ckan.md)
  and it’s s3 methods `tbl` and `src_tbls`, `sql_translate_env`. in
  addition gains the S3 methods `db_begin`, `db_explain`,
  `db_has_table`, `db_insert_into`, `db_query_fields`, `db_query_rows`

#### MINOR IMPROVEMENTS

- fix some tests ([\#62](https://github.com/ropensci/ckanr/issues/62))
- fix to
  [`ds_create()`](https://docs.ropensci.org/ckanr/reference/ds_create.md)
  to properly format body with json data
  ([\#85](https://github.com/ropensci/ckanr/issues/85)) thanks
  [@mattfullerton](https://github.com/mattfullerton)
- tests added for
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  ([\#118](https://github.com/ropensci/ckanr/issues/118)) thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  gains `format` parameter if the user knows the file format (useful
  when the file format can not be guessed)
  ([\#117](https://github.com/ropensci/ckanr/issues/117)) thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- `ckan_fetch` gain support for handling geojson
  ([\#123](https://github.com/ropensci/ckanr/issues/123)) thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- `ckan_fetch` was writing to current working directory in some cases -
  fixed to writing to temp files and cleaning up
  ([\#125](https://github.com/ropensci/ckanr/issues/125))
  ([\#128](https://github.com/ropensci/ckanr/issues/128))
  ([\#129](https://github.com/ropensci/ckanr/issues/129)) thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- add USDA CKAN instance to the
  [`servers()`](https://docs.ropensci.org/ckanr/reference/servers.md)
  function ([\#68](https://github.com/ropensci/ckanr/issues/68))
- [`ds_create_dataset()`](https://docs.ropensci.org/ckanr/reference/ds_create_dataset.md)
  marked as deprecated; see `recourse_create()` instead
  ([\#80](https://github.com/ropensci/ckanr/issues/80)) (via
  [\#79](https://github.com/ropensci/ckanr/issues/79))
- removed the internal [`stop()`](https://rdrr.io/r/base/stop.html) call
  in
  [`tag_create()`](https://docs.ropensci.org/ckanr/reference/tag_create.md):
  now can be used, though haven’t been able to test this function as you
  need to be a sysadmin to use it
  ([\#81](https://github.com/ropensci/ckanr/issues/81))
- [`ds_search()`](https://docs.ropensci.org/ckanr/reference/ds_search.md):
  code spacing fixes
  ([\#69](https://github.com/ropensci/ckanr/issues/69))
- [`resource_update()`](https://docs.ropensci.org/ckanr/reference/resource_update.md)
  gains more examples and tests
  ([\#66](https://github.com/ropensci/ckanr/issues/66))
- CKAN API key standardization: `key` parameter now in all fxns that
  make http requests - and reordering of `url` and `key` params in that
  order across all functions
  ([\#122](https://github.com/ropensci/ckanr/issues/122))
  ([\#124](https://github.com/ropensci/ckanr/issues/124))
- repair ORCID links in DESCRIPTION file
  ([\#124](https://github.com/ropensci/ckanr/issues/124)) by Florian

#### BUG FIXES

- fix to
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md):
  `upload` param was inappropriately a required param
  ([\#75](https://github.com/ropensci/ckanr/issues/75)) thanks
  [@mingbogo](https://github.com/mingbogo)
- fixes to
  [`resource_update()`](https://docs.ropensci.org/ckanr/reference/resource_update.md):
  date sent in `last_modified` in request body needed to be converted to
  character ([\#96](https://github.com/ropensci/ckanr/issues/96))
  (thanks [@jasonajones73](https://github.com/jasonajones73)); and the
  date format needed fixing
  ([\#119](https://github.com/ropensci/ckanr/issues/119)) (thanks
  [@florianm](https://github.com/florianm))
- fix to
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md) -
  use `sf` instead of `maptools`; in addition `ckan_fetch` can now parse
  xlsx files in addition to xls files;
  ([\#114](https://github.com/ropensci/ckanr/issues/114))
  ([\#115](https://github.com/ropensci/ckanr/issues/115)) thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- fix to
  [`package_search()`](https://docs.ropensci.org/ckanr/reference/package_search.md):
  this route fails if parameters that did not exist in the CKAN instance
  are given; internally remove parameters as needed from query params by
  pinging the CKAN instance for its version
  ([\#120](https://github.com/ropensci/ckanr/issues/120))

## ckanr 0.1.0

CRAN release: 2015-10-22

#### NEW FEATURES

- Released to CRAN.
