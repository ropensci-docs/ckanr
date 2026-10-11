# ckanr S3 classes

ckanr S3 classes

## The classes

- ckan_package - CKAN package

- ckan_resource - CKAN resource

- ckan_resource_view - CKAN resource view

- ckan_related - CKAN related item

- ckan_file - CKAN file (first-class file entities, CKAN 2.12+)

## Coercion

The `as.ckan_*()` functions for each CKAN object type coerce an object
to an S3 class of that type. For example, you can coerce a package ID as
a character string into an `ckan_package` object by calling
`as.ckan_package(<id>`.

## Testing for classes

To test the class of an object, use an `is._ckan_*()` function for the
classes listed above. The function returns `TRUE` or `FALSE`.

## Manipulation

These are S3 classes. Each class is an R list with an attached class.
The class tells functions what to do with the object. Functions accept
flexible inputs and return flexible outputs. You can edit one of these
classes yourself by changing values in the list.

## See also

[`as.ckan_package()`](https://docs.ropensci.org/ckanr/reference/as.ckan_package.md),
[`as.ckan_resource()`](https://docs.ropensci.org/ckanr/reference/as.ckan_resource.md),
[`as.ckan_resource_view()`](https://docs.ropensci.org/ckanr/reference/as.ckan_resource_view.md),
[`as.ckan_related()`](https://docs.ropensci.org/ckanr/reference/as.ckan_related.md),
[`as.ckan_file()`](https://docs.ropensci.org/ckanr/reference/as.ckan_file.md)
