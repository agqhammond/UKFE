# Gumbel distribution parameter estimates

Estimated parameters from a sample (with Lmoments or maximum likelihood
estimation) or from L1 (first L-moment), Lcv (linear coefficient of
variation)

## Usage

``` r
GumbelPars(x = NULL, mle = FALSE, L1, LCV)
```

## Arguments

- x:

  numeric vector. The sample

- mle:

  logical argument with a default of FALSE. If FALSE the parameters are
  estimated with Lmoments, if TRUE the parameters are estimated by
  maximum likelihood estimation

- L1:

  first Lmoment

- LCV:

  linear coefficient of variation

## Value

Parameter estimates (location, scale)

## Details

The L-moment estimated parameters are by the method detailed in 'Hosking
J. and Wallis J. 1997 Regional Frequency Analysis: An Approach Based on
L-Moments. Cambridge University Press, New York'.

This function applies a probability distribution model which assumes
that the sample data is independent and identical, i.e. the assumption
is that all observations in the sample would not impact or depend on any
other. Furthermore, all observations are from the same underlying
process which has not changed over the period of record (stationarity).

## Author

Anthony Hammond

## Examples

``` r
# Get an annual maximum sample and estimate the parameters using L-moments
am_27090 <- GetAM(27090)
GumbelPars(am_27090$Flow)
#>        Loc    Scale
#> 1 255.3437 74.70178

# Estimate parameters using MLE
GumbelPars(am_27090$Flow, mle = TRUE)
#>        loc    scale log.likelihood
#> 1 254.6239 82.86958      -190.2851

# Calculate L-moments and estimate the parameters with L1 and Lcv
pars <- as.numeric(LMoments(am_27090$Flow)[c(1, 5)])
GumbelPars(L1 = pars[1], LCV = pars[2])
#>        Loc    Scale
#> 1 255.3437 74.70178
```
