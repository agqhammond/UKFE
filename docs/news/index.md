# Changelog

## UKFE 2.0.2

CRAN release: 2026-06-19

### Minor changes

- QuickResults and Pool now have an “Exclude” argument so that
  particular sites can be specifically excluded from the pooling group.
  Particularly useful if “pretend un-gauged” estimate is wanted from
  QuickResults.  
- Some clearer error messaging has been added to the QMED function in
  regard to the source of the CDs object being applied.
- Added an error message in the CDsXML function for the case of a user
  trying to use it with a point CDs file exported from the FEH
  Webservice.

### Bug Fixes

- The legacy functions (Pool_FEH08, PoolEst_FEH08, and QMED_FEH08)
  worked with the current CDs but not with CDs read in with the
  CDsXML_Legacy function. This has been fixed and the appropriate
  descriptors used.
- The GetDataEA_QH function was returning the wrong columns from the HDE
  data when gauge searching options were used (RiverName or Lat and
  Lon). It is assumed that the columns we’re re-arranged on the data
  provider side. This has been fixed and the columns are now selected by
  column name as opposed to column index.

## UKFE 2.0.1

CRAN release: 2026-05-01

### Major changes

- FEH 2008 legacy functions have been added (Pool_FEH08, PoolEst_FEH08,
  and QMED_FEH08) for comparison with the current FEH2025 methods (now
  the UKFE default).

### Minor changes

- The LowFlows function now has the option to provide a FARL range
  (excluding catchments outside the range from the analysis). It also
  outputs the gauges used in the analysis with their weighting etc.

- The ReFH function, which is now more flexible, incorporating the
  options of changing the unit hydrograph shape, the loss model, the
  baseflow component, and the rainfall profiles, has been updated so
  that the randomised rain profiles are created by using the FSR profile
  as a probability mass function. There is also an update to the way the
  default timestep is calculated when timestep is not specified.

### Bug fixes

\*The following have been fixed: The QMED function failed when
individual descriptors were used as opposed to catchment descriptor
objects. This was also the case with the LowFlows function. When using
the GetDataEA_QH function the “DailyMax” option resulted in duplicated
dates (this is what the HDE returns - so look out when downloading
directly from the website). All fixed.

## UKFE 2.0.0

CRAN release: 2025-10-28

### Major changes

- FEH2025: The Pool, QMED, and PoolEst functions amended to apply the
  FEH2025 methods.

- QMED donors: The QMED function amended so that you can input a vector
  (‘list’ is normal parlance) of gauge IDs as donors, or you can use the
  no.Donors argument and simply choose N donors and the N closest to
  catchment centroid will be used. You can also return all the details
  of these gauges and associated adjustments and distances etc. The
  QuickResults function uses the default of 8 closest donors.

- Pooling uncertainty: By default, the uncertainty calculated for pooled
  estimates is done bespoke for your pooling group (rather than using
  generalised approximating equations - as in previous version). This is
  done by resampling of the pooling group and an assumption about the
  FSE for QMED (if Gauged = FALSE) – which can be adjusted by the user.
  The uncertainty result is provided in the form of an FSE for each
  return period and associated peak flow estimate.

- Defaults: The defaults for Pooling and QMED have been changed so that
  urban adjustments etc are applied unless otherwise specified. The
  Donor default is to choose any gauge (i.e. the URBEXT maximum is set
  at 1), you will need to reduce this if you wish to avoid urban donors
  when using the default ‘No.Donors’ argument.

- CDs: The new descriptors are now available via the GetCDs or CDsXML
  function (there is a CDsXML_legacy function to read in older ones -
  but they won’t work with the new Pool and QMED functions and would
  need to be adapted).

- Data: Removed the two dataframes QMEDData and NRFAData and replaced
  them with a single dataframe called PeakFlowData (it incorporates all
  the info about sites suitable for pooling and/or QMED. The AMSP has
  also been changed. It is a dataframe of annual maximum samples. It now
  includes sites suitable for QMED as well as sites suitable for pooling
  – and has therefore been renamed as AMPF.

- Historic flood estimation: There is now a function called
  HistoricalMLE, which allows you to estimate peak flows whilst
  accounting for k peaks over a specified threshold over h years prior
  to the AMAX record. At present it does not have the option for
  specifying historic discharges.

- Seasonality Plot: Seasonality function has been added, for seasonality
  plotting. A pooled seasonality plot has also been added to the plots
  provided by the DiagPlots function.

- LowFlows: Function called LowFlows added which estimates low flows
  from catchment descriptors (or individual inputs of AREA, SAAR, and an
  estimate of BFI). This returns Qmean, Q95, Q70, Q50, Q10, and Q05.

- ReFH: Amended ReFH function to make it a flexible tool for evaluating
  the plausible response to an input of rainfall.

### Minor changes

- The BFI function now has the option of returning the time series of
  flow along with the baseflow component.

- Accessibility. Many of the plots have been reformatted so that they
  are better for those who may have difficulty differentiating between
  certain colours. For example, the differences between plotted
  components are now highlighted by shading lines etc.

### Bug fixes:

- Hydrometric data extraction: The extraction functions for getting
  hydrometric data from the HDE had missing date times where the hours
  changed in the summer and winter. This has been corrected by making it
  all GMT (as in the HDE). Furthermore, the “hourly” option was not
  working, and it would default to 15minutes when applied; this has been
  fixed.

- CDsXML: When using CDsXML for sites in Northern Ireland, the grid
  referencing was not converted to BNG. This has been fixed.

- EVPlot: If there were NA values in the sample input, this would cause
  an error. This has been fixed.

## UKFE 1.0.0

### Major changes

- Data pre-processing script: Added to the package (note: file paths
  remain local to the package author).

- [`GenParetoPars()`](https://github.com/agqhammond/ukfe/reference/GenParetoPars.md):
  Removed the `mle` option (difficult to verify correctness).

### Minor changes

- Input validation: Added handling for invalid inputs in
  [`GenLogEst()`](https://github.com/agqhammond/ukfe/reference/GenLogEst.md),
  [`GEVEst()`](https://github.com/agqhammond/ukfe/reference/GEVEst.md),
  [`GumbelEst()`](https://github.com/agqhammond/ukfe/reference/GumbelEst.md),
  [`Kappa3Est()`](https://github.com/agqhammond/ukfe/reference/Kappa3Est.md),
  [`GenParetoEst()`](https://github.com/agqhammond/ukfe/reference/GenParetoEst.md)
  (reject scale or RP \<= 0; handle `shape = 0` where applicable).

- Error handling: Improved in
  [`Kappa3Est()`](https://github.com/agqhammond/ukfe/reference/Kappa3Est.md),
  [`GEVPars()`](https://github.com/agqhammond/ukfe/reference/GEVPars.md),
  [`LSkew()`](https://github.com/agqhammond/ukfe/reference/LSkew.md),
  and [`LKurt()`](https://github.com/agqhammond/ukfe/reference/LKurt.md)
  when required arguments (`x`, `L1`, `LCV`, `LSKEW`) are missing.

- Error messaging: More informative message in
  [`Pool()`](https://github.com/agqhammond/ukfe/reference/Pool.md) when
  `DeUrb = TRUE` but no sites are available.

- H2 method:

  - Regional average L-moments are now weighted by record length.
  - Heavy optimisation penalties applied at the boundaries to prevent
    boundary solutions.
  - Small correction applied to the kappa optimisation equation.

- `fse` implementation: Updated in
  [`QuickResults()`](https://github.com/agqhammond/ukfe/reference/QuickResults.md).

- Styling: Applied `styler::style_pkg()` to align with tidyverse
  conventions (cosmetic only).

- Improved accessibility and readability of plots across multiple
  functions (better colour contrast, line types, text sizing, axis
  labelling, and more descriptive titles).

### Bug fixes

- [`GenLogAM()`](https://github.com/agqhammond/ukfe/reference/GenLogAM.md):
  Implementing support for `k = 0` (i.e. `LSkew = 0`).

- GEV shape equation: Minor correction in
  [`GEVGF()`](https://github.com/agqhammond/ukfe/reference/GEVGF.md),
  [`GEVAM()`](https://github.com/agqhammond/ukfe/reference/GEVAM.md) and
  [`GEVPars()`](https://github.com/agqhammond/ukfe/reference/GEVPars.md).

- Exponential usage: Replaced `exp(1)^x` with `exp(x)`.

- `b` formulas: Reworked `b1`, `b2`, and `b3`
  in[`Kappa3Pars()`](https://github.com/agqhammond/ukfe/reference/Kappa3Pars.md),
  [`GenLogAM()`](https://github.com/agqhammond/ukfe/reference/GenLogAM.md),
  [`GEVAM()`](https://github.com/agqhammond/ukfe/reference/GEVAM.md),
  [`GenParetoPOT()`](https://github.com/agqhammond/ukfe/reference/GenParetoPOT.md),
  [`GumbelAM()`](https://github.com/agqhammond/ukfe/reference/GumbelAM.md),
  [`LMoments()`](https://github.com/agqhammond/ukfe/reference/LMoments.md),
  [`Lcv()`](https://github.com/agqhammond/ukfe/reference/Lcv.md),
  [`LSkew()`](https://github.com/agqhammond/ukfe/reference/LSkew.md) and
  [`LKurt()`](https://github.com/agqhammond/ukfe/reference/LKurt.md).

- Optimisation bounds: Corrected for
  [`Kappa3GF()`](https://github.com/agqhammond/ukfe/reference/Kappa3GF.md)
  and
  [`Kappa3Pars()`](https://github.com/agqhammond/ukfe/reference/Kappa3Pars.md).

- `Column indexing`: Fixed
  [`QuickResults()`](https://github.com/agqhammond/ukfe/reference/QuickResults.md)
  selecting wrong column (now indexed by name).

- [`ReFH()`](https://github.com/agqhammond/ukfe/reference/ReFH.md):
  Fixed the calculation of the nearest odd multiple of the timestep when
  the duration is unspecified.

- [`AMImport()`](https://github.com/agqhammond/ukfe/reference/AMImport.md):
  Adjusted for updated date format.

- [`Zdists()`](https://github.com/agqhammond/ukfe/reference/Zdists.md):
  Corrected GEV and GenLog results which were the wrong way round.

- [`ARF()`](https://github.com/agqhammond/ukfe/reference/ARF.md): Fixed
  typo in `b` equation when `20 < Area < 100`.

- Irish Grid & CRS:
  [`CDsXML()`](https://github.com/agqhammond/ukfe/reference/CDsXML.md)
  now uses Irish Grid CRS;
  [`ConvertGridRef()`](https://github.com/agqhammond/ukfe/reference/ConvertGridRef.md)
  uses EPSG codes (instead of self defined CRS).

- Data structures: Corrected coordinates for Northern Irish gauges in
  `AMSP`, `NRFAData`, and `QMEDData`.

## UKFE 0.4.0

CRAN release: 2025-02-09

### Major changes

- `GetDataSEPA_QH()`: A new function to get level and flow data from the
  SEPA API.

- [`DDFExtract()`](https://github.com/agqhammond/ukfe/reference/DDFExtract.md):
  A new function which extracts depth duration frequency curves from
  hourly or sub-hourly rainfall data.

- [`FlowSplit()`](https://github.com/agqhammond/ukfe/reference/FlowSplit.md):
  A new function for hydrograph splitting - separating baseflow from
  runoff. More for shorter event splitting as opposed to long flow
  series (i.e. it is not for deriving baseflow index, the BFI function
  does that).

### Minor changes

- [`FlowDurationCurve()`](https://github.com/agqhammond/ukfe/reference/FlowDurationCurve.md):
  Users can now add additional horizontal flow lines to the plot with
  the `AddQs` argument. With the `ReturnData` argument users can also
  return a data frame with the flow and percentiles.

- [`DesHydro()`](https://github.com/agqhammond/ukfe/reference/DesHydro.md):
  Have removed the `div` argument and simplified it so that the
  `EventSep` argument does both the division of events for the peak
  identification, as well as the event period. It now produces an error
  when fewer than two peaks are extracted.

- [`GetDataEA_QH()`](https://github.com/agqhammond/ukfe/reference/GetDataEA_QH.md),
  [`GetDataEA_Rain()`](https://github.com/agqhammond/ukfe/reference/GetDataEA_Rain.md):
  These functions have been updated so that if the user puts in no start
  and/or end date, it defaults to the minimum and/or maximum dates
  available.

## UKFE 0.3.9

CRAN release: 2025-01-09

Changes combined with 0.4.0 above.

## UKFE 0.3.8

CRAN release: 2024-11-17

### Major changes

- [`DesHydro()`](https://github.com/agqhammond/ukfe/reference/DesHydro.md):
  Vastly improved this function. Significantly quicker and it now
  centres around the main peak rather than the user having to truncate
  after inspecting the plot.

- [`ConvertGridRef()`](https://github.com/agqhammond/ukfe/reference/ConvertGridRef.md):
  New function to convert between latitude and longitude, British
  National Grid reference, and Irish Grid reference.

- [`FlowDurationCurve()`](https://github.com/agqhammond/ukfe/reference/FlowDurationCurve.md):
  New function for plotting flow duration curves from a data frame with
  date or date-time in the first column and flow in the second column
  (plots annual, summer, and winter). Alternatively, you can provide a
  list of flow series to compare.

- [`ERPlot()`](https://github.com/agqhammond/ukfe/reference/ERPlot.md):
  Added an option to the extreme rank plot to create a plot very similar
  to the original version, but the y-axis is the percentage difference
  from the observed. This allows better comparison across distributions.
  There is also the option for a plot of modelled versus observed values
  for each rank.

- [`Bootstrap()`](https://github.com/agqhammond/ukfe/reference/Bootstrap.md):
  Replaced the `UncSS()` function with this more generic bootstrap
  function for deriving the sampling distribution and quantifying
  associated uncertainty for a statistic of your choice (given an input
  sample).

- [`Uncertainty()`](https://github.com/agqhammond/ukfe/reference/Uncertainty.md):
  Now provides the full bespoke resampling methods to derive uncertainty
  for pooling groups detailed in “Hammond, A. (2021). Sampling
  uncertainty of UK design flood estimation. Hydrology Research.
  1357-1371. 52 (6)”. Previously, only the gauged version did this and
  the ungauged version applied the approximating equations (which are
  used by default within the
  [`PoolEst()`](https://github.com/agqhammond/ukfe/reference/PoolEst.md)
  function). The name of the `QMEDfse` argument has changed to `fseQMED`
  with the default changing from 1.46 to 1.55.

- [`AnnualStat()`](https://github.com/agqhammond/ukfe/reference/AnnualStat.md):
  Firstly, this is a name change for the `AMextract()` function (because
  it can be used for any statistic). It also now has a sliding option,
  so that maximum rainfall over any sliding period can be derived as
  opposed to just the maximum over fixed intervals.

- [`LMoments()`](https://github.com/agqhammond/ukfe/reference/LMoments.md):
  Name change because it has bugged me for a while that I initially
  called it `Lmoms`.

- `GetData...` functions. The naming convention of functions that
  extract data from the web has been homogenised so that they can easily
  be found. They all start with `GetData`. They are:

  - [`GetDataEA_QH()`](https://github.com/agqhammond/ukfe/reference/GetDataEA_QH.md)
    (get EA flow or stage, find gauges by river name or lat and lon)
  - [`GetDataEA_Rain()`](https://github.com/agqhammond/ukfe/reference/GetDataEA_Rain.md)
    (get EA rain, find gauges by lat and lon)
  - [`GetDataMetOffice()`](https://github.com/agqhammond/ukfe/reference/GetDataMetOffice.md)
    (get regional monthly rainfall or temperature)
  - [`GetDataNRFA()`](https://github.com/agqhammond/ukfe/reference/GetDataNRFA.md)
    (using gauge ID, get flow, catchment rainfall, AMAX, POT, and
    gaugings)
  - `GetDataSEPA_Rain()` (get SEPA rainfall, find gauges by lat & lon,
    or print a list of them all to the console).

### Minor change

- [`MonthlyStats()`](https://github.com/agqhammond/ukfe/reference/MonthlyStats.md):
  As well as getting all the monthly stats, there is now an option to
  output a monthly time series of the stat in the form of a data frame
  with date in the first column (first of each month) and the statistic
  of interest in the second.

## UKFE 0.3.7

CRAN release: 2024-09-20

Changes combined with 0.3.8 above.

## UKFE 0.3.6

CRAN release: 2024-09-10

### Major changes

- Updated with the new NRFA Peak Flow Dataset (version 13).

- Get data functions. Added a range of functions to get data from
  various sources using the associated APIs. These are:

  - `GetNRFA()` (this can be used to extract daily catchment rainfall,
    daily mean flow, AMAX samples, or gaugings from the NRFA, using
    gauge ID).
  - `GetMetOffice()` (this can be used to get regional series of
    rainfall or temperature on a monthly, seasonal, and annual basis).
  - `GetRainEA()` (this can be used to extract rainfall data from the
    Environment Agency’s Hydrometric Data Explorer. It is available
    under v0.3.5 but I have increased the number of rows the function
    can get – previously you could only get a little over 2 years of
    15-minute data. Now you can theoretically get 57 years. In practice,
    it fails if the extraction takes more than one minute. This
    restricts it to more like 25 years (when I tested it anyway).
  - `GetRainSEPA()` (no change from v0.3.5).

- [`ERPlot()`](https://github.com/agqhammond/ukfe/reference/ERPlot.md).
  Added this back but in revised form. It now directly compares the
  estimated flows for each rank with the observed for each rank.

- `GoF functions`:
  [`GoFCompare()`](https://github.com/agqhammond/ukfe/reference/GoFCompare.md),
  and
  [`GoFComparePool()`](https://github.com/agqhammond/ukfe/reference/GoFComparePool.md).
  New goodness-of-fit functions: one for single samples and one for
  pooling groups. They are more straightforward to interpret than
  [`Zdists()`](https://github.com/agqhammond/ukfe/reference/Zdists.md).
  The
  [`Zdists()`](https://github.com/agqhammond/ukfe/reference/Zdists.md)
  function is also very sensitive to slight differences in methodology.
  The one in WINFAP (based on FEH08) uses a theoretical L-kurtosis
  (calculated as a function of L-skewness) for comparison against the
  sampling distribution of L-kurtosis under the null hypothesis. This
  means that the Gumbel distribution can’t be compared. The
  [`Zdists()`](https://github.com/agqhammond/ukfe/reference/Zdists.md)
  function in UKFE uses the weighted average (by sample size) L-kurtosis
  of the pooled AMAX (see the associated details) – so that Gumbel can
  be included. For such reasons, I thought it would be good to have a
  more straightforward comparison, without worrying about hypothesis
  testing (hence them being called `GoFCompare`). The new
  [`GoFCompare()`](https://github.com/agqhammond/ukfe/reference/GoFCompare.md)
  function simply calculates the RMSE of the ordered observed AMAX
  against mean simulated ordered AMAX (500 simulations) and provides the
  RMSE as a percentage of the AMAX mean (the lowest across the
  distributions is the best fit). The
  [`GoFComparePool()`](https://github.com/agqhammond/ukfe/reference/GoFComparePool.md)
  version does the same but with the pooled AMAX (standardised into a
  single large sample).

### Minor changes

- Mann Kendall is now the default trend test in the
  [`TrendTest()`](https://github.com/agqhammond/ukfe/reference/TrendTest.md)
  function.

- Error catching. Added some sensible error messages here and there
  where necessary.

### Bug fix

- [`QMED()`](https://github.com/agqhammond/ukfe/reference/QMED.md)
  function for calculating QMED from catchment descriptors. The donor
  adjustment wasn’t working properly when the CDs were added
  individually (as opposed to using a `CDs` object).

## UKFE 0.3.5

CRAN release: 2024-05-16

### Major changes

- Kappa3 functionality. Better embedded the Kappa3 distribution in
  general. It can now be used with the other functions which take the
  `dist` argument, such as
  [`PoolEst()`](https://github.com/agqhammond/ukfe/reference/PoolEst.md),
  [`OptimPars()`](https://github.com/agqhammond/ukfe/reference/OptimPars.md)
  and
  [`SimData()`](https://github.com/agqhammond/ukfe/reference/SimData.md).
  Also added three functions which mirror those for the other
  distributions:
  [`Kappa3AM()`](https://github.com/agqhammond/ukfe/reference/Kappa3AM.md),
  [`Kappa3Pars()`](https://github.com/agqhammond/ukfe/reference/Kappa3Pars.md),
  [`Kappa3Est()`](https://github.com/agqhammond/ukfe/reference/Kappa3Est.md).
  The
  [`Kappa3GF()`](https://github.com/agqhammond/ukfe/reference/Kappa3GF.md)
  function is still there and has not changed.

- [`Zdists()`](https://github.com/agqhammond/ukfe/reference/Zdists.md)
  function has been updated and now Kappa3 and Gumbel have been added to
  the results.

- Added a function called
  [`POTt()`](https://github.com/agqhammond/ukfe/reference/POTt.md). This
  is a POT extraction function which works on time only (to determine
  the independence). The other
  [`POTextract()`](https://github.com/agqhammond/ukfe/reference/POTextract.md)
  function can also have a time element (as well as return to a low
  threshold) to determine independence, but the new one is significantly
  faster. This is useful for very long time series such as 10,000 years
  of simulation at an hourly sampling rate
  ([`POTextract()`](https://github.com/agqhammond/ukfe/reference/POTextract.md)
  would struggle).

- I have retired the `GoTF` functions but may add them back in improved
  form. I have also temporarily retired the
  [`ERPlot()`](https://github.com/agqhammond/ukfe/reference/ERPlot.md)
  function, but this will be back. Temporary retirement is expedient
  because it has a `GoTF` function within it which requires
  removal/replacement.

### Minor change

- [`AddGauge()`](https://github.com/agqhammond/ukfe/reference/AddGauge.md)
  function. There is now functionality to add a new AMAX with CDs etc to
  the group of sites suitable for pooling so that it can be used in the
  FEH pooling process. Remember that there is also the
  [`LRatioChange()`](https://github.com/agqhammond/ukfe/reference/LRatioChange.md)
  function which allows you to update the stats within the pooling group
  that is already there (in case you have an extra year to add for
  example).

### Bug fix

- [`H2()`](https://github.com/agqhammond/ukfe/reference/H2.md) function.
  This was providing verdicts of heterogeneity more often than it
  should. The error has been fixed.

## UKFE 0.3.4

CRAN release: 2024-03-03

### Major changes

- `Rainfall API` functions. Two new functions: One is `RainEA()` and the
  other is `RainSEPA()`. These can be used to get rainfall from rain
  gauges in Scotland and England using the Environment Agency and
  Scottish Environment Protection Agency APIs.

- [`Zdists()`](https://github.com/agqhammond/ukfe/reference/Zdists.md)
  update. The zdist for assessing the distribution fit was based on the
  FEH99 method. I’ve updated this to the FEH2008 method.

### Bug fix

- Fixed discordancy logic bug in the
  [`Pool()`](https://github.com/agqhammond/ukfe/reference/Pool.md)
  function. There is a column in the pooling group which states if a
  site is over the threshold for discordancy and is therefore considered
  discordant. When the pooling group had more than 15 catchments, this
  didn’t work and all sites were set as FALSE (not discordant) no matter
  what the discordance score was. This has been fixed.

## UKFE 0.3.3

CRAN release: 2024-01-21

### Minor changes

- The [`QMED()`](https://github.com/agqhammond/ukfe/reference/QMED.md)
  function now provides the weightings when two donors are used.

- The
  [`PoolEst()`](https://github.com/agqhammond/ukfe/reference/PoolEst.md)
  function now provides a list with four elements. First is the results,
  second is the pooled LCV and LSKEW, third is the distribution
  parameters for the growth curve, and fourth is the distribution
  parameters for the frequency curve.

- Changed the
  [`ReFH()`](https://github.com/agqhammond/ukfe/reference/ReFH.md)
  function to output a list with two data frames: one for the
  parameters, and one for the results. (As opposed to a print out of
  parameters and a data frame of results.)

- Removed erroneous warning messages from the functions `AggDayHour()`,
  `AMextract()`, and
  [`MonthlyStats()`](https://github.com/agqhammond/ukfe/reference/MonthlyStats.md).

- Added Easting and Northing into `QMEDData` and `NRFAData` which were
  missing for a couple of Northern Ireland catchments.

## UKFE 0.3.2

CRAN release: 2023-11-05

### Major change

- Updated to use the NRFA Peak Flow Dataset version 12.1.

## UKFE 0.3.1

CRAN release: 2023-11-01

### Minor change and bug fix

- [`NonFloodAdjPool()`](https://github.com/agqhammond/ukfe/reference/NonFloodAdjPool.md)
  function. Added a useful message for when there are no sites in the
  pooling group that meet the non-flood criteria (before it was failing
  without a clear reason why). Also added an argument called
  `ReturnStats`. If this is set to `TRUE`, rather than providing an
  adjusted pooling group it returns the number of years, the number of
  non-flood years and the percentage of non-flood years, for each
  station.

## UKFE 0.3.0

CRAN release: 2023-09-23

### Major changes

- Updated to use the NRFA Peak Flow Dataset version 12.

- Added new function called `AggDayHour()`, which allows you to
  aggregate a data frame based on the date time column. For example, you
  might have a time series with a 15-minute sampling rate and you want
  it at a daily or hourly rate (you can choose the number of hours).

## UKFE 0.2.9

CRAN release: 2023-07-09

### Major changes

- The
  [`NonFloodAdj()`](https://github.com/agqhammond/ukfe/reference/NonFloodAdj.md)
  function has replaced the `PermAdj()` function and now provides the
  percentage of non-flood years as well as the adjusted L-CV and
  L-skewness (the result is now a list with two data frames).

- Added new function called
  [`NonFloodAdjPool()`](https://github.com/agqhammond/ukfe/reference/NonFloodAdjPool.md).
  This allows non-flood adjustment to pooling groups. You can update all
  sites, individual sites (one or more user-selected ones), or all sites
  above a given percentage of non-flood years.

- The `DonUrbAdj` argument has been added to the
  [`QMED()`](https://github.com/agqhammond/ukfe/reference/QMED.md)
  function. This allows you to de-urbanise the QMEDcd estimate of the
  donor/s. It’s for the unlikely and usually not recommended case where
  the subject site is rural and the donor is urban.

### Bug fix

- Bug fixes for the `AMextract()` function and the
  [`DDF99Pars()`](https://github.com/agqhammond/ukfe/reference/DDF99Pars.md)
  function.

## UKFE 0.2.8

CRAN release: 2023-03-12

### Major changes

- The `DDF13Import()` function has been replaced with
  [`DDFImport()`](https://github.com/agqhammond/ukfe/reference/DDFImport.md),
  given that the FEH22 rainfall depth duration frequency results have
  been made available for the peak flow sites as part of the NRFA
  update. The function now has the option of importing the 2013 or the
  2022 version of the DDF model.

### Minor change

- Updated the
  [`Pool()`](https://github.com/agqhammond/ukfe/reference/Pool.md) and
  `PoolSmall()` functions so that you can use an `UrbMax` argument to
  increase the URBEXT2000 level at which gauges are excluded from the
  pooling group. The default is 0.03. This is particularly useful for
  users in Wales where the guidance suggests an URBEXT2000 of 0.3. The
  `DeUrb` argument is also available which de-urbanises every site with
  URBEXT2000 above 0.03.

## UKFE 0.2.7

CRAN release: 2023-02-03

### Major change

- Removed the `BivarSim()` function as it needs updating.

### Minor change

- [`POTextract()`](https://github.com/agqhammond/ukfe/reference/POTextract.md)
  function. The user can now set the `div` argument the same as the
  threshold. This essentially reverts the function to a time-based
  separation, albeit a slow one.

## UKFE 0.2.6

CRAN release: 2023-01-23

### Major changes

- Added a function called
  [`MonthlyStats()`](https://github.com/agqhammond/ukfe/reference/MonthlyStats.md)
  which can provide statistics such as mean flow or sum of rainfall for
  each month.

- Added a function called `BivarSim()`. This simulates bivariate
  extremes above a threshold using a Gaussian copula approach. See
  function details but also the multivariate extremes section at the
  bottom of this webpage: <https://www.floodhydrostats.com/howitworks>

- Added a function called
  [`UEF()`](https://github.com/agqhammond/ukfe/reference/UEF.md), which
  is the Urban Expansion Factor.

### Minor changes

- Updated the
  [`POTextract()`](https://github.com/agqhammond/ukfe/reference/POTextract.md)
  function as follows:
  - You can now change the y-axis label
  - You can now add a time element to the declustering
  - The `div` argument is now a percentile as opposed to an absolute
    value
  - Added better error messaging.
- Updated the `AMextract()` function as follows:
  - Calendar year is now an option.
  - By default it now truncates the data to avoid partial years.
  - Added better error messaging.
- Updated the
  [`TrendTest()`](https://github.com/agqhammond/ukfe/reference/TrendTest.md)
  function so that alternative hypotheses can be used. It was a
  two.sided test (still is by default), but now you can test for
  positive or negative trend specifically by using the `alternative`
  argument. See function details.

### Bug fixes

- [`QMED()`](https://github.com/agqhammond/ukfe/reference/QMED.md)
  function. There was an error when a single donor was applied.

- [`POTextract()`](https://github.com/agqhammond/ukfe/reference/POTextract.md)
  function.

## UKFE 0.2.5

CRAN release: 2023-01-22

## UKFE 0.2.4

CRAN release: 2022-10-03

### Major changes

- `ImportAM()` is now
  [`AMImport()`](https://github.com/agqhammond/ukfe/reference/AMImport.md).
  It’s assumed this will make it easier to find.

- [`CDsXML()`](https://github.com/agqhammond/ukfe/reference/CDsXML.md).
  New function to read in catchment descriptors from XML files.

- The `ImportCDs()` function has been removed because it’s based on the
  .cd3 files which are being phased out.

- `PoolSmall()`. New function for making pooling groups for small
  catchments.

- [`DDFImport()`](https://github.com/agqhammond/ukfe/reference/DDFImport.md).
  New function which imports the DDF13 results data frame from an xml
  file (from NRFA peak flows or the FEH Web Service). There is a logical
  `TRUE/FALSE` argument to make the ARF adjustment for the data frame.
  This function takes the output of the `DDF13Import()` function as an
  input. It then allows the user to select a return period and duration
  to get a rainfall estimate.

- [`Kappa3GF()`](https://github.com/agqhammond/ukfe/reference/Kappa3GF.md).
  New function to derive growth factors using the Kappa3 distribution as
  a function of L-CV and L-skewness. This hasn’t been fully embedded in
  other functions such as
  [`PoolEst()`](https://github.com/agqhammond/ukfe/reference/PoolEst.md),
  [`Zdists()`](https://github.com/agqhammond/ukfe/reference/Zdists.md)
  and
  [`EVPlot()`](https://github.com/agqhammond/ukfe/reference/EVPlot.md).
  It can however be used with the outputs of the L-CV and L-skewness
  from the
  [`PoolEst()`](https://github.com/agqhammond/ukfe/reference/PoolEst.md)
  function - or with any estimate of L-CV and L-skewness for that
  matter.

### Minor changes

- `AMextract()` now has an argument called `func`. This allows the user
  to extract other statistics from the hydrological years, such as mean
  flow, or sum of precipitation. Any base function which is applied on a
  numeric vector with no further arguments can be used.

- [`Uncertainty()`](https://github.com/agqhammond/ukfe/reference/Uncertainty.md).
  This function has been updated to make the estimation in ungauged
  catchments more flexible. The user can input the `QMEDfse` rather than
  stating number of donors (it has a default of 1.46).

- [`HydroPlot()`](https://github.com/agqhammond/ukfe/reference/HydroPlot.md).
  This function has been updated so that the user can choose to return
  the data being plotted in a data frame. The function allows the choice
  of the date / date-time range to plot; this can be returned as a
  separate data frame.

### Bug fixes

- [`SCF()`](https://github.com/agqhammond/ukfe/reference/SCF.md) bug
  fix.

## UKFE 0.2.3

CRAN release: 2022-10-01

## UKFE 0.2.2

CRAN release: 2022-01-27

### Major changes

- Added the Gumbel distribution and associated functions.

- Added a function to add lines or points to the EV plot:
  [`EVPlotAdd()`](https://github.com/agqhammond/ukfe/reference/EVPlotAdd.md)

### Minor changes

- Updated the
  [`Uncertainty()`](https://github.com/agqhammond/ukfe/reference/Uncertainty.md)
  function based on Hammond (2021) (“Hammond, A. (2021). Sampling
  uncertainty of UK design flood estimation. Hydrology Research.
  1357-1371. 52 (6)”).

- Included uncertainty as a default for pooled estimates (for the
  [`QuickResults()`](https://github.com/agqhammond/ukfe/reference/QuickResults.md)
  function and the
  [`PoolEst()`](https://github.com/agqhammond/ukfe/reference/PoolEst.md)
  function; for the latter you can choose the QMED fse).

- [`EVPlot()`](https://github.com/agqhammond/ukfe/reference/EVPlot.md):
  Improved the EV plot formatting and it now includes 95% confidence
  intervals.

- Added numerous error messages for better user information when things
  go wrong.

### Bug fixes

- Some bug fixing in the
  [`OptimPars()`](https://github.com/agqhammond/ukfe/reference/OptimPars.md),
  [`DesHydro()`](https://github.com/agqhammond/ukfe/reference/DesHydro.md),
  and
  [`HydroPlot()`](https://github.com/agqhammond/ukfe/reference/HydroPlot.md)
  functions.

## UKFE 0.2.1

## UKFE 0.2.0

CRAN release: 2021-10-14

### Minor changes and bug fixes

- Corrected some grid referencing for the Northern Ireland gauge
  locations.

- Further improved the `ImportAM()` function.

## UKFE 0.1.9

CRAN release: 2021-10-05

## UKFE 0.1.8

CRAN release: 2021-10-03

### Minor changes

- Updated the `ImportAM()` and `ImportCDs()` functions to make them more
  robust.

- Added some better error messaging to the
  [`GetCDs()`](https://github.com/agqhammond/ukfe/reference/GetCDs.md)
  and the
  [`Pool()`](https://github.com/agqhammond/ukfe/reference/Pool.md)
  functions.

## UKFE 0.1.7

CRAN release: 2021-06-11

### Minor changes and bug fixes

- Corrected the
  [`QMEDLink()`](https://github.com/agqhammond/ukfe/reference/QMEDLink.md)
  function.

- Made the `ImportCDs()` function work with both FEH Web Service and
  NRFA Peak Flow Dataset cd3 files without the need for the user to
  specify.

- Added a nice failure message for the
  [`GetCDs()`](https://github.com/agqhammond/ukfe/reference/GetCDs.md)
  function when an unknown gauge ID is entered.

- Added an option to avoid plotting when using the
  [`BFI()`](https://github.com/agqhammond/ukfe/reference/BFI.md)
  function.

## UKFE 0.1.6

CRAN release: 2021-03-20

## UKFE 0.1.4

CRAN release: 2021-02-20

## UKFE 0.1.3

CRAN release: 2021-01-14

## UKFE 0.1.2

CRAN release: 2020-12-05

## UKFE 0.1.1

CRAN release: 2020-11-24

## UKFE 0.1.0

CRAN release: 2020-11-23
