---
title: Enumeração CorDebugStepReason
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 92aee981aca3bac32c0ef264799e486315ca5103
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789251"
---
# <a name="cordebugstepreason-enumeration"></a>Enumeração CorDebugStepReason
Indica o resultado de uma etapa individual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`STEP_NORMAL`|A etapa foi concluída normalmente, dentro da mesma função.|  
|`STEP_RETURN`|A depuração continua normalmente, depois que a função é retornada.|  
|`STEP_CALL`|A etapa continuou normalmente, no início de uma função chamada recentemente.|  
|`STEP_EXCEPTION_FILTER`|Uma exceção foi gerada e o controle foi passado para um filtro de exceção.|  
|`STEP_EXCEPTION_HANDLER`|Uma exceção foi gerada e o controle foi passado para um manipulador de exceção.|  
|`STEP_INTERCEPT`|O controle foi passado para um interceptor.|  
|`STEP_EXIT`|O thread saiu antes da conclusão da etapa.|  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método StepComplete](icordebugmanagedcallback-stepcomplete-method.md)
- [Declarando enumerações](debugging-enumerations.md)
