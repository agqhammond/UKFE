# Data simulator

Simulation of a random sample from the generalised extreme value,
generalised logistic, Gumbel, Kappa3, or generalised Pareto
distributions

## Usage

``` r
SimData(n, pars = NULL, dist = "GenLog", GF = NULL)
```

## Arguments

- n:

  sample size to be simulated

- pars:

  vector of parameters in the order of location, scale, shape (only
  location and shape for Gumbel)

- dist:

  choice of distribution. Either "GEV", "GenLog", "Gumbel", "Kappa3", or
  "GenPareto"

- GF:

  vector of GF inputs in the order of Lcv, LSkew, QMED (only Lcv and
  QMED if dist = "Gumbel")

## Value

A random sample of size n for the chosen distribution.

## Details

The simulated sample can be generated using the distribution parameters
(pars) location, scale and shape, or the growth factor (GF) inputs
linear coefficient of variation (Lcv), linear skewness (LSkew) & median
annual maximum (QMED). This function applies a probability distribution
model which assumes that the sample data is independent and identical,
i.e. the assumption is that all observations in the sample would not
impact or depend on any other. Furthermore, all observations are from
the same underlying process which has not changed over the period of
record (stationarity).

## Author

Anthony Hammond

## Examples

``` r
# Simulate a sample of size 30 from a GenLog distribution with parameters 299, 51, -0.042
SimData(30, pars = c(299, 51, -0.042), dist = "GenLog")
#>  [1] 274.0172 329.7226 545.0702 422.6694 382.0729 177.7944 300.4819 390.2519
#>  [9] 320.7621 250.8635 331.4056 335.0133 254.7945 318.2937 221.8416 363.1633
#> [17] 171.1708 216.9310 203.0865 216.3657 297.3341 345.5515 333.0459 296.2135
#> [25] 333.2960 352.7701 389.9641 203.3808 263.3363 382.9259

# Now simulate using the Lcv, Lskew, and median (0.17, 0.04, 310)
SimData(30, GF = c(0.17, 0.04, 310), dist = "GenLog")
#>  [1] 333.3579 345.4705 312.2723 251.8286 259.5463 155.3348 109.7751 356.2868
#>  [9] 335.8716 414.5049 362.9411 426.9810 469.3626 289.0905 338.8779 295.8336
#> [17] 352.6609 339.9407 312.1338 183.7642 375.7741 187.5143 350.4723 300.8333
#> [25] 409.3771 219.8992 261.9359 325.7662 233.4561 240.9224
```
