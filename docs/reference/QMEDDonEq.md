# QMED donor adjustment

Applies a donor adjustment to the median annual maximum flow (QMED)
estimate

## Usage

``` r
QMEDDonEq(
  QMED.scd,
  QMEDgObs,
  QMEDgCds,
  Distance = NULL,
  xSI,
  ySI,
  xDon,
  yDon,
  alpha = TRUE
)
```

## Arguments

- QMED.scd:

  Ungauged QMED estimate for the site of interest

- QMEDgObs:

  the observed QMED at the donor site

- QMEDgCds:

  the QMED equation derived QMED at the donor site

- Distance:

  The distance in km between the catchment centroids of the site of
  interest and donor site.

- xSI:

  For when distance is not known - the catchment centroid easting for
  the site of interest.

- ySI:

  For when distance is not known - the catchment centroid northing for
  the site of interest

- xDon:

  For when distance is not known - the catchment centroid easting for
  the donor site

- yDon:

  For when distance is not known - the catchment centroid northing for
  the donor site

- alpha:

  a logical argument with a default of TRUE. When FALSE the exponent in
  the donor equation is set to one. Otherwise it is determined by the
  distance between the donor and the subject site

## Details

Although a single donor adjustment can be applied with the QMED
function, this additional function is provided for flexibility. The
method is that of FEH2025.

## Author

Anthony Hammond

## Examples

``` r
# Get observed QMED for site 15006
q_ob <- GetQMED(15006)

# Get QMED equation estimated QMED for the donor site
q_cd <- QMED(CDs = GetCDs(15006))



# Apply the QMEDDonEq function with the information gained, assuming
# a distance of 30km and subject site QMED estimate of 3.9
QMEDDonEq(
  QMED.scd = 3.9, QMEDgObs = q_ob, QMEDgCds = q_cd,
  Distance = 30
)
#> [1] 3.933878
```
