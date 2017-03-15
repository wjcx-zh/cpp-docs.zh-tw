---
title: "Implementing CComObject, CComAggObject, and CComPolyObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CComPolyObject"
  - "CComAggObject"
  - "CComObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAggObject class"
  - "CComObject class, 實作"
  - "CComPolyObject class, 實作"
  - "CreateInstance 方法"
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Implementing CComObject, CComAggObject, and CComPolyObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別 [CComObject](../atl/reference/ccomobject-class.md)， [CComAggObject](../atl/reference/ccomaggobject-class.md)，然後， [CComPolyObject](../atl/reference/ccompolyobject-class.md) 永遠在繼承鏈結中的大多數的衍生類別。  為其負責處理所有在 **IUnknown**的方法: `QueryInterface`、 `AddRef`和 **版本**。  此外， `CComAggObject` 和 `CComPolyObject` \(在用於彙總物件\) 提供計數特殊的參考與這個內部未知的必要 `QueryInterface` 語意。  
  
 是否使用 `CComObject`、 `CComAggObject`或 `CComPolyObject` 取決於您是否已宣告之一 \(或\) 下列巨集:  
  
|巨集|作用|  
|--------|--------|  
|`DECLARE_NOT_AGGREGATABLE`|永遠使用 `CComObject`。|  
|`DECLARE_AGGREGATABLE`|使用 `CComAggObject` ，如果物件彙總和 `CComObject` ，否則會傳回。  `CComCoClass` 做包含這個巨集，如果 **DECLARE\_\*\_AGGREGATABLE** 巨集都在您的類別中並未宣告任何建構函式，這會是預設值。|  
|`DECLARE_ONLY_AGGREGATABLE`|永遠使用 `CComAggObject`。  如果物件沒有彙總，則傳回 FALSE。|  
|`DECLARE_POLY_AGGREGATABLE`|當呼叫時， **IClassFactory::CreateInstance** ， ATL **CComPolyObject\<CYourClass\>** 建立執行個體。  在建立時，則外部未知的值進行檢查。  如果是 **NULL**， **IUnknown** 為 nonaggregated 物件上實作。  如果這個外部未知的參數不是 **NULL**， **IUnknown** 為彙總的物件上實作。|  
  
 使用 `CComAggObject` 和 `CComObject` 的優點是 **IUnknown** 的實作會建立哪種最佳化物件。  例如，在中，而一個彙總物件需要內部未知的參考次數和指標至外部 UNKNOWN，一 nonaggregated 物件只需要參考計數。  
  
 使用 `CComPolyObject` 的優點是您不會處理 `CComAggObject` 和的 `CComObject` 於模組彙總和 nonaggregated 情況。  單一 `CComPolyObject` 物件控制代碼兩種情況。  這表示只有一個複本的 vtable 和函式的一個複本存在於模組。  如果您 vtable 非常大，所以可以大幅降低模組大小。  不過，因此，如果您 vtable 很小，使用 `CComPolyObject` 可能造成更大的模組大小，因為它沒有為彙總或 nonaggregated 最佳化物件，就像 `CComAggObject` 和 `CComObject`。  
  
## 請參閱  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)