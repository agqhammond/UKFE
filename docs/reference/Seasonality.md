# Seasonality plot

A plot to inspect the seasonality of peak flows

## Usage

``` r
Seasonality(x, Lines = FALSE, Main = "Seasonality")
```

## Arguments

- x:

  A dataframe with Date or POSIXct in the first folumn and numeric in
  the second.

- Lines:

  Logic with a default of FALSE. If TRUE, lines are plotted instead of
  dots.

- Main:

  Title for the plot. The default is "Seasonality".

## Value

A seasonality plot

## Details

The dots (or dark lines if Lines = TRUE) show the season of individual
peaks. The red line shows the average seasonality. The longer it is the
more clustered in time the peaks are.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and plot the seasonality
am_27083 <- GetAM(27083)
Seasonality(am_27083)


# Now do the same with lines instead of dots
Seasonality(am_27083, Lines = TRUE)

```
