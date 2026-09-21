# DDF99 parameters from .xml files

Imports the FEH 1999 depth duration frequency parameters from xml files
either from an FEH webservice download or from the Peakflows dataset
downloaded from the national river flow archive (NRFA) website

## Usage

``` r
DDF99Pars(x)
```

## Arguments

- x:

  the xml file path

## Value

A list with two elements, each a data frame with columns; parameters and
associated values The first data frame is for the catchment average
parameters (these still require an ARF adjustment where appropriate) and
the second for the 1km2 grid point parameters.

## Details

This function is coded to import DDF99 parameters from xml files from
the NRFA or the FEH web-server. File paths for importing data require
forward slashes. On some operating systems, such as windows, the copy
and pasted file paths will have backward slashes and would need to be
changed accordingly.

## Author

Anthony Hammond

## Examples

``` r
# Import DDF99 parameters from an NRFA Peak Flows XML file and display in console
if (FALSE) { # \dontrun{
ddf99_4003 <- DDF99Pars("C:/Data/NRFAPeakFlow_v11/Suitable for QMED/04003.xml")
ddf99_4003
} # }

# Import DDF99 parameters from a FEH webserver XML file and display in the console
if (FALSE) { # \dontrun{
ddf99_my_site <- DDF99Pars("C:/Data/FEH_Catchment_384200_458200.xml")
ddf99_my_site
} # }
```
