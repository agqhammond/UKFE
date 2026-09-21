# Gumbel distribution estimates from parameters

Estimated quantiles as function of return period (RP) and vice versa,
from user input parameters

## Usage

``` r
GumbelEst(loc, scale, q = NULL, RP = 100)
```

## Arguments

- loc:

  location parameter

- scale:

  scale parameter

- q:

  quantile. magnitude of the variable under consideration

- RP:

  return period

## Value

quantile as a function of RP or vice versa

## Details

If the argument q is used, it overrides RP and provides RP as a function
of q (magnitude of variable) as opposed to q as a function of RP.

This function applies a probability distribution model which assumes
that the sample data is independent and identical, i.e. the assumption
is that all observations in the sample would not impact or depend on any
other. Furthermore, all observations are from the same underlying
process which has not changed over the period of record (stationarity).

## Author

Anthony Hammond

## Examples

``` r
# Get an annual maximum sample, estimate the parameters, and estimate the 50-year RP
am_27090 <- GetAM(27090)
pars <- as.numeric(GumbelPars(am_27090$Flow))
GumbelEst(pars[1], pars[2], RP = 50)
#> [1] 546.8254

# Estimate the RP for a 600 m^3/s discharge
GumbelEst(pars[1], pars[2], q = 600)
#> [1] 101.3638
```
