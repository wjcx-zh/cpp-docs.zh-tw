---
title: CriticalSectionTraits 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs:
- C++
helpviewer_keywords:
- CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 149cb7fba3d0754e47ac656c137af2d9bf759f1a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642187"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 結構
特製化`CriticalSection`支援無效的重要區段或函式來釋放重要區段物件。  
  
## <a name="syntax"></a>語法  
  
```  
struct CriticalSectionTraits;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`Type`|A **typedef**重要區段定義的指標。 `Type` 定義為`typedef CRITICAL_SECTION* Type;`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CriticalSectionTraits::GetInvalidValue 方法](../windows/criticalsectiontraits-getinvalidvalue-method.md)|特製化`CriticalSection`範本，讓範本不一定正確。|  
|[CriticalSectionTraits::Unlock 方法](../windows/criticalsectiontraits-unlock-method.md)|特製化`CriticalSection`範本，因此它支援指定的重要區段物件釋放擁有權。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CriticalSectionTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空間](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)