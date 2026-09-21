# Gumbel distribution growth factors

Estimated growth factors as a function of return period, with inputs of
Lcv & LSkew (linear coefficient of variation & linear skewness)

## Usage

``` r
GumbelGF(lcv, RP)
```

## Arguments

- lcv:

  linear coefficient of variation

- RP:

  return period

## Value

Gumbel estimated growth factor

## Details

Growth factors are calculated by the method outlined in the Flood
Estimation Handbook, volume 3, 1999.

## Author

Anthony Hammond

## Examples

``` r
# Estimate the 50-year growth factor from an Lcv of 0.17
GumbelGF(0.17, RP = 50)
#> [1] 1.914338
```
