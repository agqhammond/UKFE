# Quick pooled results

Provides pooled results, directly from the catchment descriptors

## Usage

``` r
QuickResults(
  CDs,
  no.Donors = 8,
  dist = "GenLog",
  Qmed = NULL,
  UrbMax = 0.03,
  Include = NULL,
  Exclude = NULL
)
```

## Arguments

- CDs:

  catchment descriptors derived from either GetCDs or CDsXML

- no.Donors:

  number of donors required. The default is 8.

- dist:

  a choice of distribution for the estimates. The choices are "GenLog",
  "GEV", "Kappa3", or "Gumbel; the generalised logistic, generalised
  extreme value, Kappa3,and Gumbel distributions, respectively. The
  default is "GenLog"

- Qmed:

  user supplied QMED which overrides the default QMED estimate

- UrbMax:

  A maximum value for URBEXT2015 permitted in the pooling group. The
  default is 0.03.

- Include:

  A site reference for any site you want to ensure is in the pooling
  group if it is not chosen automatically. For example, a site which has
  URBEXT2015 above UrbMax.

- Exclude:

  A site reference for any site you want to exclude from the pooling
  group. Useful for testing a gauged site as if it is ungauged.

## Value

A list of length three. Element one is a data frame with columns; return
period (RP), peak flow estimates (Q) and growth factor estimates (GF).
The second element is the estimated Lcv and Lskew (linear coefficient of
variation and skewness). The third element is a dataframe with the
distribution parameters.

## Details

The quick results function provides results with a default pooling
group. Sites are chosen from those with URBEXT2015 below or equal to
UrbMax (the default is 0.03).The LCVs in the pooling group are
'de-urbanised'. The final LCV estimate is then urban adjusted. QMED is
estimated using the QMED function with eight donors, all of which have a
de-urbanised observed QMED for the donor process. Then the QMED estimate
has an urban adjustment applied. If the CDs are for a site suitable for
pooling/QMED, this QMED estimate converges to the observed.

## Author

Anthony Hammond

## Examples

``` r
# Get some catchment descriptors
cds_73005 <- GetCDs(73005)

# Get results
QuickResults(cds_73005)
#> $Results
#>      RP   Q   GF
#> 1     2 170 1.00
#> 2     5 220 1.30
#> 3    10 257 1.51
#> 4    20 297 1.75
#> 5    30 323 1.90
#> 6    50 357 2.10
#> 7    75 388 2.28
#> 8   100 411 2.42
#> 9   200 472 2.77
#> 10  500 567 3.33
#> 11 1000 651 3.83
#> 
#> $`Weighted Lmoment Ratios`
#>         LCV     LSKEW
#> 1 0.1857649 0.2071249
#> 
#> $`Distribution Parameters`
#>        loc    scale      shape
#> 1 169.6738 31.48127 -0.2062128
#> 

# Get results with a GEV distribution
QuickResults(cds_73005, dist = "GEV")
#> $Results
#>      RP   Q   GF
#> 1     2 170 1.00
#> 2     5 225 1.33
#> 3    10 264 1.55
#> 4    20 303 1.78
#> 5    30 325 1.91
#> 6    50 355 2.09
#> 7    75 379 2.23
#> 8   100 396 2.33
#> 9   200 439 2.58
#> 10  500 498 2.93
#> 11 1000 545 3.20
#> 
#> $`Weighted Lmoment Ratios`
#>         LCV     LSKEW
#> 1 0.1857649 0.2071249
#> 
#> $`Distribution Parameters`
#>       loc    scale       shape
#> 1 152.878 46.16457 -0.05787538
#> 

```
