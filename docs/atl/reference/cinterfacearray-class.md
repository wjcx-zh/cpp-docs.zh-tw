---
title: "CInterfaceArray Class | Microsoft Docs"
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
  - "ATL.CInterfaceArray"
  - "CInterfaceArray"
  - "ATL::CInterfaceArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInterfaceArray class"
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInterfaceArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以建構一個陣列 COM 介面指標時，這個類別會提供有用的方法。  
  
## 語法  
  
```  
  
      template<  
   class I,  
   const IID* piid = & __uuidof( I )  
>  
class CInterfaceArray : public CAtlArray<  
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
|[CInterfaceArray::CInterfaceArray](../Topic/CInterfaceArray::CInterfaceArray.md)|介面陣列的建構函式。|  
  
## 備註  
 這個類別會建立陣列提供建構函式和衍生方法的 COM 介面指標。  如果需要，請使用 [CInterfaceList](../../atl/reference/cinterfacelist-class.md) 清單。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 繼承階層架構  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CAtlArray Class](../../atl/reference/catlarray-class.md)   
 [CComQIPtr Class](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits Class](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)