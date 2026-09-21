# Lmoments & Lmoment ratios

Calculates the Lmoments and Lmoment ratios from a sample of data

## Usage

``` r
LMoments(x)
```

## Arguments

- x:

  a numeric vector. The sample of interest

## Value

A data.frame with one row and column headings; L1, L2, L3, L4, Lcv,
LSkew, and LKurt. The first four are the Lmoments and the next three are
the Lmoment ratios.

## Details

Lmoments calculated according to methods outlined by Hosking & Wallis
(1997): Regional Frequency Analysis and approach based on LMoments. Also
in the Flood Estimation Handbook (1999), volume 3.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and calculate the L-moments
am_27051 <- GetAM(27051)
LMoments(am_27051$Flow)
#>         L1       L2        L3         L4       Lcv     LSkew      LKurt
#> 1 4.823769 1.037595 0.1372521 0.09184794 0.2151005 0.1322791 0.08852002
```
