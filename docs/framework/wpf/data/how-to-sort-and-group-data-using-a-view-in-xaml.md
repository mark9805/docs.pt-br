---
title: Como organizar e agrupar dados usando uma exibição em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460120"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Como organizar e agrupar dados usando uma exibição em XAML
Este exemplo mostra como criar uma exibição de uma coleção de dados em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Modos de exibição permitem as funcionalidades de agrupamento, classificação, filtragem e a noção de um item atual.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o recurso estático chamado *places* é definido como uma coleção de objetos *Place*, na qual cada objeto *Place* consiste em um nome de cidade e o estado. O prefixo *src* é mapeado para o namespace no qual a fonte de dados *Places* está definida. O prefixo *scm* mapeia para `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` e *dat* mapeia para `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 O exemplo a seguir cria uma exibição da coleta de dados classificada por nome de cidade e agrupada por estado.  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Em seguida, o modo de exibição, pode ser uma origem da associação, como no exemplo a seguir:  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Para associações a dados XML definidos em um recurso <xref:System.Windows.Data.XmlDataProvider>, preceda o nome XML com um símbolo @.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.CollectionViewSource>
- [Obter a exibição padrão de uma coleta de dados](how-to-get-the-default-view-of-a-data-collection.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
