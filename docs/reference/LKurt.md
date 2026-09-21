# Linear Kurtosis (LKurt)

Calculates the LKurtosis from a sample of data

## Usage

``` r
LKurt(x)
```

## Arguments

- x:

  a numeric vector. The sample of interest

## Value

Numeric. The LSkew of a sample.

## Details

LKurtosis calculated according to methods outlined by Hosking & Wallis
(1997): Regional Frequency Analysis and approach based on LMoments. Also
in the Flood Estimation Handbook (1999), volume 3.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and calculate the L-moments
am_27051 <- GetAM(27051)
LKurt(am_27051$Flow)
#> [1] 0.08852002
```
