# Import catchment descriptors from older .xml files

Imports catchment descriptors from xml files (prior to FEH2025) either
from an FEH webservice download or from the Peakflows dataset downloaded
from the national river flow archive (NRFA) website

## Usage

``` r
CDsXML_Legacy(x)
```

## Arguments

- x:

  the xml file path

## Value

A data.frame with columns; Descriptor and Value.

## Details

This function is to allow users to import catchment descriptors in the
format prior to the 2025 update.

## Author

Anthony Hammond

## Examples

``` r

# Import catchment descriptors from a FEH webserver XML file and display XML in the console
if (FALSE) { # \dontrun{
cds_my_site <- CDsXML(r"{C:\Data\FEH_Catchment_384200_458200.xml}")
cds_my_site
} # }
```
