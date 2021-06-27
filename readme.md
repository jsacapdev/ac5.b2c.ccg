# ac5.b2c.ccg

Asp.net Core 5 using MSAL.NET and Client Credentials Grant in a B2C scenario, as opposed to a Azure AD scenario.

[B2C has some limitations](https://www.hossambarakat.net/2020/08/14/azure-b2c-client-credentials/), as stated by the [Microsoft](https://docs.microsoft.com/en-us/azure/active-directory-b2c/application-types#daemonsserver-side-applications) documentation.

## Azure AD Configuration

The approach supports the same type of client/server manifest mapping. So it will also probably support the policy/requirement based mapping.

The following has been added to the manifest in addition to creating the application registration.

``` json
"appRoles": [
    {
        "allowedMemberTypes": [
            "User",
            "Application"
        ],
        "description": "Read messages",
        "displayName": "Read",
        "id": "6f2c2b38-4c2a-484d-bed8-5861194474e0",
        "isEnabled": true,
        "lang": null,
        "origin": "Application",
        "value": "Read"
    }
]
```

It also looks like it can handle the ability to validate the role using `HttpContext.ValidateAppRole("Read");`;

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
