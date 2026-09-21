# Get Scottish Environment Protection Agency (SEPA) Flow, Level, or Rainfall data.

Extract hydrometric data from SEPA's API.

## Usage

``` r
GetDataSEPA(
  Lat = NULL,
  Lon = NULL,
  RiverName = NULL,
  Type = "Flow",
  StationID = NULL,
  Range = 20,
  From = NULL,
  To = NULL,
  Period = "Daily"
)
```

## Arguments

- Lat:

  Latitude of the point of interest. Provided when the user wants
  information about available local gauges (by specified 'Type')

- Lon:

  Longitude of the point of interest. Provided when the user wants
  information about available local gauges (by Specified 'Type')

- RiverName:

  A river name for searching gauges by river catchment. Starting with a
  capital letter.

- Type:

  The type of hydrometric data required. Either "Flow", "Level", or
  "Rain".

- StationID:

  The ID name of the station for which you want data.

- Range:

  The radius (km) from the point of interest (Lat, Lon) for which the
  user wants a list of gauges by specified 'Type' (default is 20).

- From:

  A start date for the data in the form of "YYYY-MM-DD". Default of NULL
  means the earliest available date is used

- To:

  An end date for the data in the form of "YYYY-MM-DD". The default is
  the most recent date available.

- Period:

  This argument specifies the required timestep of the data. Either
  "15Mins", "Hourly", or "Daily".

## Value

A data.frame with POSIXct in the first column, and rainfall in the
second column. Unless the StationName provided is not in the available
list, then the available list is returned.

## Details

You can download data using the gauge station ID and you can find gauges
within a given range using the latitude and longitude, or a river name.
If the 'From' date is left as null, the earliest date of available data
will be used. If the 'To' date is left as null, the most recent date of
available data will be used.

## Author

Anthony Hammond

## Examples

``` r
# search Rain gauges by Lat and Lon
if (FALSE) { # \dontrun{
GetDataSEPA(Lat = 56, Lon = -4, Type = "Rain")
} # }

# Get daily rain from the Bannockburn station between two dates
if (FALSE) { # \dontrun{
bannockburn <- GetDataSEPA(
  StationID = "36494",
  From = "1998-10-01", To = "1998-10-31"
)
} # }

# Inspect the first few rows and plot the data
if (FALSE) { # \dontrun{
head(bannockburn)
plot(bannockburn, type = "h", ylab = "Rainfall (mm)")
} # }
```
