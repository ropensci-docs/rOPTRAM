# Crop List of Landsat Bands to AOI

Utility function to prepare BOA bands cropped to Area of Interest.

## Usage

``` r
crop_landsat_list(landsat_dir)
```

## Arguments

- landsat_dir, :

  string, directory containing the original downloaded Landsat imagery
  folders.

## Value

cropped_list, list, paths to derived BOA stacks, cropped to study area

## Examples

``` r
if (FALSE) { # \dontrun{
cropped_landsat_list <- crop_landsat_list(landsat_dir)
} # }
```
