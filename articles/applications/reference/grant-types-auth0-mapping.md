---
title: Auth0 Grant Types Mapping
description: Learn which grant types are available to which application types with Auth0.
toc: true
topics:
  - applications
  - application-types
  - grant-types
contentType: reference
useCase:
  - build-an-app
---

# Auth0 Grant Types Mappings

When they are registered, Auth0 Applications will have access to different grant types based on their application types. The biggest deciding factor is whether the application is [confidential or public](/applications/concepts/app-types-confidential-public). The application type is indicated by the value contained in the `token_endpoint_auth_method` flag.

::: panel Token Endpoint Authentication Method
The `Token Endpoint Authentication Method` defines how a Application authenticates against the [token endpoint](/api/authentication#authorization-code) and is represented by the `token_endpoint_auth_method` flag in the Management API. In the [Auth0 Dashboard](${manage_url}), you can find this field in the [Settings](${manage_url}/#/applications/${account.clientId}/settings) for your application.

Valid values include:

* `None`: For public applications without client secrets
* `Post`: For applications using HTTP POST parameters
* `Basic`: For applications using HTTP Basic parameters 
:::


## Public Applications

When a Native/Mobile Application or Single-Page Application (SPA) is registered in the Dashboard, it is automatically flagged as a public application, which is indicated by setting the `token_endpoint_auth_method` flag to `none`.

By default, public Applications are allowed the following `grant_types`:

* `implicit`
* `authorization_code`
* `refresh_token`

::: note
Public Applications **cannot** utilize the `client_credentials` grant type. To use this grant type, you will need to indicate that the application is confidential rather than public. To do so, use the [Management API](/api/management/v2#!/Clients/patch_clients_by_id) to set the **token_endpoint_auth_method** to `client_secret_post` or `client_secret_basic`.
:::

## Confidential Applications

Confidential Applications, indicated by the `token_endpoint_auth_method` flag set to anything *except* `none`, are those created in the Dashboard for Regular Web Applications or Machine to Machine Applications. Additionally, any Application where `token_endpoint_auth_method` is unspecified is confidential. By default, Confidential Applications are created with the following `grant_types`:

* `implicit`;
* `authorization_code`;
* `refresh_token`;
* `client_credentials`.

## Trusted First-Party Applications

Trusted first-party applications can additionally use the following `grant_types`:

* `password`
* `http://auth0.com/oauth/grant-type/password-realm`
* `http://auth0.com/oauth/grant-type/mfa-oob`
* `http://auth0.com/oauth/grant-type/mfa-otp`
* `http://auth0.com/oauth/grant-type/mfa-recovery-code`

::: note
If you are using the [Dashboard](${manage_url}) to enable or disable these grant types, note that all the Password and MFA grant types are enabled when you add the `Password` or `MFA` grant type on your Application. You cannot select these individually.
:::