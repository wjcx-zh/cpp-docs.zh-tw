---
title: Microsoft::WRL::Wrappers::HandleTraits 命名空間 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs:
- C++
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b114d067249e78d7fb935e473cc3cc952c76fe02
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits Namespace
說明常用的控制代碼為基礎的資源類型的特性。  
  
## <a name="syntax"></a>語法  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>成員  
  
### <a name="structures"></a>結構  
  
|名稱|描述|  
|----------|-----------------|  
|[CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)|特製化`CriticalSection`支援無效的重要區段或釋放重要區段的函式的物件。|  
|[EventTraits 結構](../windows/eventtraits-structure.md)|定義特性`Event`類別控制代碼。|  
|[FileHandleTraits 結構](../windows/filehandletraits-structure.md)|定義的檔案控制代碼的特性。|  
|[HANDLENullTraits 結構](../windows/handlenulltraits-structure.md)|定義未初始化的控制代碼的一般特性。|  
|[HANDLETraits 結構](../windows/handletraits-structure.md)|定義通用的控制代碼的特性。|  
|[MutexTraits 結構](../windows/mutextraits-structure.md)|定義的一般特性[Mutex](../windows/mutex-class1.md)類別。|  
|[SemaphoreTraits 結構](../windows/semaphoretraits-structure.md)|定義號誌物件的一般特性。|  
|[SRWLockExclusiveTraits 結構](../windows/srwlockexclusivetraits-structure.md)|描述一般特性`SRWLock`獨佔的鎖定模式的類別。|  
|[SRWLockSharedTraits 結構](../windows/srwlocksharedtraits-structure.md)|描述一般特性`SRWLock`在共用鎖定模式的類別。|  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)