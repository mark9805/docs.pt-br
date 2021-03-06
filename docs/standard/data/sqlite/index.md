---
title: Visão geral
ms.date: 12/13/2019
description: Uma visão geral do Microsoft.Data.Sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543593"
---
# <a name="microsoftdatasqlite-overview"></a>Visão geral do Microsoft.Data.Sqlite

Microsoft.Data.Sqlite é um provedor [de ADO.NET](../../../framework/data/adonet/index.md) leve para SQLite. O [provedor Entity Framework Core](/ef/core/) do SQLite é construído em cima desta biblioteca. No entanto, ele também pode ser usado independentemente ou com outras bibliotecas de acesso a dados.

## <a name="installation"></a>Instalação

A versão estável mais recente está disponível no [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-cli"></a>[CLI do .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Estúdio Visual](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Uso

Esta biblioteca implementa as abstrações comuns ADO.NET para conexões, comandos, leitores de dados e assim por diante.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Confira também

* [Cordas de conexão](connection-strings.md)
* [Referência da API](/dotnet/api/?view=msdata-sqlite-3.0)
* [Sintaxe SQL](https://www.sqlite.org/lang.html)
