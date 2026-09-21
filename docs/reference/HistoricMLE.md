# Historic flood maximum likelihood estimation

A function to estimate parameters from an annual maximum sample and a
known number of historic floods.

## Usage

``` r
HistoricMLE(x, k = NULL, h, threshold, dist = "GenLog", Uncertainty = FALSE)
```

## Arguments

- x:

  The observed annual maximum sample. A single numeric vector

- k:

  The number of exceedances of the threshold

- h:

  the time period (years) over which the exceedances occurred.

- threshold:

  The perception threshold. This is the threshold (discharge) we think
  the k events exceeded.

- dist:

  The choice of statistical distribution. Either "GenLog", or "GEV".

- Uncertainty:

  Logical argument with a default of FALSE. If TRUE, a data frame of
  results and uncertainty is also returned.

## Value

A data.frame with one column of flow estimates. The row names denote the
name of each estimate. If Uncertainty is TRUE, a list is returned and
the second element is a dataframe with estimates and factorial standard
errors.

## Details

This function applies the case where only the number of exceedances are
known. Not the case where the discharge of the historic floods is known.
This latter functionality will be added at a later date. Note that if
Uncertainty is set to TRUE, a range of return periods and associated
estimates are returned along with uncertainty - quantified as the FSE.
In some cases the uncertainty can increase. This happens when the
additional information (number of exceedances and time period) does not
outweigh an increase to the scale and/or skew parameter. The uncertainty
calculated is a function of sample size and variance.

## Author

Anthony Hammond

## Examples

``` r
# Get an annual maximum sample and assume 3 exceedances over 100 years
# with a threhsold of 140m 3/s
AM71011 <- GetAM(71011)
HistoricMLE(AM71011$Flow, k = 3, h = 100, threshold = 140)
#>           Method   Loc Scale    Shape    LCV   LSKEW
#> 1  AMAX Lmoments 121.9 8.214 0.006002 0.0674 -0.0060
#> 2 Historical MLE 120.8 7.299 0.041070 0.0608 -0.0411


# Now estimate again but set Uncertainty = TRUE
HistoricMLE(AM71011$Flow, k = 3, h = 100, threshold = 140, Uncertainty = TRUE)
#> $`Historic Adjustment`
#>           Method   Loc Scale    Shape    LCV   LSKEW
#> 1  AMAX Lmoments 121.9 8.214 0.006002 0.0674 -0.0060
#> 2 Historical MLE 120.8 7.299 0.041070 0.0608 -0.0411
#> 
#> $Uncertainty
#>    ReturnPeriod CentralAMAX CentralHistoric FSE_AMAX FSE_Historic
#> 1             2         125             123    1.012        1.011
#> 2            10         140             136    1.021        1.017
#> 3            20         146             141    1.027        1.022
#> 4            30         149             144    1.031        1.025
#> 5            50         154             147    1.036        1.028
#> 6            75         157             150    1.041        1.032
#> 7           100         159             151    1.044        1.034
#> 8           200         165             156    1.053        1.041
#> 9           500         172             161    1.067        1.050
#> 10         1000         177             165    1.077        1.057
#> 
```
