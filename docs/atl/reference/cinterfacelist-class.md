---
title: "CInterfaceList Class | Microsoft Docs"
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
  - "ATL::CInterfaceList"
  - "ATL.CInterfaceList"
  - "CInterfaceList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInterfaceList class"
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInterfaceList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以建構清單 COM 介面指標時，這個類別會提供有用的方法。  
  
## 語法  
  
```  
  
      template<  
   class I,  
   const IID* piid = & __uuidof( I )  
>   
class CInterfaceList : public CAtlList<  
   ATL::CComQIPtr< I, piid >,  
   CComQIPtrElementTraits< I, piid >  
>  
```  
  
#### 參數  
 `I`  
 指定指標型別 COM 介面的值。  
  
 `piid`  
 為 `I`IID 的指標。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CInterfaceList::CInterfaceList](../Topic/CInterfaceList::CInterfaceList.md)|介面清單中的建構函式。|  
  
## 備註  
 這個類別會建立 COM 介面指標清單提供建構函式和衍生方法。  如果需要，請使用 [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) 陣列。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 繼承階層架構  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CAtlList Class](../../atl/reference/catllist-class.md)   
 [CComQIPtr Class](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits Class](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)