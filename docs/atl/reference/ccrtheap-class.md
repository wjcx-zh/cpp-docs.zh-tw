---
title: "CCRTHeap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CCRTHeap"
  - "ATL.CCRTHeap"
  - "CCRTHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCRTHeap class"
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CCRTHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 CRT 堆積函式，這個類別會實作 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。  
  
## 語法  
  
```  
  
class CCRTHeap : public IAtlMemMgr  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCRTHeap::Allocate](../Topic/CCRTHeap::Allocate.md)|呼叫這個方法會配置記憶體區塊。|  
|[CCRTHeap::Free](../Topic/CCRTHeap::Free.md)|呼叫這個方法會釋放此記憶體管理員所配置的記憶體區塊。|  
|[CCRTHeap::GetSize](../Topic/CCRTHeap::GetSize.md)|呼叫這個方法會取得此記憶體管理員所配置的記憶體區塊的配置的大小。|  
|[CCRTHeap::Reallocate](../Topic/CCRTHeap::Reallocate.md)|呼叫這個方法會重新指派此記憶體管理員所配置的記憶體。|  
  
## 備註  
 `CCRTHeap` 實作使用 CRT 的記憶體配置堆積配置函式的函式，包括 [malloc](../../c-runtime-library/reference/malloc.md)、 [可用](../../c-runtime-library/reference/free.md)、 [realloc](../../c-runtime-library/reference/realloc.md)和 [\_msize](../../c-runtime-library/reference/msize.md)。  
  
## 範例  
 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。請參閱範例。  
  
## 繼承階層架構  
 `IAtlMemMgr`  
  
 `CCRTHeap`  
  
## 需求  
 **Header:** atlmem.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)