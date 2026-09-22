# ckan_file class helpers

ckan_file class helpers

## Usage

``` r
as.ckan_file(x, ...)

is.ckan_file(x)
```

## Arguments

- x:

  One of character, list, or ckan_file class object

- ...:

  Extra arguments. If `x` is character, the function passes them on to
  [`file_show()`](https://docs.ropensci.org/ckanr/reference/files.md)

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(
  url = "https://demo.ckan.org/",
  key = getOption("ckan_demo_key")
)

# create item class from only an item ID
as.ckan_file("file-id-here")

# gives back itself
(x <- as.ckan_file(list(id = "file-id-here", name = "file.txt")))
as.ckan_file(x)
} # }
```
