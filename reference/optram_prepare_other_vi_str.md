# Handle Third Party Imagery With Red, NIR and SWIR Bands

This function prepares vegetation index and STR rasters from other
(non-Sentinel) image files downloaded in advance.

## Usage

``` r
optram_prepare_other_vi_str(
  img_dir,
  aoi,
  viname = "NDVI",
  output_dir = tempdir()
)
```

## Arguments

- img_dir, :

  string, full path directory of downloaded images (assumes Geotiff)

- aoi, :

  string, full path to polygon spatial file of area of interest

- viname, :

  string, which VI to prepare, 'NDVI', 'SAVI', etc.

- output_dir, :

  string, where to save Geotiff, default is tempdir()

## Value

output_files, list, full paths to saved Geotiff files (not exported yet)
