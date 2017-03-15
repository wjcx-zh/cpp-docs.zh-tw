---
title: "Microsoft::WRL::Wrappers 命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Wrappers 命名空間"
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Microsoft::WRL::Wrappers 命名空間
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義簡化的物件、 字串和控制代碼的存留期管理的資源擷取為初始設定 (RAII) 包裝函式型別。  
  
## <a name="syntax"></a>語法  
  
```  
namespace Microsoft::WRL::Wrappers;  
```  
  
## <a name="members"></a>Members  
  
### <a name="typedefs"></a>Typedef  
  
|名稱|描述|  
|----------|-----------------|  
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|  
  
### <a name="classes"></a>類別  
  
|名稱|說明|  
|----------|-----------------|  
|[CriticalSection 類別](../windows/criticalsection-class.md)|表示重要區段物件。|  
|[事件類別 （Windows 執行階段 c + + 樣板程式庫）](../windows/event-class-windows-runtime-cpp-template-library.md)|表示事件。|  
|[HandleT 類別](../windows/handlet-class.md)|表示控制代碼的物件。|  
|[HString 類別](../windows/hstring-class.md)|提供支援操作 HSTRING 控點。|  
|[HStringReference 類別](../windows/hstringreference-class.md)|代表 HSTRING 建立從現有的字串。|  
|[Mutex 類別](../windows/mutex-class1.md)|表示以獨佔方式控制共用的資源的同步處理物件。|  
|[RoInitializeWrapper 類別](../windows/roinitializewrapper-class.md)|初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。|  
|[Semaphore 類別](../windows/semaphore-class.md)|表示控制項可以支援有限的使用者共用的資源的同步處理物件。|  
|[SRWLock 類別](../windows/srwlock-class.md)|代表輕型讀取器/寫入器鎖定。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** corewrappers.h  
  
 **命名空間︰** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)