# Utility Function to Prepare Polynomial Fitted Edges of Trapezoid

Called by
[`optram_wetdry_coefficients`](https://docs.ropensci.org/rOPTRAM/reference/optram_wetdry_coefficients.md)
to prepare second order polynomial curve along trapezoid edges
Calculates six coefficients: intercept (alpha) of both wet and dry edges
and first and second order coefficients (beta), as in \\STR = alpha +
beta_1 \* VI + beta_2 \* VI^2\\ and updates the edges data.frame with
these polynomila values fitted values

## Usage

``` r
polynomial_coefficients(df, output_dir)
```

## Arguments

- df, :

  data.frame, values of VI and STR along edges of trapezoid

- output_dir, :

  string, path to save coefficients CSV file

## Value

df, data.frame, the trapezoid line edge points with fitted values added
for both wet and dry edges

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
  coeffs <- rOPTRAM::polynomial_coefficients(df, output_dir)
  coeffs
 } # }
```
