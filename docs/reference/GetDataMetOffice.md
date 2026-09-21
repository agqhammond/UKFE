# Get regional Met Office average temperature or rainfall series (monthly, seasonal, and annual).

Extracts regional mean temperature or rainfall from the Met Office UK &
regional series. The total duration of bright sunshine is also
available.

## Usage

``` r
GetDataMetOffice(Variable, Region)
```

## Arguments

- Variable:

  Either Tmean, Rainfall, or Sunshine

- Region:

  One of "UK", "England", "Wales", "Scotland", "Northern_Ireland",
  "England_and_Wales", "England_N", "England_S", "Scotland_N",
  "Scotland_E", "Scotland_W", "England_E_and_NE",
  "England_NW_and_N_Wales", "Midlands", "East_Anglia",
  "England_SW_and_S_Wales", "England_SE_and_Central_S".

## Value

A data.frame with 18 columns; year, months, seasons, and annual. Rows
then represent each year of the timeseries.

## Details

The function returns time series data from the 19th century through to
the present month.

## Author

Anthony Hammond

## Examples

``` r
# Get the rainfall time series for the UK
if (FALSE) { # \dontrun{
uk_rain <- GetDataMetOffice(Variable = "Rainfall", Region = "UK")
} # }

# Get the mean temperature data for East Anglia
if (FALSE) { # \dontrun{
temp_east_anglia <- GetDataMetOffice(Variable = "Tmean", Region = "East_Anglia")
} # }
```
