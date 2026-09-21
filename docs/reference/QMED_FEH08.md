# QMED (median annual maximum flow) estimate from catchment descriptors using the FEH 2008 method.

Estimated median annual maximum flow from catchment descriptors.

## Usage

``` r
QMED_FEH08(CDs = NULL, UrbAdj = TRUE, AREA, SAAR, FARL, BFIHOST, URBEXT)
```

## Arguments

- CDs:

  catchment descriptors derived from either GetCDs or CDsXML

- UrbAdj:

  logical argument with a default of TRUE. If TRUE, an urban adjustment
  is made to the estimate.

- AREA:

  catchment area in km2

- SAAR:

  standard average annual rainfall (mm)

- FARL:

  flood attenuation from reservoirs and lakes

- BFIHOST:

  baseflow index calculated from the catchment hydrology of soil type
  classification

- URBEXT:

  measure of catchment urbanisation

## Value

An estimate of QMED from catchment descriptors.

## Details

QMED is estimated from catchment descriptors: QMED = 8.3062 \*
AREA^0.851 \* 0.1536^(1000 / SAAR) \* FARL^3.4451 \* 0.046^(BFIHOST^2)
as specified by FEH2008. If the CDs argument is used then the SAAR used
is SAAR6190, FARL is FARL (as opposed to FARL2015) and BFIHOST is
BFIHOST (as opposed to BFIHOST19 or BFIHOST19scaled). Note that this
function is a legacy function and you cannot do donor adjustment within
the function. You can however use this in conjunction with the QMEDDonEq
function.

## Author

Anthony Hammond

## Examples

``` r
# Get some catchment descriptors and calculate QMED as if it was ungauged

cds_55004 <- GetCDs(55004)
QMED_FEH08(cds_55004)
#> [1] 81.10243
```
