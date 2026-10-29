# Handle Sentinel Imagery in Original Copernicus SAFE Format

Use this function to prepares vegetation index and SWIR Transformed
Reflectance (STR) rasters when you have already downloaded Sentinel 2
image files in advance. Unzip the downloaded Sentinel 2 files and do not
change the folder structure. This function assumes that atmospheric
correction has been applied. i.e. by downloading Level L2A product or
using the SNAP L2A_Process,

## Usage

``` r
optram_safe(
  safe_dir,
  aoi,
  S2_output_dir = tempdir(),
  overwrite = TRUE,
  data_output_dir = tempdir()
)
```

## Arguments

- safe_dir, :

  string, full path to containing folder of downloaded (unzipped)
  Sentinel 2 data in original SAFE format, after atmospheric correction
  (L2A)

- aoi, :

  sf object, a POLYGON or MULTIPOLYGON of the AOI boundary

- S2_output_dir, :

  string, directory to save the derived products, defaults to tempdir()

- overwrite, :

  boolean, overwrite derived products that already were created,
  defaults to TRUE

- data_output_dir, :

  string, path to save coeffs_file and STR-VI data.frame, default is
  tempdir()

## Value

rmse_df, data.frame, RMSE values of fitted trapezoid lines

## Note

Use the `max_tbl_size` parameter to limit the total number of rows in
the VI-STR data.frame. When the area of interest is large, or the time
range of datasets is long, the total size of the data.frame can grow
beyond the capacity of computation resources. This parameter limits the
size of the table by sampling a number of data points from each time
slot. The sample size is determined based on `max_tbl_size` and the
total number of time slots in the full time range.

Two SWIR bands are available in Sentinel-2: 1610 nanometer (nm) and 2190
nm. Set which band to use with `optram_options`.

## Examples

``` r
if (FALSE) { # \dontrun{
aoi <- sf::st_read(system.file("extdata",
                  "lachish.gpkg", package = "rOPTRAM"))
safe_dir  <- "...enter directory containing downloaded SAFE folders..."
rmse <- optram_safe(safe_dir, aoi_file)
} # }
```
