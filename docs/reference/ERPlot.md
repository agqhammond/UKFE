# Extreme rank plot

A plot to inspect the distribution of ordered data

## Usage

``` r
ERPlot(x, dist = "GenLog", main = NULL, Pars = NULL, GF = NULL, ERType = 1)
```

## Arguments

- x:

  numeric vector. A sample for inspection

- dist:

  a choice of distribution. The choices are "GenLog" (the default),
  "GEV", "Kappa3,"Gumbel", and "GenPareto"

- main:

  a character string to change the default title, which is the
  distribution choice.

- Pars:

  a vector of parameters for the distribution. In the order of location,
  scale, & shape (ignoring the latter if Gumbel). If left null the
  parameters are estimated from x.

- GF:

  a vector of length growth curve parameters, in the order of; Lcv,
  LSkew and Median (ignoring the LSkew if Gumbel).

- ERType:

  Either 1, 2. If it is the default 1 then ranks are plotted on the x
  axis and percentage difference of modelled from observed is plotted on
  the y axis.

## Value

The extreme rank plot as described in the details

## Details

By default this plot compares the percentage difference of simulated
results with observed for each rank of the data. Another option (see
ERType argument) compares the simulated flows for each rank of the
sample with the observed of the same rank. For both plots 500 simulated
samples are used. With the second option for each rank they are plotted
and the mean of these is highlighted in red. There is a line of perfect
fit so you can see how much this "cloud" of simulation differs from the
observed. By default the parameters of the distribution for comparison
with the sample are estimated from the sample. However, the pars
argument can be used to compare the distribution with parameters
estimated separately. Similarly the growth factor (GF) parameters,
linear coefficient of variation (Lcv) & linear skewness (LSkew) with the
median can be entered. In this way the pooling estimated distribution
can be compared to the sample. This ERplot is an updated version of that
described in Hammond, A. (2019). Proposal of the 'extreme rank plot' for
extreme value analysis: with an emphasis on flood frequency studies.
Hydrology Research, 50 (6), 1495-1507.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and plot
if (FALSE) { # \dontrun{
am_27083 <- GetAM(27083)
ERPlot(am_27083$Flow)
} # }

# Assume pooled estimates of Lcv and LSkew of 0.23, 0.17, and a QMED of 12.
# Use these inputs for the GF argument and change the title
if (FALSE) { # \dontrun{
ERPlot(am_27083$Flow, main = "Site 27083 pooled comparison", GF = c(0.23, 0.17, 12))
} # }
```
