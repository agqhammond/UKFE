# Plot of the annual maximum sample

Provides a barplot for an annual maximum sample

## Usage

``` r
AMplot(x, ylab = "Discharge (m3/s)", xlab = "Hydrological year", main = NULL)
```

## Arguments

- x:

  A data.frame with at least two columns. The first a date column and
  the second the annual maximum (AM) sequence. A third column with the
  station id can be applied which is then used for the default plot
  title.

- ylab:

  Label for the y axis (character string).

- xlab:

  Label for the x axis (character string).

- main:

  Title for the plot (character string). The default is 'Annual maximum
  sample:', where : is followed by an ID number if this is included in a
  third column of the dataframe x.

## Value

A barplot of the annual maximum sample

## Details

When used with a GetAM object or any data.frame with dates/POSIXct in
the first column, the date-times are daily or sub-daily. Therefore,
although it's an annual maximum (AM) sequence, some bars may be closer
together depending on the number of days between them.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and plot
AMplot(GetAM(58002))

```
