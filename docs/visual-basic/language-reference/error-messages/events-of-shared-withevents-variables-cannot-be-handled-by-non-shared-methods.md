---
title: Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: d6067c75835ecd14f1dd796c20ae3f29f456e541
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642950"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
Uma variável declarada com o `Shared` modificador é uma variável compartilhada. Uma variável compartilhada identifica exatamente um local de armazenamento. Uma variável declarada com o `WithEvents` modificador declara que o tipo ao qual pertence a variável manipula o conjunto de eventos que aciona a variável. Quando um valor é atribuído à variável, a propriedade criada pela `WithEvents` declaração desengancha qualquer manipulador de eventos existente e conecta-se o novo manipulador de eventos por meio de `Add` método.  
  
 **ID do erro:** BC30594  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Declare o manipulador de eventos `Shared`.  
  
## <a name="see-also"></a>Consulte também

- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
