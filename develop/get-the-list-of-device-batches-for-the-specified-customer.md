---
title: Obter uma lista de lotes de dispositivos para o cliente especificado
description: Como recuperar uma coleção de lotes de dispositivos para o cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ea5797bbaff4d4eafd1e63428556ab784bcb0ee2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769811"
---
# <a name="get-a-list-of-device-batches-for-the-specified-customer"></a><span data-ttu-id="8280c-103">Obter uma lista de lotes de dispositivos para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="8280c-103">Get a list of device batches for the specified customer</span></span>

<span data-ttu-id="8280c-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="8280c-104">**Applies To**</span></span>

- <span data-ttu-id="8280c-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="8280c-105">Partner Center</span></span>
- <span data-ttu-id="8280c-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="8280c-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="8280c-107">Como recuperar uma coleção de lotes de dispositivos para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="8280c-107">How to retrieve a collection of device batches for the specified customer.</span></span>

<span data-ttu-id="8280c-108">Cada lote de dispositivo contém informações sobre o estado do resumo sobre dispositivos que foram matriculados na implementação de toque zero.</span><span class="sxs-lookup"><span data-stu-id="8280c-108">Each device batch contains summary status information about devices that have been enrolled in zero-touch deployment.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8280c-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8280c-109">Prerequisites</span></span>

- <span data-ttu-id="8280c-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8280c-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8280c-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="8280c-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8280c-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8280c-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8280c-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="8280c-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8280c-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="8280c-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8280c-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="8280c-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8280c-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="8280c-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8280c-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8280c-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="8280c-118">C\#</span><span class="sxs-lookup"><span data-stu-id="8280c-118">C\#</span></span>

<span data-ttu-id="8280c-119">Para obter a recolha de lotes de dispositivos para o cliente especificado, ligue primeiro para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="8280c-119">To get the collection of device batches for the specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="8280c-120">Em seguida, recupere o valor da propriedade [**DeviceBatches**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicebatches) para obter uma interface para o dispositivo operações de recolha de lotes.</span><span class="sxs-lookup"><span data-stu-id="8280c-120">Then, retrieve the value of the [**DeviceBatches**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicebatches) property to get an interface to device batch collection operations.</span></span> <span data-ttu-id="8280c-121">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.getasync) para recuperar a coleção.</span><span class="sxs-lookup"><span data-stu-id="8280c-121">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.getasync) method to retrieve the collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var devicesBatches =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.Get();
```

<span data-ttu-id="8280c-122">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8280c-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8280c-123">**Projeto**: Partner Center SDK Samples **Class**: GetDevicesBatches.cs</span><span class="sxs-lookup"><span data-stu-id="8280c-123">**Project**: Partner Center SDK Samples **Class**: GetDevicesBatches.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8280c-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8280c-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8280c-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8280c-125">Request syntax</span></span>

| <span data-ttu-id="8280c-126">Método</span><span class="sxs-lookup"><span data-stu-id="8280c-126">Method</span></span>  | <span data-ttu-id="8280c-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8280c-127">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="8280c-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="8280c-128">**GET**</span></span> | <span data-ttu-id="8280c-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/deviceBatches HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8280c-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="8280c-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="8280c-130">URI parameter</span></span>

<span data-ttu-id="8280c-131">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="8280c-131">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="8280c-132">Nome</span><span class="sxs-lookup"><span data-stu-id="8280c-132">Name</span></span>        | <span data-ttu-id="8280c-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="8280c-133">Type</span></span>   | <span data-ttu-id="8280c-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="8280c-134">Required</span></span> | <span data-ttu-id="8280c-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="8280c-135">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="8280c-136">id cliente</span><span class="sxs-lookup"><span data-stu-id="8280c-136">customer-id</span></span> | <span data-ttu-id="8280c-137">string</span><span class="sxs-lookup"><span data-stu-id="8280c-137">string</span></span> | <span data-ttu-id="8280c-138">Sim</span><span class="sxs-lookup"><span data-stu-id="8280c-138">Yes</span></span>      | <span data-ttu-id="8280c-139">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="8280c-139">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8280c-140">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8280c-140">Request headers</span></span>

<span data-ttu-id="8280c-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8280c-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8280c-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8280c-142">Request body</span></span>

<span data-ttu-id="8280c-143">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8280c-143">None</span></span>

### <a name="request-example"></a><span data-ttu-id="8280c-144">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8280c-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="8280c-145">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8280c-145">REST response</span></span>

<span data-ttu-id="8280c-146">Se for bem sucedido, o corpo de resposta contém a recolha de recursos [deviceBatch.](device-deployment-resources.md#devicebatch)</span><span class="sxs-lookup"><span data-stu-id="8280c-146">If successful, the response body contains the collection of [DeviceBatch](device-deployment-resources.md#devicebatch) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8280c-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8280c-147">Response success and error codes</span></span>

<span data-ttu-id="8280c-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8280c-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8280c-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8280c-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8280c-150">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8280c-150">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8280c-151">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="8280c-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 339
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4a5002a2-0c1b-4e57-b491-dbcf19c0e7b8
MS-RequestId: 7b3e2e00-b330-4480-9d84-59ace713427f
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:52:41 GMT

{
    "totalCount": 1,
    "items": [{
            "id": "Test batch",
            "status": "finished",
            "creationDate": "2017-07-25T01:51:00",
            "devicesCount": 5,
            "devicesLink": {
                "uri": "/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches/Test batch/devices",
                "method": "GET",
                "headers": []
            },
            "attributes": {
                "objectType": "DeviceBatch"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
