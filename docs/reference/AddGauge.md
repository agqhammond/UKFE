# Add an AMAX sample

This function allows the user to add an AMAX sample and associated
catchment descriptors for use with the FEH process.

## Usage

``` r
AddGauge(CDs, AMAX, ID)
```

## Arguments

- CDs:

  catchment descriptor object imported using the CDsXML function.

- AMAX:

  Either a data.frame with date (or POSIXct) in the first column and a
  numeric vector in the second (the AMAX). Or an AMAX sample (a numeric
  vector).

- ID:

  This is a user supplied identification number for the AMAX.

## Value

A list object. The first element is a data.frame which is a row of
statistics and descriptors to be added to the PeakFlowData data.frame.
The second element is the AMAX sample formatted to be added to the AMPF
data.frame

## Details

The function provides the necessary AMAX sample statistics and
data.frame for adding catchment descriptors to the PeakFlowData
data.frame. The user must then add these outputs using the rbind
function (see example). The AMAX could be read in or pasted in by the
user or imported using the AMImport function. Once they are added they
can be used in the current R session. If a new session is started
(rather than a saved workspace) the added AMAX would need to be added
again.

## Author

Anthony Hammond

## Examples

``` r
# Read in AMAX and catchment descriptors
if (FALSE) { # \dontrun{
am_add <- AMImport(r"{D:\NRFAPeakFlow_v12_1_0\suitable-for-neither\027003.am}")
cds_add <- CDsXML(r"{D:\NRFAPeakFlow_v12_1_0\suitable-for-neither\027003.xml}")
} # }

# Apply the function and add the results to the necessary data frames
if (FALSE) { # \dontrun{
gauge_27003 <- AddGauge(cds_add, am_add, ID = "27003")
} # }

# Append the descriptors and stats (element[[1]]) to PeakFlowData
if (FALSE) { # \dontrun{
nrfa_data <- rbind(PeakFlowData, gauge_27003[[1]])
} # }

# Append the AMAX series (element[[2]]) to AMPF
if (FALSE) { # \dontrun{
ampf <- rbind(AMPF, gauge_27003[[2]])
} # }
```
