# Convert between British National Grid Reference (BNG) and Latitude and Longitude or Irish Grid references.

Function to convert between BNG easting & northing and Latitude &
Longitude (or vice versa). Or to convert between BNG and Irish national
grid (or vice versa)

## Usage

``` r
ConvertGridRef(x, fromBNG = TRUE, IGorLatLon = "LatLon")
```

## Arguments

- x:

  A vector of length 2. Either latitude and longitude (if fromBNG =
  FALSE) or BNG easting and northing (if fromBNG = TRUE). Or Irish
  easting and northing if IGorLatLon is set to IG and fromBNG = FALSE.

- fromBNG:

  A logical argument with a default of TRUE. When TRUE it converts from
  BNG easting and northing to latitude and longitude (or to IG easting
  and northing if IGorLatLon is set to "IG"). When FALSE it converts the
  other way round.

- IGorLatLon:

  This argument allows you to choose between Latitude & Longitude and
  Irish grid reference. The acceptable options are "LatLon" or "IG". If
  you choose "IG" you are converting between BNG and IG. If you choose
  "LatLon", you are converting between BNG and Lat Lon.

## Value

A data.frame with the converted grid references. Either latitude and
longitude if BNG = TRUE. Or BNG easting and northing if fromBNG = FALSE.
Or, IG easting & northing if fromBNG = TRUE and IGorLatLon = "IG".

## Details

To convert to Lat and Lon from BNG, ensure that the fromBNG argument is
TRUE. To convert the other way, set fromBNG as FALSE. The same applies
for converting between Irish grid and BNG. To convert Irish grid and BNG
set the IGorLatLon argument to IG.

## Author

Anthony Hammond

## Examples

``` r
# Convert a BNG numeric reference to latitude and longitude
ConvertGridRef(c(462899, 187850))
#>   latitude longitude
#> 1   51.586 -1.093544

# Convert latitude and longitude to easting and northing
ConvertGridRef(c(51.6, -1), fromBNG = FALSE)
#>    easting northing
#> 1 469358.6   189491
```
