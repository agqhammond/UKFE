# British national grid reference (NGR) distances

Calculates the Euclidean distance between two British national grid
reference points using the Pythagorean/Euclidean method.

## Usage

``` r
NGRDist(i, j)
```

## Arguments

- i:

  a numeric vector of length two. The first being the easting and the
  second being the northing of the first site

- j:

  a numeric vector of length two. The first being the easting and the
  second being the northing of the second site

## Value

A distance in kilometres (if British national grid easting and northing
are applied)

## Details

Note, that the result is converted to km from m.

## Author

Anthony Hammond

## Examples

``` r
# Calculate the distance between the catchment centroid for the
# Kingston upon Thames river gauge and the catchment centroid for the
# gauge at Ardlethen on the River Ythan.
# First retrieve the catchment descriptors (CDs) to obtain eastings and northings
GetCDs(10001)
#>         Descriptor       Value
#> 1             AREA    457.1000
#> 2           ALTBAR    111.0000
#> 3           ASPBAR    115.0000
#> 4           ASPVAR      0.1400
#> 5  BFIHOST19scaled      0.5760
#> 6        BFIHOST19      0.5760
#> 7          BFIHOST      0.6140
#> 8           DPLBAR     24.3800
#> 9           DPSBAR     57.2000
#> 10        FARL2015      0.9805
#> 11            FARL      0.9920
#> 12           FPEXT      0.0432
#> 13             LDP     52.1900
#> 14         PROPWET      0.4200
#> 15         RMED.1H      8.3000
#> 16         RMED.1D     33.7000
#> 17         RMED.2D     44.3000
#> 18        SAAR9120    899.0000
#> 19        SAAR6190    830.0000
#> 20        SAAR4170    861.0000
#> 21         SPRHOST     28.3100
#> 22      URBEXT2015      0.0038
#> 23      URBEXT2000      0.0013
#> 24      URBEXT1990      0.0007
#> 25       DrainDens      1.0110
#> 26           CEast 381355.0000
#> 27          CNorth 839183.0000
GetCDs(39001)
#>         Descriptor       Value
#> 1             AREA   9931.0000
#> 2           ALTBAR    109.0000
#> 3           ASPBAR    108.0000
#> 4           ASPVAR      0.0800
#> 5  BFIHOST19scaled      0.6760
#> 6        BFIHOST19      0.6790
#> 7          BFIHOST      0.6530
#> 8           DPLBAR    139.9000
#> 9           DPSBAR     42.0000
#> 10        FARL2015      0.8732
#> 11            FARL      0.9420
#> 12           FPEXT      0.1476
#> 13             LDP    269.6000
#> 14         PROPWET      0.3000
#> 15         RMED.1H     10.8000
#> 16         RMED.1D     32.7000
#> 17         RMED.2D     41.5000
#> 18        SAAR9120    753.0000
#> 19        SAAR6190    706.0000
#> 20        SAAR4170    724.0000
#> 21         SPRHOST     26.9400
#> 22      URBEXT2015      0.0792
#> 23      URBEXT2000      0.0664
#> 24      URBEXT1990      0.0426
#> 25       DrainDens      0.7870
#> 26           CEast 462899.0000
#> 27          CNorth 187850.0000

# Calculate the distance between two centroids (eastings and northings)
NGRDist(i = c(381355, 839183), j = c(462899, 187850))
#> [1] 656.4176
```
