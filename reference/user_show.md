# Show a user.

Show a user.

## Usage

``` r
user_show(
  id,
  user_obj = NULL,
  include_datasets = FALSE,
  include_num_followers = FALSE,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) User identifier.

- user_obj:

  (user dictionary) User dictionary of the user. Optional.

- include_datasets:

  (logical) Include a list of datasets that the user creates. If the
  same user or a sysadmin requests the data, the function includes
  datasets that are draft or private. Optional. Default is False. The
  limit is 50.

- include_num_followers:

  (logical) Include the number of followers of the user. Optional.
  Default is False.

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
# Setup
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

# show user
user_show("sckottie")

# include datasets
user_show("sckottie", include_datasets = TRUE)

# include datasets
user_show("sckottie", include_num_followers = TRUE)
} # }
```
