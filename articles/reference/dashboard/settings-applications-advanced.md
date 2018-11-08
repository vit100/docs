---
title: Auth0 Dashboard Advanced Application Settings
description: Learn about the AdvancedApplication Settings available through the Auth0 Dashboard.
topics:
  - applications
  - oidc
  - dashboard
  - authentication
contentType: reference
useCase:
  - secure-api
  - call-api
  - add-login
---

# Advanced Application Settings

The **Advanced Settings** section allows you to:

* Manage or add Application Metadata, Mobile, OAuth, and WS-Federation settings 
* Obtain certificates and token endpoint information
* Set the grant type(s) for the Application

![Advanced Application Settings Page](/media/articles/applications/advanced-settings.png)

#### Application Metadata

Application metadata are custom string keys and values (each of which has a character maximum of 255), set on a per application basis. Metadata is exposed in the Application object as client_metadata, and in Rules as context.clientMetadata

You can create up to 10 sets of metadata.

#### OAuth

Set the OAuth-related settings on this tab:

* By default, all apps/APIs can make a delegation request, but if you want to explicitly grant permissions to selected apps/APIs, you can do so in **Allowed APPs/APIs**.

* Set the algorithm used (**HS256** or **RS256**) for signing your JSON Web Tokens. Learn more about [signing algorithms](/concepts/signing-algorithms).

* Toggle the switch to indicate if your application is OIDC Conformant or not.
