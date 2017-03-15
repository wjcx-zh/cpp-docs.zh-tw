---
title: "Microsoft::WRL::Wrappers::HandleTraits Namespace | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HandleTraits 命名空間"
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Microsoft::WRL::Wrappers::HandleTraits Namespace
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

說明常用的控制代碼為基礎的資源類型的特性。  
  
## <a name="syntax"></a>語法  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>Members  
  
### <a name="structures"></a>結構  
  
|名稱|說明|  
|----------|-----------------|  
|[CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)|特製化 `CriticalSection` 物件，以支援無效的重要區段或函式來釋放重要區段。|  
|[EventTraits 結構](../windows/eventtraits-structure.md)|定義特性 `Event` 類別控制代碼。|  
|[FileHandleTraits 結構](../windows/filehandletraits-structure.md)|定義檔案控制代碼的特性。|  
|[HANDLENullTraits 結構](../windows/handlenulltraits-structure.md)|定義未初始化的控制代碼的一般特性。|  
|[HANDLETraits 結構](../windows/handletraits-structure.md)|定義控制代碼的一般特性。|  
|[MutexTraits 結構](../windows/mutextraits-structure.md)|定義通用特性 [Mutex](../windows/mutex-class1.md) 類別。|  
|[SemaphoreTraits 結構](../windows/semaphoretraits-structure.md)|定義號誌物件的一般特性。|  
|[SRWLockExclusiveTraits 結構](../windows/srwlockexclusivetraits-structure.md)|描述一般特性 `SRWLock` 獨佔的鎖定模式的類別。|  
|[SRWLockSharedTraits 結構](../windows/srwlocksharedtraits-structure.md)|描述一般特性 `SRWLock` 在共用鎖定模式的類別。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** corewrappers.h  
  
 **命名空間︰** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)