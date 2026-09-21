# Areal reduction factor (ARF)

The results of applying, to a rainfall depth, the ratio of the rainfall
over an area to the rainfall depth of the same duration at a
representative point in the area.

## Usage

``` r
ARF(Depth, Area, D)
```

## Arguments

- Depth:

  depth of rainfall

- Area:

  catchment area in km2

- D:

  duration in hours

## Value

the rainfall depth or rainfall return period

## Details

The ARF and it's use is detailed in the Flood Estimation Handbook
(1999), volume 2. The DDF model is calibrated on point rainfall and the
areal reduction factor converts it to a catchment rainfall for use with
a rainfall runoff model such as ReFH (see details for ReFH function).
The ReFH model includes a design rainfall profile for winter and summer
but the depth duration frequency (DDF) model is calibrated on annual
maximum peaks as opposed to seasonal peaks. A seasonal correction factor
(SCF) is necessary to convert the DDF estimate to a seasonal one. The
final depth, therefore is; Depth = DDFdepth x ARF x SCF.

## Author

Anthony Hammond

## Examples

``` r
# Derive the ARF for a depth of 30, an area of 500km^2 and a duration of 12 hours
ARF(30, 500, 12)
#> [1] 26.54054
```
