---
title: "CComObjectRootEx Class | Microsoft Docs"
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
  - "ATL.CComObjectRootEx"
  - "ATL::CComObjectRootEx<ThreadModel>"
  - "CComObjectRootEx"
  - "ATL::CComObjectRootEx"
  - "ATL.CComObjectRootEx<ThreadModel>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reference counting"
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectRootEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供方法來處理物件的參考次數。nonaggregated 管理和彙總物件。  
  
## 語法  
  
```  
  
      template<  
   class ThreadModel   
>  
class CComObjectRootEx : public CComObjectRootBase  
```  
  
#### 參數  
 `ThreadModel`  
 方法實作所需的執行緒模型的類別。  您可以設定 `ThreadModel` 明確選取執行緒模型為 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)、 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)或 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。  您可以設定 `ThreadModel` 接受伺服器的預設執行緒模型。 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 或 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)。  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[CComObjectRootEx](../Topic/CComObjectRootEx::CComObjectRootEx.md)|建構函式。|  
|[InternalAddRef](../Topic/CComObjectRootEx::InternalAddRef.md)|將 nonaggregated 物件的參考計數。|  
|[InternalRelease](../Topic/CComObjectRootEx::InternalRelease.md)|減一 nonaggregated 物件的參考計數。|  
|[鎖定](../Topic/CComObjectRootEx::Lock.md)|如果執行緒模型多執行緒，取得關鍵區段物件的擁有權。|  
|[解除鎖定](../Topic/CComObjectRootEx::Unlock.md)|如果執行緒模型多執行緒，釋放關鍵區段物件的擁有權。|  
  
### CComObjectRootBase 方法  
  
|||  
|-|-|  
|[FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md)|在您執行任何初始化之類別的覆寫必須由您的物件。|  
|[FinalRelease](../Topic/CComObjectRootEx::FinalRelease.md)|在您執行任何清除之類別的覆寫必須由您的物件。|  
|[OuterAddRef](../Topic/CComObjectRootEx::OuterAddRef.md)|將彙總物件的參考計數。|  
|[OuterQueryInterface](../Topic/CComObjectRootEx::OuterQueryInterface.md)|彙總的物件的外部 **IUnknown** 的委派。|  
|[OuterRelease](../Topic/CComObjectRootEx::OuterRelease.md)|要彙總的物件的參考計數。|  
  
### 靜態函式  
  
|||  
|-|-|  
|[InternalQueryInterface](../Topic/CComObjectRootEx::InternalQueryInterface.md)|一 nonaggregated 物件的 **IUnknown** 的委派。|  
|[ObjectMain](../Topic/CComObjectRootEx::ObjectMain.md)|會在模組初始化和終止時在物件對應中的衍生類別的。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_dwRef](../Topic/CComObjectRootEx::m_dwRef.md)|`m_pOuterUnknown`，一部分的聯集。  使用時，物件不會彙總保留參考計數 `AddRef` 和 **版本**。|  
|[m\_pOuterUnknown](../Topic/CComObjectRootEx::m_pOuterUnknown.md)|`m_dwRef`，一部分的聯集。  使用，將物件加以彙總存放指標則外部未知。|  
  
## 備註  
 `CComObjectRootEx` 控制代碼物件參考 nonaggregated 和彙總物件的計數管理。  它會保留物件的參考次數，如果物件不可彙總，並保有指標至外部 UNKNOWN，如果您物件的彙總。  對於彙總物件， `CComObjectRootEx` 方法可用來處理內部物件的失敗\] 建構的，因此，保護外部物件遭刪除，而放開內部介面或內部物件刪除。  
  
 實作 COM 伺服器的類別必須繼承 `CComObjectRootEx` 或 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)繼承。  
  
 如果您的類別定義中指定 [DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md) 巨集， ATL **CComPolyObject\<CYourClass\>** 建立執行個體，而 **IClassFactory::CreateInstance** 時呼叫。  在建立時，則外部未知的值進行檢查。  如果是 **NULL**， **IUnknown** 為 nonaggregated 物件上實作。  如果這個外部未知的參數不是 **NULL**， **IUnknown** 為彙總的物件上實作。  
  
 如果您的類別並未指定 `DECLARE_POLY_AGGREGATABLE` ATL 巨集，建立執行個體 **CAggComObject\<CYourClass\>** 彙總物件的或 **CComObject\<CYourClass\>** nonaggregated 物件的執行個體。  
  
 使用 `CComPolyObject` 的優點是您不會處理 `CComAggObject` 和的 `CComObject` 於模組彙總和 nonaggregated 情況。  單一 `CComPolyObject` 物件控制代碼兩種情況。  因此，只有一個複本的 vtable 和函式的一個複本存在於模組。  如果您 vtable 非常大，所以可以大幅降低模組大小。  不過，因此，如果您 vtable 很小，使用 `CComPolyObject` 可能造成更大的模組大小，因為它沒有為彙總或 nonaggregated 最佳化物件，就像 `CComAggObject` 和 `CComObject`。  
  
 如果您的物件會彙總， [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 由 `CComAggObject` 或 `CComPolyObject`實作。  這些類別 `QueryInterface`委派、 `AddRef`和 **版本** 呼叫 `CComObjectRootEx` 的 `OuterQueryInterface`、 `OuterAddRef`和 `OuterRelease` 轉送至外部未知。  通常，您會覆寫類別中的所有 `CComObjectRootEx::FinalConstruct` 建立彙總物件，並覆寫 `CComObjectRootEx::FinalRelease` 釋放任何彙總物件。  
  
 如果您的物件不可彙總， **IUnknown** 由 `CComObject` 或 `CComPolyObject`實作。  在這種情況下， `QueryInterface`對的呼叫， `AddRef`和 **版本** 委派至 `CComObjectRootEx` 的 `InternalQueryInterface`、 `InternalAddRef`和 `InternalRelease` 執行實際作業。  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)