# Diagnostic plots for pooling groups

Provides 11 plots to compare the sites in the pooling group

## Usage

``` r
DiagPlots(x, gauged = FALSE, UrbMax = 0.03)
```

## Arguments

- x:

  pooling group derived from the Pool() function

- gauged:

  logical argument with a default of FALSE. TRUE adds the top site in
  the pooling group to the plots in a different colour

- UrbMax:

  This is for the plotting of the URBEXT comparison. Ideally it should
  be the same as the UrbMax used for deriving the input pooling group

## Value

Eleven diagnostic plots for pooling groups

## Author

Anthony Hammond

## Examples

``` r
# Form a gauged pooling group and plot the diagnostics
pool_28015 <- Pool(GetCDs(28015))
DiagPlots(pool_28015, gauged = TRUE)












```
