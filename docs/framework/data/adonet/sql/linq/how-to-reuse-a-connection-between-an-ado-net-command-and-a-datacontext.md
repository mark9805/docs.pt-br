---
title: 'Como: reutilizar uma conexão entre um comando ADO.NET e um DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: f1ee7726042327eae88e69e9e6d062909c5bc74e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793294"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Como: reutilizar uma conexão entre um comando ADO.NET e um DataContext
Como [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o faz parte da família de tecnologias ADO.net e é baseado em serviços fornecidos pelo ADO.net, você pode reutilizar uma conexão entre um comando ADO.net e um <xref:System.Data.Linq.DataContext>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como reutilizar a mesma conexão entre um comando ADO.NET e <xref:System.Data.Linq.DataContext>o.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Consulte também

- [Informações gerais](background-information.md)
- [ADO.NET e LINQ to SQL](ado-net-and-linq-to-sql.md)
- [Comunicação com o banco de dados](communicating-with-the-database.md)
