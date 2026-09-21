# FEH99 depth duration frequency precipitation model

Estimation of design rainfall depths, and the rarity of observed
rainfall

## Usage

``` r
DDF99(Duration, RP, pars, Depth = NULL, disc = NULL)
```

## Arguments

- Duration:

  numeric. The duration of interest (in hours)

- RP:

  return period

- pars:

  a numeric vector of length six. The six catchment parameters for the
  DDF model in the order of: c, d1, d2, d3, e, f

- Depth:

  a user supplied rainfall depth for the duration under question

- disc:

  converts from the sliding duration to fixed duration estimate. Choices
  are "hourly" or "daily"

## Value

the rainfall depth or rainfall return period

## Details

The depth duration frequency rainfall model is detailed in the Flood
Estimation Handbook (1999), volume 2. A note about the discretisation:
The user can choose between "daily" or "hourly" for the sliding duration
to fixed duration conversion. If the 'Depth' argument is used, it
overrides the return period (RP) argument and provides RP as a function
of depth. However, if both the 'Depth' and the 'disc' arguments are
used, the sliding duration depth is provided as a function of the user
input depth. This resulting depth can then be used without the 'disc'
argument to determine the sliding duration RP.

## Author

Anthony Hammond

## Examples

``` r
# Examples from FEH volume 2
# The parameters for these examples are from FEH v2

# What is the 2-day rainfall with return period 100 years for Norwich?
DDF99(Duration = 48, RP = 100, pars = c(-0.023, 0.273, 0.351, 0.236, 0.309, 2.488))
#> [1] 106.147

# What is the 4-hour rainfall with return period 20 years for a typical point in the Lyne catchment?
DDF99(Duration = 4, RP = 20, pars = c(-0.025, 0.344, 0.485, 0.402, 0.287, 2.374))
#> [1] 36.613

# How rare was the rainfall of 6th August 1978 at Broughshane, County Antrim?
DDF99(Duration = 5, Depth = 47.7, pars = c(-0.022, 0.412, 0.551, 0.276, 0.261, 2.252))
#> [1] "Return Period"
#> [1] 67.88738
```
