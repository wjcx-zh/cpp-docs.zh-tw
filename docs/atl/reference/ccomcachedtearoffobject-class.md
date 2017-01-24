---
title: "CComCachedTearOffObject Class | Microsoft Docs"
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
  - "ATL::CComCachedTearOffObject"
  - "ATL.CComCachedTearOffObject"
  - "ATL.CComCachedTearOffObject<contained>"
  - "CComCachedTearOffObject"
  - "ATL::CComCachedTearOffObject<contained>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "快取, ATL cached tear-off objects"
  - "CComCachedTearOffObject class"
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCachedTearOffObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作介面的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) Tear\-Off。  
  
## 語法  
  
```  
  
      template <  
   class contained  
>  
class CComCachedTearOffObject : public IUnknown,  
   public CComObjectRootEx< contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### 參數  
 `contained`  
 請 Tear\-Off 類別，衍生自 `CComTearOffObjectBase` ，而您希望 Tear\-Off 為支援介面的物件。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](../Topic/CComCachedTearOffObject::CComCachedTearOffObject.md)|建構函式。|  
|[CComCachedTearOffObject::~CComCachedTearOffObject](../Topic/CComCachedTearOffObject::~CComCachedTearOffObject.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComCachedTearOffObject::AddRef](../Topic/CComCachedTearOffObject::AddRef.md)|將 `CComCachedTearOffObject` 物件的參考計數。|  
|[CComCachedTearOffObject::FinalConstruct](../Topic/CComCachedTearOffObject::FinalConstruct.md)|呼叫 `m_contained::FinalConstruct` \(Tear\-Off 類別的方法\)。|  
|[CComCachedTearOffObject::FinalRelease](../Topic/CComCachedTearOffObject::FinalRelease.md)|呼叫 `m_contained::FinalRelease` \(Tear\-Off 類別的方法\)。|  
|[CComCachedTearOffObject::QueryInterface](../Topic/CComCachedTearOffObject::QueryInterface.md)|傳回指向 `CComCachedTearOffObject` 物件的 `IUnknown` ，或是在您需求的介面會 Tear\-Off 類別 \(類別 `contained`\)。|  
|[CComCachedTearOffObject::Release](../Topic/CComCachedTearOffObject::Release.md)|如果參考計數為 0，以 `CComCachedTearOffObject` 物件的參考次數並終止。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComCachedTearOffObject::m\_contained](../Topic/CComCachedTearOffObject::m_contained.md)|從衍生的物件 `CComContainedObject` Tear\-Off 類別 \(類別 `contained`\)。|  
  
## 備註  
 `CComCachedTearOffObject` Tear\-Off 介面的實作 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 。  這個類別與 `CComTearOffObject` 不同 `CComCachedTearOffObject` 都有自己的 **IUnknown**，不同於主控物件的 **IUnknown** \(主控為 Tear\-Off\) 建立的物件。  會參考計數為零，`CComCachedTearOffObject` 維護其 **IUnknown** 的參考計數和刪除。  不過，如果您為任，它會查詢中 Tear\-Off 介面，物件的 **IUnknown** 要加入擁有者的參考計數。  
  
 如果實作 Tear\-Off 的 `CComCachedTearOffObject` 物件已具現化，而且 Tear\-Off 介面，以便重新進行查詢，重複使用相同 `CComCachedTearOffObject` 物件。  相反地，如果 `CComTearOffObject` ，實作的介面 Tear\-Off 透過主控物件重新進行查詢，另一個 `CComTearOffObject` 要具現化。  
  
 擁有者類別必須實作 `FinalRelease` 並在快取的 **IUnknown** 的 **版本**`CComCachedTearOffObject`的，則會將其參考計數。  這會造成  `CComCachedTearOffObject` 的 `FinalRelease` 呼叫和刪除 Tear\-Off。  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComTearOffObject Class](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)