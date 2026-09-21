# QMED factorial standard error for gauged sites

Estimates the median annual maximum flow (QMED) factorial standard error
(FSE) by bootstrapping the sample

## Usage

``` r
QMEDfseSS(x)
```

## Arguments

- x:

  a numeric vector. The sample of interest

## Value

The factorial standard error for the median of a sample.

## Details

The bootstrapping procedure resamples from the sample N\*500 times with
replacement. After splitting into 500 samples of size N, the median is
calculated for each. Then the exponent of the standard deviation of the
log transformed residuals is taken as the FSE. i.e.
exp(sd(log(x)-mean(log(x)))), where x is the bootstrapped medians.

## Author

Anthony Hammond

## Examples

``` r
# Extract an AMAX sample and estimate the QMED factorial standard error
am_203018 <- GetAM(203018)
QMEDfseSS(am_203018$Flow)
#> [1] 1.052773
```
