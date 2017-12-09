---
section: libraries
title: Migrating to Auth0.js v9
description: How to migrate to Auth0.js v9
toc: true
---
# Migrating to Auth0.js v9

Auth0.js v9 has been improved to work better in embedded login scenarios. It operates with enhanced security and removes dependencies that have been deprecated as per Auth0's roadmap. In some cases, these security enhancements may impact application behavior when upgrading from an earlier versions of Auth0.js. 

Auth0.js can be used to implement authentication in different ways:

- Centralized Login, using the `.authorize()` method, where the user is redirected from your website to an Auth0's Hosted Login Page.

- Embedded Login, using the `.login()`, `popup.loginWithCredentials()`, `client.loginWithCredentials()` methods, where the login dialog is displayed in the application's website.

- In the [Hosted Login Page](/hosted-pages/login), where you can use the same methods as in Embedded Login but from inside a customized Auth0's Hosted Login Page. Most customers don't customize Auth0 Hosted Login Page with Auth0.js, so your probably don't need to worry about this scenario.

Depending on how you are using Auth0.js, you have different options:

| Scenario | Migration to v9 | 
| --- | --- | 
| Centralized Login | Recommended |
| Embedded Login | Required |
| Customized Hosted Page | Not Supported |

If your application is configured to use Centralized Login, and your web application uses `.authorize()`, you can update Auth0.js to v9 in your web application, without requiring any code changes.

If you are not using Centralized Login in your applications, we recommend you to use it as [most secure, powerful and flexible approach for authentication](/guides/login/centralized-vs-embedded). 

# Migration Instructions

If you decide to keep using Embedded Login, you will need to migrate to v9. 

This document links to all the changes that you should be aware of between different versions of Auth0.js. It includes information on what is changing and why, details on new or deprecated features, and instructions on how you can migrate your implementation. Make sure you go through them before upgrading.

[Migrating from Auth0.js v8](/libraries/auth0js/v9/migration-v8-v9)

[Migrating from Auth0.js v7](/libraries/auth0js/v9/migration-v7-v9)

[Migrating from Auth0.js v6](/libraries/auth0js/v9/migration-v6-v9)

[Migrating from Auth0.js v6 in Angular.js Applications](/libraries/auth0js/v9/migration-angularjs-v7)

[Migrating from Auth0.js v7 in Angular.js Applications](/libraries/auth0js/v9/migration-angularjs-v7)

[Migrating from Auth0.js v8 in Angular.js Applications](/libraries/auth0js/v9/migration-angularjs-v8)

[Migrating to Auth0.js v9 in Angular Applications](/libraries/auth0js/v9/migration-angular)

[Migrating to Auth0.js v9 in React.js Applications](/libraries/auth0js/v9/migration-react)


::: note
If you have any questions or concerns, you can submit them using the [Support Center](${env.DOMAIN_URL_SUPPORT}), or directly through your account representative, if applicable. 
:::