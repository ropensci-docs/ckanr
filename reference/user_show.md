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

  (character) Package identifier.

- user_obj:

  (user dictionary) The user dictionary of the user (optional)

- include_datasets:

  (logical) Include a list of datasets the user has created. If it is
  the same user or a sysadmin requesting, it includes datasets that are
  draft or private. (optional, default:False, limit:50)

- include_num_followers:

  (logical) Include the number of followers the user has (optional,
  default:False)

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
