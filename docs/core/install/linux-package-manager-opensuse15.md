---
title: Instalar o .NET Core no openSUSE 15-Package Manager-.NET Core
description: Use um Gerenciador de pacotes para instalar SDK do .NET Core e tempo de execução no openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 0ea232438aa4c61e2064d0323dc706dffac15039
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836965"
---
# <a name="opensuse-15-package-manager---install-net-core"></a>Gerenciador de pacotes do openSUSE 15 – instalar o .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Este artigo descreve como usar um Gerenciador de pacotes para instalar o .NET Core no openSUSE 15. Se você estiver instalando o tempo de execução, sugerimos que instale o [ASP.NET Core Runtime](#install-the-aspnet-core-runtime), pois ele inclui o .NET Core e ASP.NET Core Runtimes.

## <a name="register-microsoft-key-and-feed"></a>Registrar a chave e o feed da Microsoft

Antes de instalar o .NET, você precisará:

- Registrar a chave da Microsoft
- registrar o repositório do produto
- Instalar dependências necessárias

Isso só precisa ser feito uma vez por computador.

Abra um terminal e execute os comandos a seguir.

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Atualize os produtos disponíveis para instalação e, em seguida, instale o SDK do .NET Core. No seu terminal, execute o comando a seguir.

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalar o ASP.NET Core Runtime

Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do ASP.NET. No seu terminal, execute o comando a seguir.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalar o tempo de execução do .NET Core

Atualize os produtos disponíveis para instalação e, em seguida, instale o tempo de execução do .NET Core. No seu terminal, execute o comando a seguir.

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]