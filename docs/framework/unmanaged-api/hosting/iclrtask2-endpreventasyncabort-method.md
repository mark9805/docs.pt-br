---
title: Método ICLRTask2::EndPreventAsyncAbort
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 8ae66e0bf96138e5bc2f33e4c14ad86e7dabc6b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124547"
---
# <a name="iclrtask2endpreventasyncabort-method"></a>Método ICLRTask2::EndPreventAsyncAbort
Permite solicitações de anulação de thread novas ou pendentes para resultar em anulações de thread no thread atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|HOST_E_INVALIDOPERATION|O método foi chamado em um thread que não é o thread atual.|  
  
## <a name="remarks"></a>Comentários  
 Chamar esse método diminui o contador atraso-thread-anulação do thread atual em um.  
  
 As chamadas para [ICLRTask2:: BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) e `EndPreventAsyncAbort` podem ser aninhadas. Desde que o contador seja maior que zero, as anulações de thread para o thread atual serão atrasadas.  
  
 A funcionalidade exposta por esse recurso é usada internamente pela VM (máquina virtual). O uso indevido desses métodos pode causar um comportamento não especificado na VM. Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` pode definir o contador como zero quando a VM o incrementaa anteriormente. Da mesma forma, o contador interno não é verificado quanto ao estouro. Se ele exceder seu limite integral porque é incrementado pelo host e pela VM, o comportamento resultante não é especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [Interface ICLRTask2](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
