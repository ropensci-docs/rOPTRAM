# Display or Set Package Options

rOPTRAM uses several package options. This function displays the current
defined options, (showing the default options when the package is first
loaded), and allows users to set new values for each option.

## Usage

``` r
optram_options(opt_name = NULL, opt_value = NULL, show_opts = TRUE)
```

## Arguments

- opt_name, :

  string, one of the package options. Default NULL

- opt_value, :

  string, numeric, or boolean, depending on opt_name.

- show_opts, :

  boolean, default TRUE, prints a list of all optram options Default
  NULL

## Note

When no new option name or value is specified, a list of currently
defined options is printed.

`rOPTRAM` defines the following options at startup

|  |  |  |
|----|----|----|
| opt_name | default | other possible values |
| —————- | ————— | ——————- |
| veg_index | "NDVI" | "SAVI", "MSAVI" |
| remote | "scihub" | "openeo" |
| period | "full" | "seasonal" |
| max_cloud | 12 | between 0 and 100 |
| vi_step | 0.005 | usually between 0.01 and 0.001 |
| trapezoid_method | "linear" | "polynomial" or "exponential" |
| SWIR_band | 11 | 12 |
| max_tbl_size | 1e+6 | depends on computer resources, default 1e6, minimum: 1e4 |
| rm.low.vi | FALSE | TRUE |
| rm.hi.str | FALSE | TRUE |
| plot_colors | "no" | "no" = uniform green color for all points |
|  |  | "features" = points colored by aoi features |
|  |  | "density" = points colored by point density |
|  |  | "contours" = plots density contour lines |
|  |  | "months" = points colored by month of image date |
| feature_col | "ID" | string, name of *numeric* column |
|  |  | that contains feature ID's for coloring plot |
| edge_points | TRUE | FALSE, whether to add |
|  |  | the trapezoid edge points to the plot |
| only_vi_str | FALSE | TRUE (avoids downloading all Sentinel bands) |
| tileid | NA | a string of 5 characters, |
|  |  | download only the requested tileid |
| scm_mask | TRUE | FALSE, whether to mask out: |
|  |  | cloud shadows, clouds, water, snow, using the Copernicus SCM product. |
| overwrite | FALSE | Set to TRUE to re-download previously acquired images. |
| save_img_list | FALSE | Set to TRUE to save list of available images to RDS file. |
| resolution | 10 | Choose resolution of downloaded Sentinel images, 10m, 20m or 60m |
| area_cover | 99.0 | Use only images that cover at least area_cover % of AOI |
| porosity | 0.4 | Soil porosity value applied to OPTRAM output to get VWC |

## Examples

``` r
opts <- options()
optram_options()      # prints out list of current options
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
#> [1] "trapezoid_method = linear"
#> [1] "veg_index = NDVI"
#> [1] "vi_step = 0.005"
#> NULL
optram_options("SWIR_band", 12)
#> 
#> Option for: SWIR_band set to: 12
#> [1] "SWIR_band = 12"
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
#> [1] "trapezoid_method = linear"
#> [1] "veg_index = NDVI"
#> [1] "vi_step = 0.005"
optram_options("veg_index", "SAVI")
#> 
#> Option for: veg_index set to: SAVI
#> [1] "SWIR_band = 12"
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
#> [1] "trapezoid_method = linear"
#> [1] "veg_index = SAVI"
#> [1] "vi_step = 0.005"
optram_options("trapezoid_list", "exp")  # fails
#> 
#> Unknown option name: trapezoid_list
options(opts)
```
