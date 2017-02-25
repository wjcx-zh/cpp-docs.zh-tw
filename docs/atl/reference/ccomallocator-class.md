---
title: "CComAllocator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComAllocator"
  - "ATL::CComAllocator"
  - "CComAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAllocator class"
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 COM 記憶體的常式，這個類別會提供管理記憶體的方法。  
  
## 語法  
  
```  
  
class CComAllocator  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComAllocator::Allocate](../Topic/CComAllocator::Allocate.md)|呼叫這個靜態方法會配置記憶體。|  
|[CComAllocator::Free](../Topic/CComAllocator::Free.md)|呼叫這個靜態方法釋放配置的記憶體。|  
|[CComAllocator::Reallocate](../Topic/CComAllocator::Reallocate.md)|呼叫這個靜態方法會重新配置記憶體。|  
  
## 備註  
 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) 用於這個類別會提供 COM 記憶體配置常式。  使用 CRT 常式，對應項目分類， [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)，這樣會提供相同的方法。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [CCRTAllocator Class](../../atl/reference/ccrtallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)