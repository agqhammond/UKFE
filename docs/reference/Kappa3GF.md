# Kappa3 distribution growth factors

Estimated growth factors as a function of return period, with inputs of
Lcv & LSkew (linear coefficient of variation & linear skewness)

## Usage

``` r
Kappa3GF(lcv, lskew, RP)
```

## Arguments

- lcv:

  linear coefficient of variation

- lskew:

  linear skewness

- RP:

  return period

## Value

Kappa3 distribution estimated growth factor

## Details

Growth factors are calculated by the method outlined in Kjeldsen, T
(2019), 'The 3-parameter Kappa distribution as an alternative for use
with FEH pooling groups.'Circulation - The Newsletter of the British
Hydrological Society, no. 142

## Author

Anthony Hammond

## Examples

``` r
# Calculate Kappa growth factor for the 100-year flood
#assuming LCV and LSKEW of 0.165 and 0.17
Kappa3GF(0.165, 0.17, RP = 100)
#> [1] 1
```
