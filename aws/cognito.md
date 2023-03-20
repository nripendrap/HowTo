1. All Services -> Security, Identity, & Compliance -> Cognito
2. From Amazon Cognito page, choose __Manage User Pools__
3. Click __Create a user pool__ button
4. Pool name: tmt-medicalwarnings 
5. Keep everything as default and keep selecting __Next Step__ button
6. Select __Create pool__ button
7. Choose __App clients__ under General settings from left menu in __tmt-medicalwarnings__ user pool page
8. App client name: tmt-medicalwarnings-handler
9. Leave other as default
10. Remember App client id and App client secret
11. Choose __App client settings__ under __App integration__
12. In __App client__ tmt-medicalwarnings-handler box
```
Enable Identity Providers: Select all

Callback URL(s): <Application URL>/signin-oidc
Sign out URL(s): <Application URL>

Allowed OAuth Flows: Authorization code grant
Allowed OAuth Scopes: email, openid, aws.cognito.signin.user.admin, profile

```
13. Select __Save changes__
14. Select __Choose domain name__
15. Alternatively, choose __Domain name__ under __App integration__
16. 
```
Domain prefix: tmt-medicalwarnings
```

#### Integration with ASP.NET Core web API
1. We need following parameters:
    i. ClientId: _&lt;From above&gt;_
    ii. ClientSecret: _&lt;From above&gt;_
    iii. Metadata Address: https://cognito-idp.ap-southeast-2.amazonaws.com/_&lt;Pool Id&gt;_/.well-known/openid-configuration
    iv. Logout URL: _&lt;Domain name&gt;_/logout
    v. Base URL: _&lt;Application URL&gt;_ This URL should match the URL defined in Sign out URL(s) above.
2. Open Startup.cs class
3. Add in ConfigureServices(...) function
```
services.AddAuthentication(options =>
            {
                options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
                options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
            }).AddCookie()
            .AddOpenIdConnect(options =>
            {
                options.ResponseType = "code";
                options.MetadataAddress = metadataAddress;
                options.ClientId = clientId;
                options.ClientSecret = clientSecret;
                options.GetClaimsFromUserInfoEndpoint = true;
                options.Scope.Add("email");
                options.Events = new OpenIdConnectEvents
                {
                    OnRedirectToIdentityProviderForSignOut = (context) =>
                    {
                        var logoutUri = logoutUrl;
                        logoutUri += $"?client_id={clientId}&logout_uri={baseUrl}";
                        context.Response.Redirect(logoutUri);
                        context.HandleResponse();
                        return Task.CompletedTask;
                    }
                };
            });
```
4. Add in Configure(...) method
```
app.UseAuthentication();
```
5. In controller, add [authorize] annotation


Check out chrome://net-internals/#events (or chrome://net-export in the latest version of Chrome) for a detailed overview of all network events happening in your browser.