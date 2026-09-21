# Generalised Pareto distribution estimates from parameters

Estimated quantiles as function of return period (RP) and vice versa,
from user input parameters

## Usage

``` r
GenParetoEst(loc, scale, shape, q = NULL, RP = 100, ppy = 1)
```

## Arguments

- loc:

  location parameter

- scale:

  scale parameter

- shape:

  shape parameter

- q:

  quantile. magnitude of the variable under consideration

- RP:

  return period

- ppy:

  peaks per year. Default is one

## Value

quantile as a function of RP or vice versa

## Details

If the argument q is used, it overrides RP and provides RP as a function
of q (magnitude of variable) as opposed to q as a function of RP. The
average number of peaks per year argument (ppy) is necessary when ppy is
not equal to 1.

This function applies a probability distribution model which assumes
that the sample data is independent and identical, i.e. the assumption
is that all observations in the sample would not impact or depend on any
other. Furthermore, all observations are from the same underlying
process which has not changed over the period of record (stationarity).

## Author

Anthony Hammond

## Examples

``` r
# Get a POT sample, estimate the parameters, and estimate the 50-year RP
thames_pot <- POTextract(ThamesPQ[, c(1, 3)], thresh = 0.90)

#> [1] "Peaks per year: 1.867263"
GenParetoPars(thames_pot$peak)
#>        Loc    Scale     Shape
#> 1 174.2862 127.4085 0.1805716

# Store the parameters in an object
pars <- as.numeric(GenParetoPars(thames_pot$peak))

# Get an estimate of 50-year flow
GenParetoEst(pars[1], pars[2], pars[3], ppy = 1.867, RP = 50)
#> [1] 263.0135

# Estimate the RP for a 600 m^3/s discharge
GenParetoEst(pars[1], pars[2], pars[3], ppy = 1.867, q = 600)
#> [1] 89.71398
```
