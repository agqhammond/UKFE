# Create pooling group using the FEH08 method

Legacy function to develop a pooling group based on catchment
descriptors

## Usage

``` r
Pool_FEH08(
  CDs,
  N = 500,
  UrbMax = 0.03,
  DeUrb = TRUE,
  exclude = NULL,
  include = NULL
)
```

## Arguments

- CDs:

  catchment descriptors derived from either GetCDs or CDsXML

- N:

  minimum Number of total gauged record years for the pooling group

- UrbMax:

  Maximum URBEXT2000 level with a default of 0.03. Any catchment with
  URBEXT2000 above this level will be excluded from the pooling group

- DeUrb:

  logical argument with a default of TRUE. If TRUE, the LCVs of all
  sites in the pooling group are "De-Urbanised" according to the FEH08
  method.

- exclude:

  sites to exclude from the pooling group. Either a single site
  reference or a vector of site references (numeric). If this is used
  the next site with the lowest SDM is included such that the total
  sample of AMAX is at least N.

- include:

  sites to include that otherwise would not be included by default. For
  example if it is a subject site that has URBEXT2015 above UrbMax. Or
  one that has not been selected automatically using the similarity
  distance measure.

## Value

A data.frame of the pooling group with site reference row names and 14
columns, each providing catchment & gauge details for the sites in the
pooling group.

## Details

A pooling group is created from a CDs object, derived from GetCDs or
CDsXML (CDsXML_Legacy). To change the default pooling group, one or more
sites can be excluded using the 'exclude' option, which requires either
a site reference or multiple site references in a vector. If this is
done, the site with the next lowest similarity distance measure is added
to the group (until the total number of years is at least N). Sites with
URBEXT2000 (urban extent) \> 0.03 are excluded from the pooling group by
default. This threshold can be adjusted with UrbMax. If DeUrb is set as
TRUE (the default), the LCV and LSKEW values for sites in the pooling
group are de-urbanised.

The pooling method is as specified by FEH2008. Accordingly the SAAR
applied is SAAR6190, FARL is FARL (as opposed to FARL2015) and BFIHOST
is BFIHOST (as opposed to BFIHOST19 or BFIHOST19scaled)

## Author

Anthony Hammond

## Examples

``` r
# Get some catchment descriptors
cds_73005 <- GetCDs(73005)

# Set up a pooling group object called pool_73005 excluding sites 79005 & 46003
# Then print the group to the console
pool_73005 <- Pool_FEH08(cds_73005, exclude = c(79005, 46003))
pool_73005
#>        AREA SAAR6190  FARL  FPEXT BFIHOST URBEXT2000        Lcv      LSkew
#> 73005 212.2     1726 0.976 0.0739   0.514     0.0179 0.21424824 0.21112965
#> 73012 183.2     1787 0.972 0.0712   0.496     0.0052 0.19359236 0.19270100
#> 72005 219.2     1670 0.995 0.0484   0.438     0.0019 0.19321623 0.19289057
#> 59001 227.5     1890 0.996 0.0503   0.407     0.0238 0.13285037 0.12898347
#> 71008 258.2     1602 0.970 0.0550   0.330     0.0021 0.16119938 0.16084910
#> 81003 170.7     1504 0.977 0.0584   0.296     0.0002 0.12801509 0.12798268
#> 3002  237.1     1784 0.974 0.0377   0.436     0.0000 0.14600000 0.14600000
#> 58002 190.7     1946 0.983 0.0427   0.346     0.0114 0.16611227 0.16420397
#> 71011 203.2     1446 0.998 0.0987   0.382     0.0071 0.06768261 0.06659409
#> 56006 184.7     1674 0.963 0.0365   0.477     0.0016 0.20018868 0.19991282
#>       LKurt QMED  N    SDM Discordancy Discordant
#> 73005 0.192  170 56 0.0000       0.629      FALSE
#> 73012 0.227  144 40 0.2194       0.785      FALSE
#> 72005 0.169  272 55 0.3190       1.180      FALSE
#> 59001 0.239  259 50 0.3538       0.707      FALSE
#> 71008 0.243  223 55 0.3763       0.109      FALSE
#> 81003 0.138  135 58 0.4379       1.140      FALSE
#> 3002  0.166  178 48 0.4382       0.629      FALSE
#> 58002 0.317  224 46 0.4455       1.460      FALSE
#> 71011 0.239  122 54 0.4630       2.170      FALSE
#> 56006 0.235  164 44 0.4719       1.180      FALSE

```
