# Derive Coefficients of Slope and Intercept

Derive slope and intercept coefficients for both wet and dry trapezoid
lines. Write coefficients to a CSV file (as input to
[`optram_calculate_soil_moisture`](https://docs.ropensci.org/rOPTRAM/reference/optram_calculate_soil_moisture.md)
function)

## Usage

``` r
optram_wetdry_coefficients(full_df, output_dir = tempdir())
```

## Arguments

- full_df, :

  data.frame of STR and NDVI values

- output_dir, :

  string, directory to save coefficients CSV file

## Value

rmse_df, data.frame, RMSE values of fitted trapezoid edges

## Note

The vegetation index column is named "VI" though it can represent
several vegetation indices, such as SAVI, or MSAVI.

The `trapezoid method` option (see
[`optram_options`](https://docs.ropensci.org/rOPTRAM/reference/optram_options.md))
allows to choose one of three models for creating the edge coefficients
of the trapezoid.

- "linear" prepares a simple OLS regression line along the wet and dry
  edges of the trapezoid. Four coefficients are returned: intercept and
  slope for both edges.

- "exponential" creates an exponential curve fitted to the intercept and
  slope, following: Ambrosone, Mariapaola, Alessandro Matese, et
  al. 2020. “Retrieving Soil Moisture in Rainfed and Irrigated Fields
  Using Sentinel-2 Observations and a Modified OPTRAM Approach.”
  International Journal of Applied Earth Observation and Geoinformation
  [doi:10.1016/j.jag.2020.102113](https://doi.org/10.1016/j.jag.2020.102113)
  .

- "polynomial" fits a second order polynomial curve to the wet and dry
  edges of the trapezoid, following: Ma, Chunfeng, Kasper Johansen, and
  Matthew F. McCabe. 2022. “Combining Sentinel-2 Data with an
  Optical-Trapezoid Approach to Infer within-Field Soil Moisture
  Variability and Monitor Agricultural Production Stages.” Agricultural
  Water Management 274 (December): 107942.
  [doi:10.1016/j.agwat.2022.107942](https://doi.org/10.1016/j.agwat.2022.107942)
  This curve fitting function returns six coefficients: alpha, beta_1,
  and beta_2 for both wet and dry edges

## Examples

``` r
full_df <- readRDS(system.file("extdata", "VI_STR_data.rds",
  package = "rOPTRAM"))
rmse_df <- optram_wetdry_coefficients(full_df, tempdir())
#> VI series length:105
print(rmse_df)
#>    RMSE.wet  RMSE.dry
#> 1 0.1642536 0.1018425
optram_options("trapezoid_method", "polynomial")
#> 
#> Option for: trapezoid_method set to: polynomial
#> [1] "SWIR_band = 11"
#> [1] "area_cover = 99"
#> [1] "edge_points = TRUE"
#> [1] "feature_col = ID"
#> [1] "max_cloud = 12"
#> [1] "max_tbl_size = 1e+06"
#> [1] "only_vi_str = FALSE"
#> [1] "overwrite = FALSE"
#> [1] "period = full"
#> [1] "plot_colors = no"
#> [1] "porosity = 0.4"
#> [1] "remote = scihub"
#> [1] "resolution = 10"
#> [1] "rm.hi.str = FALSE"
#> [1] "rm.low.vi = FALSE"
#> [1] "save_img_list = FALSE"
#> [1] "scm_mask = TRUE"
#> [1] "tileid = NA"
#> [1] "trapezoid_method = polynomial"
#> [1] "veg_index = NDVI"
#> [1] "vi_step = 0.005"
rmse_df <- optram_wetdry_coefficients(full_df, tempdir())
#> VI series length:105
print(rmse_df)
#>    RMSE.wet   RMSE.dry
#> 1 0.1628496 0.07835765
```
