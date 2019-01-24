---
title: Interface IXCLRDataMethodDefinition
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4265db62b11453d9fc087928adb0cc0c05c052ca
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416276"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="16be1-102">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="16be1-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="16be1-103">Fornece métodos para consultar informações sobre uma definição de método.</span><span class="sxs-lookup"><span data-stu-id="16be1-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="16be1-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="16be1-104">Methods</span></span>

<span data-ttu-id="16be1-105">Os métodos a seguir estão alguns dos métodos disponíveis na interface.</span><span class="sxs-lookup"><span data-stu-id="16be1-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="16be1-106">Método</span><span class="sxs-lookup"><span data-stu-id="16be1-106">Method</span></span>                                                                                                                          | <span data-ttu-id="16be1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="16be1-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="16be1-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="16be1-108">StartEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="16be1-109">Fornece um identificador para a enumeração de instâncias de método para um determinado `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="16be1-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="16be1-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="16be1-110">EnumInstance</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="16be1-111">Enumera as instâncias desta definição de método.</span><span class="sxs-lookup"><span data-stu-id="16be1-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="16be1-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="16be1-112">EndEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="16be1-113">Libera os recursos usados pelos iteradores internos usados durante a enumeração de instância.</span><span class="sxs-lookup"><span data-stu-id="16be1-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="16be1-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="16be1-114">Remarks</span></span>

<span data-ttu-id="16be1-115">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="16be1-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="16be1-116">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="16be1-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="16be1-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16be1-117">Requirements</span></span>

<span data-ttu-id="16be1-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16be1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="16be1-119">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="16be1-119">**Header:** None</span></span>  
<span data-ttu-id="16be1-120">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="16be1-120">**Library:** None</span></span>  
<span data-ttu-id="16be1-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="16be1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="16be1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16be1-122">See Also</span></span>

- [<span data-ttu-id="16be1-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="16be1-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="16be1-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="16be1-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)