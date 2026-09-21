# Non-flood adjustment

Adjusts the linear coefficient of variation (Lcv) and the linear
skewness (LSkew) to account for non-flood years

## Usage

``` r
NonFloodAdj(x)
```

## Arguments

- x:

  The annual maximum sample. Numeric vector

## Value

A list is returned. The first element of the list is a dataframe with
one row and two columns - the adjusted Lcv in the first column and Lskew
in the second. The second element of the list is another dataframe with
one row and three columns. Number of non-flood years in the first
column, sample size in the second and the percent of non-flood year in
the third.

## Details

The method is the "permeable adjustment method" detailed in chapter 19,
volume three of the Flood Estimation Handbook, 1999. The method makes no
difference for sites where there are no annual maximums (AM) in the
sample that are \< median(AM)/2. Once applied the results can be used
with the LRatioChange function to update the associated member of a
pooling group. There is also the NonFloodAdjPool() function which can be
used for multiple sites in a pooling group. The non flood adjustment
procedure makes the assumption that annual maxima below QMED/2 are not
from the same distribution and will result in a biased estimate. In turn
it assumes that the AMAX are from a stationary process. The process adds
uncertainty to the usual fitting process for three main reasons.
Firstly, the definition of non-flood year (QMED/2). Secondly, the
reduced sample size. Thirdly, the calculation process is based, in part,
on the proportion of non-flood years to flood years. This proportion has
uncertainty as a function of the sample size and the proportion because
the standard error of a proportion (p) = sqrt((p \* (1 - p)) / n).

## Author

Anthony Hammond

## Examples

``` r
# Get an annual maximum sample with a BFIHOST above 0.65 and with some
# annual maxima lower than half the median of the AMAX series, then apply the function
NonFloodAdj(GetAM(44013)[, 2])
#> [[1]]
#>         Lcv        LSkew
#> 1 0.6911011 -0.004704584
#> 
#> [[2]]
#>   No.NonFlood  N PercentNonFlood
#> 1          12 32            37.5
#> 
```
