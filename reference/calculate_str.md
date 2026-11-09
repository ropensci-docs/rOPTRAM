# Calculate STR from SWIR Bottom of Atmosphere Band

Use this function to prepare STR from SAFE imagery when you have already
downloaded Sentinel 2 image files in advance

## Usage

``` r
calculate_str(img_stk, scale_factor = 10000)
```

## Arguments

- img_stk, :

  terra SpatRaster, multiband stack of images, already clipped to aoi

- scale_factor, :

  integer, scaling factor for EO data source default 10000, to scale
  Sentinel-2 15 bit DN to range (0, 1)

## Value

STR, SpatRaster of STR band

## Note

For Landsat images, scale_factor should be 1, since Landsat metadata
contains gain and offset for scaling image bands.

## Examples

``` r
img_stk <- terra::rast(system.file("extdata", "BOA",
         "BOA_2022-12-11_T36RXV.tif", package = "rOPTRAM"))
STR_dir = tempdir()
str <- calculate_str(img_stk)
```
