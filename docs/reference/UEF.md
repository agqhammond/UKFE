# Urban expansion factor

This function provides a coefficient to multiply by URBEXT2015 to adjust
it to a given year

## Usage

``` r
UEF(Year)
```

## Arguments

- Year:

  The year for consideration. Numeric

## Value

A numeric urban expansion factor.

## Details

The urban expansion factor is that of the FEH2025 method. The urban
expansion model assumes a national average expansion as a function of
year. This means that on some catchments the value will be overestimated
(primarily on rural ones) and on others the value will be underestimated
(primarily on urban ones).

## Author

Anthony Hammond

## Examples

``` r
# Get an expansion factor for the year 2025
UEF(2025)
#> [1] 1.047059
```
