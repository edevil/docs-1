---
title: OIDC-conformant clients
description: List of breaking changes for OIDC-conformant clients
---

# OIDC-conformant clients

<%= include('./_about.md') %>

In order to make the transition to the [OIDC-conformant authentication pipeline](/api-auth/tutorials/adoption) more predictable, clients now include an option called "OIDC Conformant", available under **Advanced Settings > OAuth**:

![OIDC-conformant client setting](/media/articles/dashboard/oidc_conformant.png)

The objective of this flag is to disable as many legacy features as possible, so you can run into the OIDC-conformant pipeline's breaking changes at configuration time rather than run time.
Enabling this flag on a client will have the following effects:

* The following features are deprecated in favor of [silent authentication](/api-auth/tutorials/adoption/implicit):
    - Refresh tokens on authentication with the [implicit grant](/api-auth/tutorials/adoption/implicit)
    - /ssodata endpoint and `getSSOData()` method from Lock/auth0.js
* [Single sign-on (SSO)](/api-auth/tutorials/adoption/single-sign-on) can only be performed from Auth0-hosted login pages.
* Using `response_type=token` will only return an access token, not an ID token. Use `response_type=id_token` or `response_type=token id_token` instead.
* ID tokens obtained with the implicit grant will be signed asymmetrically using RS256.
* The /tokeninfo endpoint is disabled.
* Responses from /userinfo will [conform to the OIDC specification](https://openid.net/specs/openid-connect-core-1_0.html#UserInfoResponse), similar to the [contents of ID tokens](/api-auth/tutorials/adoption/scope-custom-claims)
* Implicit grant authentication requests made without a [`nonce` parameter](/api-auth/tutorials/nonce) will be rejected.
* [Refresh tokens must be used at the token endpoint]() instead of /delegation.
* The `device` parameter, originally used to obtain refresh tokens, is now considered invalid.
* The legacy [resource owner endpoint](/api/authentication#database-ad-ldap-active-) is disabled.
    - Passwordless authentication is implemented at this endpoint, so it will be disabled as well.
      Support for OIDC-conformant passwordless authentication will be added in future releases.
* The [/oauth/access_token endpoint](/api/authentication#post-oauth-access_token), used for social authentication from native mobile applications, is disabled.
  An OIDC-conformant alternative will be added in future releases.
* The [`scope` parameter of authentication requests](/api-auth/tutorials/adoption/scope-custom-claims) will comply to the OIDC specification:
    - Custom claims must be namespaced and added to ID tokens or access tokens via rules.
    - Custom scope values can be defined by a [resource server (API)](/api-auth/tutorials/adoption/api-tokens).
* OIDC-conformant clients cannot be the source or target client of a [delegation request](/api-auth/tutorials/adoption/delegation).

## I don't want to make all these changes at once!

The "OIDC Conformant" flag will force all of these changes at the same time for a given client, but it's not the only option to gradually transition to the OIDC-conformant authentication pipeline.
Any authentication requests made with an `audience` parameter will use the new pipeline, and all other requests will continue to work as usual.

If your application doesn't need a resource server but you want opt-in to the new pipeline on a per-request basis, you can use the following `audience` parameter:

```
https://${account.namespace}/userinfo
```

## Further reading

<%= include('./_index.md') %>
