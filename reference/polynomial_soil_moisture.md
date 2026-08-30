# Calculate Soil Moisture, Polynomial Fitted Curve

Prepare soil moisture grid from STR and VI images for a single date,
based on polynomial function fitted to trapezoid edges.

## Usage

``` r
polynomial_soil_moisture(coeffs, VI, STR)
```

## Arguments

- coeffs, :

  list, 6 trapezoid coefficients

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
moisture raster is saved to `output_dir` This function implements an
polynomial fitted curve, following: Ma, Chunfeng, Kasper Johansen, and
Matthew F. McCabe. 2022. “Combining Sentinel-2 Data with an
Optical-Trapezoid Approach to Infer within-Field Soil Moisture
Variability and Monitor Agricultural Production Stages.” Agricultural
Water Management 274 (December): 107942.
[doi:10.1016/j.agwat.2022.107942](https://doi.org/10.1016/j.agwat.2022.107942)
.

## Examples

``` r
img_date <- "2023-03-11"
VI_dir <- system.file("extdata", "NDVI", package = "rOPTRAM")
STR_dir <- system.file("extdata", "STR", package = "rOPTRAM")
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
SM <- optram_calculate_soil_moisture(img_date,
                          VI_dir, STR_dir,
                          data_dir = tempdir())
#> Multiple tiles created: 
#> /tmp/RtmpNj7FVj/soil_moisture_2023-03-11_NA.tif/tmp/RtmpNj7FVj/soil_moisture_2023-03-11_NA.tif
```
