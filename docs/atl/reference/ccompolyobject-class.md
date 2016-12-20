---
title: "CComPolyObject Class | Microsoft Docs"
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
  - "CComPolyObject"
  - "ATL.CComPolyObject<contained>"
  - "ATL::CComPolyObject"
  - "ATL::CComPolyObject<contained>"
  - "ATL.CComPolyObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], 在 ATL 中"
  - "aggregation [C++], ATL 物件"
  - "CComPolyObject class"
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComPolyObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作彙總或 nonaggregated 物件的 **IUnknown** 。  
  
## 語法  
  
```  
  
      template<  
   class contained   
>  
class CComPolyObject : public IUnknown, public CComObjectRootEx  
   < contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### 參數  
 `contained`  
 您的類別，衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及從任何其他介面在物件要支援。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComPolyObject::CComPolyObject](../Topic/CComPolyObject::CComPolyObject.md)|建構函式。|  
|[CComPolyObject::~CComPolyObject](../Topic/CComPolyObject::~CComPolyObject.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComPolyObject::AddRef](../Topic/CComPolyObject::AddRef.md)|將物件的參考計數。|  
|[CComPolyObject::CreateInstance](../Topic/CComPolyObject::CreateInstance.md)|\(靜態\) 可讓您建立新的 **CComPolyObject\<** `contained`**\>** 物件，而不需額外負荷 [CoCreateInstance\(\)](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComPolyObject::FinalConstruct](../Topic/CComPolyObject::FinalConstruct.md)|執行 `m_contained`的最後的初始化。|  
|[CComPolyObject::FinalRelease](../Topic/CComPolyObject::FinalRelease.md)|執行 `m_contained`的最終解構。|  
|[CComPolyObject::QueryInterface](../Topic/CComPolyObject::QueryInterface.md)|擷取指標所要求的介面。|  
|[CComPolyObject::Release](../Topic/CComPolyObject::Release.md)|將物件的參考計數遞減。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComPolyObject::m\_contained](../Topic/CComPolyObject::m_contained.md)|委派 **IUnknown** 呼叫外部 UNKNOWN，如果物件彙總或物件的 **IUnknown** 物件是否不可彙總。|  
  
## 備註  
 彙總的 nonaggregated 或物件的`CComPolyObject` 實作 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 。  
  
 當 `CComPolyObject` 建立的執行個體時，這個外部未知的值進行檢查。  如果是 **NULL**， **IUnknown** 為 nonaggregated 物件上實作。  如果這個外部未知的參數不是 **NULL**， **IUnknown** 為彙總的物件上實作。  
  
 使用 `CComPolyObject` 的優點是您不會處理 [CComAggObject](../../atl/reference/ccomaggobject-class.md) 和的 [CComObject](../../atl/reference/ccomobject-class.md) 於模組彙總和 nonaggregated 情況。  單一 `CComPolyObject` 物件控制代碼兩種情況。  這表示只有一個複本的 vtable 和函式的一個複本存在於模組。  如果您 vtable 非常大，所以可以大幅降低模組大小。  不過，因此，如果您 vtable 很小，使用 `CComPolyObject` 可能造成更大的模組大小，因為它沒有為彙總或 nonaggregated 最佳化物件，就像 `CComAggObject` 和 `CComObject`。  
  
 如果 `DECLARE_POLY_AGGREGATABLE` 巨集會在您的物件類別定義中指定， `CComPolyObject` 將用來建立您自己的物件。  如果您使用 ATL 專案精靈建立完整的控制項或 Internet Explorer 控制項，`DECLARE_POLY_AGGREGATABLE` 會自動宣告。  
  
 如果彙總， `CComPolyObject` 物件都有自己的 **IUnknown**，不同於外部物件的 **IUnknown**，並保留它的參考計數。  `CComPolyObject` 使用 [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 委派至外部未知。  
  
 如需集合的詳細資訊，請參閱本文 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)