---
title: Loja Web para clientes CSP
description: Este código do site da amostra mostra uma loja online funcionando para os clientes comprarem subscrições de produtos Microsoft.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bd488b9b9bf2c1df4bebc8513d230a02b06b2ce4
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768798"
---
# <a name="csp-customer-web-storefront"></a><span data-ttu-id="f5568-103">Loja Web para clientes CSP</span><span class="sxs-lookup"><span data-stu-id="f5568-103">CSP customer web storefront</span></span>

<span data-ttu-id="f5568-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="f5568-104">**Applies to:**</span></span>

- <span data-ttu-id="f5568-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="f5568-105">Partner Center</span></span>

> [!NOTE]
> <span data-ttu-id="f5568-106">Esta aplicação de amostra aplica-se apenas à instância global do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f5568-106">This sample app applies only to the global instance of Partner Center.</span></span> <span data-ttu-id="f5568-107">Não se aplica ao Partner Center da Microsoft Cloud Germany ou ao Partner Center for Microsoft Cloud para o Governo dos EUA.</span><span class="sxs-lookup"><span data-stu-id="f5568-107">It does not apply to Partner Center for Microsoft Cloud Germany or to Partner Center for Microsoft Cloud for US Government.</span></span>

<span data-ttu-id="f5568-108">A [loja Partner Center](https://github.com/Microsoft/Partner-Center-Storefront) é um site de **amostras** para uma loja online que os clientes podem usar para comprar subscrições de produtos microsoft.</span><span class="sxs-lookup"><span data-stu-id="f5568-108">The [Partner Center storefront](https://github.com/Microsoft/Partner-Center-Storefront) is a **sample website** for an online store that customers can use to buy subscriptions to Microsoft products.</span></span> <span data-ttu-id="f5568-109">Pode modificar este **código de amostra** para seu próprio uso para [configurar as ofertas,](#configure-offers) [adicionar branding](#configure-branding) e adicionar um [método de pagamento](#configure-payment-types).</span><span class="sxs-lookup"><span data-stu-id="f5568-109">You can modify this **sample code** for your own use to [configure the offers](#configure-offers), [add branding](#configure-branding) and [add a payment method](#configure-payment-types).</span></span>

## <a name="sample-code"></a><span data-ttu-id="f5568-110">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="f5568-110">Sample code</span></span>

<span data-ttu-id="f5568-111">Descarregue o código de amostra da [loja Partner Center](https://github.com/Microsoft/Partner-Center-Storefront) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="f5568-111">Download the [Partner Center storefront sample code](https://github.com/Microsoft/Partner-Center-Storefront) from GitHub.</span></span>

## <a name="configure-authentication"></a><span data-ttu-id="f5568-112">Configurar a autenticação</span><span class="sxs-lookup"><span data-stu-id="f5568-112">Configure authentication</span></span>

<span data-ttu-id="f5568-113">Antes de construir a aplicação, atualize os seguintes valores no ficheiro Web.config para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="f5568-113">Before you build the application, update the following values in the Web.config file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f5568-114">Deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testes em produção (TiP).</span><span class="sxs-lookup"><span data-stu-id="f5568-114">You should use your integration sandbox account settings during early development or for testing in production (TiP).</span></span>

- <span data-ttu-id="f5568-115">**partnerCenter.applicationD**</span><span class="sxs-lookup"><span data-stu-id="f5568-115">**partnerCenter.applicationId**</span></span>
- <span data-ttu-id="f5568-116">**partnerCenter.applicationSecret**</span><span class="sxs-lookup"><span data-stu-id="f5568-116">**partnerCenter.applicationSecret**</span></span>
- <span data-ttu-id="f5568-117">**partnerCenter.domain**</span><span class="sxs-lookup"><span data-stu-id="f5568-117">**partnerCenter.domain**</span></span>
- <span data-ttu-id="f5568-118">**webPortal.clientId**</span><span class="sxs-lookup"><span data-stu-id="f5568-118">**webPortal.clientId**</span></span>
- <span data-ttu-id="f5568-119">**webPortal.clientSecret**</span><span class="sxs-lookup"><span data-stu-id="f5568-119">**webPortal.clientSecret**</span></span>
- <span data-ttu-id="f5568-120">**webPortal.domínio**</span><span class="sxs-lookup"><span data-stu-id="f5568-120">**webPortal.domain**</span></span>
- <span data-ttu-id="f5568-121">**webPortal.azureStorageConnectionString**</span><span class="sxs-lookup"><span data-stu-id="f5568-121">**webPortal.azureStorageConnectionString**</span></span>

## <a name="configure-offers"></a><span data-ttu-id="f5568-122">Configure ofertas</span><span class="sxs-lookup"><span data-stu-id="f5568-122">Configure offers</span></span>

<span data-ttu-id="f5568-123">Pode configurar o conjunto de ofertas **(MicrosoftOffer)** no **OfferCatalogViewModel**.</span><span class="sxs-lookup"><span data-stu-id="f5568-123">You can configure the set of offers (**MicrosoftOffer**) in the **OfferCatalogViewModel**.</span></span>

## <a name="configure-branding"></a><span data-ttu-id="f5568-124">Configurar a marca</span><span class="sxs-lookup"><span data-stu-id="f5568-124">Configure branding</span></span>

<span data-ttu-id="f5568-125">Este site de amostras acompanha as seguintes informações da empresa e da marca em *BrandingConfiguration.cs* e *PortalBranding.cs:*</span><span class="sxs-lookup"><span data-stu-id="f5568-125">This sample website tracks the following company and brand information in *BrandingConfiguration.cs* and *PortalBranding.cs*:</span></span>

- <span data-ttu-id="f5568-126">Nome da organização</span><span class="sxs-lookup"><span data-stu-id="f5568-126">Organization name</span></span>
- <span data-ttu-id="f5568-127">Logotipo da organização</span><span class="sxs-lookup"><span data-stu-id="f5568-127">Organization logo</span></span>
- <span data-ttu-id="f5568-128">Imagem de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="f5568-128">Header image</span></span>
- <span data-ttu-id="f5568-129">Acordo de privacidade</span><span class="sxs-lookup"><span data-stu-id="f5568-129">Privacy agreement</span></span>
- <span data-ttu-id="f5568-130">E-mail de contacto</span><span class="sxs-lookup"><span data-stu-id="f5568-130">Contact email</span></span>
- <span data-ttu-id="f5568-131">Número de telefone de contato</span><span class="sxs-lookup"><span data-stu-id="f5568-131">Contact phone number</span></span>
- <span data-ttu-id="f5568-132">E-mail de apoio</span><span class="sxs-lookup"><span data-stu-id="f5568-132">Support email</span></span>
- <span data-ttu-id="f5568-133">Número de telefone de suporte</span><span class="sxs-lookup"><span data-stu-id="f5568-133">Support phone number</span></span>

### <a name="configure-payment-types"></a><span data-ttu-id="f5568-134">Configurar tipos de pagamento</span><span class="sxs-lookup"><span data-stu-id="f5568-134">Configure payment types</span></span>

<span data-ttu-id="f5568-135">A aplicação utiliza atualmente um gateway PayPal, implementado em *PayPalGateway.cs.*</span><span class="sxs-lookup"><span data-stu-id="f5568-135">The app currently uses a PayPal gateway, implemented in *PayPalGateway.cs*.</span></span>