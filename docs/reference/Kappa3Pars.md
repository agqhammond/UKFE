# Kappa3 distribution parameter estimates

Estimated parameters from a sample (using Lmoments) or from user
supplied L1 (first L-moment), Lcv (linear coefficient of variation), and
LSkew (linear skewness)

## Usage

``` r
Kappa3Pars(x = NULL, L1 = NULL, LCV = NULL, LSKEW = NULL)
```

## Arguments

- x:

  numeric vector. The sample

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
L-moments. Cambridge University Press, New York'. This is the Kappa3
distribution as defined in Kjeldsen, T (2019), 'The 3-parameter Kappa
distribution as an alternative for use with FEH pooling groups.'
(Circulation - The Newsletter of the British Hydrological Society, no.
142).

This function applies a probability distribution model which assumes
that the sample data is independent and identical, i.e. the assumption
is that all observations in the sample would not impact or depend on any
other. Furthermore, all observations are from the same underlying
process which has not changed over the period of record (stationarity).

## Author

Anthony Hammond

## Examples

``` r
# Get an annual maximum sample and estimate the parameters
am_27090 <- GetAM(27090)
Kappa3Pars(am_27090$Flow)
#>        Loc    Scale      Shape
#> 1 280.8044 67.66839 0.09640913

# Calculate L-moments and estimate the parameters with L1, LCV, and LSKEW
l_pars <- as.numeric(LMoments(am_27090$Flow))[c(1, 5, 6)]
Kappa3Pars(L1 = l_pars[1], LCV = l_pars[2], LSKEW = l_pars[3])
#>        Loc    Scale      Shape
#> 1 280.8044 67.66839 0.09640912
```
