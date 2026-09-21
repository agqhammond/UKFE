# Generalised extreme value distribution parameter estimates

Estimated parameters from a sample (with Lmoments or maximum likelihood
estimation) or from L1 (first L-moment), Lcv (linear coefficient of
variation), and LSkew (linear skewness)

## Usage

``` r
GEVPars(x = NULL, mle = FALSE, L1 = NULL, LCV = NULL, LSKEW = NULL)
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

- LSKEW:

  linear skewness

## Value

Parameter estimates (location, scale, shape)

## Details

The L-moment estimated parameters are by the method detailed in 'Hosking
J. and Wallis J. 1997 Regional Frequency Analysis: An Approach Based on
L-moments. Cambridge University Press, New York'.

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
GEVPars(am_27090$Flow)
#>        Loc    Scale     Shape
#> 1 264.4741 89.29227 0.2407794

# Estimate parameters using MLE
GEVPars(am_27090$Flow, mle = TRUE)
#>        loc    scale     shape log.likelihood
#> 1 264.7234 85.96655 0.2238061      -188.9231

# Calculate L-moments and estimate the parameters with L1, Lcv, and Lskew
LMoments(am_27090$Flow)
#>         L1       L2       L3       L4       Lcv      LSkew     LKurt
#> 1 298.4615 51.77933 1.279072 7.818461 0.1734875 0.02470237 0.1509958

# Store L-moments in an object
l_pars <- as.numeric(LMoments(am_27090$Flow))[c(1, 5, 6)]
GEVPars(L1 = l_pars[1], LCV = l_pars[2], LSKEW = l_pars[3])
#>        Loc    Scale     Shape
#> 1 264.4741 89.29227 0.2407794
```
