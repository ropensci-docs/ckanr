# Generic action function

You must set the CKAN action and the HTTP verb. You also set query
parameters, body data, and headers.

## Usage

``` r
ckan_action(
  action,
  query = NULL,
  body = NULL,
  headers = list(),
  verb = "POST",
  url = get_default_url(),
  key = get_default_key(),
  ...
)
```

## Arguments

- action:

  A valid CKAN API action name (for example, "package_list",
  "package_show"). See the CKAN API documentation for a full list of
  actions: https://docs.ckan.org/en/latest/api/index.html

- query:

  a named list of URL query parameters

- body:

  Data for the body of a request. See
  https://docs.ropensci.org/crul/reference/verb-POST.html for options

- headers:

  a named list of request headers

- verb:

  HTTP request verb, for example, GET, POST

- url:

  Base url to use. Default: https://demo.ckan.org/ See also
  [`ckanr_setup()`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)
  and
  [`get_default_url()`](https://docs.ropensci.org/ckanr/reference/ckanr_settings.md)

- key:

  A privileged CKAN API key. Default: your key set with
  [`ckanr_setup`](https://docs.ropensci.org/ckanr/reference/ckanr_setup.md)

- ...:

  Curl args. The function sends them to the relevant
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)
  method for the `verb` parameter (optional)

## Value

A text string. The function returns text because the data type is
unknown ahead of time. You parse the text as needed.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

ckan_action("package_list")
ckan_action("package_list", verb = "GET")
ckan_action("package_list", url = "https://data.nhm.ac.uk")
} # }
```
