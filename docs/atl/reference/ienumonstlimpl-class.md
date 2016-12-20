---
title: "IEnumOnSTLImpl Class | Microsoft Docs"
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
  - "IEnumOnSTLImpl"
  - "ATL.IEnumOnSTLImpl"
  - "ATL::IEnumOnSTLImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IEnumOnSTLImpl class"
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IEnumOnSTLImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會定義以 STL 集合的列舉值介面。  
  
## 語法  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class CollType  
>  
class ATL_NO_VTABLE IEnumOnSTLImpl :  
   public Base  
```  
  
#### 參數  
 `Base`  
 COM 列舉值 \([IEnumXXXX](https://msdn.microsoft.com/en-us/library/ms680089.aspx)\) 介面。  
  
 `piid`  
 out 列舉值介面的介面 ID 的指標。  
  
 `T`  
 列舉值介面公開的項目型別。  
  
 `Copy`  
 [複製原則類別](../../atl/atl-copy-policy-classes.md)。  
  
 `CollType`  
 STL 容器類別。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IEnumOnSTLImpl::Clone](../Topic/IEnumOnSTLImpl::Clone.md)|[IEnumXXXX::Clone](https://msdn.microsoft.com/en-us/library/ms690336.aspx) 的實作。|  
|[IEnumOnSTLImpl::Init](../Topic/IEnumOnSTLImpl::Init.md)|初始化列舉值。|  
|[IEnumOnSTLImpl::Next](../Topic/IEnumOnSTLImpl::Next.md)|[IEnumXXXX::Next](https://msdn.microsoft.com/en-us/library/ms695273.aspx) 的實作。|  
|[IEnumOnSTLImpl::Reset](../Topic/IEnumOnSTLImpl::Reset.md)|[IEnumXXXX::Reset](https://msdn.microsoft.com/en-us/library/ms693414.aspx) 的實作。|  
|[IEnumOnSTLImpl::Skip](../Topic/IEnumOnSTLImpl::Skip.md)|[IEnumXXXX::Skip](https://msdn.microsoft.com/en-us/library/ms690392.aspx) 的實作。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[IEnumOnSTLImpl::m\_iter](../Topic/IEnumOnSTLImpl::m_iter.md)|表示集合中位於列舉值目前位置的 Iterator。|  
|[IEnumOnSTLImpl::m\_pcollection](../Topic/IEnumOnSTLImpl::m_pcollection.md)|一個指標保留項目 STL 容器中列舉型別。|  
|[IEnumOnSTLImpl::m\_spUnk](../Topic/IEnumOnSTLImpl::m_spUnk.md)|提供集合中物件的 **IUnknown** 指標。|  
  
## 備註  
 `IEnumOnSTLImpl` 為列舉中的項目是以 STL 相容的容器中的 COM 列舉值介面的實作。  這個類別 \(Class\) 類似 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) 類別，以根據陣列的列舉值介面的實作。  
  
> [!NOTE]
>  請參閱 [CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md) 有關在其他差異的詳細資料。 `CComEnumImpl` 和 `IEnumOnSTLImpl`。  
  
 通常，您不需要從衍生以建立自己的列舉型別類別從這個介面實作。  如果您想要使用根據 STL 容器之 ATL 提供的列舉值，但更常用的 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)建立執行個體，或是可以取得傳回列舉值從 [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)的集合類別。  
  
 不過，因此，如果您需要提供自訂列舉值 \(例如，公開介面的列舉值介面以外的 ID\)，您可以從這個類別衍生。  在這個案例中的可能需要覆寫 [複製品](../Topic/IEnumOnSTLImpl::Clone.md) 方法提供自己的實作。  
  
## 繼承階層架構  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)