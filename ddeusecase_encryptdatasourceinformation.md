---

copyright:
  years: 2018
lastupdated: "2018-01-19"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Encrypting data source information

When applications use {{site.data.keyword.dynamdashbemb_full}}, they provide data source modules (JSON documents) to describe the metadata of the data that they want {{site.data.keyword.dynamdashbemb_short}} to query. Part of this information is the database connection and credential information.

To provide a secure way to pass this information from the embedding application to {{site.data.keyword.dynamdashbemb_short}}, and keep the plain text of these sensitive fields out of the browser, you must ensure that the calling application does things that are described in this section.

When your embedding application creates a session, a public encryption key, in JSON Web Key format, is returned. 
For more information on a {{site.data.keyword.dynamdashbemb_short}} session, see [Getting started tutorial](/docs/services/dynamic-dashboard-embedded/dde_getting_started.html#step-3-creating-a-dynamic-dashboard-embedded-session).
For information on JSON Web Key, see [JSON Web Key](https://tools.ietf.org/html/rfc7517).

Public encryption key in JSON Web Key format:
![opendashboardflow](publicencryptionkey.jpg "Public encryption key")

When the embedding application provides a data source module specification, then the calling application provides a module to {{site.data.keyword.dynamdashbemb_short}}, for exampling with the methods *addSources()* or *updateModuleDefinitions()*, then you can choose to provide any of the following fields in an encrypted form:
-	user
-	password
-	schema
-	jdbcUrl
-	sourceUrl

Before sending the module, your application uses the public key to encrypt the sensitive fields of the module.
**Note:** This key is only valid during the session.

Use the prefix *{enc}* on encrypted field values. For example: "password" : "{enc}encryptedpassword". Encrypted values are Base64 encoded.

**Note:** When starting a new session, you must re-encrypt sensitive information that is contained in modules. Before you encrypt these fields, you must update the data sources.  Update the data sources by calling the *updateModuleDefinitions()* method. 

For more information on using the *updateModuleDefinitions()* method, see [Updating data source information](/docs/services/dynamic-dashboard-embedded/ddeusecase_updatedatasourceinfo.html).

Update all modules with the encrypted fields, by using the encryption key of this session.
