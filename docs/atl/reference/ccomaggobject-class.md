---
title: "CComAggObject Class | Microsoft Docs"
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
  - "ATL::CComAggObject<contained>"
  - "ATL.CComAggObject"
  - "ATL.CComAggObject<contained>"
  - "CComAggObject"
  - "ATL::CComAggObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], 在 ATL 中"
  - "aggregation [C++], ATL 物件"
  - "CComAggObject class"
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
caps.latest.revision: 29
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComAggObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作彙總物件的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 介面。  根據定義，彙總的物件在外部物件內。  `CComAggObject` 類別類似 [CComObject Class](../../atl/reference/ccomobject-class.md)，不過，前者會公開可直接存取的外部用戶端的介面。  
  
## 語法  
  
```  
  
      template<  
   class contained  
>  
class CComAggObject :  
   public IUnknown, public CComObjectRootEx  
   < contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### 參數  
 `contained`  
 您的類別，衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及從任何其他介面在物件要支援。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComAggObject::CComAggObject](../Topic/CComAggObject::CComAggObject.md)|建構函式。|  
|[CComAggObject::~CComAggObject](../Topic/CComAggObject::~CComAggObject.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComAggObject::AddRef](../Topic/CComAggObject::AddRef.md)|將彙總物件的參考計數。|  
|[CComAggObject::CreateInstance](../Topic/CComAggObject::CreateInstance.md)|這個靜態函式可讓您建立新的 **CComAggObject\<** `contained`**\>** 物件，而不需額外負荷 [CoCreateInstance\(\)](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComAggObject::FinalConstruct](../Topic/CComAggObject::FinalConstruct.md)|執行 `m_contained`的最後的初始化。|  
|[CComAggObject::FinalRelease](../Topic/CComAggObject::FinalRelease.md)|執行 `m_contained`的最終解構。|  
|[CComAggObject::QueryInterface](../Topic/CComAggObject::QueryInterface.md)|擷取指標所要求的介面。|  
|[CComAggObject::Release](../Topic/CComAggObject::Release.md)|會在彙總物件的參考計數。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComAggObject::m\_contained](../Topic/CComAggObject::m_contained.md)|委派給外部未知的 `IUnknown` 呼叫。|  
  
## 備註  
 彙總的物件的`CComAggObject` 實作 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 。  `CComAggObject` 都有自己的 **IUnknown** 介面，不同於外部物件的 **IUnknown** 介面，並保留它的參考計數。  
  
 如需集合的詳細資訊，請參閱本文 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)   
 [DECLARE\_ONLY\_AGGREGATABLE](../Topic/DECLARE_ONLY_AGGREGATABLE.md)   
 [DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)