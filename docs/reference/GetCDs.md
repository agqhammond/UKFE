# Get catchment descriptors from the National River Flow Archive sites considered suitable for median annual maximum flow estimation (QMED) and pooling.

Extracts the catchment descriptors for a site of interest from the
National River Flow Archive.

## Usage

``` r
GetCDs(x)
```

## Arguments

- x:

  the site reference of interest (numeric)

## Value

A data.frame with columns; Descriptor and Value.

## Details

If the site is considered suitable for QMED and pooling the CDs are
extracted from the PeakFlowData data.frame. Otherwise they are extracted
using the NRFA website. Note that if they are from the NRFA website then
the 'easting' and 'northing' are not for the catchment centroid, they're
for the gauge location. Also, where the gauge has NRFA peak flows
available, but is not considered suitable for pooling or QMED, it will
be derived from the NRFA webpage, and some descriptors differ a little
between the data sets (NRFA website and NRFA peak flows), notably the
Area.

## Author

Anthony Hammond

## Examples

``` r
# Get CDs and display in the console
cds_203018 <- GetCDs(203018)
cds_203018
#>         Descriptor       Value
#> 1             AREA    277.8000
#> 2           ALTBAR    146.0000
#> 3           ASPBAR    256.0000
#> 4           ASPVAR      0.1600
#> 5  BFIHOST19scaled      0.4240
#> 6        BFIHOST19      0.4250
#> 7          BFIHOST      0.4250
#> 8           DPLBAR     20.2800
#> 9           DPSBAR     53.2000
#> 10        FARL2015      0.9931
#> 11            FARL      0.9930
#> 12           FPEXT      0.0894
#> 13             LDP     33.5600
#> 14         PROPWET      0.5200
#> 15         RMED.1H     10.4000
#> 16         RMED.1D     36.9000
#> 17         RMED.2D     48.6000
#> 18        SAAR9120   1140.0000
#> 19        SAAR6190   1075.0000
#> 20        SAAR4170   1106.0000
#> 21         SPRHOST     38.0300
#> 22      URBEXT2015      0.0427
#> 23      URBEXT2000      0.0255
#> 24      URBEXT1990      0.0304
#> 25       DrainDens      1.2040
#> 26           CEast 139781.0000
#> 27          CNorth 544597.0000
```
