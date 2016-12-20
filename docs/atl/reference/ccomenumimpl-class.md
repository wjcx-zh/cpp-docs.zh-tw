---
title: "CComEnumImpl Class | Microsoft Docs"
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
  - "ATL.CComEnumImpl"
  - "ATL::CComEnumImpl"
  - "CComEnumImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnumImpl class"
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComEnumImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供列舉項目儲存在陣列中的 COM 列舉值介面的實作。  
  
## 語法  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy  
>  
class ATL_NO_VTABLE CComEnumImpl :   
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
 同質性 [複製原則類別](../../atl/atl-copy-policy-classes.md)。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComEnumImpl::CComEnumImpl](../Topic/CComEnumImpl::CComEnumImpl.md)|建構函式。|  
|[CComEnumImpl::~CComEnumImpl](../Topic/CComEnumImpl::~CComEnumImpl.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComEnumImpl::Clone](../Topic/CComEnumImpl::Clone.md)|[IEnumXXXX::Clone](https://msdn.microsoft.com/en-us/library/ms690336.aspx) 的實作。|  
|[CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md)|初始化列舉值。|  
|[CComEnumImpl::Next](../Topic/CComEnumImpl::Next.md)|[IEnumXXXX::Next](https://msdn.microsoft.com/en-us/library/ms695273.aspx) 的實作。|  
|[CComEnumImpl::Reset](../Topic/CComEnumImpl::Reset.md)|[IEnumXXXX::Reset](https://msdn.microsoft.com/en-us/library/ms693414.aspx) 的實作。|  
|[CComEnumImpl::Skip](../Topic/CComEnumImpl::Skip.md)|[IEnumXXXX::Skip](https://msdn.microsoft.com/en-us/library/ms690392.aspx) 的實作。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComEnumImpl::m\_begin](../Topic/CComEnumImpl::m_begin.md)|為第一個項目的指標陣列。|  
|[CComEnumImpl::m\_dwFlags](../Topic/CComEnumImpl::m_dwFlags.md)|複製旗標傳遞 `Init`。|  
|[CComEnumImpl::m\_end](../Topic/CComEnumImpl::m_end.md)|之位置的指標會在陣列中的最後一個項目以外的項目。|  
|[CComEnumImpl::m\_iter](../Topic/CComEnumImpl::m_iter.md)|目前項目的指標陣列。|  
|[CComEnumImpl::m\_spUnk](../Topic/CComEnumImpl::m_spUnk.md)|提供集合的物件 **IUnknown** 指標被列舉。|  
  
## 備註  
 `CComEnumImpl` 為列舉項目儲存在陣列中的 COM 列舉值介面的實作。  這個類別 \(Class\) 類似 `IEnumOnSTLImpl` 類別，提供根據 STL 容器的列舉值介面實作。  
  
> [!NOTE]
>  如需在其他差異的詳細資料。 `CComEnumImpl` 和 `IEnumOnSTLImpl`之間切換，請參閱 [CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md)。  
  
 通常，您不需要從衍生以建立自己的列舉型別類別從這個介面實作。  如果您想要使用根據陣列之 ATL 提供的列舉值，但更常用的 [CComEnum](../../atl/reference/ccomenum-class.md)建立執行個體。  
  
 不過，因此，如果您需要提供自訂列舉值 \(例如，公開介面的列舉值介面以外的 ID\)，您可以從這個類別衍生。  在這種情況下，您可能還需要覆寫 [CComEnumImpl::Clone](../Topic/CComEnumImpl::Clone.md) 方法提供自己的實作。  
  
 如需詳細資訊，請參閱 [ATL 集合和列舉值。](../../atl/atl-collections-and-enumerators.md)。  
  
## 繼承階層架構  
 `Base`  
  
 `CComEnumImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [IEnumOnSTLImpl Class](../../atl/reference/ienumonstlimpl-class.md)   
 [CComEnum Class](../../atl/reference/ccomenum-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)