---
title: Atualizar uma política de configuração para o cliente especificado
description: Como atualizar a política de configuração especificada para o cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6bf3b6f4db7516779c157b647725368ff0e4a570
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769793"
---
# <a name="update-a-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="eb98c-103">Atualizar uma política de configuração para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="eb98c-103">Update a configuration policy for the specified customer</span></span>

<span data-ttu-id="eb98c-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="eb98c-104">**Applies To**</span></span>

- <span data-ttu-id="eb98c-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="eb98c-105">Partner Center</span></span>
- <span data-ttu-id="eb98c-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="eb98c-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="eb98c-107">Como atualizar a política de configuração especificada para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="eb98c-107">How to update the specified configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb98c-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="eb98c-108">Prerequisites</span></span>

- <span data-ttu-id="eb98c-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eb98c-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eb98c-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="eb98c-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="eb98c-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb98c-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="eb98c-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="eb98c-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="eb98c-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="eb98c-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="eb98c-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="eb98c-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="eb98c-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="eb98c-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="eb98c-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb98c-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="eb98c-117">O identificador de apólices.</span><span class="sxs-lookup"><span data-stu-id="eb98c-117">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="eb98c-118">C\#</span><span class="sxs-lookup"><span data-stu-id="eb98c-118">C\#</span></span>

<span data-ttu-id="eb98c-119">Para atualizar uma política de configuração existente para o cliente especificado, instantânea um novo objeto [**ConfigurationPolicy,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) tal como mostrado no seguinte corte de código.</span><span class="sxs-lookup"><span data-stu-id="eb98c-119">To update an existing configuration policy for the specified customer, instantiate a new [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) object as shown in the following code snippet.</span></span> <span data-ttu-id="eb98c-120">Os valores deste novo objeto substituem os valores correspondentes no objeto existente.</span><span class="sxs-lookup"><span data-stu-id="eb98c-120">The values in this new object replace the corresponding values in the existing object.</span></span> <span data-ttu-id="eb98c-121">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="eb98c-121">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="eb98c-122">Em seguida, ligue para o método [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) com o ID da política para recuperar uma interface para configurar operações de política para a política especificada.</span><span class="sxs-lookup"><span data-stu-id="eb98c-122">Next, call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span> <span data-ttu-id="eb98c-123">Por fim, ligue para o método [**Patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) ou [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) para atualizar a política de configuração.</span><span class="sxs-lookup"><span data-stu-id="eb98c-123">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) or [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) method to update the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;

ConfigurationPolicy configPolicyToBeUpdated = new ConfigurationPolicy()
{
    Name= "Test Config Policy",
    Id = selectedConfigurationPolicyId,
    PolicySettings = new List<PolicySettingsType>() {
        PolicySettingsType.OobeUserNotLocalAdmin,
        PolicySettingsType.RemoveOemPreinstalls }
};

ConfigurationPolicy updatedConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedConfigurationPolicyId).Patch(configPolicyToBeUpdated);
```

<span data-ttu-id="eb98c-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="eb98c-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="eb98c-125">**Projeto**: Partner Center SDK Samples **Class**: UpdateConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="eb98c-125">**Project**: Partner Center SDK Samples **Class**: UpdateConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="eb98c-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="eb98c-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eb98c-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb98c-127">Request syntax</span></span>

| <span data-ttu-id="eb98c-128">Método</span><span class="sxs-lookup"><span data-stu-id="eb98c-128">Method</span></span>  | <span data-ttu-id="eb98c-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="eb98c-129">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb98c-130">**PUT**</span><span class="sxs-lookup"><span data-stu-id="eb98c-130">**PUT**</span></span> | <span data-ttu-id="eb98c-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/policies/{policy-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="eb98c-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="eb98c-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="eb98c-132">URI parameter</span></span>

<span data-ttu-id="eb98c-133">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="eb98c-133">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="eb98c-134">Nome</span><span class="sxs-lookup"><span data-stu-id="eb98c-134">Name</span></span>        | <span data-ttu-id="eb98c-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="eb98c-135">Type</span></span>   | <span data-ttu-id="eb98c-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="eb98c-136">Required</span></span> | <span data-ttu-id="eb98c-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb98c-137">Description</span></span>                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| <span data-ttu-id="eb98c-138">id cliente</span><span class="sxs-lookup"><span data-stu-id="eb98c-138">customer-id</span></span> | <span data-ttu-id="eb98c-139">string</span><span class="sxs-lookup"><span data-stu-id="eb98c-139">string</span></span> | <span data-ttu-id="eb98c-140">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-140">Yes</span></span>      | <span data-ttu-id="eb98c-141">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="eb98c-141">A GUID-formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="eb98c-142">id de política</span><span class="sxs-lookup"><span data-stu-id="eb98c-142">policy-id</span></span>   | <span data-ttu-id="eb98c-143">string</span><span class="sxs-lookup"><span data-stu-id="eb98c-143">string</span></span> | <span data-ttu-id="eb98c-144">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-144">Yes</span></span>      | <span data-ttu-id="eb98c-145">Uma cadeia formatada por GUID que identifica a política de atualização.</span><span class="sxs-lookup"><span data-stu-id="eb98c-145">A GUID-formatted string that identifies the policy to update.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="eb98c-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="eb98c-146">Request headers</span></span>

<span data-ttu-id="eb98c-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="eb98c-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="eb98c-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="eb98c-148">Request body</span></span>

<span data-ttu-id="eb98c-149">O organismo de pedido deve conter um objeto que forneça a informação da apólice.</span><span class="sxs-lookup"><span data-stu-id="eb98c-149">The request body must contain an object that provides the policy information.</span></span>

| <span data-ttu-id="eb98c-150">Nome</span><span class="sxs-lookup"><span data-stu-id="eb98c-150">Name</span></span>            | <span data-ttu-id="eb98c-151">Tipo</span><span class="sxs-lookup"><span data-stu-id="eb98c-151">Type</span></span>             | <span data-ttu-id="eb98c-152">Necessário</span><span class="sxs-lookup"><span data-stu-id="eb98c-152">Required</span></span> | <span data-ttu-id="eb98c-153">Updatable</span><span class="sxs-lookup"><span data-stu-id="eb98c-153">Updatable</span></span> | <span data-ttu-id="eb98c-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb98c-154">Description</span></span>                                                                                                                                              |
|-----------------|------------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb98c-155">ID</span><span class="sxs-lookup"><span data-stu-id="eb98c-155">id</span></span>              | <span data-ttu-id="eb98c-156">string</span><span class="sxs-lookup"><span data-stu-id="eb98c-156">string</span></span>           | <span data-ttu-id="eb98c-157">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-157">Yes</span></span>      | <span data-ttu-id="eb98c-158">Não</span><span class="sxs-lookup"><span data-stu-id="eb98c-158">No</span></span>        | <span data-ttu-id="eb98c-159">A cadeia formatada pelo GUID que identifica a política.</span><span class="sxs-lookup"><span data-stu-id="eb98c-159">The GUID-formatted string that identifies the policy.</span></span>                                                                                                    |
| <span data-ttu-id="eb98c-160">name</span><span class="sxs-lookup"><span data-stu-id="eb98c-160">name</span></span>            | <span data-ttu-id="eb98c-161">string</span><span class="sxs-lookup"><span data-stu-id="eb98c-161">string</span></span>           | <span data-ttu-id="eb98c-162">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-162">Yes</span></span>      | <span data-ttu-id="eb98c-163">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-163">Yes</span></span>       | <span data-ttu-id="eb98c-164">O nome amigável da apólice.</span><span class="sxs-lookup"><span data-stu-id="eb98c-164">The friendly name of the policy.</span></span>                                                                                                                         |
| <span data-ttu-id="eb98c-165">categoria</span><span class="sxs-lookup"><span data-stu-id="eb98c-165">category</span></span>        | <span data-ttu-id="eb98c-166">string</span><span class="sxs-lookup"><span data-stu-id="eb98c-166">string</span></span>           | <span data-ttu-id="eb98c-167">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-167">Yes</span></span>      | <span data-ttu-id="eb98c-168">Não</span><span class="sxs-lookup"><span data-stu-id="eb98c-168">No</span></span>        | <span data-ttu-id="eb98c-169">A categoria política.</span><span class="sxs-lookup"><span data-stu-id="eb98c-169">The policy category.</span></span>                                                                                                                                     |
| <span data-ttu-id="eb98c-170">descrição</span><span class="sxs-lookup"><span data-stu-id="eb98c-170">description</span></span>     | <span data-ttu-id="eb98c-171">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="eb98c-171">string</span></span>           | <span data-ttu-id="eb98c-172">No</span><span class="sxs-lookup"><span data-stu-id="eb98c-172">No</span></span>       | <span data-ttu-id="eb98c-173">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-173">Yes</span></span>       | <span data-ttu-id="eb98c-174">A descrição da apólice.</span><span class="sxs-lookup"><span data-stu-id="eb98c-174">The policy description.</span></span>                                                                                                                                  |
| <span data-ttu-id="eb98c-175">dispositivosAssed</span><span class="sxs-lookup"><span data-stu-id="eb98c-175">devicesAssigned</span></span> | <span data-ttu-id="eb98c-176">número</span><span class="sxs-lookup"><span data-stu-id="eb98c-176">number</span></span>           | <span data-ttu-id="eb98c-177">Não</span><span class="sxs-lookup"><span data-stu-id="eb98c-177">No</span></span>       | <span data-ttu-id="eb98c-178">Não</span><span class="sxs-lookup"><span data-stu-id="eb98c-178">No</span></span>        | <span data-ttu-id="eb98c-179">O número de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="eb98c-179">The number of devices.</span></span>                                                                                                                                   |
| <span data-ttu-id="eb98c-180">policySettings</span><span class="sxs-lookup"><span data-stu-id="eb98c-180">policySettings</span></span>  | <span data-ttu-id="eb98c-181">matriz de cadeias (de carateres)</span><span class="sxs-lookup"><span data-stu-id="eb98c-181">array of strings</span></span> | <span data-ttu-id="eb98c-182">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-182">Yes</span></span>      | <span data-ttu-id="eb98c-183">Sim</span><span class="sxs-lookup"><span data-stu-id="eb98c-183">Yes</span></span>       | <span data-ttu-id="eb98c-184">As definições de política: "nenhum", "remover \_ oem \_ pré-instalações", "utilizador oobe \_ não administrador \_ \_ \_ local", "saltar \_ as \_ definições expressas", "saltar \_ o registo de \_ oem", "saltar \_ eula".</span><span class="sxs-lookup"><span data-stu-id="eb98c-184">The policy settings: "none","remove\_oem\_preinstalls","oobe\_user\_not\_local\_admin","skip\_express\_settings","skip \_oem\_registration,"skip\_eula".</span></span> |

### <a name="request-example"></a><span data-ttu-id="eb98c-185">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="eb98c-185">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies/56edf752-ee77-4fd8-b7f5-df1f74a3a9ac HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 256
Content-Type: application/json
Host: api.partnercenter.microsoft.com

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Windows test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"]
}
```

## <a name="rest-response"></a><span data-ttu-id="eb98c-186">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="eb98c-186">REST response</span></span>

<span data-ttu-id="eb98c-187">Se for bem sucedido, o organismo de resposta contém o recurso [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) para a nova política.</span><span class="sxs-lookup"><span data-stu-id="eb98c-187">If successful, the response body contains the [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource for the new policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eb98c-188">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="eb98c-188">Response success and error codes</span></span>

<span data-ttu-id="eb98c-189">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="eb98c-189">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eb98c-190">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="eb98c-190">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eb98c-191">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="eb98c-191">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eb98c-192">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="eb98c-192">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 421
Content-Type: application/json; charset=utf-8
MS-CorrelationId: f9fd5973-6ad8-4585-aadc-f2b0443fe27b
MS-RequestId: cb1fa1f3-1381-45d9-99c5-511e5d3efa7c
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:10:29 GMT

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Windows test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"],
    "createdDate": "2017-01-01T00:00:00",
    "lastModifiedDate": "2017-07-25T18:10:15",
    "attributes": {
        "objectType": "ConfigurationPolicy"
    }
}
```
