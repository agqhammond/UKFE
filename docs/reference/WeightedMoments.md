# Weighted Lmoment ratios (LCV and LSKEW) from a pooling group

Provides the weighted LCV and LSKEW for a pooling group

## Usage

``` r
WeightedMoments(x)
```

## Arguments

- x:

  pooling group derived with the Pool() function

## Value

A data.frame with site references in the first column and associated
weights in the second

## Details

Weighting method as according to: FEH2025

## Author

Anthony Hammond

## Examples

``` r
# Get some CDs, form a gauged pooling group, and estimate gauged Lcv
cds_27051 <- GetCDs(27051)
pool_27051 <- Pool(cds_27051)
WeightedMoments(pool_27051)
#>         LCV    LSKEW
#> 1 0.2401301 0.224733
```
