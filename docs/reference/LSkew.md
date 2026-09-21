# Linear Skewness (LSkew)

Calculates the LSkew from a sample of data

## Usage

``` r
LSkew(x)
```

## Arguments

- x:

  a numeric vector. The sample of interest

## Value

Numeric. The LSkew of a sample.

## Details

LSkew calculated according to methods outlined by Hosking & Wallis
(1997): Regional Frequency Analysis and approach based on LMoments. Also
in the Flood Estimation Handbook (1999), volume 3.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and calculate the L-moments
am_27051 <- GetAM(27051)
LSkew(am_27051$Flow)
#> [1] 0.1322791
```
