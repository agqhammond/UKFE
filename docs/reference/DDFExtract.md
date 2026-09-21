# Derive and plot rainfall Depth Duration Frequency curves.

Derive and plot rainfall Depth Duration Frequency curves from an input
of rainfall data.

## Usage

``` r
DDFExtract(x, Plot = TRUE, main = NULL, Truncate = TRUE)
```

## Arguments

- x:

  A data.frame with POSIXct in the first column and rainfall in the
  second. The data must have an hourly or sub-hourly sampling rate.

- Plot:

  Logical argument with a default of TRUE. If TRUE, the DDF curves are
  plotted.

- main:

  Title for the plot (character string). The default is no title.

- Truncate:

  Logical argument with a default of TRUE. If TRUE the extraction of
  annual maximum process truncates the data to incorporate only full
  hydrological years. If there is significant rainfall within a partial
  year it will not be included unless Truncate = FALSE. If Truncate =
  FALSE, ensure that there are at least 92 hours of data available in
  the partial years or the function will fail.

## Value

A dataframe with hours (1 to 96) in the first column then depths
associated with a range of return periods (2 to 1000) in the remaining
nine columns. If Plot = TRUE, a plot of the DDF curves is also returned.

## Details

The function works by extracting the annual maximum sample (by
hydrological year - starting Oct 1st) of rainfall for a range of sliding
durations (1 hour to 96 hours). It then calculates the median annual
maximum rainfall depth (RMED) and a GEV growth curve for each duration.
To ensure RMED increases with duration a power curve is fit as a
function of duration to provide the final RMED estimates. Then the
average growth factor for each return period (across the durations) is
assumed.

## Author

Anthony Hammond

## Examples

``` r
# Extract all available 15-minute rainfall from the St Ives (Cambridgeshire)
# rain gauge (WISKI ID = 179365).
if (FALSE) { # \dontrun{
st_ives <- GetDataEA_Rain(WISKI_ID = "179365", Period = "15Mins")
} # }

# Apply the DDF function.
if (FALSE) { # \dontrun{
DDFExtract(st_ives)
} # }
```
