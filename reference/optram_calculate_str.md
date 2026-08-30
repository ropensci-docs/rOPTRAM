# Create SWIR Transformed Reflectance

Create SWIR Transformed Reflectance

## Usage

``` r
optram_calculate_str(BOA_dir, STR_dir = NULL)
```

## Arguments

- BOA_dir, :

  string, the path to the Bottom of Atmosphere bands

- STR_dir, :

  string, output directory for STR rasters, Default is NULL, in which
  case, the STR_dir will be created alongside BOA_dir

## Value

list of string, the path to transformed raster

## Note

This function follows: Sadeghi, M., Babaeian, E., Tuller, M., Jones,
S.B., 2017. The optical trapezoid model: A novel approach to remote
sensing of soil moisture applied to Sentinel-2 and Landsat-8
observations. Remote Sensing of Environment 198, 52–68.
[doi:10.1016/j.rse.2017.05.041](https://doi.org/10.1016/j.rse.2017.05.041)

SWIR Transformed Reflectance is calculated as STR = (1-SWIR)^2 / 2\*SWIR
SWIR is band 12 (2190 nm) or 11 (1610 nm)

## Examples

``` r
BOA_dir <- system.file("extdata", "BOA", package = "rOPTRAM")
STR_dir = tempdir()
STR <- optram_calculate_str(BOA_dir, STR_dir)
#> Prepared: 20 STR files
```
