---
title: SRWLockExclusiveTraits 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d6543ada6840b292d6a7b981eefeab41642c42df
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017928"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits 結構
描述一般特性`SRWLock`獨佔的鎖定模式的類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
struct SRWLockExclusiveTraits;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`Type`|指標的同義字[SRWLOCK](../windows/srwlock-class.md)類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[SRWLockExclusiveTraits::GetInvalidValue 方法](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|擷取**SRWLockExclusiveTraits**一律是無效的物件。|  
|[SRWLockExclusiveTraits::Unlock 方法](../windows/srwlockexclusivetraits-unlock-method.md)|釋放指定獨佔控制`SRWLock`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `SRWLockExclusiveTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空間](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)