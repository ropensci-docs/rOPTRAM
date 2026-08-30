# Utility Function to Acquire Sentinel-2 Imagery Using `CDSE` Package

This function uses the `CDSE` package to send a request to Copernicus
Dataspace, and prepare the products. Called by
[`optram_acquire_s2`](https://docs.ropensci.org/rOPTRAM/reference/optram_acquire_s2.md)

## Usage

``` r
acquire_scihub(
  aoi,
  from_date,
  to_date,
  output_dir = tempdir(),
  save_creds = TRUE,
  clientid = NULL,
  secret = NULL
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

- save_creds, :

  logical, whether to save CDSE credentials. Default TRUE.

- clientid, :

  string, user's OAuth client id. Required if `save_creds` is TRUE.

- secret, :

  string, user's OAuth secret. Required if `save_creds` is TRUE.

## Value

list of STR files

## Note

\#' This function utilizes the `CDSE` package. Make sure to install the
`CDSE` and `jsonlite` packages. Create OAuth account and token: Creating
an Account:

1.  Navigate to the <https://dataspace.copernicus.eu/>.

2.  Click the "Register" button to access the account creation page.

3.  If already registered, enter your username and password, and click
    "Login."

4.  Once logged in, go to the User dashboard and click "User Settings"
    to access the Settings page.

Creating OAuth Client:

1.  On the Settings page, click the green "Create New" button located on
    the right.

2.  Enter a suitable "Client Name" and click the green "Create Client"
    button.

3.  A Client secret is generated.

The user must save her secret and clientid somewhere. These credentials
will be saved automatically to a standard filesystem location if the
user calls
[`store_cdse_credentials()`](https://docs.ropensci.org/rOPTRAM/reference/store_cdse_credentials.md)
with the `clientid` and `secret` parameters. If the user chooses not to
save credentials to the standard filesystem location, then she will need
to add both clientid and secret to each `acquire_scihub()` function
call.

Using Credentials with `aquire_scihub`:

- If the credentials were stored using
  [`store_cdse_credentials()`](https://docs.ropensci.org/rOPTRAM/reference/store_cdse_credentials.md),
  the credentials are retrieved automatically.

- Otherwise, you can utilize the generated `clientid` and `secret` from
  <https://dataspace.copernicus.eu/> within the `aquire_scihub()`
  function.

- If you want to store your credentials on your computer, ensure that
  when running `aquire_scihub()`, the `save_creds` parameter is set to
  'TRUE'.

- During the first run of `aquire_scihub()`, manually input your
  `clientid` and `secret` in the function signature. Subsequent runs
  will use the stored credentials.

**Subject Area Constraint:** The downloadable images are restricted to a
maximum size of 2500 pixels on each side. This limitation is established
due to the final resolution set to 10 meters using JavaScript.
Consequently, the subject area available for download is limited to 25
kilometers in both directions. Please be aware of this restriction when
selecting your desired area for download. **Area of Interest (AOI)
Specification:** When defining your Area of Interest (AOI), please
ensure that it is represented as a polygonal layer with only one
feature. This feature can either be a single POLYGON or a MULTIPOLYGON,
which may consist of non-contiguous areas, but only one feature is
permissible.

## Examples
