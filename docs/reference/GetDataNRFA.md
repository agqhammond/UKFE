# Get National River Flow Archive data using gauge ID.

Extracts NRFA data using the API.

## Usage

``` r
GetDataNRFA(ID = NULL, Type = "Q")
```

## Arguments

- ID:

  ID number of the gauge of interest.

- Type:

  Type of data required. One of "Q", "P", "PQ", "Gaugings", "AMAX",
  "POT", "CDs", or "Catalogue".

## Value

A data.frame with date in the first columns and variable/s of interest
in the remaining column/s. Except for the following circumstances: When
Type = "Catalogue", then a large dataframe is returned with all the NRFA
gauge metadata. When Type = "AMAX" or "POT" and there are rejected years
a list is returned, where the first element is the dataframe of data and
the second is rejected year/s (character string).

## Details

The function can be used to get daily catchment rainfall or mean flow,
or both together (concurrent). It can also be used to get gaugings,
AMAX, and POT data. Note that some sites have rejected peak flow years.
In which case, if Type = AMAX or POT, the function returns a list, the
first element of which is the rejected years, the second is the full
AMAX or POT. Lastly if Type = "Catalogue" and ID is NULL, it will return
a dataframe of all the NRFA gauges, associated details, comments, and
descriptors. If Type equals "Catalogue" and a valid ID is used, then all
these gauge details are provided for that gauge.

## Author

Anthony Hammond

## Examples

``` r
# Get the concurrent rainfall (P) and mean flow (Q) series for the Tay at Ballathie (site 15006)
if (FALSE) { # \dontrun{
ballathie_pq <- GetDataNRFA(15006, Type = "PQ")
} # }

# Get the gaugings
if (FALSE) { # \dontrun{
ballathie_gaugings <- GetDataNRFA(15006, Type = "Gaugings")
} # }
```
