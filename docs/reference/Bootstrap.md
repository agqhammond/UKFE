# Bootstrap

Resampling with replacement to approximate the sampling distribution of
a statistic and quantify uncertainty.

## Usage

``` r
Bootstrap(x, Stat, n = 500, Conf = 0.95, ReturnSD = FALSE, ...)
```

## Arguments

- x:

  a numeric vector. The sample of interest

- Stat:

  the function (to calculate the statistic) to be applied to the
  bootstrapped samples. For example mean, max, or median.

- n:

  the number of bootstrapped samples (default 500). i.e. the size of the
  derived sampling distribution.

- Conf:

  the confidence level of the intervals (default 0.95). Must be between
  0 and 1.

- ReturnSD:

  Logical argument with a default of FALSE. If true the bootstrapped
  sampling distribution is returned.

- ...:

  further arguments for the Stat function. For example if you use the
  GEVAM function you might want to add RP = 50 to derive a sampling
  distribution for the 50-year quantile.

## Value

If ReturnSD is FALSE a data.frame is returned with one row and three
columns; Mean, lower, and upper (statistics of the bootsrapped sampling
distribution). If ReturnSD is TRUE, the sampling distribution is
returned.

## Details

The bootstrapping procedure resamples from a sample length(x) \* n times
with replacement. After splitting into n samples of size length(x), the
statistic of interest is calculated on each.

## Author

Anthony Hammond

## Examples

``` r
# Extract an AMAX sample and quantify uncertainty for the Gumbel estimated 50-year flow
am_203018 <- GetAM(203018)
Bootstrap(am_203018$Flow, Stat = GumbelAM, RP = 50)
#>   Mean Lower Upper
#> 1  156   130   186

# Quantify uncertainty for the sample standard deviation at the 90% confidence level
Bootstrap(am_203018$Flow, Stat = sd, Conf = 0.90)
#>   Mean Lower Upper
#> 1 28.6  20.4  36.6

# Return the sampling distribution of the mean and plot an associated histogram
samp_dist <- Bootstrap(am_203018$Flow, Stat = mean, ReturnSD = TRUE)
hist(samp_dist)

```
