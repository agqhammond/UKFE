# Non-flood adjustment for pooling groups

Applies the NonFloodAdj function to adjust the LCV and LSKEW of one or
more sites in a pooling group.

## Usage

``` r
NonFloodAdjPool(x, Index = NULL, AutoP = NULL, ReturnStats = FALSE)
```

## Arguments

- x:

  A pooling group, derived from the Pool() or PoolSmall() functions.

- Index:

  A vector of indices (row numbers) of sites to be adjusted. If Index =
  NULL (the default) the function is applied to all sites.

- AutoP:

  A percentage (numeric) of non flood years. Any sites in the group
  exceeding this value will be adjusted. This is an automated approach
  so that the user doesn't need to specify Index. If no sites are above
  AutoP, the function is applied to all sites.

- ReturnStats:

  Logical with a default of FALSE. If set to TRUE, a dataframe of
  non-flood year stats is returned (see 'Value' section below) instead
  of the adjusted Pooling group.

## Value

By default the pooling group is returned with adjusted LCVs and LSKEWs
for all sites indexed (or all sites when Index = NULL), or all sites
with percentage of non-flood years above AutoP. No difference will be
seen for sites with no AMAX \< 0.5QMED. If ReturnStats is set to TRUE, a
dataframe with Non-flood year stats is returned. The dataframe has a row
for each site in the pooling group and three columns. The first is the
number of non-flood years, the second is the number of years, and the
third is the associated percentage.

## Details

For more details of the method for individual sites see the details
section of the NonFloodAdj function. As a default this function applies
NonFloodAdj to every member of the pooling group. Index can be supplied
which is the row name/s of the members you wish to adjust. Or AutoP can
be applied and is a percentage. Any member with a greater percentage of
non-flood years than AutoP is then adjusted. The non-flood adjustment
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
# Set up a pooling group for site 44013, then apply the function
pool_44013 <- Pool(GetCDs(44013), N = 500)
pool_nf <- NonFloodAdjPool(pool_44013)

# Return the non-flood stats for the pooling group
NonFloodAdjPool(pool_44013, ReturnStats = TRUE)
#>       ID No.NonFlood  N PercentNonFlood
#> 1  44013          12 32       37.500000
#> 2  44008          11 33       33.333333
#> 3  43029           9 41       21.951220
#> 4  44003           1 14        7.142857
#> 5  44011           1 29        3.448276
#> 6  49002           2 56        3.571429
#> 7  49004           6 55       10.909091
#> 8  41023           8 47       17.021277
#> 9  42008           1 53        1.886792
#> 10 42006           5 65        7.692308
#> 11 47009           1 55        1.818182
#> 12 27095           2 24        8.333333
```
