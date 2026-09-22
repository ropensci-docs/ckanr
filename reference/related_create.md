# Create a related item

Create a related item

## Usage

``` r
related_create(
  id,
  title,
  type,
  description = NULL,
  related_id = NULL,
  related_url = NULL,
  image_url = NULL,
  url = get_default_url(),
  key = get_default_key(),
  as = "list",
  ...
)
```

## Arguments

- id:

  (character) ID of the package. You add the related item to this
  package. The value must be an alphanumeric string. Required.

- title:

  (character) Title of the related item. Required.

- type:

  (character) Type of the related item. The value is one of API,
  application, idea, news article, paper, post or visualization.
  Required.

- description:

  (character) Description of the related item. Optional.

- related_id:

  (character) ID to assign to the related item. If the value is blank,
  the function assigns an ID. Optional.

- related_url:

  (character) URL for the related item. Optional.

- image_url:

  (character) URL of an image for the related item. Optional.

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

# create a package
(res <- package_create("hello-mars"))

# create a related item
related_create(res, title = "asdfdaf", type = "idea")

# pipe operations together
package_create("foobbbbbarrrr") |>
  related_create(
    title = "my resource",
    type = "visualization"
  )
} # }
```
