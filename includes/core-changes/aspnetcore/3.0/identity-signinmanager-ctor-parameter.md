---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393892"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="3664e-101">Identity: o Construtor SignInManager aceita o novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="3664e-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="3664e-102">A partir do ASP.NET Core 3,0, um novo parâmetro `IUserConfirmation<TUser>` foi adicionado ao Construtor `SignInManager`.</span><span class="sxs-lookup"><span data-stu-id="3664e-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="3664e-103">Para obter mais informações, consulte [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="3664e-103">For more information, see [aspnet/AspNetCore#8356](https://github.com/aspnet/AspNetCore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3664e-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="3664e-104">Version introduced</span></span>

<span data-ttu-id="3664e-105">3.0</span><span class="sxs-lookup"><span data-stu-id="3664e-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3664e-106">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="3664e-106">Reason for change</span></span>

<span data-ttu-id="3664e-107">A motivação para a alteração foi adicionar suporte a novos fluxos de email/confirmação em identidade.</span><span class="sxs-lookup"><span data-stu-id="3664e-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3664e-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="3664e-108">Recommended action</span></span>

<span data-ttu-id="3664e-109">Se você construir manualmente um `SignInManager`, forneça uma implementação de `IUserConfirmation` ou pegue um da injeção de dependência a ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="3664e-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="3664e-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="3664e-110">Category</span></span>

<span data-ttu-id="3664e-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3664e-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3664e-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3664e-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->