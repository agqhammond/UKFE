# Goodness of fit comparison (single sample)

compares the RMSE of four distribution fits for a single AMAX sample.

## Usage

``` r
GoFCompare(x)
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
GenLog, Gumbel, & Kappa3). The lowest RMSE is the best fit. It works as
follows. For each distribution: Step1. Simulate 500 samples the same
size as x. Step2. Calculate the mean across all 500 samples for each
rank to create an ordered central estimate. Step3. Calculate the RMSE
between the result of step 2 and the ordered x. Step4. Standardise the
RMSE by dividing it by the mean of x and multiply it by 100 (RMSE as a
percentage of mean). Note that this is not a hypothesis test. It is only
for comparing the fit across the distributions.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and then compare the fit
am_15006 <- GetAM(15006)
GoFCompare(am_15006$Flow)
#> [[1]]
#>     GEV GenLog Gumbel Kappa3
#> 1 3.452  3.302  3.381  3.189
#> 
#> [[2]]
#> [1] "Kappa3 has the best fit"
#> 
```
