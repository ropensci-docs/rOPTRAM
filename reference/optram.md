# Prepare Sentinel Imagery for Soil Moisture Prediction Using OPTRAM.

The main wrapper function to download, and preprocess Sentinel 2 imagery
then prepare the OPTRAM trapezoid to derive slope and intercept for wet
and dry trapezoid lines. See: Sadeghi, M., Babaeian, E., Tuller, M.,
Jones, S.B., 2017. The optical trapezoid model: A novel approach to
remote sensing of soil moisture applied to Sentinel-2 and Landsat-8
observations. Remote Sensing of Environment 198, 52–68,
[doi:10.1016/j.rse.2017.05.041](https://doi.org/10.1016/j.rse.2017.05.041)

## Usage

``` r
optram(
  aoi,
  from_date,
  to_date,
  S2_output_dir = tempdir(),
  data_output_dir = tempdir()
)
```

## Arguments

- aoi, :

  sf object, a POLYGON or MULTIPOLYGON, boundary of area of interest

- from_date, :

  string, the start of the date range, Formatted as "YYYY-MM-DD"

- to_date, :

  the end of the date range.

- S2_output_dir, :

  string, directory to save downloaded S2 and the derived products,
  defaults to tempdir()

- data_output_dir, :

  string, path to save coeffs_file and STR-VI data.frame, default is
  tempdir()

## Value

rmse_df, data.frame, RMSE values of fitted trapezoid lines the
coefficients are also saved to a csv file in `data_output_dir`.

## Note

- Sentinel downloaded products are saved to S2_output_dir. Data files
  (Trapezoid coefficients and STR-VI data) to data_output_dir

- Products can be downloaded covering two "period" options: either
  "full" - all available images from `from_date` to `to_date` or
  "seasonal" - available images for all years but only for the months
  between day/month of `from_date` to the day/month of `to_date`. Use
  [`optram_options`](https://docs.ropensci.org/rOPTRAM/reference/optram_options.md)
  to set this option.

- Three trapezoid fitting methods are implemented: "linear",
  "exponential" and "polynomial". See the
  [`optram_options`](https://docs.ropensci.org/rOPTRAM/reference/optram_options.md)
  function for details

- Two SWIR wavelength bands are available in Sentinel-2: 1610 nanometer
  (nm) and 2190 nm. The option `SWIR_bands` can be set in
  [`optram_options`](https://docs.ropensci.org/rOPTRAM/reference/optram_options.md)
  to choose which band is used in this model.

- Several vegetation indices are implemented: "NDVI", "SAVI", etc. The
  [`optram_options`](https://docs.ropensci.org/rOPTRAM/reference/optram_options.md)function
  also sets this option.

## Examples

``` r
if (FALSE) { # \dontrun{
from_date <- "2018-12-01"
to_date <- "2020-04-30"
aoi <- sf::st_read(system.file("extdata",
                              "lachish.gpkg", package = "rOPTRAM"))
rmse <- optram(aoi,
               from_date, to_date)
} # }
```
