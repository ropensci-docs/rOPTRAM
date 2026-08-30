# Calculate Soil Moisture Grid

Prepare soil moisture grid from STR and VI images for a single date
using the derived slope and intercept coefficients

## Usage

``` r
optram_calculate_soil_moisture(
  img_date,
  VI_dir,
  STR_dir,
  data_dir,
  output_dir = tempdir()
)
```

## Arguments

- img_date, :

  string, image date of single Sentinel 2 acquisition formatted as
  "YYYY-MM-DD"

- VI_dir, :

  string, full path to directory holding the VI rasters

- STR_dir, :

  string, full path to directory holding the STR rasters

- data_dir, :

  string, the directory where coefficients file was saved (the
  `output_dir` parameter in
  [`optram_wetdry_coefficients`](https://docs.ropensci.org/rOPTRAM/reference/optram_wetdry_coefficients.md)
  function)

- output_dir, :

  string, full path to output directory for saving soil moisture raster

## Value

SpatRaster, raster of soil moisture, file(s) saved in output_dir

## Note

This function is used after preparing the OPTRAM model coefficients
with:
[`optram_wetdry_coefficients`](https://docs.ropensci.org/rOPTRAM/reference/optram_wetdry_coefficients.md).
Typically a new image date, (possibly an image that was not used for
preparing the model), will be referenced in the `img_date` parameter.
The resulting soil moisture raster, representing Volumetric Water
Content, is saved to `output_dir`.

Three trapezoid models are offered through the trapezoid_method option:
either "linear", "exponential", or "polynomial". (set using
[`optram_options`](https://docs.ropensci.org/rOPTRAM/reference/optram_options.md))
The `data_dir` parameter is a directory name. The coefficients CSV file
that matches `trapezoid_method` should be in that directory

For further details see: Ambrosone, Mariapaola, et al. 2020. “Retrieving
Soil Moisture in Rainfed and Irrigated Fields Using Sentinel-2
Observations and a Modified OPTRAM Approach.” International Journal of
Applied Earth Observation and Geoinformation 89 (July): 102113.
[doi:10.1016/j.jag.2020.102113](https://doi.org/10.1016/j.jag.2020.102113)
.

The data_dir directory must contain the coefficients CSV file i.e. for
"linear" method the file was saved as 'coefficients_lin.csv' for
"exponential" it was saved as 'coefficients_exp.csv' for "polynomial" it
was saved as 'coefficients_pol.csv'

## Examples

``` r
img_date <- "2023-03-11"
VI_dir <- system.file("extdata", "NDVI", package = "rOPTRAM")
STR_dir <- system.file("extdata", "STR", package = "rOPTRAM")
data_dir <- system.file("extdata")
SM <- optram_calculate_soil_moisture(img_date,
      VI_dir, STR_dir, data_dir)
#> No data directory:
```
