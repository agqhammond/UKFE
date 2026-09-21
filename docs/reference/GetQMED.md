# QMED from a gauged site suitable for QMED

Provides QMED (median annual maximum flow) from a site suitable for
QMED, using the site reference. This provides the observed median of the
annual maximum sample (excluding rejected observations) for the site of
interest. It does not apply any adjustments or updates to account for
non-stationarity.

## Usage

``` r
GetQMED(x)
```

## Arguments

- x:

  the gauged reference

## Value

the median annual maximum

## Author

Anthony Hammond

## Examples

``` r
# Get the observed QMED from site 55002
GetQMED(55002)
#> [1] 431
```
