---
title: "Module::ReleaseNotifier 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::ReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseNotifier 類別"
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::ReleaseNotifier 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

發行在模組中的最後一個物件時，會叫用事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[Module:: releasenotifier:: ~ ReleaseNotifier 解構函式](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Deinitializes releasenotifier 類別的目前執行個體。|  
|[Module::ReleaseNotifier::ReleaseNotifier 建構函式](../windows/module-releasenotifier-releasenotifier-constructor.md)|初始化 releasenotifier 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Module:: releasenotifier:: Invoke 方法](../windows/module-releasenotifier-invoke-method.md)|實作時，會呼叫事件處理常式放開模組中的最後一個物件。|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|刪除目前的 releasenotifier 物件，如果物件已使用的參數建構 `true`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)