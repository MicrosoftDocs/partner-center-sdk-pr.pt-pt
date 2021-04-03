---
title: Criar um cliente
description: Saiba como um parceiro cloud Solution Provider (CSP) pode usar APIs do Partner Center para criar um novo cliente. O artigo descreve os pré-requisitos e o que mais acontece.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: bc8e9d38353511e747ba4da99b11be40d08781e3
ms.sourcegitcommit: faea78fe3264cbafc2b02c04d98d5ce30e992124
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274602"
---
# <a name="create-a-customer-using-partner-center-apis"></a><span data-ttu-id="47e55-104">Criar um cliente usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="47e55-104">Create a customer using Partner Center APIs</span></span>

<span data-ttu-id="47e55-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="47e55-105">**Applies to:**</span></span>

- <span data-ttu-id="47e55-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="47e55-106">Partner Center</span></span>
- <span data-ttu-id="47e55-107">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="47e55-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="47e55-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="47e55-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="47e55-109">Este artigo explica como criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-109">This article explains how to create a new customer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47e55-110">Se é um fornecedor indireto e pretende criar um cliente para um revendedor indireto, consulte [criar um cliente para um revendedor indireto.](create-a-customer-for-an-indirect-reseller.md)</span><span class="sxs-lookup"><span data-stu-id="47e55-110">If you are an indirect provider and you want to create a customer for an indirect reseller, please see [Create a customer for an indirect reseller](create-a-customer-for-an-indirect-reseller.md).</span></span>

<span data-ttu-id="47e55-111">Como parceiro de fornecedor de soluções em nuvem (CSP), quando criar um cliente pode fazer encomendas em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-111">As a cloud solution provider (CSP) partner, when you create a customer you can place orders on behalf of the customer.</span></span> <span data-ttu-id="47e55-112">Quando cria um cliente, também cria:</span><span class="sxs-lookup"><span data-stu-id="47e55-112">When you create a customer, you also create:</span></span>

- <span data-ttu-id="47e55-113">Um objeto de inquilino Azure Ative (AD) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-113">An Azure Active Directory (AD) tenant object for the customer.</span></span>

- <span data-ttu-id="47e55-114">Uma relação entre o revendedor e o cliente, usada para privilégios administrativos delegados.</span><span class="sxs-lookup"><span data-stu-id="47e55-114">A relationship between the reseller and customer, used for delegated admin privileges.</span></span>

- <span data-ttu-id="47e55-115">Um nome de utilizador e senha para iniciar sinscrônico para o cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-115">A user name and password to sign in as an admin for the customer.</span></span>

<span data-ttu-id="47e55-116">Uma vez criado o cliente, certifique-se de guardar os detalhes de ID e AD do cliente para utilização futura com o Partner Center SDK (por exemplo, gestão de conta).</span><span class="sxs-lookup"><span data-stu-id="47e55-116">Once the customer is created, be sure to save the customer ID and Azure AD details for future use with the Partner Center SDK (for example, account management).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47e55-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="47e55-117">Prerequisites</span></span>

- <span data-ttu-id="47e55-118">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="47e55-118">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="47e55-119">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="47e55-119">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47e55-120">Para criar um inquilino do cliente deve fornecer um endereço físico válido durante o processo de criação.</span><span class="sxs-lookup"><span data-stu-id="47e55-120">To create a customer tenant you must provide a valid physical address during the creation process.</span></span> <span data-ttu-id="47e55-121">Um endereço pode ser validado seguindo os passos descritos no cenário [de validação de um endereço.](validate-an-address.md)</span><span class="sxs-lookup"><span data-stu-id="47e55-121">An address can be validated by following the steps outlined in the [Validate an address](validate-an-address.md) scenario.</span></span> <span data-ttu-id="47e55-122">Se criar um cliente usando um endereço inválido no ambiente da caixa de areia, não poderá eliminar esse cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-122">If you create a customer using an invalid address in the sandbox environment, you will not be able to delete that customer tenant.</span></span>

## <a name="c"></a><span data-ttu-id="47e55-123">C\#</span><span class="sxs-lookup"><span data-stu-id="47e55-123">C\#</span></span>

<span data-ttu-id="47e55-124">Para adicionar um cliente:</span><span class="sxs-lookup"><span data-stu-id="47e55-124">To add a customer:</span></span>

1. <span data-ttu-id="47e55-125">Instantaneamente um novo objeto [**cliente.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer)</span><span class="sxs-lookup"><span data-stu-id="47e55-125">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object.</span></span> <span data-ttu-id="47e55-126">Certifique-se de preencher o [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) e [**o CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span><span class="sxs-lookup"><span data-stu-id="47e55-126">Be sure to fill in the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span>

2. <span data-ttu-id="47e55-127">Adicione o novo cliente à sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) chamando [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) ou [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync).</span><span class="sxs-lookup"><span data-stu-id="47e55-127">Add the new customer to your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection by calling [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync).</span></span>

### <a name="c-example"></a><span data-ttu-id="47e55-128">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="47e55-128">C\# example</span></span>

```csharp
// IAggregatePartner partnerOperations;

var partnerOperations = this.Context.UserPartnerOperations;

var customerToCreate = new Customer()
{
    CompanyProfile = new CustomerCompanyProfile()
    {
        Domain = string.Format(CultureInfo.InvariantCulture,
            "SampleApplication{0}.{1}",
            new Random().Next(),
            this.Context.Configuration.Scenario.CustomerDomainSuffix),
        //// OrganizationRegistrationNumber = "123456" // Please add if in specific country that requires
    },
    BillingProfile = new CustomerBillingProfile()
    {
        Culture = "EN-US",
        Email = "someone@example.com",
        Language = "En",
        CompanyName = "Some Company" + new Random().Next(),
        DefaultAddress = new Address()
        {
            FirstName = "Tania",
            MiddleName = "MiddleName",
            LastName = "Carr",
            AddressLine1 = "One Microsoft Way",
            City = "Redmond",
            State = "WA",
            Country = "US",
            PostalCode = "98052",
            PhoneNumber = ""
        }
    }
};

var newCustomer = partnerOperations.Customers.Create(customerToCreate);
```

<span data-ttu-id="47e55-129">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="47e55-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="47e55-130">**Projeto**: Partner Center SDK Samples **Class**: CreateCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="47e55-130">**Project**: Partner Center SDK Samples **Class**: CreateCustomer.cs</span></span>

## <a name="java"></a><span data-ttu-id="47e55-131">Java</span><span class="sxs-lookup"><span data-stu-id="47e55-131">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="47e55-132">Para criar um novo cliente:</span><span class="sxs-lookup"><span data-stu-id="47e55-132">To create a new customer:</span></span>

1. <span data-ttu-id="47e55-133">Crie uma nova instância do **CustomerBillingProfile** e dos objetos **CustomerCompanyProfile.**</span><span class="sxs-lookup"><span data-stu-id="47e55-133">Create a new instance of the **CustomerBillingProfile** and the **CustomerCompanyProfile** objects.</span></span> <span data-ttu-id="47e55-134">Certifique-se de povoar os campos necessários.</span><span class="sxs-lookup"><span data-stu-id="47e55-134">Be sure to populate the required fields.</span></span>

2. <span data-ttu-id="47e55-135">Crie o cliente chamando o **IAggregatePartner.getCustomers().criar** função.</span><span class="sxs-lookup"><span data-stu-id="47e55-135">Create the customer by calling the **IAggregatePartner.getCustomers().create** function.</span></span>

### <a name="java-example"></a><span data-ttu-id="47e55-136">Exemplo de Java</span><span class="sxs-lookup"><span data-stu-id="47e55-136">Java example</span></span>

```java
// IAggregatePartner partnerOperations;

Address address = new Address();

address.setFirstName( "Gena" );
address.setLastName( "Soto" );
address.setAddressLine1( "One Microsoft Way" );
address.setCity( "Redmond" );
address.setState( "WA" );
address.setCountry( "US" );
address.setPostalCode( "98052" );
address.setPhoneNumber( "4255550101" );

CustomerBillingProfile billingProfile = new CustomerBillingProfile();

billingProfile.setCulture( "en-US" );
billingProfile.setEmail( "gena@wingtiptoys.com" );
billingProfile.setLanguage( "en" );
billingProfile.setCompanyName( "Wingtip Toys" + new Random().nextInt() );
billingProfile.setDefaultAddress( address );

CustomerCompanyProfile companyProfile = new CustomerCompanyProfile();

companyProfile.setDomain( "WingtipToys" + Math.abs( new Random().nextInt() ) + ".onmicrosoft.com" );

Customer customerToCreate = new Customer();

customerToCreate.setBillingProfile( billingProfile );
customerToCreate.setCompanyProfile( companyProfile );

Customer newCustomer = partnerOperations.getCustomers().create( customerToCreate );
```

## <a name="powershell"></a><span data-ttu-id="47e55-137">PowerShell</span><span class="sxs-lookup"><span data-stu-id="47e55-137">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="47e55-138">Para criar um cliente execute o comando [**New-PartnerCustomer.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md)</span><span class="sxs-lookup"><span data-stu-id="47e55-138">To create a customer execute the [**New-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md) command.</span></span>

```powershell
New-PartnerCustomer -BillingAddressLine1 '1 Microsoft Way' -BillingAddressCity 'Redmond' -BillingAddressCountry 'US' -BillingAddressPostalCode '98052' -BillingAddressState 'WA' -ContactEmail 'jdoe@customer.com' -ContactFirstName 'Jane' -ContactLastName 'Doe' -Culture 'en-US' -Domain 'newcustomer.onmicrosoft.com' -Language 'en' -Name 'New Customer'
```

## <a name="rest-request"></a><span data-ttu-id="47e55-139">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="47e55-139">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="47e55-140">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="47e55-140">Request syntax</span></span>

| <span data-ttu-id="47e55-141">Método</span><span class="sxs-lookup"><span data-stu-id="47e55-141">Method</span></span>   | <span data-ttu-id="47e55-142">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="47e55-142">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="47e55-143">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="47e55-143">**POST**</span></span> | <span data-ttu-id="47e55-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="47e55-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="47e55-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="47e55-145">Request headers</span></span>

- <span data-ttu-id="47e55-146">Esta API é idempotente (não produzirá um resultado diferente se lhe chamar várias vezes).</span><span class="sxs-lookup"><span data-stu-id="47e55-146">This API is idempotent (it will not yield a different result if you call it multiple times).</span></span>

- <span data-ttu-id="47e55-147">É necessária uma identificação de pedido e uma identificação de correlação.</span><span class="sxs-lookup"><span data-stu-id="47e55-147">A request ID and correlation ID are required.</span></span>

- <span data-ttu-id="47e55-148">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="47e55-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="47e55-149">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="47e55-149">Request body</span></span>

<span data-ttu-id="47e55-150">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="47e55-150">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="47e55-151">Nome</span><span class="sxs-lookup"><span data-stu-id="47e55-151">Name</span></span>                              | <span data-ttu-id="47e55-152">Tipo</span><span class="sxs-lookup"><span data-stu-id="47e55-152">Type</span></span>   | <span data-ttu-id="47e55-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="47e55-153">Description</span></span>                                 |
|-----------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="47e55-154">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="47e55-154">BillingProfile</span></span>](#billing-profile) | <span data-ttu-id="47e55-155">objeto</span><span class="sxs-lookup"><span data-stu-id="47e55-155">object</span></span> | <span data-ttu-id="47e55-156">A informação do perfil de faturação do cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-156">The customer's billing profile information.</span></span> |
| [<span data-ttu-id="47e55-157">EmpresaProfile</span><span class="sxs-lookup"><span data-stu-id="47e55-157">CompanyProfile</span></span>](#company-profile) | <span data-ttu-id="47e55-158">objeto</span><span class="sxs-lookup"><span data-stu-id="47e55-158">object</span></span> | <span data-ttu-id="47e55-159">Informação do perfil da empresa do cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-159">The customer's company profile information.</span></span> |

#### <a name="billing-profile"></a><span data-ttu-id="47e55-160">Perfil de faturação</span><span class="sxs-lookup"><span data-stu-id="47e55-160">Billing profile</span></span>

<span data-ttu-id="47e55-161">Esta tabela descreve os campos mínimos exigidos do recurso [CustomerBillingProfile](customer-resources.md#customerbillingprofile) necessário para criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-161">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="47e55-162">Nome</span><span class="sxs-lookup"><span data-stu-id="47e55-162">Name</span></span>             | <span data-ttu-id="47e55-163">Tipo</span><span class="sxs-lookup"><span data-stu-id="47e55-163">Type</span></span>                                     | <span data-ttu-id="47e55-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="47e55-164">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="47e55-165">e-mail</span><span class="sxs-lookup"><span data-stu-id="47e55-165">email</span></span>            | <span data-ttu-id="47e55-166">string</span><span class="sxs-lookup"><span data-stu-id="47e55-166">string</span></span>                                   | <span data-ttu-id="47e55-167">O endereço de e-mail do cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-167">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="47e55-168">cultura</span><span class="sxs-lookup"><span data-stu-id="47e55-168">culture</span></span>          | <span data-ttu-id="47e55-169">string</span><span class="sxs-lookup"><span data-stu-id="47e55-169">string</span></span>                                   | <span data-ttu-id="47e55-170">A sua cultura preferida para a comunicação e a moeda, como "en-US".</span><span class="sxs-lookup"><span data-stu-id="47e55-170">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="47e55-171">Consulte [o Partner Center com línguas e locais apoiados](partner-center-supported-languages-and-locales.md) para as culturas apoiadas.</span><span class="sxs-lookup"><span data-stu-id="47e55-171">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="47e55-172">language</span><span class="sxs-lookup"><span data-stu-id="47e55-172">language</span></span>         | <span data-ttu-id="47e55-173">string</span><span class="sxs-lookup"><span data-stu-id="47e55-173">string</span></span>                                   | <span data-ttu-id="47e55-174">A linguagem padrão.</span><span class="sxs-lookup"><span data-stu-id="47e55-174">The default language.</span></span> <span data-ttu-id="47e55-175">Dois códigos linguísticos de caracteres (por exemplo `en` `fr` ou) são suportados.</span><span class="sxs-lookup"><span data-stu-id="47e55-175">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="47e55-176">nome da empresa \_</span><span class="sxs-lookup"><span data-stu-id="47e55-176">company\_name</span></span>    | <span data-ttu-id="47e55-177">string</span><span class="sxs-lookup"><span data-stu-id="47e55-177">string</span></span>                                   | <span data-ttu-id="47e55-178">O nome de empresa/organização registado.</span><span class="sxs-lookup"><span data-stu-id="47e55-178">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="47e55-179">endereço padrão \_</span><span class="sxs-lookup"><span data-stu-id="47e55-179">default\_address</span></span> | [<span data-ttu-id="47e55-180">Endereço</span><span class="sxs-lookup"><span data-stu-id="47e55-180">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="47e55-181">O endereço registado da empresa/organização do cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-181">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="47e55-182">Consulte o recurso [Address](utility-resources.md#address) para obter informações sobre eventuais limitações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="47e55-182">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="47e55-183">Perfil da empresa</span><span class="sxs-lookup"><span data-stu-id="47e55-183">Company profile</span></span>

<span data-ttu-id="47e55-184">Esta tabela descreve os campos mínimos exigidos do recurso [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) necessário para criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-184">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="47e55-185">Nome</span><span class="sxs-lookup"><span data-stu-id="47e55-185">Name</span></span>   | <span data-ttu-id="47e55-186">Tipo</span><span class="sxs-lookup"><span data-stu-id="47e55-186">Type</span></span>   | <span data-ttu-id="47e55-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="47e55-187">Description</span></span>                                                  |
|--------|--------|--------------------------------------------------------------|
| <span data-ttu-id="47e55-188">domínio</span><span class="sxs-lookup"><span data-stu-id="47e55-188">domain</span></span> | <span data-ttu-id="47e55-189">string</span><span class="sxs-lookup"><span data-stu-id="47e55-189">string</span></span> | <span data-ttu-id="47e55-190">O nome de domínio do cliente, como contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="47e55-190">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
|<span data-ttu-id="47e55-191">organizaçãoRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="47e55-191">organizationRegistrationNumber</span></span>|<span data-ttu-id="47e55-192">String</span><span class="sxs-lookup"><span data-stu-id="47e55-192">String</span></span>|<span data-ttu-id="47e55-193">Número de registo da organização do cliente (também referido como número INN em determinados países).</span><span class="sxs-lookup"><span data-stu-id="47e55-193">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="47e55-194">Apenas necessário para a empresa/organização do cliente localizada nos seguintes países: Arménia(AM), Azerbaijão(AZ), Bielorrússia(BY), Hungria (HU), Cazaquistão(KZ), Quirguistão(KG), Moldávia (MD), Rússia(RU), Tajiquistão (TJ), Uz, Ucrânia(UA), Brasil(BR), Índia, África do Sul, Polónia, Emirados Árabes Unidos, Arábia Saudita, Turquia, Tailândia,</span><span class="sxs-lookup"><span data-stu-id="47e55-194">Only required for customer’s company/organization located in the following countries: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA), Brazil(BR), India, South Africa, Poland, United Arab Emirates, Saudi Arabia, Turkey, Thailand, Vietnam, Myanmar, Iraq, South Sudan and Venezuela.</span></span> <span data-ttu-id="47e55-195">Para a empresa/organização do cliente localizada noutros países este é um campo opcional.</span><span class="sxs-lookup"><span data-stu-id="47e55-195">For customer’s company/organization located in other countries this is an optional field.</span></span>|

### <a name="request-example"></a><span data-ttu-id="47e55-196">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="47e55-196">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 789
Expect: 100-continue
Connection: Keep-Alive

{
    "CompanyProfile": {
        "Domain": "xyz.ccsctp.net",
    },
    "BillingProfile": {
        "Culture": "EN-US",
        "Email": "test@outlook.com",
        "Language": "en",
        "CompanyName": "test company",
        "DefaultAddress": {
            "FirstName": "Test",
            "LastName": "Test",
            "AddressLine1": "One Microsoft Way",
            "City": "Redmond",
            "State": "WA",
            "PostalCode": "98052",
            "Country": "US",
        }
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="47e55-197">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="47e55-197">REST response</span></span>

<span data-ttu-id="47e55-198">Se for bem sucedido, esta API devolve um recurso [ao Cliente](customer-resources.md#customer) para o novo cliente.</span><span class="sxs-lookup"><span data-stu-id="47e55-198">If successful, this API returns a [Customer](customer-resources.md#customer) resource for the new customer.</span></span> <span data-ttu-id="47e55-199">Guarde os detalhes do ID e AD do cliente para utilização futura com o Partner Center SDK.</span><span class="sxs-lookup"><span data-stu-id="47e55-199">Save the customer ID and Azure AD details for future use with the Partner Center SDK.</span></span> <span data-ttu-id="47e55-200">Você vai precisar deles para uso com gestão de conta, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="47e55-200">You will need them for use with account management, for example.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="47e55-201">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="47e55-201">Response success and error codes</span></span>

<span data-ttu-id="47e55-202">As respostas vêm com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="47e55-202">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="47e55-203">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="47e55-203">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="47e55-204">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="47e55-204">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="47e55-205">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="47e55-205">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 834
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CV: ObwhuhD2tUKJoM+Z.0
MS-ServerId: 202010223
Date: Tue, 14 Feb 2017 20:06:02 GMT

{
    "id": "dfd8cc0a-c592-468c-8461-869a38d24738",
    "commerceId": "0a4ce58a-6f96-4273-8035-d9c7d31b9ba4",
    "companyProfile": {
        "tenantId": "dfd8cc0a-c592-468c-8461-869a38d24738",
        "domain": "xyz.ccsctp.net",
        "attributes": {
            "objectType": "CustomerCompanyProfile"
        }
    },
    "billingProfile": {
        "id": "d17c0275-da92-5c33-9032-782ef1d0b69b",
        "email": "test@outlook.com",
        "culture": "en-US",
        "language": "en",
        "companyName": "test company",
        "defaultAddress": {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "One Microsoft Way",
            "postalCode": "98052",
            "firstName": "Test",
            "lastName": "Test",
            "phoneNumber": ""
        },
        "attributes": {
            "etag": "5920358838484612121",
            "objectType": "CustomerBillingProfile"
        }
    },
    "relationshipToPartner": "none",
    "userCredentials": {
        "userName": "admin",
        "password": "=;;n.=s9Z"
    },
    "attributes": {
        "objectType": "Customer"
    }
}
```
