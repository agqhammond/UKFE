# Create pooling group

Function to develop a pooling group based on catchment descriptors

## Usage

``` r
Pool(CDs, N = 800, UrbMax = 0.03, DeUrb = TRUE, exclude = NULL, include = NULL)
```

## Arguments

- CDs:

  catchment descriptors derived from either GetCDs or CDsXML

- N:

  minimum Number of total gauged record years for the pooling group

- UrbMax:

  Maximum URBEXT2015 level with a default of 0.03. Any catchment with
  URBEXT2015 above this level will be excluded from the pooling group

- DeUrb:

  logical argument with a default of TRUE. If TRUE, the LCVs of all
  sites in the pooling group are "De-Urbanised".

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

A data.frame of the pooling group with site reference row names and 24
columns, each providing catchment & gauge details for the sites in the
pooling group.

## Details

A pooling group is created from a CDs object, derived from GetCDs or
CDsXML, or specifically with the catchment descriptors (see arguments).
To change the default pooling group, one or more sites can be excluded
using the 'exclude' option, which requires either a site reference or
multiple site references in a vector. If this is done, the site with the
next lowest similarity distance measure is added to the group (until the
total number of years is at least N). Similarly a site can be included
specifically by using the include argument. Sites with URBEXT2015 (urban
extent) \> 0.03 are excluded from the pooling group by default. This
threshold can be adjusted with UrbMax. If DeUrb is set as TRUE (the
default), the LCV values for sites in the pooling group are
de-urbanised. If the user has more data available for a particular site
within the pooling group, the LCV and LSKEW for the site can be updated
after the group has been finalised using the LRatioChange function.

The pooling method is as specified by FEH2025. The de-urbanisation
functionality assumes that the growth curve associated with an annual
maximum flow sample is impacted by urbanisation and that this impact can
be modelled as a function of the catchment URBEXT. The method for
pooling the catchments together is based on the similarity of AREA,
SAAR, FARL, FPEXT, and BFIHOST. These were seen to have the most
significant impact on the LCV and LSKEW - and ultimately to provide the
lowest 'Pooling Uncertainty Measure' (a statistic for assessing the
similarity between pooled and single site gauged estimates).

## Author

Anthony Hammond

## Examples

``` r
# Get some catchment descriptors
cds_73005 <- GetCDs(73005)

# Set up a pooling group object called pool_73005 excluding sites 79005 & 46003
# Then print the group to the console
pool_73005 <- Pool(cds_73005, exclude = c(79005, 46003))
pool_73005
#>        AREA SAAR9120 FARL2015  FPEXT BFIHOST19scaled URBEXT2015       Lcv LSkew
#> 73005 212.2     1905   0.9823 0.0739           0.465     0.0261 0.2155752 0.265
#> 73012 183.2     1976   0.9795 0.0712           0.450     0.0116 0.1944398 0.320
#> 63001 170.1     1620   0.9942 0.0471           0.430     0.0039 0.1824554 0.201
#> 72005 219.2     1811   0.9967 0.0484           0.390     0.0029 0.1933590 0.121
#> 13012 130.6     1718   0.9874 0.0414           0.455     0.0001 0.2150138 0.174
#> 72015 140.8     1790   0.9948 0.0549           0.392     0.0038 0.1533730 0.122
#> 56006 184.7     1849   0.9614 0.0365           0.413     0.0030 0.2003848 0.183
#> 60013 243.0     1673   0.9976 0.0336           0.439     0.0023 0.2073053 0.256
#> 60002 298.7     1688   0.9980 0.0315           0.444     0.0026 0.2093485 0.228
#> 48011 167.2     1529   0.9680 0.0349           0.448     0.0054 0.1906585 0.173
#> 15013 173.3     1613   0.9960 0.0308           0.421     0.0014 0.1961759 0.140
#> 76022 249.7     1327   0.9985 0.0781           0.415     0.0068 0.2048908 0.231
#> 60006 131.1     1688   0.9996 0.0296           0.467     0.0071 0.1727843 0.153
#> 76021 223.0     1372   0.9965 0.0471           0.414     0.0039 0.1924804 0.168
#> 49001 209.9     1413   0.9855 0.0338           0.481     0.0226 0.2211798 0.243
#> 79004 142.7     1719   0.9985 0.0319           0.405     0.0008 0.1340687 0.141
#> 73008 127.4     1385   0.9587 0.0931           0.483     0.0126 0.2096861 0.301
#> 54038 241.1     1386   0.9952 0.0382           0.427     0.0031 0.1573122 0.186
#> 47004 135.3     1477   0.9950 0.0339           0.482     0.0128 0.2258447 0.298
#>       LKurt  QMED  N    SDM Discordancy Discordant
#> 73005 0.192 170.0 56 0.0000       0.405      FALSE
#> 73012 0.227 144.0 40 0.1966       1.880      FALSE
#> 63001 0.180  95.1 63 0.6601       0.102      FALSE
#> 72005 0.169 272.0 55 0.7344       1.080      FALSE
#> 13012 0.204  76.6 33 0.7650       1.060      FALSE
#> 72015 0.189 199.0 45 0.7766       1.730      FALSE
#> 56006 0.235 164.0 44 0.7774       1.030      FALSE
#> 60013 0.131 123.0 10 0.7780       1.420      FALSE
#> 60002 0.203 179.0 63 0.8566       0.189      FALSE
#> 48011 0.187  50.9 22 0.8591       0.203      FALSE
#> 15013 0.142 121.0 37 0.8954       0.808      FALSE
#> 76022 0.144 159.0 27 0.9250       0.647      FALSE
#> 60006 0.113  84.1 56 0.9392       0.721      FALSE
#> 76021 0.103 184.0 24 0.9454       1.200      FALSE
#> 49001 0.233  57.5 55 0.9476       0.623      FALSE
#> 79004 0.126 149.0 43 0.9594       2.230      FALSE
#> 73008 0.275  37.0 55 0.9655       1.750      FALSE
#> 54038 0.142  79.3 51 0.9807       1.010      FALSE
#> 47004 0.209  46.3 59 0.9916       0.924      FALSE

```
