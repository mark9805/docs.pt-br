---
title: Instale o .NET Core no gerenciador de pacotes Linux RHEL 8 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b564a386eb67b6e414a832ad3bca10d3d09022bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134186"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="9d948-103">Gerenciador de pacotes RHEL 8 - Instalar .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d948-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="9d948-104">Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="9d948-104">This article describes how to use a package manager to install .NET Core on RHEL 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="9d948-105">Registre sua assinatura do Red Hat</span><span class="sxs-lookup"><span data-stu-id="9d948-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="9d948-106">Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Red Hat Subscription Manager.</span><span class="sxs-lookup"><span data-stu-id="9d948-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="9d948-107">Se isso não foi feito em seu sistema, ou se você não tem certeza, consulte a [Documentação do Produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="9d948-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="9d948-108">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d948-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="9d948-109">Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9d948-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="9d948-110">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="9d948-110">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="9d948-111">Instale o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="9d948-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="9d948-112">Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="9d948-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="9d948-113">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="9d948-113">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="9d948-114">Instale o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d948-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="9d948-115">Depois de se registrar no Gerenciador de Assinaturas, você está pronto para instalar e ativar o .NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="9d948-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="9d948-116">Em seu terminal, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="9d948-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a><span data-ttu-id="9d948-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="9d948-117">See also</span></span>

- [<span data-ttu-id="9d948-118">Usando o .NET Core 3.1 no Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="9d948-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)