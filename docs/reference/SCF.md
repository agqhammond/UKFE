# Seasonal correction factor (SCF)

The results of applying the ratio of the seasonal annual maximum
rainfall for a given duration to the annual maximum rainfall for the
same duration

## Usage

``` r
SCF(SAAR, duration)
```

## Arguments

- SAAR:

  standardised average annual rainfall. Numeric

- duration:

  duration in hours. Numeric

## Value

A data.frame of one row and two columns: SCFSummer and SCFWinter.

## Details

The SCF and its use is detailed in R&D Technical Report FD1913/TR -
Revitalisation of the FSR/FEH rainfall runoff method (2005). The ReFH
model has a design rainfall profile included for winter and summer but
the depth duration frequency (DDF) model is calibrated on annual maximum
peaks as opposed to seasonal peaks. The SCF is necessary to convert the
DDF estimate to a seasonal one. Similarly, the DDF model is calibrated
on point rainfall and the area reduction factor converts it to a
catchment rainfall for use with a rainfall runoff model such as ReFH
(see details of the ReFH function). The final depth, therefore, is;
Depth = DDFdepth x ARF x SCF. Note that the SCF function (as detailed in
FEH volume 2) was derived for durations of up to one day.

## Author

Anthony Hammond

## Examples

``` r
# Derive the SCF for a SAAR of 1981 and a duration of 6.5 hours
SCF(1981, 6.5)
#>   SCFSummer SCFWinter
#> 1      0.92     0.918
```
