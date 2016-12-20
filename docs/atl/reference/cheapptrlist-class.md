---
title: "CHeapPtrList Class | Microsoft Docs"
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
  - "ATL::CHeapPtrList"
  - "CHeapPtrList"
  - "ATL.CHeapPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrList class"
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHeapPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以建構清單堆積指標時，這個類別會提供有用的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
typename E,  
class Allocator = ATL::CCRTAllocator  
>  
class CHeapPtrList : public CAtlList<  
ATL::CHeapPtr< E, Allocator>,  
CHeapPtrElementTraits< E, Allocator>  
>  
```  
  
#### 參數  
 `E`  
 集合類別會儲存物件的型別。  
  
 `Allocator`  
 要使用的記憶體配置類別。  預設值為 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtrList::CHeapPtrList](../Topic/CHeapPtrList::CHeapPtrList.md)|建構函式。|  
  
## 備註  
 這個類別會提供建構函式並從 [CAtlList](../../atl/reference/catllist-class.md) 和 [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) 衍生方法協助儲存堆積指標集合類別物件的建立。  
  
## 繼承階層架構  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CAtlList Class](../../atl/reference/catllist-class.md)   
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrElementTraits Class](../../atl/reference/cheapptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)