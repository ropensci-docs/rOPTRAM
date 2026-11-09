# Calculate Soil Moisture Grid, Exponential Trapezoid

Prepare soil moisture grid from STR and VI images for a single date,
based on exponential function to derive trapezoid edges, using the
derived slope and intercept coefficients

## Usage

``` r
exponential_soil_moisture(coeffs, VI, STR)
```

## Arguments

- coeffs, :

  list, 4 trapezoid coefficients

- VI, :

  terra rast, the vegetation index raster

- STR, :

  terra rast, the STR raster

## Value

rast, soil moisture grid

## Note

This function is used after preparing the OPTRAM model coefficients
with:
[`optram_wetdry_coefficients`](https://docs.ropensci.org/rOPTRAM/reference/optram_wetdry_coefficients.md).
Typically a new image date, (that was not used for preparing the model),
will be referenced in the `img_date` parameter. The resulting soil
moisture raster is saved to `output_dir`. This function implements an
exponential trapezoid, following: Ambrosone, Mariapaola, et al. 2020.
“Retrieving Soil Moisture in Rainfed and Irrigated Fields Using
Sentinel-2 Observations and a Modified OPTRAM Approach.” International
Journal of Applied Earth Observation and Geoinformation 89 (July):
102113.
[doi:10.1016/j.jag.2020.102113](https://doi.org/10.1016/j.jag.2020.102113)

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
