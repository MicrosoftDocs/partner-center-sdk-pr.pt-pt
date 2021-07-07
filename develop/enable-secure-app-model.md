---
title: Ativar o modelo de aplicação seguro
description: Proteja o centro de parceiros e as aplicações do painel de controlo.
ms.date: 01/20/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-csp
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 5d35c0512ba8edcf3742ee69d38c699a9a8c16d2
ms.sourcegitcommit: d20e7d572fee09a83a4b23a92da7ff09cfebe75a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111906406"
---
# <a name="enabling-the-secure-application-model-framework"></a><span data-ttu-id="ddd5e-103">Enabling the Secure Application Model framework (Ativar a arquitetura do Modelo de Aplicação Segura)</span><span class="sxs-lookup"><span data-stu-id="ddd5e-103">Enabling the Secure Application Model framework</span></span>

<span data-ttu-id="ddd5e-104">A Microsoft está a introduzir uma estrutura segura e escalável para autenticar parceiros de soluções de nuvem (CSP) e fornecedores de painéis de controlo (CPV) através da arquitetura de autenticação multi-factor (MFA) Microsoft Azure Ative Directory.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-104">Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure Active Directory Multi-Factor Authentication (MFA) architecture.</span></span>

<span data-ttu-id="ddd5e-105">Pode utilizar o novo modelo para elevar a segurança para chamadas de integração da API do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-105">You can use the new model to elevate security for Partner Center API integration calls.</span></span> <span data-ttu-id="ddd5e-106">Isto ajudará todas as partes (incluindo Microsoft, parceiros CSP e CPVs) a proteger as suas infraestruturas e dados dos clientes contra riscos de segurança.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-106">This will help all parties (including Microsoft, CSP partners, and CPVs) to protect their infrastructure and customer data from security risks.</span></span>

## <a name="scope"></a><span data-ttu-id="ddd5e-107">Âmbito</span><span class="sxs-lookup"><span data-stu-id="ddd5e-107">Scope</span></span>

<span data-ttu-id="ddd5e-108">Este artigo diz respeito aos seguintes intervenientes:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-108">This article concerns the following actors:</span></span>

- <span data-ttu-id="ddd5e-109">CPVs</span><span class="sxs-lookup"><span data-stu-id="ddd5e-109">CPVs</span></span>
  - <span data-ttu-id="ddd5e-110">Um CPV é um fornecedor de software independente que desenvolve aplicações a serem utilizadas por parceiros CSP para integração com as APIs do Centro de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-110">A CPV is an independent software vendor that develops apps for use by CSP partners to integrate with Partner Center APIs.</span></span>
  - <span data-ttu-id="ddd5e-111">Um CPV não é um parceiro CSP com acesso direto ao dashboard ou às APIs do Centro de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-111">A CPV isn't a CSP partner with direct access to the Partner Center dashboard or APIs.</span></span>

- <span data-ttu-id="ddd5e-112">Os fornecedores indiretos da CSP e os parceiros diretos da CSP que estão a utilizar o ID + a autenticação do utilizador e a integrar-se diretamente com as APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-112">CSP indirect providers and CSP direct partners who are using app ID + user authentication and directly integrate with Partner Center APIs.</span></span>

## <a name="security-requirements"></a><span data-ttu-id="ddd5e-113">Requisitos de segurança</span><span class="sxs-lookup"><span data-stu-id="ddd5e-113">Security requirements</span></span>

<span data-ttu-id="ddd5e-114">Para obter informações sobre os requisitos de segurança, consulte [os Requisitos de Segurança do Parceiro.](/partner-center/partner-security-requirements)</span><span class="sxs-lookup"><span data-stu-id="ddd5e-114">For details on security requirements, see [Partner Security Requirements](/partner-center/partner-security-requirements).</span></span>

## <a name="secure-application-model"></a><span data-ttu-id="ddd5e-115">Modelo de aplicação segura</span><span class="sxs-lookup"><span data-stu-id="ddd5e-115">Secure Application Model</span></span>

<span data-ttu-id="ddd5e-116">As aplicações do marketplace precisam de personificar os privilégios dos parceiros CSP para chamar APIs da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-116">Marketplace applications need to impersonate CSP partner privileges to call Microsoft APIs.</span></span> <span data-ttu-id="ddd5e-117">Os ataques de segurança a estas aplicações sensíveis podem levar ao compromisso dos dados dos clientes.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-117">Security attacks on these sensitive applications can lead to the compromise of customer data.</span></span>

<span data-ttu-id="ddd5e-118">Para uma visão geral e detalhes sobre o novo quadro de autenticação, descarregue o [documento-quadro Do Modelo de Aplicação Segura.](https://assetsprod.microsoft.com/secure-application-model-guide.pdf)</span><span class="sxs-lookup"><span data-stu-id="ddd5e-118">For an overview and details of the new authentication framework, download the [Secure Application Model framework](https://assetsprod.microsoft.com/secure-application-model-guide.pdf) document.</span></span> <span data-ttu-id="ddd5e-119">Este documento abrange princípios e boas práticas para tornar as aplicações de mercado sustentáveis e robustas a partir de compromissos de segurança.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-119">This document covers principles and best practices to make marketplace applications sustainable and robust from security compromises.</span></span>

## <a name="samples"></a><span data-ttu-id="ddd5e-120">Amostras</span><span class="sxs-lookup"><span data-stu-id="ddd5e-120">Samples</span></span>

<span data-ttu-id="ddd5e-121">Os seguintes documentos de visão geral e código de amostra descrevem como os parceiros podem implementar o quadro do Modelo de Aplicação Segura:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-121">The following overview documents and sample code describe how partners can implement the Secure Application Model framework:</span></span>

- [<span data-ttu-id="ddd5e-122">Documento geral do CPV</span><span class="sxs-lookup"><span data-stu-id="ddd5e-122">CPV overview document</span></span>](https://assetsprod.microsoft.com/cpv-partner-application-overview.pdf)
- [<span data-ttu-id="ddd5e-123">Documento de visão geral da CSP</span><span class="sxs-lookup"><span data-stu-id="ddd5e-123">CSP overview document</span></span>](https://assetsprod.microsoft.com/csp-partner-application-overview.pdf)
- [<span data-ttu-id="ddd5e-124">.AMOSTRAS LÍQUIDAS</span><span class="sxs-lookup"><span data-stu-id="ddd5e-124">.NET Samples</span></span>](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
- [<span data-ttu-id="ddd5e-125">Amostras de Java</span><span class="sxs-lookup"><span data-stu-id="ddd5e-125">Java Samples</span></span>](https://github.com/microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model)

    [!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

- [<span data-ttu-id="ddd5e-126">Instruções e amostras de REPOUSO</span><span class="sxs-lookup"><span data-stu-id="ddd5e-126">REST instructions and samples</span></span>](#rest)
- [<span data-ttu-id="ddd5e-127">Instruções e amostras powerShell</span><span class="sxs-lookup"><span data-stu-id="ddd5e-127">PowerShell instructions and samples</span></span>](#powershell)

## <a name="rest"></a><span data-ttu-id="ddd5e-128">REST</span><span class="sxs-lookup"><span data-stu-id="ddd5e-128">REST</span></span>

<span data-ttu-id="ddd5e-129">Para então fazer chamadas REST com o quadro do Modelo de Aplicação Segura com código de amostra, siga estes passos:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-129">To to make REST calls with the Secure Application Model framework with sample code, follow these steps:</span></span>

1. [<span data-ttu-id="ddd5e-130">Criar uma aplicação Web</span><span class="sxs-lookup"><span data-stu-id="ddd5e-130">Create a web app</span></span>](#create-a-web-app)

2. [<span data-ttu-id="ddd5e-131">Obtenha um código de autorização</span><span class="sxs-lookup"><span data-stu-id="ddd5e-131">Get an authorization code</span></span>](#get-authorization-code)

3. [<span data-ttu-id="ddd5e-132">Obter um token refrescante</span><span class="sxs-lookup"><span data-stu-id="ddd5e-132">Get a refresh token</span></span>](#get-refresh-token)

4. [<span data-ttu-id="ddd5e-133">Obter um token de acesso</span><span class="sxs-lookup"><span data-stu-id="ddd5e-133">Get an access token</span></span>](#get-access-token)

5. [<span data-ttu-id="ddd5e-134">Faça uma chamada à API do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="ddd5e-134">Make a Partner Center API call</span></span>](#make-partner-center-api-calls)

> [!TIP]
> <span data-ttu-id="ddd5e-135">Pode utilizar o módulo Partner Center PowerShell para obter um código de autorização e um token de atualização.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-135">You can use the Partner Center PowerShell module to get an authorization code and a refresh token.</span></span> <span data-ttu-id="ddd5e-136">Pode escolher esta opção no lugar dos passos 2 e 3.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-136">You can choose this option in place of steps 2 and 3.</span></span> <span data-ttu-id="ddd5e-137">Para obter mais informações, consulte a [secção PowerShell e os exemplos](#powershell).</span><span class="sxs-lookup"><span data-stu-id="ddd5e-137">For more information, see the [PowerShell section and examples](#powershell).</span></span>

### <a name="create-a-web-app"></a><span data-ttu-id="ddd5e-138">Criar uma aplicação Web</span><span class="sxs-lookup"><span data-stu-id="ddd5e-138">Create a web app</span></span>

<span data-ttu-id="ddd5e-139">Tem de criar e registar uma aplicação web no Partner Center antes de e fazer chamadas REST.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-139">You must create and register a web app in Partner Center before making REST calls.</span></span>

1. <span data-ttu-id="ddd5e-140">Inicie sessão no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ddd5e-140">Sign in to the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="ddd5e-141">Crie uma aplicação Azure Ative Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="ddd5e-141">Create an Azure Active Directory (Azure AD) app.</span></span>

3. <span data-ttu-id="ddd5e-142">Forneça permissões de candidatura delegadas aos seguintes recursos, *dependendo dos requisitos da sua aplicação.*</span><span class="sxs-lookup"><span data-stu-id="ddd5e-142">Give delegated application permissions to the following resources, *depending on your application's requirements*.</span></span> <span data-ttu-id="ddd5e-143">Se necessário, pode adicionar mais permissões delegadas para recursos de aplicação.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-143">If necessary, you can add more delegated permissions for application resources.</span></span>

   1. <span data-ttu-id="ddd5e-144">**Microsoft Partner Center** (alguns inquilinos mostram isto como **SampleBECApp)**</span><span class="sxs-lookup"><span data-stu-id="ddd5e-144">**Microsoft Partner Center** (some tenants show this as **SampleBECApp**)</span></span>

   2. <span data-ttu-id="ddd5e-145">**APIs de gestão de Azure** (se estiver a planear ligar para a Azure APIs)</span><span class="sxs-lookup"><span data-stu-id="ddd5e-145">**Azure Management APIs** (if you are planning to call Azure APIs)</span></span>

   3. <span data-ttu-id="ddd5e-146">**Microsoft Azure Active Directory**</span><span class="sxs-lookup"><span data-stu-id="ddd5e-146">**Windows Azure Active Directory**</span></span>

4. <span data-ttu-id="ddd5e-147">Certifique-se de que o URL inicial da sua aplicação está definido para um ponto final onde uma aplicação web ao vivo está em execução.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-147">Make sure that the home URL of your app is set to an endpoint where a live web app is running.</span></span> <span data-ttu-id="ddd5e-148">Esta aplicação terá de aceitar o código de [autorização](#get-authorization-code) a partir da chamada de login Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-148">This app will need to accept the [authorization code](#get-authorization-code) from the Azure AD login call.</span></span> <span data-ttu-id="ddd5e-149">Por exemplo, no código de exemplo na [secção seguinte,](#get-authorization-code)a aplicação web está em execução `https://localhost:44395/` em .</span><span class="sxs-lookup"><span data-stu-id="ddd5e-149">For example, in the example code in [the following section](#get-authorization-code), the web app is running at `https://localhost:44395/`.</span></span>

5. <span data-ttu-id="ddd5e-150">Note as seguintes informações a partir das definições da sua aplicação web em Azure AD:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-150">Note the following information from your web app's settings in Azure AD:</span></span>

   - <span data-ttu-id="ddd5e-151">ID da aplicação</span><span class="sxs-lookup"><span data-stu-id="ddd5e-151">Application ID</span></span>
   - <span data-ttu-id="ddd5e-152">Segredo da aplicação</span><span class="sxs-lookup"><span data-stu-id="ddd5e-152">Application secret</span></span>

> [!NOTE]
> <span data-ttu-id="ddd5e-153">Recomenda-se a [utilização de um certificado como segredo de aplicação.](/azure/active-directory/develop/active-directory-certificate-credentials)</span><span class="sxs-lookup"><span data-stu-id="ddd5e-153">It is recommended to [use a certificate as your application secret](/azure/active-directory/develop/active-directory-certificate-credentials).</span></span> <span data-ttu-id="ddd5e-154">No entanto, também pode criar uma chave de aplicação no portal Azure.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-154">However, you can also create an application key in the Azure portal.</span></span> <span data-ttu-id="ddd5e-155">O código [de](#get-authorization-code) amostra na secção seguinte utiliza uma chave de aplicação.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-155">The sample code in [the following section](#get-authorization-code) uses an application key.</span></span>

### <a name="get-authorization-code"></a><span data-ttu-id="ddd5e-156">Obter código de autorização</span><span class="sxs-lookup"><span data-stu-id="ddd5e-156">Get authorization code</span></span>

<span data-ttu-id="ddd5e-157">Tem de obter um código de autorização para que a sua aplicação web aceite a partir da chamada de login Azure AD:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-157">You must get an authorization code for your web app to accept from the Azure AD login call:</span></span>

1. <span data-ttu-id="ddd5e-158">Faça login no Azure AD no seguinte URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1) .</span><span class="sxs-lookup"><span data-stu-id="ddd5e-158">Log in to Azure AD at the following URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1).</span></span> <span data-ttu-id="ddd5e-159">Certifique-se de que faz login na conta de utilizador a partir da qual fará chamadas API do Partner Center (como um agente administrativo ou conta de agente de vendas).</span><span class="sxs-lookup"><span data-stu-id="ddd5e-159">Be sure to log in with the user account from which you will make Partner Center API calls (such as an admin agent or sales agent account).</span></span>

2. <span data-ttu-id="ddd5e-160">Substitua **o ID da aplicação Ad** (GUID) pela aplicação Azure.id.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-160">Replace **Application-Id** with your Azure AD app ID (GUID).</span></span>

3. <span data-ttu-id="ddd5e-161">Quando solicitado, inicie sessão com a sua conta de utilizador com MFA configurada.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-161">When prompted, log in with your user account with MFA configured.</span></span>

4. <span data-ttu-id="ddd5e-162">Quando solicitado, introduza informações adicionais de MFA (número de telefone ou endereço de e-mail) para verificar o seu login.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-162">When prompted, enter additional MFA information (phone number or email address) to verify your login.</span></span>

5. <span data-ttu-id="ddd5e-163">Depois de iniciar sessão, o navegador irá redirecionar a chamada para o ponto final da sua aplicação web com o seu código de autorização.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-163">After you are logged in, the browser will redirect the call to your web app endpoint with your authorization code.</span></span> <span data-ttu-id="ddd5e-164">Por exemplo, o seguinte código de amostra redireciona para `https://localhost:44395/` .</span><span class="sxs-lookup"><span data-stu-id="ddd5e-164">For example, the following sample code redirects to `https://localhost:44395/`.</span></span>

#### <a name="authorization-code-call-trace"></a><span data-ttu-id="ddd5e-165">Traço de chamada de código de autorização</span><span class="sxs-lookup"><span data-stu-id="ddd5e-165">Authorization code call trace</span></span>

```http
POST https://localhost:44395/ HTTP/1.1
Origin: https://login.microsoftonline.com
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Referrer: https://login.microsoftonline.com/kmsi
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Cookie: OpenIdConnect.nonce.hOMjjrivcxzuI4YqAw4uYC%2F%2BILFk4%2FCx3kHTHP3lBvA%3D=dHVyRXdlbk9WVUZFdlFONVdiY01nNEpUc0JRR0RiYWFLTHhQYlRGNl9VeXJqNjdLTGV3cFpIWFg1YmpnWVdQUURtN0dvMkdHS2kzTm02NGdQS09veVNEbTZJMDk1TVVNYkczYmstQmlKUzFQaTBFMEdhNVJGVHlES2d3WGlCSlVlN1c2UE9sd2kzckNrVGN2RFNULWdHY2JET3RDQUxSaXRfLXZQdG00RnlUM0E1TUo1YWNKOWxvQXRwSkhRYklQbmZUV3d3eHVfNEpMUUthMFlQUFgzS01RS2NvMXYtbnV4UVJOYkl4TTN0cw%3D%3D

code=AuthorizationCodeValue&id_token=IdTokenValue&<rest of properties for state>
```

### <a name="get-refresh-token"></a><span data-ttu-id="ddd5e-166">Obter token refresh</span><span class="sxs-lookup"><span data-stu-id="ddd5e-166">Get refresh token</span></span>

<span data-ttu-id="ddd5e-167">Em seguida, deve utilizar o seu código de autorização para obter um token de atualização:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-167">You must then use your authorization code to get a refresh token:</span></span>

1. <span data-ttu-id="ddd5e-168">Faça uma chamada POST para o ponto final de login Azure AD `https://login.microsoftonline.com/CSPTenantID/oauth2/token` com o código de autorização.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-168">Make a POST call to the Azure AD login endpoint `https://login.microsoftonline.com/CSPTenantID/oauth2/token` with the authorization code.</span></span> <span data-ttu-id="ddd5e-169">Por exemplo, consulte a seguinte [chamada de amostra](#sample-refresh-call).</span><span class="sxs-lookup"><span data-stu-id="ddd5e-169">For an example, see the following [sample call](#sample-refresh-call).</span></span>

2. <span data-ttu-id="ddd5e-170">Reparem no token de atualização que é devolvido.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-170">Note the refresh token that is returned.</span></span>

3. <span data-ttu-id="ddd5e-171">Guarde o token refresh no Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-171">Store the refresh token in Azure Key Vault.</span></span> <span data-ttu-id="ddd5e-172">Para mais informações, consulte a documentação da [API key Vault](/rest/api/keyvault/).</span><span class="sxs-lookup"><span data-stu-id="ddd5e-172">For more information, see the [Key Vault API documentation](/rest/api/keyvault/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ddd5e-173">O token de atualização deve ser [armazenado como um segredo](/rest/api/keyvault/setsecret/setsecret) no Key Vault.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-173">The refresh token must be [stored as a secret](/rest/api/keyvault/setsecret/setsecret) in Key Vault.</span></span>

#### <a name="sample-refresh-call"></a><span data-ttu-id="ddd5e-174">Chamada de atualização de amostra</span><span class="sxs-lookup"><span data-stu-id="ddd5e-174">Sample refresh call</span></span>

<span data-ttu-id="ddd5e-175">Pedido de espaço reservado:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-175">Placeholder request:</span></span>

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 966
Expect: 100-continue
```

<span data-ttu-id="ddd5e-176">Corpo do pedido:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-176">Request body:</span></span>

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id&client_secret=Application-Secret&grant_type=authorization_code&code=AuthorizationCodeValue
```

<span data-ttu-id="ddd5e-177">Resposta do espaço reservado:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-177">Placeholder response:</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

<span data-ttu-id="ddd5e-178">Corpo de resposta:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-178">Response body:</span></span>

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3599","ext_expires_in":"3599","expires_on":"1547579127","not_before":"1547575227","resource":"https://api.partnercenter.microsoft.com","access_token":"Access
```

### <a name="get-access-token"></a><span data-ttu-id="ddd5e-179">Obter ficha de acesso</span><span class="sxs-lookup"><span data-stu-id="ddd5e-179">Get access token</span></span>

<span data-ttu-id="ddd5e-180">Tem de obter um token de acesso antes de poder fazer chamadas para as APIs do Centro de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-180">You must obtain an access token before you can make calls to the Partner Center APIs.</span></span> <span data-ttu-id="ddd5e-181">Você deve usar um token de atualização para obter um token de acesso porque os tokens de acesso geralmente têm uma vida útil muito limitada (por exemplo, menos de uma hora).</span><span class="sxs-lookup"><span data-stu-id="ddd5e-181">You must use a refresh token to obtain an access token because access tokens generally have a very limited lifetime (for example, less than an hour).</span></span>

<span data-ttu-id="ddd5e-182">Pedido de espaço reservado:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-182">Placeholder request:</span></span>

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 1212
Expect: 100-continue
```

<span data-ttu-id="ddd5e-183">Corpo do pedido:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-183">Request body:</span></span>

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id &client_secret= Application-Secret&grant_type=refresh_token&refresh_token=RefreshTokenVlaue&scope=openid
```

<span data-ttu-id="ddd5e-184">Resposta do espaço reservado:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-184">Placeholder response:</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

<span data-ttu-id="ddd5e-185">Corpo de resposta:</span><span class="sxs-lookup"><span data-stu-id="ddd5e-185">Response body:</span></span>

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3600","ext_expires_in":"3600","expires_on":"1547581389","not_before":"1547577489","resource":"https://api.partnercenter.microsoft.com","access_token":"AccessTokenValue","id_token":"IDTokenValue"}
```

### <a name="make-partner-center-api-calls"></a><span data-ttu-id="ddd5e-186">Faça chamadas API do Centro Parceiro</span><span class="sxs-lookup"><span data-stu-id="ddd5e-186">Make Partner Center API calls</span></span>

<span data-ttu-id="ddd5e-187">Você deve usar o seu token de acesso para ligar para as APIs do Centro Parceiro.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-187">You must use your access token to call the Partner Center APIs.</span></span> <span data-ttu-id="ddd5e-188">Consulte a chamada de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-188">See the following example call.</span></span>

#### <a name="example-partner-center-api-call"></a><span data-ttu-id="ddd5e-189">Chamada API do Centro parceiro de exemplo</span><span class="sxs-lookup"><span data-stu-id="ddd5e-189">Example Partner Center API call</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/CustomerTenantId/users HTTP/1.1
Authorization: Bearer AccessTokenValue
Accept: application/json
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="powershell"></a><span data-ttu-id="ddd5e-190">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddd5e-190">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="ddd5e-191">Pode utilizar o [módulo PowerShell do Partner Center](https://www.powershellgallery.com/packages/PartnerCenter) para reduzir a infraestrutura necessária para trocar um código de autorização para um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-191">You can use the [Partner Center PowerShell module](https://www.powershellgallery.com/packages/PartnerCenter) to reduce the required infrastructure to exchange an authorization code for an access token.</span></span> <span data-ttu-id="ddd5e-192">Este método é opcional para fazer [chamadas de Partner Center REST](#rest).</span><span class="sxs-lookup"><span data-stu-id="ddd5e-192">This method is optional for making [Partner Center REST calls](#rest).</span></span>

<span data-ttu-id="ddd5e-193">Para obter mais informações sobre este processo, consulte a documentação [Secure App Model](/powershell/partnercenter/secure-app-model) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-193">For more information on this process, see [Secure App Model](/powershell/partnercenter/secure-app-model) PowerShell documentation.</span></span>

1. <span data-ttu-id="ddd5e-194">Instale os módulos AD AD e Partner Center PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-194">Install the Azure AD and Partner Center PowerShell modules.</span></span>

    ```powershell
    Install-Module AzureAD
    ```

    ```powershell
    Install-Module PartnerCenter
    ```

2. <span data-ttu-id="ddd5e-195">Utilize o comando **[New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** para executar o processo de consentimento e capturar o token de atualização necessário.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-195">Use the **[New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** command to perform the consent process and capture the required refresh token.</span></span>

    ```powershell
    $credential = Get-Credential

    New-PartnerAccessToken -ApplicationId 'xxxx-xxxx-xxxx-xxxx' -Scopes 'https://api.partnercenter.microsoft.com/user_impersonation' -ServicePrincipal -Credential $credential -Tenant 'yyyy-yyyy-yyyy-yyyy' -UseAuthorizationCode
    ```

    > [!NOTE]
    > <span data-ttu-id="ddd5e-196">O parâmetro **ServicePrincipal** é utilizado com o comando **New-PartnerAccessToken** porque está a ser utilizada uma aplicação AD Azure com um tipo de **Web/API.**</span><span class="sxs-lookup"><span data-stu-id="ddd5e-196">The **ServicePrincipal** parameter is used with the **New-PartnerAccessToken** command because an Azure AD app with a type of **Web/API** is being used.</span></span> <span data-ttu-id="ddd5e-197">Este tipo de aplicação requer que um identificador de clientes e segredo seja incluído no pedido de token de acesso.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-197">This type of app requires that a client identifier and secret be included in the access token request.</span></span> <span data-ttu-id="ddd5e-198">Quando o comando **Get-Credential** for invocado, será solicitado que introduza um nome de utilizador e senha.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-198">When the **Get-Credential** command is invoked, you will be prompted to enter a username and password.</span></span> <span data-ttu-id="ddd5e-199">Introduza o identificador de aplicação como o nome de utilizador.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-199">Enter the application identifier as the username.</span></span> <span data-ttu-id="ddd5e-200">Insira o segredo da aplicação como senha.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-200">Enter the application secret as the password.</span></span> <span data-ttu-id="ddd5e-201">Quando o comando **New-PartnerAccessToken** for invocado, será solicitado a introduzir novamente credenciais.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-201">When the **New-PartnerAccessToken** command is invoked, you will be prompted to enter credentials again.</span></span> <span data-ttu-id="ddd5e-202">Insira as credenciais para a conta de serviço que está a usar.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-202">Enter the credentials for the service account that you are using.</span></span> <span data-ttu-id="ddd5e-203">Esta conta de serviço deve ser uma conta parceira com permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-203">This service account should be a partner account with appropriate permissions.</span></span>

3. <span data-ttu-id="ddd5e-204">Copie o valor simbólico da atualização.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-204">Copy the refresh token value.</span></span>

    ```powershell
    $token.RefreshToken | clip
    ```

<span data-ttu-id="ddd5e-205">Deve armazenar o valor simbólico da atualização num repositório seguro, como o Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="ddd5e-205">You should store the refresh token value in a secure repository, such as Azure Key Vault.</span></span> <span data-ttu-id="ddd5e-206">Para obter mais informações sobre como alavancar o módulo de aplicação seguro com o PowerShell, consulte o artigo [de autenticação de vários fatores.](/powershell/partnercenter/multi-factor-auth)</span><span class="sxs-lookup"><span data-stu-id="ddd5e-206">For more information on how to leverage the secure application module with PowerShell, see the [multi-factor authentication](/powershell/partnercenter/multi-factor-auth) article.</span></span>
