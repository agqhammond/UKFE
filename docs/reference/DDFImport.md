# DDF13 or DDF22 results from .xml files

Imports the depth duration frequency 2013 or 2022 results from xml files
either from an FEH webservice download or from the Peakflows dataset
downloaded from the national river flow archive (NRFA) website

## Usage

``` r
DDFImport(x, ARF = TRUE, Plot = TRUE, DDFVersion = 22)
```

## Arguments

- x:

  the xml file path

- ARF:

  logical argument with a default of TRUE. If TRUE, the areal reduction
  factor is applied to the results. If FALSE, no area reduction factor
  is applied. This is not relevant for a point estimate.

- Plot:

  logical argument with a default of TRUE. If TRUE the DDF curve is
  plotted for a few return periods

- DDFVersion:

  Version of the DDF model (numeric). either 22 or 13. The default is
  22.

## Value

A data frame of DDF results (mm) with columns for duration and rows for
return period. If Plot equals TRUE a DDF plot is also returned.

## Details

This function returns a data-frame of design rainfall estimates. For
further durations and return periods, the separate DDF function can be
applied with the data-frame as the argument/input.

## Author

Anthony Hammond

## Examples

``` r
# Import DDF22 results from an NRFA Peak Flows XML file and display them in console
if (FALSE) { # \dontrun{
ddf22_4003 <- DDFImport(r"{C:\Data\NRFAPeakFlow_v11\Suitable for QMED\04003.xml}")
ddf22_4003
} # }

# Import DDF22 results from a FEH webserver XML file and display them in the console
if (FALSE) { # \dontrun{
ddf22_my_site <- DDFImport(r"{C:\Data\FEH_Catchment_384200_458200.xml}")
ddf22_my_site
} # }
```
