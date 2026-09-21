# Generalised logistic distribution - estimates directly from sample

Estimated quantiles as a function of return period (RP) and vice versa,
directly from the data

## Usage

``` r
GenLogAM(x, RP = 100, q = NULL)
```

## Arguments

- x:

  numeric vector (block maxima sample)

- RP:

  return period (default = 100)

- q:

  quantile (magnitude of variable)

## Value

quantile as a function of RP or vice versa.

## Details

If the argument q is used, it overrides RP and provides RP as a function
of q (magnitude of variable) as opposed to q as a function of RP. The
parameters are estimated by the method of L-moments, as detailed in
'Hosking J. and Wallis J. 1997 Regional Frequency Analysis: An Approach
Based on L-Moments. Cambridge University Press, New York'.

This function applies a probability distribution model which assumes
that the sample data is independent and identical, i.e. the assumption
is that all observations in the sample would not impact or depend on any
other. Furthermore, all observations are from the same underlying
process which has not changed over the period of record (stationarity).

## Author

Anthony Hammond

## Examples

``` r
# Get an annual maximum sample and estimate the 50-year RP
am_27090 <- GetAM(27090)
GenLogAM(am_27090$Flow, RP = 50)
#> [1] 507.6664

# Estimate the RP for a 600 m^3/s discharge
GenLogAM(am_27090$Flow, q = 600)
#> [1] 241.2265
```
