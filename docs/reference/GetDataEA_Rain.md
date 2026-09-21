# Get Environment Agency rainfall data (England).

Extract rainfall data from the Environment Agency's Hydrology Data
Explorer.

## Usage

``` r
GetDataEA_Rain(
  Lat = 54,
  Lon = -2,
  Range = 10,
  WISKI_ID = NULL,
  Period = "Daily",
  From = NULL,
  To = NULL
)
```

## Arguments

- Lat:

  Latitude (as a decimal) for the centre of the search for gauges. You
  can convert BNG to Lat and Lon using the GridRefConvert function.

- Lon:

  Longitude (as a decimal) for the centre of the search for gauges. You
  can convert BNG to Lat and Lon using the GridRefConvert function.

- Range:

  The radius (km) from the point of interest (Lat, Lon) for which the
  user wants rain gauge information (currently works to a maximum of
  just over 20km).

- WISKI_ID:

  The WISKI identification (as "character") for the rain gauge of
  interest

- Period:

  The sampling rate of the rainfall in hours. Either "Daily", "15Mins",
  "Hourly".

- From:

  The start date of the data extraction in the form of "YYYY-MM-DD". To
  get data from the first date available leave as NULL.

- To:

  The end date of the data extraction in the form of "YYYY-MM-DD". To
  get data from the first date available leave as NULL.

## Value

If searching for rain gauge details with the Latitude and Longitude a
dataframe of gauges is returned. If extracting rainfall using the
WISKI_ID, a dataframe is returned with Date / POSIXct in the first
columns and rainfall in the second.

## Details

The function provides one of two outputs. Either information about
available local rain gauges, or the data from a specified gauge
(specified by WISKI ID). The process is to find the local information
(including WISKI ID) by using the latitude and longitude and range (You
can convert BNG to Lat and Lon using the GridRefConvert function). Then
use the WISKI ID to get the data. If data requested is not available,
for example - outside the date range or not available at the requested
sampling rate, an error message is returned stating "no lines available
in input". To extract all the available data leave the From and To
arguments as Null.

## Author

Anthony Hammond

## Examples

``` r
# Get information about available rain gauges
# within a 10km radius of latitude 54.5 and longitude -3.2
if (FALSE) { # \dontrun{
GetDataEA_Rain(Lat = 54.5, Lon = -3.2)
} # }

# Use the WISKI reference ID for the Honister rain gauge
# to get some hourly rain data for December 2015
if (FALSE) { # \dontrun{
honister_dec_2015 <- GetDataEA_Rain(
  WISKI_ID = "592463",
  Period = "Hourly", From = "2015-12-01", To = "2015-12-31"
)
} # }

# Inspect the first few rows and plot the data
if (FALSE) { # \dontrun{
head(honister_dec_2015)
plot(honister_dec_2015, type = "h", ylab = "Rainfall (mm)")
} # }
```
