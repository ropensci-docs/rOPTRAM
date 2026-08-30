# Handle Satellite Imagery in Original Landsat Format

Use this function to prepare vegetation index and SWIR Transformed
Reflectance (STR) rasters when you have already downloaded Landsat image
files in advance. This function assumes that atmospheric correction has
been applied.

## Usage

``` r
optram_landsat(
  landsat_dir,
  aoi,
  LC_output_dir = tempdir(),
  data_output_dir = tempdir()
)
```

## Arguments

- landsat_dir, :

  string, full path to containing folder of downloaded (unzipped)
  Landsat data in original landsat format, after atmospheric correction
  (L2A)

- aoi, :

  sf object, POLYGON or MULTIPOLYGON of AOI boundary of area of interest

- LC_output_dir, :

  string, directory to save the derived products, defaults to tempdir()

- data_output_dir, :

  string, path to save coeffs_file and STR-VI data.frame, default is
  tempdir()

## Value

rmse_df, data.frame, RMSE values of fitted trapezoid edges

## Note

Unlike the
[`optram_acquire_s2`](https://docs.ropensci.org/rOPTRAM/reference/optram_acquire_s2.md)
function, there is no implementation for automatic download of Landsat
images. This function requires a directory, set in the `landsat_dir`
parameter, which contains the set of Landsat tiles downloaded manually
by the user, in advance. This directory should contain folders of
Landsat images, where each folder consists of the individual Landsat
bands as Geotiff files, as well as the metadata files as downloaded
from, i.e. the USGS EarthExplorer <https://earthexplorer.usgs.gov/>
website.

## Examples

``` r
if (FALSE) { # \dontrun{
aoi <- sf::st_read(system.file("extdata",
                              "lachish.gpkg", package = "rOPTRAM"))
# landsat_dir is a directory containing the original downloaded Landsat images.
landsat_dir <- "...enter full path here..."
optram_landsat(landsat_dir,  aoi,
               veg_index = 'SAVI',
               LC_output_dir = tempdir(), data_output_dir = tempdir())
} # }
```
