---
title: "IUnknown Implementation Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.Iunknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUnknown implementation classes"
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IUnknown Implementation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列類別會實作 **IUnknown** 和相關方法:  
  
-   [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 處理計數為彙總和 nonaggregated 物件的參考。  可讓您指定執行緒模型。  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) 處理計數為彙總和 nonaggregated 物件的參考。  使用伺服器上的預設執行緒模型。  
  
-   彙總的物件的[CComAggObject](../atl/reference/ccomaggobject-class.md) 實作 **IUnknown** 。  
  
-   一 nonaggregated 物件的[CComObject](../atl/reference/ccomobject-class.md) 實作 **IUnknown** 。  
  
-   [CComPolyObject](../atl/reference/ccompolyobject-class.md) 實作彙總和 nonaggregated 物件的 **IUnknown** 。  使用 `CComPolyObject` 避免 `CComAggObject` 和 `CComObject` 中的模組。  單一 `CComPolyObject` 物件控制代碼收集並 nonaggregated 情況。  
  
-   一 nonaggregated 物件的[CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) 實作 **IUnknown** ，則不會修改模組鎖定計數。  
  
-   [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) Tear\-Off 介面的實作 **IUnknown** 。  
  
-   「快取」的[CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) 實作 **IUnknown** Tear\-Off 介面。  
  
-   彙總或 Tear\-Off 介面的內部物件的[CComContainedObject](../atl/reference/ccomcontainedobject-class.md) 實作 **IUnknown** 。  
  
-   [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) 嘗試在模組的參考次數確保您的物件不會被刪除。  
  
-   使用 **IUnknown**的基本架構實作，[CComObjectStack](../atl/reference/ccomobjectstack-class.md) 建立暫時的 COM 物件。  
  
## 相關文件  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)  
  
## 請參閱  
 [Class Overview](../atl/atl-class-overview.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)   
 [COM Map Macros](../atl/reference/com-map-macros.md)   
 [COM Map Global Functions](../atl/reference/com-map-global-functions.md)