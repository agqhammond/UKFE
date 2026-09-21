# Generalised logistic distribution growth factors

Estimated growth factors as a function of return period, with inputs of
Lcv & LSkew (linear coefficient of variation & linear skewness)

## Usage

``` r
GenLogGF(lcv, lskew, RP)
```

## Arguments

- lcv:

  linear coefficient of variation

- lskew:

  linear skewness

- RP:

  return period

## Value

Generalised logistic estimated growth factor

## Details

Growth factors are calculated by the method outlined in the Flood
Estimation Handbook, volume 3, 1999.

## Author

Anthony Hammond

## Examples

``` r
# Estimate the 50-year growth factor from an Lcv and Lskew of 0.17 and 0.04, respectively
GenLogGF(0.17, 0.04, RP = 50)
#> [1] 1.722074
```
