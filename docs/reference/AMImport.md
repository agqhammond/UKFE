# Import an annual maximum (AMAX) sample from NRFA peak flow .am files

Imports the peak flows and dates from from NRFA peak flow .am files,
excluding the rejected years

## Usage

``` r
AMImport(x)
```

## Arguments

- x:

  the file path for the .AM file

## Value

A data.frame with columns; Date and Flow

## Author

Anthony Hammond

## Examples

``` r
# Import an AMAX sample and display the first six rows in the console
if (FALSE) { # \dontrun{
am_4003 <- AMImport(r"{C:\Data\NRFAPeakFlow_v11\Suitable for QMED\4003.AM}")
} # }
if (FALSE) { # \dontrun{
head(am_4003)
} # }
```
