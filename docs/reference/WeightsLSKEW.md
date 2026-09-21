# Linear Skewness (LSKEW) weightings for a pooling group

Provides the LSKEW weights for each site in a pooling group

## Usage

``` r
WeightsLSKEW(x)
```

## Arguments

- x:

  pooling group derived with the Pool() function

## Value

A data.frame with site references in the first column and associated
weights in the second

## Details

Weighting method for FEH2025.

## Author

Anthony Hammond

## Examples

``` r
# Get some CDs, form an ungauged pooling group, and estimate ungauged LSkew
cds_27051 <- GetCDs(27051)
pool_27051 <- Pool(cds_27051, exclude = 27051)
WeightsLSKEW(pool_27051)
#>     Site     Weight
#> 1  27010 0.04933204
#> 2  28033 0.05187725
#> 3  25019 0.05081532
#> 4  24007 0.03050763
#> 5   7012 0.02256277
#> 6  28041 0.04799936
#> 7  41020 0.05291340
#> 8  47022 0.04298593
#> 9  24006 0.03607533
#> 10 28058 0.02761752
#> 11 49005 0.02907085
#> 12 45816 0.04407113
#> 13 36010 0.05323740
#> 14 25011 0.04742137
#> 15 48009 0.02602364
#> 16 41022 0.05249228
#> 17 72007 0.05027649
#> 18 24004 0.05480588
#> 19 25012 0.05272874
#> 20  9006 0.02904002
#> 21 27032 0.05295210
#> 22 20006 0.04224574
#> 23 51003 0.05294782
```
