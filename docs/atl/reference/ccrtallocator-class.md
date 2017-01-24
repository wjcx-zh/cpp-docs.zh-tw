---
title: "CCRTAllocator Class | Microsoft Docs"
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
  - "CCRTAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCRTAllocator class"
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCRTAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 CRT 記憶體的常式，這個類別會提供管理記憶體的方法。  
  
## 語法  
  
```  
  
class ATL::CCRTAllocator  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCRTAllocator::Allocate](../Topic/CCRTAllocator::Allocate.md)|\(靜態\) 會呼叫這個方法會配置記憶體。|  
|[CCRTAllocator::Free](../Topic/CCRTAllocator::Free.md)|\(靜態\) 會呼叫這個方法以釋放記憶體。|  
|[CCRTAllocator::Reallocate](../Topic/CCRTAllocator::Reallocate.md)|\(靜態\) 會呼叫這個方法會重新配置記憶體。|  
  
## 備註  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) 用於這個類別會提供 CRT 記憶體配置常式。  使用 COM 常式，對應項目分類， [CComAllocator](../../atl/reference/ccomallocator-class.md)，這樣會提供相同的方法。  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CComAllocator Class](../../atl/reference/ccomallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)