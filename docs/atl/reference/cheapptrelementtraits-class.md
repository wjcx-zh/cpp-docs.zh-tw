---
title: "CHeapPtrElementTraits Class | Microsoft Docs"
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
  - "ATL.CHeapPtrElementTraits"
  - "CHeapPtrElementTraits"
  - "ATL::CHeapPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrElementTraits class"
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHeapPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示建立堆積指標集合時，這個類別會提供靜態方法、函式和有用的 Typedef。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
typename T,  
class Allocator= ATL::CCRTAllocator  
>  
class CHeapPtrElementTraits : public CDefaultElementTraits<  
ATL::CHeapPtr< T, Allocator>  
>  
```  
  
#### 參數  
 `T`  
 集合類別會儲存物件的型別。  
  
 `Allocator`  
 要使用的記憶體配置類別。  預設值為 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtrElementTraits::INARGTYPE](../Topic/CHeapPtrElementTraits::INARGTYPE.md)|使用的資料型別會將項目加入至集合類別物件。|  
|[CHeapPtrElementTraits::OUTARGTYPE](../Topic/CHeapPtrElementTraits::OUTARGTYPE.md)|使用資料型別來擷取項目從集合類別物件。|  
  
## 備註  
 這個類別會提供協助集合包含堆積指標的類別建立物件時提供方法、靜態函式及 Typedef。  類別 `CHeapPtrList``CHeapPtrElementTraits`從衍生。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 繼承階層架構  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)