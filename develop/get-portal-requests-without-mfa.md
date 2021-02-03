---
title: Obter pedidos do portal sem MFA
description: Obtenha uma lista de pedidos de utilizador sem autenticação multi-factor (MFA) utilizando a API partner REST.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
ms.openlocfilehash: fd350aa3301f00926942ae6c6af359b0d0edc423
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769074"
---
# <a name="get-portal-requests-without-mfa"></a><span data-ttu-id="84426-103">Obter pedidos do portal sem MFA</span><span class="sxs-lookup"><span data-stu-id="84426-103">Get portal requests without MFA</span></span>

<span data-ttu-id="84426-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="84426-104">Applies to:</span></span>

- <span data-ttu-id="84426-105">API do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="84426-105">Partner Center API</span></span>

<span data-ttu-id="84426-106">Este artigo explica como obter uma lista dos pedidos mais recentes dos utilizadores que acedem ao portal Partner Center sem completar a autenticação multi-factor (MFA).</span><span class="sxs-lookup"><span data-stu-id="84426-106">This article explains how to obtain a list of the most recent requests from users who access Partner Center portal without completing multi-factor authentication (MFA).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84426-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="84426-107">Prerequisites</span></span>

- <span data-ttu-id="84426-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="84426-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="84426-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="84426-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="84426-110">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="84426-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="84426-111">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="84426-111">Request syntax</span></span>

| <span data-ttu-id="84426-112">Método</span><span class="sxs-lookup"><span data-stu-id="84426-112">Method</span></span>  | <span data-ttu-id="84426-113">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="84426-113">Request URI</span></span>                                                  |
|---------|--------------------------------------------------------------|
| <span data-ttu-id="84426-114">**Obter**</span><span class="sxs-lookup"><span data-stu-id="84426-114">**GET**</span></span> | <span data-ttu-id="84426-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/nonMfaCompliantPartnerPrincipals</span><span class="sxs-lookup"><span data-stu-id="84426-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/nonMfaCompliantPartnerPrincipals</span></span> |

### <a name="request-headers"></a><span data-ttu-id="84426-116">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="84426-116">Request headers</span></span>

- <span data-ttu-id="84426-117">Consulte [os cabeçalhos REST do Partner Center](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="84426-117">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="84426-118">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="84426-118">Request body</span></span>

<span data-ttu-id="84426-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="84426-119">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="84426-120">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="84426-120">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/nonMfaCompliantPartnerPrincipals HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Accept: application/json
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
Connection: keep-alive

```

## <a name="rest-response"></a><span data-ttu-id="84426-121">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="84426-121">REST response</span></span>

<span data-ttu-id="84426-122">Se for bem sucedido, este método devolve uma coleção de recursos de [pedido do Portal](mfa-resources.md#portal-request-without-mfa) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="84426-122">If successful, this method returns a collection of [Portal request](mfa-resources.md#portal-request-without-mfa) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="84426-123">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="84426-123">Response success and error codes</span></span>

<span data-ttu-id="84426-124">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="84426-124">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="84426-125">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="84426-125">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="84426-126">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="84426-126">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="84426-127">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="84426-127">Response example</span></span>

``` http
HTTP/1.1 200 OK
Content-Length: 296
Content-Type: application/json
MS-CorrelationId: 4cb80cbe-566b-4d8b-8b8f-af1454b73089
MS-RequestId: 566330a7-1e4b-4848-9c23-f135c70fd810
Date: Thu, 23 Apr 2020 22:10:30 GMT
{
    "totalCount": 1,
    "items": [
        {
            "objectId": "adc77aa5-7968-4c57-9f48-361018265c1a",
            "tenantId": "6e6aef4a-4ca9-40a8-b5bf-b53a1923c540",
            "upn": "portalnonmfa@yourdomain.onmicrosoft.com",
            "lastNonMfaCompliantRequestDateTime": "2020-04-21T22:09:53.051"
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
