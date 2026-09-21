# Goodness of fit comparison (for a pooling group)

compares the RMSE of four distribution fits for a pooling group.

## Usage

``` r
GoFComparePool(x)
```

## Arguments

- x:

  a numeric vector (your AMAX sample)

## Value

A list. The first element is a dataframe with four columns and one row
of results. Each column has the standardised RMSE associated with one of
the four distributions (GEV, GenLog, Gumbel, Kappa3). The second element
is a character string stating the distribution with the best fit.

## Details

This function calculates an RMSE fit score for four distributions (GEV,
GenLog, Gumbel, & Kappa3). The lowest RMSE is the best fit. It works for
pooling groups created using the Pool or PoolSmall function. It uses the
same method as GoFCompare (see the associated details of that function).
It first standardises the pooled AMAX samples (by dividing them by
median) and then treats them as a single large sample. Note that this is
not a hypothesis test. It is only for comparing the fit across the
distributions.

## Author

Anthony Hammond

## Examples

``` r
# Get a pooling group and then compare the fit
pool_60009 <- Pool(GetCDs(60009))
GoFComparePool(pool_60009)
#> [[1]]
#>    GEV GenLog Gumbel Kappa3
#> 1 3.65  2.519  3.022  2.556
#> 
#> [[2]]
#> [1] "GenLog has the best fit"
#> 
```
