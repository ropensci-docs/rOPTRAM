# Utility Function to Prepare Exponential Fitted Edges of Trapezoid

Called by
[`optram_wetdry_coefficients`](https://docs.ropensci.org/rOPTRAM/reference/optram_wetdry_coefficients.md)
to prepare exponential curve along trapezoid edges. Calculates the
intercept and slope of both wet and dry edges and updates the edges
data.frame with these exp fitted values. Not exported.

## Usage

``` r
exponential_coefficients(df, output_dir)
```

## Arguments

- df, :

  data.frame, values of VI and STR along edges of trapezoid

- output_dir, :

  string, path to save coefficients CSV file

## Value

df, data.frame, the trapezoid line edge points with fitted wet/dry
values added

## Note

Three CSV files are saved:

- the regressions coefficients,

- the trapezoid edge points

- RMSE of the fitted curve

## Examples

``` r
if (FALSE) { # \dontrun{
  df <- read.csv(system.file("extdata", "trapezoid_edges.csv",
                package = "rOPTRAM"))
  output_dir <- tempdir()
  coeffs <- rOPTRAM::exponential_coefficients(df, output_dir)
  coeffs
} # }
```
