---
title: "Module::MethodReleaseNotifier 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::MethodReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MethodReleaseNotifier 類別"
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::MethodReleaseNotifier 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

發行目前模組中的最後一個物件時，會叫用事件處理常式。 事件處理常式是由物件和指定其指標-至-a-方法的成員。  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   typename T  
>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 事件處理常式成員函式的物件類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier 建構函式](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|初始化 methodreleasenotifier 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Module:: methodreleasenotifier:: Invoke 方法](../windows/module-methodreleasenotifier-invoke-method.md)|呼叫目前 methodreleasenotifier 物件相關聯的事件處理常式。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_ 資料成員](../windows/module-methodreleasenotifier-method-data-member.md)|目前的 methodreleasenotifier 物件的事件處理常式會保留指標。|  
|[Module::MethodReleaseNotifier::object_ 資料成員](../windows/module-methodreleasenotifier-object-data-member.md)|保留目前的 methodreleasenotifier 物件的事件處理常式成員函式的物件指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)