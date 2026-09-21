# Extreme value plot (frequency and growth curves)

Plots the extreme value frequency curve or growth curve with observed
sample points.

## Usage

``` r
EVPlot(
  x,
  dist = "GenLog",
  scaled = TRUE,
  Title = "Extreme value plot",
  ylabel = NULL,
  LineName = NULL,
  Unc = TRUE
)
```

## Arguments

- x:

  a numeric vector. The sample of interest

- dist:

  a choice of distribution. "GEV", "GenLog", "Kappa3","Gumbel" or
  "GenPareto". The default is "GenLog"

- scaled:

  logical argument with a default of TRUE. If TRUE the plot is a growth
  curve (scaled by the QMED). If FALSE, the plot is a frequency curve

- Title:

  a character string. The user chosen plot title. The default is
  "Extreme value plot"

- ylabel:

  a character string. The user chosen label for the y axis. The default
  is "Q/QMED" if scaled = TRUE and "Discharge (m3/s)" if scaled = FALSE

- LineName:

  a character string. User chosen label for the plotted curve

- Unc:

  logical argument with a default of TRUE. If TRUE, 95 percent
  uncertainty intervals are plotted.

## Value

An extreme value plot (frequency or growth curve) with intervals to
quantify uncertainty

## Details

The plotting has the option of generalised extreme value (GEV),
generalised Pareto (GenPareto), Gumbel, or generalised logistic (GenLog)
distributions. The uncertainty is quantified by bootstrapping.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and plot the growth curve with the GEV distribution
am_203018 <- GetAM(203018)
EVPlot(am_203018$Flow, dist = "GEV")

```
