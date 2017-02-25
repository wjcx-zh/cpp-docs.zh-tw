---
title: "ICollectionOnSTLImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.ICollectionOnSTLImpl"
  - "ATL::ICollectionOnSTLImpl"
  - "ICollectionOnSTLImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICollectionOnSTLImpl class"
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# ICollectionOnSTLImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供集合類別的方法。  
  
## 語法  
  
```  
  
      template <  
   class T,  
   class CollType,  
   class ItemType,  
   class CopyItem,  
   class EnumType  
>  
class ICollectionOnSTLImpl :  
   public T  
```  
  
#### 參數  
 `T`  
 COM 介面集合。  
  
 `CollType`  
 STL 容器類別。  
  
 *ItemType*  
 容器介面公開的項目型別。  
  
 *CopyItem*  
 [複製原則類別](../../atl/atl-copy-policy-classes.md)。  
  
 *EnumType*  
 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)相容的列舉值類別。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ICollectionOnSTLImpl::get\_\_NewEnum](../Topic/ICollectionOnSTLImpl::get__NewEnum.md)|傳回集合的列舉值物件。|  
|[ICollectionOnSTLImpl::get\_Count](../Topic/ICollectionOnSTLImpl::get_Count.md)|傳回集合中的項目數。|  
|[ICollectionOnSTLImpl::get\_Item](../Topic/ICollectionOnSTLImpl::get_Item.md)|從集合傳回要求的項目。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[ICollectionOnSTLImpl::m\_coll](../Topic/ICollectionOnSTLImpl::m_coll.md)|集合。|  
  
## 備註  
 這個類別會提供集合介面的三種方法的實作: [get\_Count](../Topic/ICollectionOnSTLImpl::get_Count.md)、 [get\_Item](../Topic/ICollectionOnSTLImpl::get_Item.md)和 [get\_\_NewEnum](../Topic/ICollectionOnSTLImpl::get__NewEnum.md)。  
  
 使用這個類別:  
  
-   定義 \(或借用\) 要實作的介面集合。  
  
-   從 `ICollectionOnSTLImpl` 的特製化衍生您的類別會根據這個集合的介面。  
  
-   使用您的衍生類別會從 `ICollectionOnSTLImpl`尚未處理的集合介面的所有方法。  
  
> [!NOTE]
>  如果集合介面是雙重介面，從 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)衍生您的類別，它可以 `ICollectionOnSTLImpl` 特製化做為第一個樣板參數，如果您要 `IDispatch` ATL 提供方法的實作。  
  
-   將項目加入至 [m\_coll](../Topic/ICollectionOnSTLImpl::m_coll.md) 成員填入集合。  
  
 如需詳細資訊和範例，請參閱 [ATL 集合和列舉值。](../../atl/atl-collections-and-enumerators.md)。  
  
## 繼承階層架構  
 `T`  
  
 `ICollectionOnSTLImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [ATLCollections 範例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)