# Calculate Soil Moisture Grid, Linear Trapezoid

Prepare soil moisture grid from STR and VI images for a single date,
using linear trapezoid method, and using the derived slope and intercept
coefficients

## Usage

``` r
linear_soil_moisture(coeffs, VI, STR)
```

## Arguments

- coeffs, :

  list, 4 trapezoid coefficients

- VI, :

  SpatRaster, the vegetation index raster

- STR, :

  SpatRaster, the STR raster

## Value

rast, soil moisture grid

## Note

This function is used after preparing the OPTRAM model coefficients
with:
[`optram_wetdry_coefficients`](https://docs.ropensci.org/rOPTRAM/reference/optram_wetdry_coefficients.md).
Typically a new image date, (that was not used for preparing the model),
will be referenced in the `img_date` parameter. The resulting soil
moisture raster is saved to `output_dir`.

## Examples

``` r
img_date <- "2023-03-11"
VI_dir <- system.file("extdata", "NDVI", package = "rOPTRAM")
STR_dir <- system.file("extdata", "STR", package = "rOPTRAM")
SM <- optram_calculate_soil_moisture(img_date,
            VI_dir, STR_dir,
            data_dir = tempdir())
#> No coefficients file, Exiting...
```
