# Urban adjustment for the linear coefficient of variation (Lcv)

Urbanises or de-urbanises the Lcv using the FEH2025 methods

## Usage

``` r
LcvUrb(LCV, URBEXT, DeUrb = FALSE)
```

## Arguments

- LCV:

  the Lcv (numeric)

- URBEXT:

  quantification of urban and suburbanisation for the subject catchment
  (URBEXT2015)

- DeUrb:

  logical argument with a default of FALSE. If set to TRUE,
  de-urbanisation adjustment is performed, if FALSE, urbanisation
  adjustment is performed

## Value

The urban adjust Lcv or the de-urbanised Lcv

## Author

Anthony Hammond

## Examples

``` r
# Apply a de-urbanisation with an LCV of 0.21 and an URBEXT of 0.1138
LcvUrb(0.21, 0.1138, DeUrb = TRUE)
#> [1] 0.2258846

# Apply and urban adjustment using LCV 0.196 and URBEXT of 0.1138
LcvUrb(0.196, 0.1138)
#> [1] 0.1822169
```
