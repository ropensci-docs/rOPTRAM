# Prepare Dataframe with Pairs of NDVI and STR Values

Collect all pixel values of both vegetation index, and Swir Transformed
Reflectance, for a time series of images. Prepare data.frame of all
pairs of values (as input for the
[`optram_wetdry_coefficients`](https://docs.ropensci.org/rOPTRAM/reference/optram_wetdry_coefficients.md)
function)

## Usage

``` r
optram_ndvi_str(STR_list, VI_list, output_dir = tempdir(), aoi = NULL)
```

## Arguments

- STR_list, :

  list of paths to STR raster files

- VI_list, :

  list of paths to NDVI raster files

- output_dir, :

  string, path to save data.frames (in RDS format)

- aoi, :

  sf POLYGON or MULTIPOLYGON, must have a numeric column named "ID" for
  coloring trapezoid points by features Default NULL, (no coloring)

## Value

full_df, data.frame with 7 columns: X,Y,Date,Month,NDVI,STR,Density and
optionally a 7th column with feature ID values from the AOI polygon. The
columns Month, Density, Feature_ID can be used in
[`plot_vi_str_cloud()`](https://docs.ropensci.org/rOPTRAM/reference/plot_vi_str_cloud.md)
function to color the points in the scatter plot in various ways.

## Note

Use the option `max_tbl_size` (see
[`optram_options`](https://docs.ropensci.org/rOPTRAM/reference/optram_options.md))
to limit size of the NDVI-STR data.frame. With a large area of interest,
and long time frame, the number of data points can overrun the
computation resources. This parameter sets a total size of data.frame
from the `max_tbl_size` parameter, together with the number of image
time slots in the time range.

All rows in the data.frame where either NDVI or STR are NA are removed.

In some cases (i.e. water surfaces) NDVI can have values below zero.
These pixels can be removed from the trapezoid by setting `rm.low.vi`
option to TRUE.

The vegetation index column is named "NDVI" even though it can represent
other vegetation indices, such as SAVI, or MSAVI.

## Examples

``` r
VI_list <- list.files(system.file("extdata", "NDVI", package = "rOPTRAM"),
        pattern = ".tif$", full.names = TRUE)
STR_list <- list.files(system.file("extdata", "STR", package = "rOPTRAM"),
        pattern = ".tif$", full.names = TRUE)
full_df <- optram_ndvi_str(STR_list, VI_list)
#> Saved: 96360 rows of VI-STR data to: /tmp/RtmpNj7FVj/VI_STR_data.rds
# Show structure of output data.frame
str(full_df)
#> 'data.frame':    96360 obs. of  7 variables:
#>  $ x           : num  34.9 34.9 34.9 34.9 34.9 ...
#>  $ y           : num  31.6 31.6 31.6 31.6 31.6 ...
#>  $ VI          : num  0.432 0.418 0.428 0.528 0.538 ...
#>  $ STR         : num  1.72 1.95 1.96 2.11 2.13 ...
#>  $ TimestampUTC: POSIXct, format: NA NA ...
#>  $ Tile        : chr  NA NA NA NA ...
#>  $ Month       : chr  NA NA NA NA ...
```
