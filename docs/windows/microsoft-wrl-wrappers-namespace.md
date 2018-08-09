---
title: Microsoft::WRL::Wrappers 命名空間 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9667a3660f46db0a61991545108d66bf0cac9f38
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017792"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers 命名空間
定義資源擷取為初始設定 (RAII) 包裝函式類型，可簡化物件、 字串和控制代碼的存留期管理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
namespace Microsoft::WRL::Wrappers;  
```  
  
## <a name="members"></a>成員  
  
### <a name="typedefs"></a>Typedef  
  
|名稱|描述|  
|----------|-----------------|  
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|  
  
### <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[CriticalSection 類別](../windows/criticalsection-class.md)|表示重要區段物件。|  
|[Event 類別 (Windows 執行階段 C++ 範本庫)](../windows/event-class-windows-runtime-cpp-template-library.md)|表示事件。|  
|[HandleT 類別](../windows/handlet-class.md)|物件表示的控制代碼。|  
|[HString 類別](../windows/hstring-class.md)|提供對管理 HSTRING 控制代碼支援。|  
|[HStringReference 類別](../windows/hstringreference-class.md)|表示從現有字串建立的 HSTRING。|  
|[Mutex 類別](../windows/mutex-class1.md)|表示以獨佔方式控制共用的資源的同步處理物件。|  
|[RoInitializeWrapper 類別](../windows/roinitializewrapper-class.md)|初始化 Windows 執行階段。|  
|[Semaphore 類別](../windows/semaphore-class.md)|表示控制項可以支援有限的數目的使用者共用的資源的同步處理物件。|  
|[SRWLock 類別](../windows/srwlock-class.md)|表示輕型讀取器/寫入器鎖定。|  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)