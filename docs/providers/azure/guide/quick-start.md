<!--
title: Serverless Framework - Azure Functions Guide - Quick Start
menuText: Quick Start
menuOrder: 1
description: Getting started with the Serverless Framework on Azure Functions
layout: Doc
-->

# Azure - Quick Start

## Pre-requisites

1. Node.js `v6.5.0` or later. *(this is the runtime version supported by Azure Functions)*
2. Serverless CLI `v1.9.0` or later. You can run
`npm install -g serverless` to install it.
3. An Azure account. If you don't already have one, you can sign up for a [free trial](https://azure.microsoft.com/en-us/free/) that includes $200 of free credit.
4. **Set-up your [Provider Credentials](./credentials.md)**.

## Create a new service

Create a new service using the Node.js template, specifying a unique name and an optional path for your service.

```bash
# Create a new Serverless Service/Project
$ serverless create --template aws-nodejs --path my-service
# Change into the newly created directory
$ cd my-service
# Install npm dependencies
$ npm install
```

## Deploy, test and diagnose your service

1. **Deploy the Service:**

  Deploy your new service to Azure! The first time you do this, you will be asked to authenticate with your Azure account, so the `serverless` CLI can manage Functions on your behalf. Simply follow the provided instructions, and the deployment will continue as soon as the authentication process is completed.

  ```bash
  serverless deploy -v
  ```

  > Note: Once you've authenticated, a new Azure "service principal" will be created, and used for subsequent deployments. This prevents you from needing to manually login again. See [below](#advanced-authentication) if you'd prefer to use a custom service principal instead.

2. **Deploy the Function**

  Use this to quickly upload and overwrite your function code,  allowing you to develop faster. If you're working on a single function, you can simply deploy the specified function instead of the entire service.

  ```bash
  serverless deploy function -f hello
  ```

3. **Invoke the Function**

  Invoke a function, in order to test that it works:

  ```bash
  serverless invoke -f hello
  ```

4. **Fetch the Function Logs**

  Open up a separate tab in your console and stream all logs for a specific Function using this command.

  ```bash
  serverless logs -f hello -t
  ```

## Cleanup

If at any point, you no longer need your service, you can run the following command to remove the Functions, Events and Resources that were created, and ensure that you don't incur any unexpected charges.

```bash
serverless remove
```

Check out the [Serverless Framework Guide](./README.md) for more information.

## Advanced Authentication

The getting started walkthrough illustrates the interactive login experience, which is recommended for most users. However, if you'd prefer to create an Azure ["service principal"](https://github.com/Azure/azure-sdk-for-node/blob/master/Documentation/Authentication.md#2-azure-cli) yourself, you can indicate that this plugin should use its credentials instead, by setting the following environment variables:

**Bash**
```bash
export azureSubId='<subscriptionId>'
export azureServicePrincipalTenantId='<tenantId>'
export azureServicePrincipalClientId='<servicePrincipalName>'
export azureServicePrincipalPassword='<password>'
```

**Powershell**
```powershell
$env:azureSubId='<subscriptionId>'
$env:azureServicePrincipalTenantId='<tenantId>'
$env:azureServicePrincipalClientId='<servicePrincipalName>'
$env:azureServicePrincipalPassword='<password>'
```
