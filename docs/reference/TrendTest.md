# Trend hypothesis test

A hypothesis test for trend

## Usage

``` r
TrendTest(x, Variance = FALSE, method = "mk", alternative = "two.sided")
```

## Arguments

- x:

  a numeric vector or a data.frame with dates in the first column and
  chronologically ordered variable in the second.

- Variance:

  Logical with a default of FALSE. If TRUE, the test is for a trend in
  variance rather than central tendency.

- method:

  a choice of test method. Choices are "mk" (Mann Kendall - the
  default), "pearson", and "spearman".

- alternative:

  the alternative hypothesis. Options are "less", "greater", and
  "two.sided". The default is "two.sided".

## Value

A data.frame with columns and associated values: P_value, statistic
(Kendall's tau, Spearman's rho, or Pearson's correlation coefficient),
and a standardised distribution value. The latter is either the z score
(for MK test) or students 't' of the observed statistic under the null
hypothesis.

## Details

The test can be performed on a numeric vector, or a data.frame with
dates in the first column and the associated variable of interest in the
second. A choice can be made between Mann Kendall, Pearson, or Spearman
tests. The Spearman and Mann Kendall are based on ranks and will
therefore have the same results whether dates are included or not. The
default is Mann Kendall. The default is to test for any trend
(alternative = "two.sided"). For positive trend set alternative to
"greater", and to test for negative trend set alternative to "less".

Interpretation: When testing for positive trend (alternative =
"greater") the P_value is the probability of exceeding the observed
statistic under the null hypothesis (that it is less than zero). The
vice versa is true when testing for negative trend (alternative =
"less"). For alternative = "two.sided" the P_value is the probability of
exceeding the absolute value of the observed statistic under the null
hypothesis (that it is different from zero). Low P values indicate that
the null hypothesis is less likely.

## Author

Anthony Hammond

## Examples

``` r
# Get an AMAX sample and apply a trend test with the default Mann-Kendall test
am_27083 <- GetAM(27083)
TrendTest(am_27083)
#>           P_value       tau         z
#> Result: 0.3335023 0.1142857 0.9670835

# Apply the test with the Pearson correlation method with dates
# included (full object) and not (flow values only)
TrendTest(am_27083, method = "pearson")
#>           P_value       cor      t
#> Result: 0.3123685 0.1732133 1.0255
TrendTest(am_27083$Flow, method = "pearson")
#>           P_value       cor        t
#> Result: 0.3154241 0.1721395 1.018947

# Apply the default Mann-Kendall test for positive trend
TrendTest(am_27083$Flow, alternative = "greater")
#>           P_value       tau         z
#> Result: 0.1667512 0.1142857 0.9670835
```
