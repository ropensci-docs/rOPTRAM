# Retrieve CDSE Client Credentials from File

Retrieve CDSE clientid and secret from file The file location is system
specific. It would have been setup in advance using the
[`store_cdse_credentials`](https://docs.ropensci.org/rOPTRAM/reference/store_cdse_credentials.md)
function

## Usage

``` r
retrieve_cdse_credentials()
```

## Value

A data frame containing the retrieved CDSE clientid and secret, or NULL
if credentials are not available.
