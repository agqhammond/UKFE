# DDF results from a DDFImport object

Extracts results from a data frame imported using the DDFImport function

## Usage

``` r
DDF(x, duration, RP = 100)
```

## Arguments

- x:

  A data frame of DDF13 or DDF22 results imported using the DDFImport
  function

- duration:

  the duration (hrs) for which a rainfall depth estimate is required

- RP:

  the return period (years) for which a rainfall depth estimate is
  required

## Value

A DDF13 or DDF22 estimate of rainfall depth (mm)

## Details

The .xml files only provide a set number of durations and return periods
for DDF13 and DDF22. This is an interpolator function to derive depths
for intervening durations and return periods. The result is rounded to
an integer.

## Author

Anthony Hammond

## Examples

``` r
# Import DDF13 results from an NRFA Peak Flows XML file
if (FALSE) { # \dontrun{
ddf13_4003 <- DDFImport("C:/Data/NRFAPeakFlow_v9/Suitable for QMED/04003.xml", DDFVersion = 13)
} # }

# Estimate the 20-year, 5-hour depth
if (FALSE) { # \dontrun{
DDF(ddf13_4003, duration = 5, RP = 20)
} # }
```
