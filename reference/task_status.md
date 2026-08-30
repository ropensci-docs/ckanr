# CKAN task status maintenance

These helpers wrap the sysadmin-only task status endpoints that CKAN
uses to track background operations (eg DataPusher runs).

## Usage

``` r
task_status_show(
  id = NULL,
  entity_id = NULL,
  entity_type = NULL,
  task_type = NULL,
  task_key = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

task_status_update(
  id = NULL,
  entity_id = NULL,
  entity_type = NULL,
  task_type = NULL,
  task_key = NULL,
  value = NULL,
  state = NULL,
  last_updated = NULL,
  error = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

task_status_update_many(
  data,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)

task_status_delete(
  id = NULL,
  entity_id = NULL,
  entity_type = NULL,
  task_type = NULL,
  task_key = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) Task status identifier to inspect or mutate.

- entity_id:

  (character) ID of the dataset/resource related to the task.

- entity_type:

  (character) CKAN domain object type (e.g., "dataset").

- task_type:

  (character) Task namespace such as "datapusher".

- task_key:

  (character) Additional task key (e.g., queue name).

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

- value:

  (character) Free-form value, often notes or payload references.

- state:

  (character) Task state such as "queued", "running", or "finished".

- last_updated:

  (character) Timestamp string for the last state change.

- error:

  (character) Optional serialized error blob attached to the task.

- data:

  (list) For `task_status_update_many()`, a list of task status
  dictionaries to update.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = "my-ckan-key")
task_status_show(entity_type = "dataset", entity_id = "my-dataset")
task_status_update(
  entity_id = "my-dataset",
  entity_type = "dataset",
  task_type = "datapusher",
  task_key = "default",
  value = "queued",
  state = "running"
)
} # }
```
