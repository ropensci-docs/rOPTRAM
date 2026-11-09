# Utility Function to Acquire Sentinel-2 Imagery using openEO

This non-exported function uses the `openeo` package to send a request
to Copernicus DataSpace, and prepare the products. Called by
[`optram_acquire_s2`](https://docs.ropensci.org/rOPTRAM/reference/optram_acquire_s2.md)

## Usage

``` r
acquire_openeo(
  aoi,
  from_date,
  to_date,
  output_dir = tempdir(),
  scale_factor = 10000
)
```

## Arguments

- aoi, :

  sf object, POLYGON or MULTIPOLYGON of area of interest

- from_date, :

  string, represents start of date range, formatted as "YYYY-MM-DD"

- to_date, :

  string, end of date range, formatted as "YYYY-MM-DD"

- output_dir, :

  string, path to save downloaded, and processed imagery

- scale_factor, :

  integer, scaling factor for EO data source default 10000 , to scale
  Sentinel-2 15 bit DN to range (0, 1)

## Value

list of BOA files

## Note

This function utilizes the `openeo` package. Instructions for the login
process: First of all, to authenticate your account on the backend of
the Copernicus Data Space Ecosystem, it is necessary for you to complete
the registration process. Follow these instructions for registration:
<https://documentation.dataspace.copernicus.eu/Registration.html> After
you have registered and installed the `openeo` package, you can run the
`acquire_openeo` function. During the process of connecting to the
server and logging in, you need to follow these steps:

1.  When the message "Press to proceed:" appears in the console, press
    enter.

2.  When prompted with 'Copy CTGB-UGFU and paste when requested by the
    browser' in the console, it may appear but can be ignored, as it is
    related to an older version of the openeo package.

3.  Calling this method opens your system web browser, with which you
    can authenticate yourself on the back-end authentication system.

4.  After that, the website will give you instructions to go back to the
    R client, where your connection has logged your account in. This
    means that every call that comes after that via the connection
    variable is executed by your user account.

5.  You will be redirected to
    <https://identity.dataspace.copernicus.eu/>. Ensure you have an
    account and are logged in. You will be required to grant access -
    press "yes".

## Examples
