# ckan_vocabulary class helpers

ckan_vocabulary class helpers

## Usage

``` r
as.ckan_vocabulary(x, ...)

is.ckan_vocabulary(x)
```

## Arguments

- x:

  Variety of inputs: character, list, or ckan_vocabulary object

- ...:

  Additional arguments passed to
  [`vocabulary_show()`](https://docs.ropensci.org/ckanr/reference/vocabulary.md)
  when retrieving by identifier.

## Examples

``` r
if (FALSE) { # \dontrun{
ckanr_setup(url = "https://demo.ckan.org/", key = getOption("ckan_demo_key"))

vocab <- vocabulary_create(name = sprintf("demo_vocab_%s", sample.int(1e4, 1)))

# create class from an id
as.ckan_vocabulary(vocab$id)

# passing through existing objects is a no-op
as.ckan_vocabulary(vocab)
} # }
```
