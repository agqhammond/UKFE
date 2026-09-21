# Pooled flood estimates using the FEH2008 method

Provides pooled results from a pooling group - gauged, ungauged and with
urban adjustment if necessary.

## Usage

``` r
PoolEst_FEH08(
  x,
  gauged = FALSE,
  QMED,
  dist = "GenLog",
  RP = c(2, 5, 10, 20, 50, 75, 100, 200, 500, 1000),
  UrbAdj = FALSE,
  CDs = NULL,
  URBEXT = NULL
)
```

## Arguments

- x:

  pooling group derived from the Pool function

- gauged:

  logical argument with a default of FALSE. TRUE for gauged results and
  FALSE for ungauged

- QMED:

  estimate of the median annual maximum flow

- dist:

  a choice of distribution for the estimates. The choices are "GenLog",
  "GEV", "Kappa3", or "Gumbel"; the generalised logistic, generalised
  extreme value, Kappa3, and Gumbel distribution, respectively. The
  default is "GenLog"

- RP:

  return period of interest. By default the following RPs are provided:
  2, 5, 10, 20, 50, 75, 100, 200, 500, 1000

- UrbAdj:

  logical argument with a default of FALSE. When TRUE, an urban
  adjustment (FEH08 method) is applied to the pooled Lcv and LSkew

- CDs:

  catchment descriptors derived from either GetCDs or CDsXML

- URBEXT:

  the catchment URBEXT2000, to be supplied if UrbAdj is TRUE and if the
  CDs argument is not used.

## Value

If RP is default then a list of length 4. Element one is a data frame
with columns; return period (a range from 2 - 1000), peak flow estimates
(Q), growth factor estimates (GF), lower and upper intervals of
uncertainty (68 percent intervals for ungauged and 95 percent for
gauged). The second element is the estimated Lcv and Lskew. The third
provides distribution parameters for the growth curve. The fourth
provides distribution parameters for the frequency curve. If RP is not
the default only the first two elements are returned.

## Details

PoolEst_FEH08 is a function to provide results from a pooling group
derived using the FEH08Pool function. QMED (median annual maximum flow)
needs to be supplied and can be derived from the FEH08QMED function for
ungauged estimates or the annual maximum sample for gauged estimates.
The UrbAdj argument can be set to TRUE to provide urbanised results. If
this is done, either URBEXT (urban extent) needs to be provided or the
catchment descriptors, derived from CDsXML or GetCDs. The methods for
estimating pooled growth curves are according to Science Report:
SC050050 - Improving the FEH statistical procedures for flood frequency
estimation. The methods for estimating the L-moments and growth factors
are outlined in the Flood Estimation Handbook (1999), volume 3. The
methods for quantifying uncertainty are detailed in Hammond, A. (2022).
Easy methods for quantifying the uncertainty of FEH pooling analysis.
Circulation - The Newsletter of the British Hydrological Society (152).
When UrbAdj = TRUE, urban adjustment is applied to the QMED estimate
according to the method outlined in the guidance by Wallingford
HydroSolutions: 'WINFAP 4 Urban Adjustment Procedures'. Note that if
Gauged = TRUE, the functionality assumes that the top site in the
pooling group (i.e. the first row) is the subject "gauged" catchment. It
is important to check that this is the case because if the site is urban
it may not be included by default. The estimation procedure assumes that
the pooled AMAX samples are from the same underlying distribution (aside
from the QMED scaling factor), that the distribution is correctly
specified, that the individual samples are all independent and
identically distributed, and that the samples are independent of each
other. The urban adjustment assumes that the growth curve associated
with an annual maximum flow sample is impacted by urbanisation and that
this impact can be modelled as a function of the catchment URBEXT2000.

## Author

Anthony Hammond

## Examples

``` r
# Get some catchment descriptors and form a pooling group. It's urban and
# therefore the site of interest is not included
cds_27083 <- GetCDs(27083)
pool_27083 <- Pool_FEH08(cds_27083)

# Get results for the ungauged case, with urban adjustment
PoolEst_FEH08(pool_27083, QMED = 12, UrbAdj = TRUE, CDs = cds_27083)
#> [[1]]
#>      RP      Q    GF
#> 1     2 12.000 1.000
#> 2     5 16.835 1.403
#> 3    10 20.560 1.713
#> 4    20 24.742 2.062
#> 5    50 31.321 2.610
#> 6    75 34.716 2.893
#> 7   100 37.336 3.111
#> 8   200 44.469 3.706
#> 9   500 56.011 4.668
#> 10 1000 66.696 5.558
#> 
#> [[2]]
#>      PooledLcv PooledLSkew
#> [1,] 0.2436355   0.2537155
#> 
#> [[3]]
#>   loc scale  shape
#> 1   1 0.243 -0.254
#> 
#> [[4]]
#>   loc scale  shape
#> 1  12  2.91 -0.254
#> 

# Form the group again with the urban gauge included & undertake a gauged estimate
# with urban adjustment. QMED in this example is estimated as the median of the annual
# maximum series for site 27083.
pool_g_27083 <- Pool_FEH08(cds_27083, include = 27083, DeUrb = TRUE)
PoolEst_FEH08(pool_g_27083, QMED = 12.5, UrbAdj = TRUE, CDs = cds_27083)
#> [[1]]
#>      RP      Q    GF
#> 1     2 12.500 1.000
#> 2     5 17.574 1.406
#> 3    10 21.483 1.719
#> 4    20 25.872 2.070
#> 5    50 32.778 2.622
#> 6    75 36.342 2.907
#> 7   100 39.092 3.127
#> 8   200 46.581 3.726
#> 9   500 58.699 4.696
#> 10 1000 69.918 5.593
#> 
#> [[2]]
#>      PooledLcv PooledLSkew
#> [1,] 0.2452548   0.2538149
#> 
#> [[3]]
#>   loc scale  shape
#> 1   1 0.244 -0.254
#> 
#> [[4]]
#>    loc scale  shape
#> 1 12.5  3.06 -0.254
#> 
```
