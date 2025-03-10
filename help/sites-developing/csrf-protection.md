---
title: The CSRF Protection Framework
seo-title: The CSRF Protection Framework
description: The framework makes use of tokens to guarantee that the client request is legitimate
seo-description: The framework makes use of tokens to guarantee that the client request is legitimate
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
exl-id: e6b0f8f7-54b0-4dd6-86ad-5516954c6d90
---
# The CSRF Protection Framework{#the-csrf-protection-framework}

In addition to the Apache Sling Referrer Filter, Adobe also provides a new CSRF Protection Framework to protect against this type of attack.

The framework makes use of tokens to guarantee that the client request is legitimate. The tokens are generated when the form is sent to the client and validated when the form is sent back to the server.

>[!NOTE]
>
>There are no tokens on the publish instances for anonymous users.

## Requirements {#requirements}

### Dependencies {#dependencies}

Any component that relies on the `granite.jquery` dependency will benefit from the CSRF Protection Framework automatically. If this is not the case for any of your components, you must declare a dependency to `granite.csrf.standalone` before you can use the framework.

### Replicating the Crypto Key {#replicating-crypto-keys}

In order to make use of the tokens, you need to replicate the HMAC binary to all of the instances in your deployment. See [Replicating the HMAC key](/help/sites-administering/encapsulated-token.md#replicating-the-hmac-key) for more details.

>[!NOTE]
>
>Make sure you also make the necessary [Dispatcher configuration changes](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) in order to use the CSRF Protection Framework.

>[!NOTE]
>
>If you use the manifest cache with your web application, make sure you add "**&ast;**" to the manifest in order to make sure the token does not take the CSRF token generation call offline. For more information, consult this [link](https://www.w3.org/TR/offline-webapps/).
>
>For more information on CSRF attacks and ways to mitigate them, see the [Cross-Site Request Forgery OWASP page](https://owasp.org/www-community/attacks/csrf).
