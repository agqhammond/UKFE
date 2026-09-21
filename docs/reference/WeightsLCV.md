# Linear coefficient of variation (Lcv) weightings for a pooling group

Provides the LCV weights for each site in a pooling group

## Usage

``` r
WeightsLCV(x)
```

## Arguments

- x:

  pooling group derived with the Pool() function

## Value

A data.frame with site references in the first column and associated
weights in the second

## Details

Weighting method for FEH2025

## Author

Anthony Hammond

## Examples

``` r
# Get some CDs, form an ungauged pooling group, and estimate ungauged Lcv
cds_27051 <- GetCDs(27051)
pool_27051 <- Pool(cds_27051, exclude = 27051)
WeightsLCV(pool_27051)
#>     Site     Weight
#> 1  27010 0.06024179
#> 2  28033 0.06216435
#> 3  25019 0.05900696
#> 4  24007 0.03388159
#> 5   7012 0.02583666
#> 6  28041 0.05070103
#> 7  41020 0.05411434
#> 8  47022 0.04435035
#> 9  24006 0.03731600
#> 10 28058 0.02938777
#> 11 49005 0.03045644
#> 12 45816 0.04270717
#> 13 36010 0.04977128
#> 14 25011 0.04493360
#> 15 48009 0.02670630
#> 16 41022 0.04713943
#> 17 72007 0.04539954
#> 18 24004 0.04859593
#> 19 25012 0.04705329
#> 20  9006 0.02874001
#> 21 27032 0.04655949
#> 22 20006 0.03865947
#> 23 51003 0.04627719
```
