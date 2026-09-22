# Changelog

## ckanr (development version)

## ckanr 0.9.0

#### BUG FIXES

- Refresh the DataStore DBI and dbplyr integration for the dbplyr
  2nd-edition interface. Use
  [`dplyr::tbl()`](https://dplyr.tidyverse.org/reference/tbl.html) with
  a `CKANConnection` as the primary interface. The connection remains
  read-only ([\#187](https://github.com/ropensci/ckanr/issues/187),
  [\#240](https://github.com/ropensci/ckanr/issues/240)).
- Mark [`median()`](https://rdrr.io/r/stats/median.html) and
  [`quantile()`](https://rdrr.io/r/stats/quantile.html) as unsupported
  DataStore translations. Add execution tests for joins, semi-joins, set
  operations, wrapped queries, and the supported custom aggregate
  translations ([\#188](https://github.com/ropensci/ckanr/issues/188)).
- [`revision_list()`](https://docs.ropensci.org/ckanr/reference/revision_list.md)
  and
  [`package_revision_list()`](https://docs.ropensci.org/ckanr/reference/package_revision_list.md)
  no longer crash when the CKAN version is unknown. An unknown version
  passes through to the API call
  ([\#200](https://github.com/ropensci/ckanr/issues/200)).
- `parse_version_number()` returns `NA` with no warning for short or
  missing input.
- [`ping()`](https://docs.ropensci.org/ckanr/reference/ping.md)
  validates the `as` argument. `as = "logical"` returns `FALSE` on
  failure. `as = "json"` signals an error on failure.
- Availability checks (`ckan_action_available()`,
  `activity_email_notifications_enabled()`) no longer cache transient
  failures.
- `read_session()` stops with a clear error for unsupported file formats
  instead of returning `NULL`.
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  rejects a missing format before any download.
- `resolve_group_or_org_id()` returns the name for name-only lists,
  matching the sibling helpers.
- The `related_*()` helpers stop with a clear message when the CKAN
  instance lacks the related API.
- Startup resets an empty `CKANR_DEFAULT_URL` to the default. Docs name
  the correct default URL.
- Add
  [`ds_upsert()`](https://docs.ropensci.org/ckanr/reference/datastore_extra.md)
  for inserting or updating records in an existing DataStore resource
  ([\#98](https://github.com/ropensci/ckanr/issues/98)).
- Requests now stop early with a clear message when the CKAN URL is
  empty or does not start with `http://` or `https://`
  ([\#154](https://github.com/ropensci/ckanr/issues/154)).
- HTTP API calls now report a clear error when CKAN or a proxy returns a
  non-JSON response instead of exposing a JSON parsing error
  ([\#92](https://github.com/ropensci/ckanr/issues/92)).
- CSV downloads that trigger `EOF within quoted string` now use a base R
  fallback that preserves the remaining rows without adding a dependency
  ([\#180](https://github.com/ropensci/ckanr/issues/180)).

#### DOCS

- Rewrote package prose (help pages, README, vignette, NEWS) in plain
  language. No facts changed.
- Added
  [`ds_search()`](https://docs.ropensci.org/ckanr/reference/ds_search.md)
  examples for selecting fields and filtering several fields
  ([\#101](https://github.com/ropensci/ckanr/issues/101)). Added
  migration guidance for deprecated
  [`ds_create_dataset()`](https://docs.ropensci.org/ckanr/reference/ds_create_dataset.md)
  users ([\#214](https://github.com/ropensci/ckanr/issues/214)).
- Added guidance for
  [`package_patch()`](https://docs.ropensci.org/ckanr/reference/package_patch.md)
  with ckanext-scheming custom fields
  ([\#233](https://github.com/ropensci/ckanr/issues/233)), thanks
  [@sboots](https://github.com/sboots).
- Added a vignette example for listing all datasets in an organization
  ([\#183](https://github.com/ropensci/ckanr/issues/183)).

#### MAINTENANCE

- Replaced the `magrittr` dependency with the native R pipe
  ([\#213](https://github.com/ropensci/ckanr/issues/213)).
- Added support for external resource URLs in
  [`resource_update()`](https://docs.ropensci.org/ckanr/reference/resource_update.md)
  and
  [`resource_patch()`](https://docs.ropensci.org/ckanr/reference/resource_patch.md)
  ([\#232](https://github.com/ropensci/ckanr/issues/232)).
- Added the remaining CKAN 2.11 and 2.12 API wrappers
  ([\#238](https://github.com/ropensci/ckanr/issues/238)).

## ckanr 0.8.1

#### MAINTENANCE

- Change the default CKAN URL to <https://demo.ckan.org/>
- Update servers(), thanks [@nn-at](https://github.com/nn-at)
  ([\#176](https://github.com/ropensci/ckanr/issues/176))
- Replace the deprecated `lazyeval` dependency with `rlang`. Update
  dplyr tests and development tooling. Contributors need only the modern
  tidy-eval stack ([\#93](https://github.com/ropensci/ckanr/issues/93))

## ckanr 0.8.0

#### NEW FEATURES

This release adds the remaining endpoints of the CKAN 2.11 API.

- Add dataset collaborator helpers
  [`package_collaborator_list()`](https://docs.ropensci.org/ckanr/reference/package_collaborator_list.md),
  [`package_collaborator_list_for_user()`](https://docs.ropensci.org/ckanr/reference/package_collaborator_list_for_user.md),
  [`package_collaborator_create()`](https://docs.ropensci.org/ckanr/reference/package_collaborator_create.md),
  and
  [`package_collaborator_delete()`](https://docs.ropensci.org/ckanr/reference/package_collaborator_delete.md).
- Add membership utilities
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
  [`organization_list_for_user()`](https://docs.ropensci.org/ckanr/reference/organization_list_for_user.md).
  They manage user access across groups and organizations.
- Add relationship management wrappers
  [`package_relationships_list()`](https://docs.ropensci.org/ckanr/reference/package_relationships_list.md),
  [`package_relationship_create()`](https://docs.ropensci.org/ckanr/reference/package_relationship_create.md),
  [`package_relationship_update()`](https://docs.ropensci.org/ckanr/reference/package_relationship_update.md),
  and
  [`package_relationship_delete()`](https://docs.ropensci.org/ckanr/reference/package_relationship_delete.md).
  They accept S3 inputs.
- Add dataset maintenance helpers
  [`package_revise()`](https://docs.ropensci.org/ckanr/reference/package_revise.md),
  [`package_resource_reorder()`](https://docs.ropensci.org/ckanr/reference/package_resource_reorder.md),
  [`package_owner_org_update()`](https://docs.ropensci.org/ckanr/reference/package_owner_org_update.md),
  and
  [`dataset_purge()`](https://docs.ropensci.org/ckanr/reference/dataset_purge.md)
  for automation workflows.
- Add the `ckan_resource_view` S3 class with wrappers for
  [`resource_view_list()`](https://docs.ropensci.org/ckanr/reference/resource_view_list.md),
  [`resource_view_show()`](https://docs.ropensci.org/ckanr/reference/resource_view_show.md),
  [`resource_view_create()`](https://docs.ropensci.org/ckanr/reference/resource_view_create.md),
  [`resource_view_update()`](https://docs.ropensci.org/ckanr/reference/resource_view_update.md),
  [`resource_view_reorder()`](https://docs.ropensci.org/ckanr/reference/resource_view_reorder.md),
  [`resource_view_delete()`](https://docs.ropensci.org/ckanr/reference/resource_view_delete.md),
  [`resource_view_clear()`](https://docs.ropensci.org/ckanr/reference/resource_view_clear.md),
  [`resource_create_default_resource_views()`](https://docs.ropensci.org/ckanr/reference/resource_create_default_resource_views.md),
  and
  [`package_create_default_resource_views()`](https://docs.ropensci.org/ckanr/reference/package_create_default_resource_views.md).
  They manage CKAN previews from R.
- Refresh the follower/followee helpers: `dataset_*`, `group_*`, and
  `user_*` functions now expose counts, lists, follow/unfollow flows,
  and “am I following” probes, plus followee dashboards
  ([`followee_count()`](https://docs.ropensci.org/ckanr/reference/followee_counts.md),
  [`followee_list()`](https://docs.ropensci.org/ckanr/reference/followee_lists.md),
  `dataset_followee_*()`, `group_followee_*()`, `user_followee_*()`).
  Organization helpers stay unavailable because CKAN 2.11+ no longer
  exposes those endpoints.
- Add activity-stream helpers
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
  [`send_email_notifications()`](https://docs.ropensci.org/ckanr/reference/activity_helpers.md).
  They skip when the `activity` plugin is disabled.
- Add sysadmin-only vocabulary helpers
  ([`vocabulary_list()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md),
  [`vocabulary_show()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md),
  [`vocabulary_create()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md),
  [`vocabulary_update()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md),
  [`vocabulary_delete()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md))
  plus
  [`tag_autocomplete()`](https://docs.ropensci.org/ckanr/reference/tag_autocomplete.md).
  They complete the tag discovery toolkit.
- Add the admin and operations toolkit: task-status maintenance
  (`task_status_*()`), term translations, runtime config editing,
  Redis/RQ job controls, API token lifecycle helpers, and diagnostic
  wrappers for
  [`status_show()`](https://docs.ropensci.org/ckanr/reference/diagnostics.md)/[`help_show()`](https://docs.ropensci.org/ckanr/reference/diagnostics.md).

#### TESTS

- Add integration coverage for collaborator and membership endpoints.
  Tests skip when the target CKAN instance lacks the relevant feature
  flags.
- Cover the new relationship and dataset maintenance helpers. Opt-in
  purge coverage runs behind the `CKANR_ALLOW_PURGE_TESTS` gate.
- Exercise the resource view lifecycle
  (create/list/show/update/reorder/delete) plus default view helpers
  when the `text_view` plugin is available. Tests skip otherwise.
- Expand the follower tests to follow/unfollow datasets, groups, and
  users. Tests verify the followee dashboards and clean up temporary
  relationships.
- Add skips keyed off
  [`status_show()`](https://docs.ropensci.org/ckanr/reference/diagnostics.md)
  for all activity and dashboard tests. Tests use the new helpers when
  the `activity` plugin is available.
- Cover the new vocabulary lifecycle and
  [`tag_autocomplete()`](https://docs.ropensci.org/ckanr/reference/tag_autocomplete.md)
  helpers. Tests skip when the configured CKAN user lacks sysadmin
  rights.
- Exercise the admin/ops helpers with sysadmin-gated tests. They verify
  task-status roundtrips, term translations, config changes, job
  management, API tokens, and diagnostics. Tests skip when the test key
  lacks sufficient privileges.

#### MAINTENANCE

- Add file `.github/copilot-instructions.md` to allow GenAI to reason
  over the codebase. The file also helps human contributors.

## ckanr 0.7.1

#### NEW FEATURES

- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md),
  `read_session()` and `fetch_GET()` now support parquet files, thanks
  [@hannaboe](https://github.com/hannaboe)
  ([\#217](https://github.com/ropensci/ckanr/issues/217))

#### MAINTENANCE

- A devcontainer provides a disposable CKAN instance for testing. It
  replaces an external CKAN instance and GitHub secrets for testing. It
  offers CKAN v2.9-2.11
  ([\#216](https://github.com/ropensci/ckanr/issues/216)
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

- [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md),
  [`package_update()`](https://docs.ropensci.org/ckanr/reference/package_update.md),
  and
  [`package_patch()`](https://docs.ropensci.org/ckanr/reference/package_patch.md)
  gain parameter `http_method`. It passes to
  [`as.ckan_package()`](https://docs.ropensci.org/ckanr/reference/as.ckan_package.md)
  internally, but it does not affect the HTTP request for the main point
  of the function
  ([\#163](https://github.com/ropensci/ckanr/issues/163)), thanks
  [@hannaboe](https://github.com/hannaboe)
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
- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  returns `NA` rather than `character(0)` when a zip file has a
  subdirectory ([\#164](https://github.com/ropensci/ckanr/issues/164))
- The `...` parameter in
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  passes additional parameters to `read.csv`,
  [`xml2::read_xml`](http://xml2.r-lib.org/reference/read_xml.md),
  [`jsonlite::fromJSON`](https://jeroen.r-universe.dev/jsonlite/reference/fromJSON.html),
  [`sf::st_read()`](https://r-spatial.github.io/sf/reference/st_read.html),
  [`read.table()`](https://rdrr.io/r/utils/read.table.html), or
  [`readxl::read_excel`](https://readxl.tidyverse.org/reference/read_excel.html)
  ([\#165](https://github.com/ropensci/ckanr/issues/165)). It no longer
  passes curl options to the http request
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
  now pass on `key` parameter value to `as.ckan_package` internally. The
  same holds for
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
  calls
  [`as.ckan_package()`](https://docs.ropensci.org/ckanr/reference/as.ckan_package.md)
  within it, which calls
  [`package_show()`](https://docs.ropensci.org/ckanr/reference/package_show.md).
  This is fixed ([\#127](https://github.com/ropensci/ckanr/issues/127))

#### BUG FIXES

- Fix
  [`resource_search()`](https://docs.ropensci.org/ckanr/reference/resource_search.md)
  and `tag_search`. They allow a query of length more than 1
  ([\#153](https://github.com/ropensci/ckanr/issues/153))
- Fix `print.ckan_package`. It handles results from
  [`package_search()`](https://docs.ropensci.org/ckanr/reference/package_search.md)
  with a named list of locale specific results
  ([\#152](https://github.com/ropensci/ckanr/issues/152))

## ckanr 0.4.0

CRAN release: 2019-10-11

#### NEW FEATURES

- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  gains parameter `key` for a CKAN API key. If given, the API key is now
  included in the request headers
  ([\#133](https://github.com/ropensci/ckanr/issues/133),
  [\#122](https://github.com/ropensci/ckanr/issues/122)), thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  gains ability to read xls/xlsx files with multiple sheets
  ([\#135](https://github.com/ropensci/ckanr/issues/135)), thanks
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
  get file path ([\#140](https://github.com/ropensci/ckanr/issues/140)),
  thanks [@sharlagelfand](https://github.com/sharlagelfand)
- in
  [`package_search()`](https://docs.ropensci.org/ckanr/reference/package_search.md)
  handle better cases where the CKAN version can not be determined
  ([\#139](https://github.com/ropensci/ckanr/issues/139)) and fix logic
  for when `default_schema` and `include_private` parameters are
  included based on the CKAN version
  ([\#137](https://github.com/ropensci/ckanr/issues/137)), thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  works with more zip files. Old behavior works only with zip files with
  shp files. It now works with other files, for example a zip file with
  a csv file ([\#132](https://github.com/ropensci/ckanr/issues/132)),
  thanks [@sharlagelfand](https://github.com/sharlagelfand)
- Fix
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md)
  examples that were not working
  ([\#134](https://github.com/ropensci/ckanr/issues/134)), thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- Fix parsing of CKAN version numbers with new internal fxn
  `parse_version_number()`. It parses CKAN version numbers with patch
  and dev versions
  ([\#136](https://github.com/ropensci/ckanr/issues/136)), thanks
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
  and its s3 methods `tbl` and `src_tbls`, `sql_translate_env`. In
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
- `ckan_fetch` writes to temp files and cleans up. It no longer writes
  to the current working directory in some cases
  ([\#125](https://github.com/ropensci/ckanr/issues/125))
  ([\#128](https://github.com/ropensci/ckanr/issues/128))
  ([\#129](https://github.com/ropensci/ckanr/issues/129)) thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- add USDA CKAN instance to the
  [`servers()`](https://docs.ropensci.org/ckanr/reference/servers.md)
  function ([\#68](https://github.com/ropensci/ckanr/issues/68))
- [`ds_create_dataset()`](https://docs.ropensci.org/ckanr/reference/ds_create_dataset.md)
  is deprecated. Use `recourse_create()` instead
  ([\#80](https://github.com/ropensci/ckanr/issues/80)) (via
  [\#79](https://github.com/ropensci/ckanr/issues/79))
- Remove the internal [`stop()`](https://rdrr.io/r/base/stop.html) call
  in
  [`tag_create()`](https://docs.ropensci.org/ckanr/reference/tag_create.md).
  You can use it now. No test covers it because it needs sysadmin rights
  ([\#81](https://github.com/ropensci/ckanr/issues/81))
- [`ds_search()`](https://docs.ropensci.org/ckanr/reference/ds_search.md):
  code spacing fixes
  ([\#69](https://github.com/ropensci/ckanr/issues/69))
- [`resource_update()`](https://docs.ropensci.org/ckanr/reference/resource_update.md)
  gains more examples and tests
  ([\#66](https://github.com/ropensci/ckanr/issues/66))
- CKAN API key standardization: `key` parameter is now in all fxns that
  make http requests. `url` and `key` params follow that order across
  all functions ([\#122](https://github.com/ropensci/ckanr/issues/122))
  ([\#124](https://github.com/ropensci/ckanr/issues/124))
- repair ORCID links in DESCRIPTION file
  ([\#124](https://github.com/ropensci/ckanr/issues/124)) by Florian

#### BUG FIXES

- fix to
  [`resource_create()`](https://docs.ropensci.org/ckanr/reference/resource_create.md):
  `upload` param was inappropriately a required param
  ([\#75](https://github.com/ropensci/ckanr/issues/75)) thanks
  [@mingbogo](https://github.com/mingbogo)
- Fix
  [`resource_update()`](https://docs.ropensci.org/ckanr/reference/resource_update.md).
  The date in `last_modified` in the request body converts to character
  ([\#96](https://github.com/ropensci/ckanr/issues/96)), thanks
  [@jasonajones73](https://github.com/jasonajones73). The date format is
  fixed ([\#119](https://github.com/ropensci/ckanr/issues/119)), by
  [@florianm](https://github.com/florianm)
- Fix
  [`ckan_fetch()`](https://docs.ropensci.org/ckanr/reference/ckan_fetch.md).
  It uses `sf` instead of `maptools`. `ckan_fetch` parses xlsx files and
  xls files ([\#114](https://github.com/ropensci/ckanr/issues/114))
  ([\#115](https://github.com/ropensci/ckanr/issues/115)) thanks
  [@sharlagelfand](https://github.com/sharlagelfand)
- Fix
  [`package_search()`](https://docs.ropensci.org/ckanr/reference/package_search.md).
  This route fails if parameters that did not exist in the CKAN instance
  are given. The code removes parameters as needed from query params. It
  pings the CKAN instance for its version
  ([\#120](https://github.com/ropensci/ckanr/issues/120))

## ckanr 0.1.0

CRAN release: 2015-10-22

#### NEW FEATURES

- Released to CRAN.
