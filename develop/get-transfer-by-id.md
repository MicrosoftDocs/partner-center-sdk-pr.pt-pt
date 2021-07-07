---
title: Obtenha detalhes de transferência por ID
description: Como obter detalhes de uma transferência de subscrições para um cliente.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1347f95debec458b8c70c5e803cef6203ad34818
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445940"
---
# <a name="get-transfer-details-by-id"></a><span data-ttu-id="0b77b-103">Obtenha detalhes de transferência por ID</span><span class="sxs-lookup"><span data-stu-id="0b77b-103">Get transfer details by ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0b77b-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0b77b-104">Prerequisites</span></span>

- <span data-ttu-id="0b77b-105">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0b77b-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0b77b-106">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="0b77b-106">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="0b77b-107">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0b77b-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="0b77b-108">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="0b77b-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="0b77b-109">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="0b77b-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="0b77b-110">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="0b77b-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="0b77b-111">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="0b77b-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="0b77b-112">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0b77b-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="0b77b-113">Um identificador de transferência para uma transferência existente.</span><span class="sxs-lookup"><span data-stu-id="0b77b-113">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="0b77b-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="0b77b-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0b77b-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b77b-115">Request syntax</span></span>

| <span data-ttu-id="0b77b-116">Método</span><span class="sxs-lookup"><span data-stu-id="0b77b-116">Method</span></span>   | <span data-ttu-id="0b77b-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="0b77b-117">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0b77b-118">**Obter**</span><span class="sxs-lookup"><span data-stu-id="0b77b-118">**GET**</span></span> | <span data-ttu-id="0b77b-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers/{transfer-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0b77b-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="0b77b-120">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="0b77b-120">URI parameter</span></span>

<span data-ttu-id="0b77b-121">Utilize o seguinte parâmetro de percurso para identificar o cliente e especificar a transferência a aceitar.</span><span class="sxs-lookup"><span data-stu-id="0b77b-121">Use the following path parameter to identify the customer and specify the transfer to be accepted.</span></span>

| <span data-ttu-id="0b77b-122">Nome</span><span class="sxs-lookup"><span data-stu-id="0b77b-122">Name</span></span>            | <span data-ttu-id="0b77b-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="0b77b-123">Type</span></span>     | <span data-ttu-id="0b77b-124">Necessário</span><span class="sxs-lookup"><span data-stu-id="0b77b-124">Required</span></span> | <span data-ttu-id="0b77b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b77b-125">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="0b77b-126">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="0b77b-126">**customer-id**</span></span> | <span data-ttu-id="0b77b-127">string</span><span class="sxs-lookup"><span data-stu-id="0b77b-127">string</span></span>   | <span data-ttu-id="0b77b-128">Yes</span><span class="sxs-lookup"><span data-stu-id="0b77b-128">Yes</span></span>      | <span data-ttu-id="0b77b-129">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="0b77b-129">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="0b77b-130">**transferência id**</span><span class="sxs-lookup"><span data-stu-id="0b77b-130">**transfer-id**</span></span> | <span data-ttu-id="0b77b-131">string</span><span class="sxs-lookup"><span data-stu-id="0b77b-131">string</span></span>   | <span data-ttu-id="0b77b-132">Yes</span><span class="sxs-lookup"><span data-stu-id="0b77b-132">Yes</span></span>      | <span data-ttu-id="0b77b-133">Um id de transferência formatado GUID que identifica a transferência.</span><span class="sxs-lookup"><span data-stu-id="0b77b-133">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="0b77b-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="0b77b-134">Request headers</span></span>

<span data-ttu-id="0b77b-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="0b77b-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-example"></a><span data-ttu-id="0b77b-136">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="0b77b-136">Request example</span></span>

```http
GET /v1/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/46e8ed67-8adf-4f65-b3d8-d31318080556 HTTP/1.1
Authorization: Bearer <token>
Connection: keep-alive
MS-RequestId: 0d61b5ce-b396-4f5e-a50b-e8779d0d23cc
MS-CorrelationId: 68eacc61-971c-43b0-c06f-2622bf79b090
Accept: application/json
```

## <a name="rest-response"></a><span data-ttu-id="0b77b-137">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="0b77b-137">REST response</span></span>

<span data-ttu-id="0b77b-138">Se for bem sucedido, este método devolve o recurso [da Entidade de Transferência](transfer-entity-resources.md) povoada no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="0b77b-138">If successful, this method returns the populated [TransferEntity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0b77b-139">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="0b77b-139">Response success and error codes</span></span>

<span data-ttu-id="0b77b-140">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="0b77b-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0b77b-141">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="0b77b-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0b77b-142">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0b77b-142">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0b77b-143">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="0b77b-143">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1501
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 68eacc61-971c-43b0-c06f-2622bf79b090
MS-RequestId: 0d61b5ce-b396-4f5e-a50b-e8779d0d23cc
X-Locale: en-US
Date: Fri, 27 Mar 2020 18:25:25 GMT

{
  "id": "46e8ed67-8adf-4f65-b3d8-d31318080556",
  "status": "Active",
  "createdTime": "2020-03-27T18:22:33.2875302Z",
  "lastModifiedTime": "2020-03-27T18:22:33Z",
  "customerTenantId": "b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0",
  "partnertenantid": "3a9a35ce-d5be-4814-ab58-4451c36fe157",
  "sourcePartnerName": "Test_Test_09092019GBL",
  "sourcePartnerTenantId": "7c8db11f-1e5e-4472-8386-f0b627d1f3e1",
  "targetPartnerName": "Test_Test_09032019GBL",
  "targetPartnerTenantId": "3a9a35ce-d5be-4814-ab58-4451c36fe157",
  "lastModifiedUser": "edc0524d-2e42-4619-af7e-349c015cfdfd",
  "lineItems": [
    {
      "id": 0,
      "subscriptionId": "75B71186-73C3-45B4-A403-281C0D7EB032",
      "offerId": "F72752C8-3E37-4C9B-A1A0-69E8442068DC",
      "billingCycle": "annual",
      "friendlyName": "Dynamics 365 Business Central Team Member",
      "quantity": 1,
      "partnerIdOnRecord": "5139005",
      "addonItems": [

      ]
    },
    {
      "id": 1,
      "subscriptionId": "1FB4CB0A-EB79-4300-9E87-7D486054888A",
      "offerId": "88F9EB8A-0636-45E8-A601-553E0A48AA9E",
      "billingCycle": "annual",
      "friendlyName": "Dynamics 365 Business Central External Accountant",
      "quantity": 1,
      "partnerIdOnRecord": "5139005",
      "addonItems": [

      ]
    },
    {
      "id": 2,
      "subscriptionId": "08AB3010-B647-402E-8955-B6C0FB364D8F",
      "offerId": "4D8F3B90-29B3-4E7B-B37C-4A435DDEF1D9",
      "billingCycle": "annual",
      "friendlyName": "Common Area Phone",
      "quantity": 1,
      "partnerIdOnRecord": "5139005",
      "addonItems": [

      ]
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/46e8ed67-8adf-4f65-b3d8-d31318080556",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "TransferEntity"
  }
}

```
