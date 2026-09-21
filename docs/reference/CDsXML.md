# Import catchment descriptors from .xml files

Imports catchment descriptors from xml files either from an FEH
webservice download or from the Peakflows dataset downloaded from the
national river flow archive (NRFA) website

## Usage

``` r
CDsXML(x)
```

## Arguments

- x:

  the xml file path

## Value

A data.frame with columns; Descriptor and Value.

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
