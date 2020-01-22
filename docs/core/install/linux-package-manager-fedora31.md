---
title: Instalar o .NET Core no Fedora 31-Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no Fedora 31.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 25c670694ed2d9e89fe37cedf0b06efd8bc93293
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116962"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="dde72-103">Fedora 31 Package Manager-instalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="dde72-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="dde72-104">Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no Fedora 31.</span><span class="sxs-lookup"><span data-stu-id="dde72-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="dde72-105">Se você estiver instalando o tempo de execução, sugerimos que instale o [ASP.NET Core Runtime](#install-the-aspnet-core-runtime), pois ele inclui o .NET Core e ASP.NET Core Runtimes.</span><span class="sxs-lookup"><span data-stu-id="dde72-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="dde72-106">Registrar a chave e o feed da Microsoft</span><span class="sxs-lookup"><span data-stu-id="dde72-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="dde72-107">Antes de instalar o .NET, você precisará:</span><span class="sxs-lookup"><span data-stu-id="dde72-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="dde72-108">Registre a chave da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dde72-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="dde72-109">Registre o repositório do produto.</span><span class="sxs-lookup"><span data-stu-id="dde72-109">Register the product repository.</span></span>
- <span data-ttu-id="dde72-110">Instale as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="dde72-110">Install required dependencies.</span></span>

<span data-ttu-id="dde72-111">Isso só precisa ser feito uma vez por computador.</span><span class="sxs-lookup"><span data-stu-id="dde72-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="dde72-112">Abra um terminal e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="dde72-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="dde72-113">Instalar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="dde72-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="dde72-114">Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dde72-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="dde72-115">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="dde72-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="dde72-116">Instalar o ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="dde72-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="dde72-117">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="dde72-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="dde72-118">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="dde72-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="dde72-119">Instalar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="dde72-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="dde72-120">Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dde72-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="dde72-121">No seu terminal, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="dde72-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="dde72-122">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="dde72-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]