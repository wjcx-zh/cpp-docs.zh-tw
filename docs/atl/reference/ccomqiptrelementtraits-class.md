---
title: "CComQIPtrElementTraits Class | Microsoft Docs"
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
  - "ATL.CComQIPtrElementTraits"
  - "CComQIPtrElementTraits"
  - "ATL::CComQIPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComQIPtrElementTraits class"
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComQIPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供靜態方法、函式和有用的 typedef，在建立集合時的 COM 介面指標。  
  
## 語法  
  
```  
  
      template<  
   typename I,  
   const IID* piid = & __uuidof( I )   
>   
class CComQIPtrElementTraits : public CDefaultElementTraits<  
   ATL::CComQIPtr< I, piid >  
>  
```  
  
#### 參數  
 `I`  
 指定指標型別 COM 介面的值。  
  
 `piid`  
 為 `I`IID 的指標。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CComQIPtrElementTraits::INARGTYPE](../Topic/CComQIPtrElementTraits::INARGTYPE.md)|使用的資料型別會將項目加入至集合類別物件。|  
  
## 備註  
 表示建立 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM 介面指標集合類別物件時，這個類別衍生方法並提供有用的 typedef。  [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) 和 [CInterfaceList](../../atl/reference/cinterfacelist-class.md) 類別會使用這個類別。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 繼承階層架構  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CComQIPtrElementTraits`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)