---
title: Criar uma transferência
description: Como criar uma transferência de subscrições para um cliente.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d459a0a96912ab27f312bc73af16af2d4fdb518c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973711"
---
# <a name="create-a-transfer"></a><span data-ttu-id="48e6d-103">Criar uma transferência</span><span class="sxs-lookup"><span data-stu-id="48e6d-103">Create a transfer</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48e6d-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="48e6d-104">Prerequisites</span></span>

- <span data-ttu-id="48e6d-105">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="48e6d-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="48e6d-106">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="48e6d-106">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="48e6d-107">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="48e6d-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="48e6d-108">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="48e6d-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="48e6d-109">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="48e6d-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="48e6d-110">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="48e6d-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="48e6d-111">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="48e6d-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="48e6d-112">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="48e6d-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="48e6d-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="48e6d-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="48e6d-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="48e6d-114">Request syntax</span></span>

| <span data-ttu-id="48e6d-115">Método</span><span class="sxs-lookup"><span data-stu-id="48e6d-115">Method</span></span>   | <span data-ttu-id="48e6d-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="48e6d-116">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="48e6d-117">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="48e6d-117">**POST**</span></span> | <span data-ttu-id="48e6d-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="48e6d-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="48e6d-119">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="48e6d-119">URI parameter</span></span>

<span data-ttu-id="48e6d-120">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="48e6d-120">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="48e6d-121">Nome</span><span class="sxs-lookup"><span data-stu-id="48e6d-121">Name</span></span>            | <span data-ttu-id="48e6d-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="48e6d-122">Type</span></span>     | <span data-ttu-id="48e6d-123">Necessário</span><span class="sxs-lookup"><span data-stu-id="48e6d-123">Required</span></span> | <span data-ttu-id="48e6d-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="48e6d-124">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="48e6d-125">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="48e6d-125">**customer-id**</span></span> | <span data-ttu-id="48e6d-126">string</span><span class="sxs-lookup"><span data-stu-id="48e6d-126">string</span></span>   | <span data-ttu-id="48e6d-127">Yes</span><span class="sxs-lookup"><span data-stu-id="48e6d-127">Yes</span></span>      | <span data-ttu-id="48e6d-128">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="48e6d-128">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="48e6d-129">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="48e6d-129">Request headers</span></span>

<span data-ttu-id="48e6d-130">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="48e6d-130">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="48e6d-131">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="48e6d-131">Request body</span></span>

<span data-ttu-id="48e6d-132">Esta tabela descreve as propriedades da [Entidade transferina](transfer-entity-resources.md) no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="48e6d-132">This table describes the [TransferEntity](transfer-entity-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="48e6d-133">Propriedade</span><span class="sxs-lookup"><span data-stu-id="48e6d-133">Property</span></span>              | <span data-ttu-id="48e6d-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="48e6d-134">Type</span></span>          | <span data-ttu-id="48e6d-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="48e6d-135">Required</span></span>  | <span data-ttu-id="48e6d-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="48e6d-136">Description</span></span>                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="48e6d-137">ID</span><span class="sxs-lookup"><span data-stu-id="48e6d-137">id</span></span>                    | <span data-ttu-id="48e6d-138">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-138">string</span></span>        | <span data-ttu-id="48e6d-139">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-139">No</span></span>    | <span data-ttu-id="48e6d-140">Um identificador de entidade de transferência que é fornecido após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-140">A transferEntity identifier that is supplied upon successful creation of the transferEntity.</span></span>                               |
| <span data-ttu-id="48e6d-141">createdTime</span><span class="sxs-lookup"><span data-stu-id="48e6d-141">createdTime</span></span>           | <span data-ttu-id="48e6d-142">DateTime</span><span class="sxs-lookup"><span data-stu-id="48e6d-142">DateTime</span></span>      | <span data-ttu-id="48e6d-143">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-143">No</span></span>    | <span data-ttu-id="48e6d-144">A data em que a Entidade de Transferência foi criada, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="48e6d-144">The date the transferEntity was created, in date-time format.</span></span> <span data-ttu-id="48e6d-145">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-145">Applied upon successful creation of the transferEntity.</span></span>      |
| <span data-ttu-id="48e6d-146">última Hora DaModified</span><span class="sxs-lookup"><span data-stu-id="48e6d-146">lastModifiedTime</span></span>      | <span data-ttu-id="48e6d-147">DateTime</span><span class="sxs-lookup"><span data-stu-id="48e6d-147">DateTime</span></span>      | <span data-ttu-id="48e6d-148">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-148">No</span></span>    | <span data-ttu-id="48e6d-149">A data em que a Entidade de Transferência foi atualizada pela última vez, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="48e6d-149">The date the transferEntity was last updated, in date-time format.</span></span> <span data-ttu-id="48e6d-150">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-150">Applied upon successful creation of the transferEntity.</span></span> |
| <span data-ttu-id="48e6d-151">últimoModifiedUser</span><span class="sxs-lookup"><span data-stu-id="48e6d-151">lastModifiedUser</span></span>      | <span data-ttu-id="48e6d-152">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-152">string</span></span>        | <span data-ttu-id="48e6d-153">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-153">No</span></span>    | <span data-ttu-id="48e6d-154">O utilizador que atualizou pela última vez a Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-154">The user who last updated the transferEntity.</span></span> <span data-ttu-id="48e6d-155">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-155">Applied upon successful creation of transferEntity.</span></span>                          |
| <span data-ttu-id="48e6d-156">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="48e6d-156">customerName</span></span>          | <span data-ttu-id="48e6d-157">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-157">string</span></span>        | <span data-ttu-id="48e6d-158">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-158">No</span></span>    | <span data-ttu-id="48e6d-159">Opcional.</span><span class="sxs-lookup"><span data-stu-id="48e6d-159">Optional.</span></span> <span data-ttu-id="48e6d-160">O nome do cliente cujas assinaturas estão a ser transferidas.</span><span class="sxs-lookup"><span data-stu-id="48e6d-160">The name of the customer whose subscriptions are being transferred.</span></span>                                              |
| <span data-ttu-id="48e6d-161">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="48e6d-161">customerTenantId</span></span>      | <span data-ttu-id="48e6d-162">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-162">string</span></span>        | <span data-ttu-id="48e6d-163">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-163">No</span></span>    | <span data-ttu-id="48e6d-164">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="48e6d-164">A GUID formatted customer-id that identifies the customer.</span></span> <span data-ttu-id="48e6d-165">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-165">Applied upon successful creation of the transferEntity.</span></span>         |
| <span data-ttu-id="48e6d-166">partnertenantid</span><span class="sxs-lookup"><span data-stu-id="48e6d-166">partnertenantid</span></span>       | <span data-ttu-id="48e6d-167">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-167">string</span></span>        | <span data-ttu-id="48e6d-168">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-168">No</span></span>    | <span data-ttu-id="48e6d-169">Um parceiro-id formatado GUID que identifica o parceiro.</span><span class="sxs-lookup"><span data-stu-id="48e6d-169">A GUID formatted partner-id that identifies the partner.</span></span>                                                                   |
| <span data-ttu-id="48e6d-170">fontePartnerName</span><span class="sxs-lookup"><span data-stu-id="48e6d-170">sourcePartnerName</span></span>     | <span data-ttu-id="48e6d-171">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-171">string</span></span>        | <span data-ttu-id="48e6d-172">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-172">No</span></span>    | <span data-ttu-id="48e6d-173">Opcional.</span><span class="sxs-lookup"><span data-stu-id="48e6d-173">Optional.</span></span> <span data-ttu-id="48e6d-174">O nome da organização do parceiro que está a iniciar a transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-174">The name of the partner's organization who is initiating the transfer.</span></span>                                           |
| <span data-ttu-id="48e6d-175">sourcePartnerTenantId</span><span class="sxs-lookup"><span data-stu-id="48e6d-175">sourcePartnerTenantId</span></span> | <span data-ttu-id="48e6d-176">string</span><span class="sxs-lookup"><span data-stu-id="48e6d-176">string</span></span>        | <span data-ttu-id="48e6d-177">Yes</span><span class="sxs-lookup"><span data-stu-id="48e6d-177">Yes</span></span>   | <span data-ttu-id="48e6d-178">Um parceiro-id formatado GUID que identifica o parceiro que inicia a transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-178">A GUID formatted partner-id that identifies the partner initiating the transfer.</span></span>                                           |
| <span data-ttu-id="48e6d-179">targetPartnerName</span><span class="sxs-lookup"><span data-stu-id="48e6d-179">targetPartnerName</span></span>     | <span data-ttu-id="48e6d-180">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-180">string</span></span>        | <span data-ttu-id="48e6d-181">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-181">No</span></span>    | <span data-ttu-id="48e6d-182">Opcional.</span><span class="sxs-lookup"><span data-stu-id="48e6d-182">Optional.</span></span> <span data-ttu-id="48e6d-183">O nome da organização do parceiro a quem a transferência é dirigida.</span><span class="sxs-lookup"><span data-stu-id="48e6d-183">The name of the partner's organization to whom the transfer is targeted.</span></span>                                         |
| <span data-ttu-id="48e6d-184">targetPartnerTenantId</span><span class="sxs-lookup"><span data-stu-id="48e6d-184">targetPartnerTenantId</span></span> | <span data-ttu-id="48e6d-185">string</span><span class="sxs-lookup"><span data-stu-id="48e6d-185">string</span></span>        | <span data-ttu-id="48e6d-186">Yes</span><span class="sxs-lookup"><span data-stu-id="48e6d-186">Yes</span></span>   | <span data-ttu-id="48e6d-187">Um parceiro-id formatado GUID que identifica o parceiro a quem a transferência é alvo.</span><span class="sxs-lookup"><span data-stu-id="48e6d-187">A GUID formatted partner-id that identifies the partner to whom the transfer is targeted.</span></span>                                  |
| <span data-ttu-id="48e6d-188">lineitems</span><span class="sxs-lookup"><span data-stu-id="48e6d-188">lineItems</span></span>             | <span data-ttu-id="48e6d-189">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="48e6d-189">Array of objects</span></span> | <span data-ttu-id="48e6d-190">Yes</span><span class="sxs-lookup"><span data-stu-id="48e6d-190">Yes</span></span>| <span data-ttu-id="48e6d-191">Uma matriz de recursos [TransferLineItem.](transfer-entity-resources.md#transferlineitem)</span><span class="sxs-lookup"><span data-stu-id="48e6d-191">An Array of [TransferLineItem](transfer-entity-resources.md#transferlineitem) resources.</span></span>                                   |
| <span data-ttu-id="48e6d-192">status</span><span class="sxs-lookup"><span data-stu-id="48e6d-192">status</span></span>                | <span data-ttu-id="48e6d-193">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-193">string</span></span>        | <span data-ttu-id="48e6d-194">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-194">No</span></span>    | <span data-ttu-id="48e6d-195">O estado da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-195">The status of the transferEntity.</span></span> <span data-ttu-id="48e6d-196">Os valores possíveis são "Ative" (pode ser eliminado/submetido) e "Concluído" (já foi concluído).</span><span class="sxs-lookup"><span data-stu-id="48e6d-196">Possible values are "Active" (can be deleted/submitted) and "Completed" (has already been completed).</span></span> <span data-ttu-id="48e6d-197">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-197">Applied upon successful creation of the transferEntity.</span></span>|

<span data-ttu-id="48e6d-198">Esta tabela descreve as propriedades [transferLineItem](transfer-entity-resources.md#transferlineitem) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="48e6d-198">This table describes the [TransferLineItem](transfer-entity-resources.md#transferlineitem) properties in the request body.</span></span>

|      <span data-ttu-id="48e6d-199">Propriedade</span><span class="sxs-lookup"><span data-stu-id="48e6d-199">Property</span></span>       |            <span data-ttu-id="48e6d-200">Tipo</span><span class="sxs-lookup"><span data-stu-id="48e6d-200">Type</span></span>             | <span data-ttu-id="48e6d-201">Necessário</span><span class="sxs-lookup"><span data-stu-id="48e6d-201">Required</span></span> | <span data-ttu-id="48e6d-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="48e6d-202">Description</span></span>                                                                                     |
|---------------------|-----------------------------|----------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="48e6d-203">ID</span><span class="sxs-lookup"><span data-stu-id="48e6d-203">id</span></span>                   | <span data-ttu-id="48e6d-204">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-204">string</span></span>                     | <span data-ttu-id="48e6d-205">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-205">No</span></span>       | <span data-ttu-id="48e6d-206">Um identificador único para um item de linha de transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-206">A unique identifier for a transfer line item.</span></span> <span data-ttu-id="48e6d-207">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-207">Applied upon successful creation of the transferEntity.</span></span>|
| <span data-ttu-id="48e6d-208">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="48e6d-208">subscriptionId</span></span>       | <span data-ttu-id="48e6d-209">string</span><span class="sxs-lookup"><span data-stu-id="48e6d-209">string</span></span>                     | <span data-ttu-id="48e6d-210">Yes</span><span class="sxs-lookup"><span data-stu-id="48e6d-210">Yes</span></span>      | <span data-ttu-id="48e6d-211">O identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="48e6d-211">The subscription identifier.</span></span>                                                                         |
| <span data-ttu-id="48e6d-212">quantidade</span><span class="sxs-lookup"><span data-stu-id="48e6d-212">quantity</span></span>             | <span data-ttu-id="48e6d-213">int</span><span class="sxs-lookup"><span data-stu-id="48e6d-213">int</span></span>                        | <span data-ttu-id="48e6d-214">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-214">No</span></span>       | <span data-ttu-id="48e6d-215">O número de licenças ou instâncias.</span><span class="sxs-lookup"><span data-stu-id="48e6d-215">The number of licenses or instances.</span></span>                                                                 |
| <span data-ttu-id="48e6d-216">billingCycle</span><span class="sxs-lookup"><span data-stu-id="48e6d-216">billingCycle</span></span>         | <span data-ttu-id="48e6d-217">Objeto</span><span class="sxs-lookup"><span data-stu-id="48e6d-217">Object</span></span>                     | <span data-ttu-id="48e6d-218">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-218">No</span></span>       | <span data-ttu-id="48e6d-219">O tipo de ciclo de faturação definido para o período atual.</span><span class="sxs-lookup"><span data-stu-id="48e6d-219">The type of billing cycle set for the current period.</span></span>                                                |
| <span data-ttu-id="48e6d-220">nome amigável</span><span class="sxs-lookup"><span data-stu-id="48e6d-220">friendlyName</span></span>         | <span data-ttu-id="48e6d-221">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-221">string</span></span>                     | <span data-ttu-id="48e6d-222">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-222">No</span></span>       | <span data-ttu-id="48e6d-223">Opcional.</span><span class="sxs-lookup"><span data-stu-id="48e6d-223">Optional.</span></span> <span data-ttu-id="48e6d-224">O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="48e6d-224">The friendly name for the item defined by the partner to help disambiguate.</span></span>                |
| <span data-ttu-id="48e6d-225">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="48e6d-225">partnerIdOnRecord</span></span>    | <span data-ttu-id="48e6d-226">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-226">string</span></span>                     | <span data-ttu-id="48e6d-227">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-227">No</span></span>       | <span data-ttu-id="48e6d-228">PartnerId on Record (MPN ID) sobre a compra que acontece quando a transferência é aceite.</span><span class="sxs-lookup"><span data-stu-id="48e6d-228">PartnerId on Record (MPN ID) on the purchase that happens when the transfer is accepted.</span></span>              |
| <span data-ttu-id="48e6d-229">offerId</span><span class="sxs-lookup"><span data-stu-id="48e6d-229">offerId</span></span>              | <span data-ttu-id="48e6d-230">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-230">string</span></span>                     | <span data-ttu-id="48e6d-231">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-231">No</span></span>       | <span data-ttu-id="48e6d-232">O identificador da oferta.</span><span class="sxs-lookup"><span data-stu-id="48e6d-232">The offer identifier.</span></span>                                                                                |
| <span data-ttu-id="48e6d-233">addonItems</span><span class="sxs-lookup"><span data-stu-id="48e6d-233">addonItems</span></span>           | <span data-ttu-id="48e6d-234">Lista de objetos **TransferLineItem**</span><span class="sxs-lookup"><span data-stu-id="48e6d-234">List of **TransferLineItem** objects</span></span> | <span data-ttu-id="48e6d-235">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-235">No</span></span> | <span data-ttu-id="48e6d-236">Uma recolha de itens de linha da TransferEntity para addons que serão transferidos juntamente com a subscrição base que está a ser transferida.</span><span class="sxs-lookup"><span data-stu-id="48e6d-236">A collection of transferEntity line items for addons that will be transferred along with the base subscription that is being transferred.</span></span> <span data-ttu-id="48e6d-237">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-237">Applied upon successful creation of the transferEntity.</span></span>|
| <span data-ttu-id="48e6d-238">transferEror</span><span class="sxs-lookup"><span data-stu-id="48e6d-238">transferError</span></span>        | <span data-ttu-id="48e6d-239">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-239">string</span></span>                     | <span data-ttu-id="48e6d-240">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-240">No</span></span>       | <span data-ttu-id="48e6d-241">Aplicada após transferência A Entidade é aceite se houver um erro.</span><span class="sxs-lookup"><span data-stu-id="48e6d-241">Applied after transferEntity is accepted if there is an error.</span></span>                                        |
| <span data-ttu-id="48e6d-242">status</span><span class="sxs-lookup"><span data-stu-id="48e6d-242">status</span></span>               | <span data-ttu-id="48e6d-243">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="48e6d-243">string</span></span>                     | <span data-ttu-id="48e6d-244">No</span><span class="sxs-lookup"><span data-stu-id="48e6d-244">No</span></span>       | <span data-ttu-id="48e6d-245">O estado do lineitem na Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="48e6d-245">The status of the lineitem in the transferEntity.</span></span>                                                    |

### <a name="request-example"></a><span data-ttu-id="48e6d-246">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="48e6d-246">Request example</span></span>

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Expect: 100-continue

{
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lineItems": [
        {
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "partnerIdOnRecord": "517285"
        },
        {
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "partnerIdOnRecord": "517285"
        }
    ]
}
```

## <a name="rest-response"></a><span data-ttu-id="48e6d-247">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="48e6d-247">REST response</span></span>

<span data-ttu-id="48e6d-248">Se for bem sucedido, este método devolve o recurso [transferenity](transfer-entity-resources.md) povoado no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="48e6d-248">If successful, this method returns the populated [TransferEnity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="48e6d-249">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="48e6d-249">Response success and error codes</span></span>

<span data-ttu-id="48e6d-250">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="48e6d-250">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="48e6d-251">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="48e6d-251">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="48e6d-252">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="48e6d-252">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="48e6d-253">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="48e6d-253">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 138
Content-Type: application/json; charset=utf-8
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US,en-US
{
    "id": "67c5b05b-09b5-47ba-9047-5056fe2afa4f",
    "status": "Active",
    "createdTime": "2020-03-24T20:44:14.9602781Z",
    "lastModifiedTime": "2020-03-24T20:44:15Z",
    "customerTenantId": "823c6c3f-9259-4d51-bae2-5dd06743177f",
    "partnertenantid": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lastModifiedUser": "d0648481-b615-45c9-8cd1-ff87940dbdc4",
    "lineItems": [
        {
            "id": 0,
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "offerId": "50E9A47A-7B4D-4970-9D90-CAE927F53753",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 for Sales Enterprise Attach to Qualifying Dynamics 365 Base Offer",
            "quantity": 1,
            "addonItems": [
                {
                    "id": 0,
                    "subscriptionId": "D738C6C9-DDBD-46E9-B316-65F9D9B3ECB4",
                    "offerId": "2BCF9FE8-8B65-4FCF-9240-419203FB8CF4",
                    "billingCycle": "annual",
                    "friendlyName": "Dynamics 365 - Additional Production Instance (Qualified Offer)",
                    "quantity": 4
                }
            ]
        },
        {
            "id": 0,
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "offerId": "455DDD41-32ED-4E2D-B3A2-BBCB22CAA467",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 Customer Engagement Plan Patch",
            "quantity": 8,
            "addonItems": []
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "TransferEntity"
    }
}
```
