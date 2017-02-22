---
title: "CComObjectNoLock Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComObjectNoLock"
  - "ATL::CComObjectNoLock"
  - "ATL.CComObjectNoLock<Base>"
  - "CComObjectNoLock"
  - "ATL::CComObjectNoLock<Base>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectNoLock class"
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComObjectNoLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 nonaggregated 物件的 **IUnknown** ，，但不會在建構函式的模組鎖定計數。  
  
## 語法  
  
```  
  
      template<  
   class Base   
>  
class CComObjectNoLock :  
   public Base  
```  
  
#### 參數  
 `Base`  
 您的類別，衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及從其他介面在物件要支援。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComObjectNoLock::CComObjectNoLock](../Topic/CComObjectNoLock::CComObjectNoLock.md)|建構函式。|  
|[CComObjectNoLock::~CComObjectNoLock](../Topic/CComObjectNoLock::~CComObjectNoLock.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComObjectNoLock::AddRef](../Topic/CComObjectNoLock::AddRef.md)|將物件的參考計數。|  
|[CComObjectNoLock::QueryInterface](../Topic/CComObjectNoLock::QueryInterface.md)|傳回指向所要求的介面。|  
|[CComObjectNoLock::Release](../Topic/CComObjectNoLock::Release.md)|遞減物件的參考計數。|  
  
## 備註  
 `CComObjectNoLock` 類似 [CComObject](../../atl/reference/ccomobject-class.md) 因為它實作 nonaggregated 物件的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) ;不過， `CComObjectNoLock` 不會在建構函式的模組鎖定計數。  
  
 ATL 會 `CComObjectNoLock` 內部的 Class Factory。  一般而言，您不會直接使用這個類別。  
  
## 繼承階層架構  
 `Base`  
  
 `CComObjectNoLock`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)