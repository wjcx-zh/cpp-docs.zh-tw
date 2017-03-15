---
title: "Module::GenericReleaseNotifier 類別 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::GenericReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GenericReleaseNotifier 類別"
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::GenericReleaseNotifier 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

發行目前模組中的最後一個物件時，會叫用事件處理常式。 事件處理常式是 lambda、 仿函式或函式指標上所指定的。  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   typename T  
>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 包含事件處理常式的位置之資料成員的型別。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier 建構函式](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|初始化 genericreleasenotifier 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Module:: genericreleasenotifier:: Invoke 方法](../windows/module-genericreleasenotifier-invoke-method.md)|呼叫目前 genericreleasenotifier 物件相關聯的事件處理常式。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_ 資料成員](../windows/module-genericreleasenotifier-callback-data-member.md)|保存 lambda、 仿函式或目前的 genericreleasenotifier 物件相關聯的函式指標事件處理常式。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)