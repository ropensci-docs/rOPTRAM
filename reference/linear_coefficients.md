# Utility Function to Prepare Linear Regression Edges of Trapezoid

Called by
[`optram_wetdry_coefficients`](https://docs.ropensci.org/rOPTRAM/reference/optram_wetdry_coefficients.md)
to prepare linear regression line along trapezoid edges Calculates the
intercept and slope of both wet and dry edges Not exported

## Usage

``` r
linear_coefficients(df, output_dir)
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
edges_file <- system.file("extdata/trapezoid_edges.csv",
                           package = "rOPTRAM")
df <- read.csv(edges_file)
output_dir <- tempdir()
coeffs <- linear_coefficients(df, output_dir)
coeffs
} # }
```
