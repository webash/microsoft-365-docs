---
title: Restrict app execution API
description: Use this API to create calls related to restricting an application from executing.
keywords: apis, graph api, supported apis, collect investigation package
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
---

# Restrict app execution API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Applies to:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## API description
Restrict execution of all applications on the device except a predefined set.


## Limitations
1. Rate limitations for this API are 100 calls per minute and 1500 calls per hour.


[!include[Device actions note](../../includes/machineactionsnote.md)]

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](apis-intro.md)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	Machine.RestrictExecution |	'Restrict code execution'
Delegated (work or school account) | Machine.RestrictExecution | 'Restrict code execution'

>[!Note]
> When obtaining a token using user credentials:
>- The user needs to have at least the following role permission: 'Active remediation actions' (See [Create and manage roles](user-roles.md) for more information)
>- The user needs to have access to the device, based on device group settings (See [Create and manage device groups](machine-groups.md) for more information)

## HTTP request
```
POST https://api.securitycenter.microsoft.com/api/machines/{id}/restrictCodeExecution
```

## Request headers

Name | Type | Description
:---|:---|:---
Authorization | String | Bearer {token}. **Required**.
Content-Type | string | application/json. **Required**.

## Request body
In the request body, supply a JSON object with the following parameters:

Parameter |	Type	| Description
:---|:---|:---
Comment |	String |	Comment to associate with the action. **Required**.

## Response
If successful, this method returns 201 - Created response code and [Machine Action](machineaction.md) in the response body.


## Example

**Request**

Here is an example of the request.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/restrictCodeExecution 
```

```json
{
  "Comment": "Restrict code execution due to alert 1234"
}

```

- To remove code execution restriction from a device, see [Remove app restriction](unrestrict-code-execution.md).
