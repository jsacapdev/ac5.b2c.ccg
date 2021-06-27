# ac5.b2c.ccg

Asp.net Core 5 using MSAL.NET and Client Credentials Grant in a B2C scenario, as opposed to a Azure AD scenario.

[B2C has some limitations](https://www.hossambarakat.net/2020/08/14/azure-b2c-client-credentials/), as stated by the [Microsoft](https://docs.microsoft.com/en-us/azure/active-directory-b2c/application-types#daemonsserver-side-applications) documentation.

## Azure AD Configuration

There is no client. The server has the secret and that is what is used to get the token. Also, no manifests, which also probably means no role/requirement/policy mapping.

## Configuration

This type of thing has been set in the local configuration file:

``` json
  "ClientId": "???",
  "TenantId": "???"
```

You can also put it in your VSCode `launch.json`:

``` json
"env": {
    "ClientId": "???",
    "TenantId": "???"
}
```

## Testing

To populate the `http` rest extension run the secret for the client through the following command:

`[System.Web.HTTPUtility]::UrlEncode("your_password")`
