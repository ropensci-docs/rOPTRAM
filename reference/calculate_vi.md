# Calculate Vegetation Index from Bottom of Atmosphere Image Bands

Use this function to prepare vegetation index from SAFE imagery when you
have already downloaded Sentinel 2 image files in advance

## Usage

``` r
calculate_vi(
  img_stk,
  redband = 4,
  greenband = 3,
  blueband = 2,
  nirband = 5,
  scale_factor = 2^15
)
```

## Arguments

- img_stk, :

  terra SpatRaster, multiband stack of images, already clipped to aoi

- redband, :

  integer, number of red band

- greenband, :

  integer, number of green band

- blueband, :

  integer, number of blue band

- nirband, :

  integer, number of NIR band

- scale_factor, :

  numeric, scales Sentinel-2 15 bit values down to range (0,255) as
  expected for vegetation indices default 32768 (2^15)

## Value

vi_rast, SpatRaster of vegetation index

## Note

The scale_factor parameter reduces numeric range "digital number", (DN)
of Sentinel-2 images from 15 bit integer to 8 bit. Vegetation indices
such as SAVI expect values in the range (0, 255). This scale_factor
produces values in that range. When using Landsat 8 images (DN already
in range of (0, 255)) then set scale_factor to 255.

## Examples

``` r
img_stk <- terra::rast(system.file("extdata", "BOA",
         "BOA_2023-01-20_T36RXV.tif", package = "rOPTRAM"))
vi <- calculate_vi(img_stk)
```
