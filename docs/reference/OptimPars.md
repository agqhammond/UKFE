# Optimise distribution parameters

Estimates the parameters of the Generalised extreme value, generalised
logistic, Kappa3, or Gumbel distribution from known return period
estimates

## Usage

``` r
OptimPars(x, dist = "GenLog")
```

## Arguments

- x:

  a data.frame with RPs in the first column and associated estimates in
  the second column

- dist:

  a choice of distribution for the estimates. The choices are "GenLog",
  "GEV", "Kappa3", or "Gumbel" - the generalised logistic, generalised
  extreme value, Kappa3, and Gumbel distribution, respectively. The
  default is "GenLog"

## Value

The parameters of one of four user chosen distributions; Generalised
logistic, generalised extreme value, Gumbel, and Kappa3.

## Details

Given a dataframe with return periods (RPs) in the first column and
associated estimates in the second column, this function provides an
estimate of the distribution parameters. Ideally the first RP should be
2. Extrapolation outside the RPs used for calibration comes with greater
uncertainty.

## Author

Anthony Hammond

## Examples

``` r
# Get some catchment descriptors and some quick results
# Then estimate the GenLog parameters
results <- QuickResults(GetCDs(27051))[[1]]
OptimPars(results[, 1:2])
#>       loc    scale      shape
#> 1 4.63568 1.112919 -0.2251567
```
