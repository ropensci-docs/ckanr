# CKAN server URLS and other info

CKAN server URLS and other info

## Usage

``` r
servers()
```

## Details

CKAN instances from https://github.com/ckan/ckan-instances/

## Examples

``` r
if (FALSE) { # \dontrun{
servers()
ckan_info(servers()[5])

# what version is each CKAN server running
out <- lapply(servers()[1:6], function(w) {
  ckan_version(w)$version_num
})
} # }
```
