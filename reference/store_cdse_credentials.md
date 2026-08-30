# Store CDSE Client Credentials

Store CDSE clientid and secret into a file The file location is system
specific. Users who chose to save CDSE credentials can use this function
(and then the
[`retrieve_cdse_credentials`](https://docs.ropensci.org/rOPTRAM/reference/retrieve_cdse_credentials.md)
afterwards) The clientid and secret are obtained from:

## Usage

``` r
store_cdse_credentials(clientid = NULL, secret = NULL)
```

## Arguments

- clientid, :

  string, user's OAuth client id

- secret, :

  string, user's OAuth secret

## Note

Both `clientid` and `secret` can alternatively be supplied as
environment variables: OAUTH_CLIENTID and OAUTH_SECRET. If these env
variables are available (and no values are entered as function
arguments) they will be used to store credentials.

## Examples

``` r
if (FALSE) { # \dontrun{
store_cdse_credentials(clientid="<...enter your client id...>",
                      secret = "<...enter your secret...>")
} # }
```
