# Pooled flood estimates

Provides pooled results from a pooling group.

## Usage

``` r
PoolEst(
  x,
  dist = "GenLog",
  CDs,
  QMEDEstimate,
  UrbAdj = TRUE,
  URBEXT = NULL,
  Gauged = FALSE,
  fseQMED = 1.5,
  Uncertainty = TRUE
)
```

## Arguments

- x:

  pooling group derived from the Pool function

- dist:

  a choice of distribution for the estimates. The choices are "GenLog",
  "GEV", "Kappa3", or "Gumbel"; the generalised logistic, generalised
  extreme value, Kappa3, and Gumbel distribution, respectively. The
  default is "GenLog"

- CDs:

  catchment descriptors for the subject site. They can be derived from
  either GetCDs or CDsXML

- QMEDEstimate:

  estimate of the median annual maximum flow

- UrbAdj:

  Logical with a default of TRUE. If TRUE, the final LCV estimate is
  urban adjusted.

- URBEXT:

  the catchment URBEXT (at the time of writing the current URBEXT is
  URBEXT2015), to be supplied if UrbAdj is TRUE and if the CDs argument
  is NULL.

- Gauged:

  Logical argument with a default of FALSE. This only impacts the
  uncertainty calculations. If it is set to TRUE, the top site of the
  group is considered the subject gauged site.

- fseQMED:

  The factorial standard error for the QMED estimate. If Gauged = TRUE,
  the fse is estimated from the observed, otherwise the default is 1.5.

- Uncertainty:

  Logical with a default of TRUE. If TRUE, an extra column of factorial
  standard errors is returned in the results dataframe.

## Value

A list of length 3. Element one is a data frame with columns; return
period (a range from 2 - 1000), peak flow estimates (Q), growth factor
estimates (GF), and factorial standard error (if Uncertainty = TRUE).
The second element is the estimated Lcv and Lskew. The third provides
distribution parameters for the frequency curve.

## Details

PoolEst is a function to provide results from a pooling group derived
using the Pool function. QMED (median annual maximum flow) needs to be
supplied and can be derived from the QMED function for ungauged
estimates or the annual maximum sample for gauged estimates. The method
applied is based on FEH2025. The methods for estimating the L-moments
and growth factors are outlined in the Flood Estimation Handbook (1999),
volume 3. The estimation procedure assumes that the pooled AMAX samples
are from the same underlying distribution (aside from the QMED scaling
factor), that the distribution is correctly specified, that the
individual samples are all independent and identically distributed, and
that the samples are independent of each other. The urban adjustment
(which is applied as default) assumes that the growth curve associated
with an annual maximum flow sample is impacted by urbanisation and that
this impact can be modelled as a function of the catchment URBEXT. A
quantification of uncertainty is provided if Uncertainty is set to TRUE
(the default). For more information see the Uncertainty function.

## Author

Anthony Hammond

## Examples

``` r
# Get some catchment descriptors and form a pooling group.
cds_27083 <- GetCDs(27083)
pool_27083 <- Pool(cds_27083)

#Get results assuming a GEV distribution
PoolEst(pool_27083, CDs = cds_27083, dist = "GEV", QMEDEstimate = 12, Uncertainty = FALSE)
#> $Results
#>      RP    Q   GF
#> 1     2 12.0 1.00
#> 2     5 16.7 1.39
#> 3    10 19.8 1.65
#> 4    20 22.7 1.89
#> 5    30 24.4 2.03
#> 6    50 26.4 2.20
#> 7    75 28.0 2.34
#> 8   100 29.2 2.43
#> 9   200 31.9 2.66
#> 10  500 35.4 2.95
#> 11 1000 38.0 3.16
#> 
#> $`Weighted Lmoment Ratios`
#>         LCV    LSKEW
#> 1 0.2259106 0.157821
#> 
#> $`Distribution Parameters`
#>       loc    scale      shape
#> 1 10.4417 4.238708 0.01756671
#> 
```
