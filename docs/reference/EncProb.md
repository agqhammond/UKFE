# Encounter probabilities

Calculates the probability of experiencing at least n events with a
given return period (RP), over a given number of years

## Usage

``` r
EncProb(n, yrs, RP, dist = "Poisson")
```

## Arguments

- n:

  number of events

- yrs:

  number of years

- RP:

  return period of the events

- dist:

  choice of probability distribution. Either "Poisson" or "Binomial"

## Value

A probability

## Details

The choice of binomial or Poisson distributions for calculating
encounter probablities is akin to annual maximum (AM) versus peaks over
threshold (POT) approaches to extreme value analysis. AM and binomial
assume only one "event" can occur in the blocked time period. Whereas
Poisson and POT don't make this assumption. In the case of most
catchments in the UK, it is rare to have less than two independent
"events" per year; in which case the Poisson and POT choices are more
suitable. In large catchments, with seasonally distinctive baseflow,
there may only be one independent peak in the year. However, the results
from both methods converge with increasing magnitude, yielding
insignificant difference beyond a 20-year return period.

## Author

Anthony Hammond

## Examples

``` r
# Calculate the probability of exceeding at least one 50-year RP event
# over a 10-year period, using the Poisson distribution
EncProb(n = 1, yrs = 10, RP = 50)
#> [1] 0.1812692

# Calculate the probability of exceeding at least two 100-year RP events
# over a 100-year period, using the Binomial distribution
EncProb(n = 2, yrs = 100, RP = 100, dist = "Binomial")
#> [1] 0.264238
```
