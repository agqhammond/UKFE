# Generalised Pareto distribution - estimates directly from sample

Estimated quantiles as function of return period (RP) and vice versa,
directly from the data

## Usage

``` r
GenParetoPOT(x, ppy = 1, RP = 100, q = NULL)
```

## Arguments

- x:

  numeric vector (peaks over threshold sample)

- ppy:

  peaks per year

- RP:

  return period (default = 100)

- q:

  quantile (magnitude of variable)

## Value

quantile as a function of RP or vice versa

## Details

If the argument q is used, it overrides RP and provides RP as a function
of q (magnitude of variable) as opposed to q as a function of RP. The
average number of peaks per year argument (ppy) is for the function to
convert from the peaks over threshold (POT) scale to the annual scale.
For example, if there are 3 peaks per year, the probability associated
with the 100-yr return period estimate would be 0.01/3 (i.e. an RP of
300 on the POT scale) rather than 0.01. The parameters are estimated by
the method of L-moments, as detailed in 'Hosking J. and Wallis J. 1997
Regional Frequency Analysis: An Approach Based on L-Moments. Cambridge
University Press, New York'.

This function applies a probability distribution model which assumes
that the sample data is independent and identical, i.e. the assumption
is that all observations in the sample would not impact or depend on any
other. Furthermore, all observations are from the same underlying
process which has not changed over the period of record (stationarity).

## Author

Anthony Hammond

## Examples

``` r
# Get a POT series and estimate the 50-year RP
thames_pot <- POTextract(ThamesPQ[, c(1, 3)], thresh = 0.90)

#> [1] "Peaks per year: 1.867263"
GenParetoPOT(thames_pot$peak, ppy = 1.867, RP = 50)
#> [1] 568.8404

# Estimate the RP for a 600 m^3/s discharge
GenParetoPOT(thames_pot$peak, ppy = 1.867, q = 600)
#> [1] 89.71398
```
