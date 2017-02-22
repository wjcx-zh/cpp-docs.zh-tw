---
title: "IAtlMemMgr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAtlMemMgr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlMemMgr class"
  - "記憶體, 管理"
  - "記憶體, memory manager"
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# IAtlMemMgr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示介面給記憶體管理員。  
  
## 語法  
  
```  
  
__interface __declspec( uuid( "654F7EF5-CFDF-4df9-A450-6C6A13C622C0" )) IAtlMemMgr  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[配置](../Topic/IAtlMemMgr::Allocate.md)|呼叫這個方法會配置記憶體區塊。|  
|[Free](../Topic/IAtlMemMgr::Free.md)|呼叫這個方法會釋放記憶體區塊。|  
|[GetSize](../Topic/IAtlMemMgr::GetSize.md)|呼叫這個方法會擷取一個配置的記憶體區塊的大小。|  
|[重新配置](../Topic/IAtlMemMgr::Reallocate.md)|呼叫這個方法會重新配置記憶體區塊。|  
  
## 備註  
 這個介面是由 [CComHeap](../../atl/reference/ccomheap-class.md)、 [CCRTHeap](../../atl/reference/ccrtheap-class.md)、 [CLocalHeap](../../atl/reference/clocalheap-class.md)、 [CGlobalHeap](../../atl/reference/cglobalheap-class.md)或 [CWin32Heap](../../atl/reference/cwin32heap-class.md)實作。  
  
> [!NOTE]
>  區域和全域堆積函式比其他記憶體管理函式緩慢而且不提供許多功能。  因此，新的應用程式應使用 [堆積函式](http://msdn.microsoft.com/library/windows/desktop/aa366711)。  這些是適用於 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 類別。  
  
## 範例  
 [!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/CPP/iatlmemmgr-class_1.cpp)]  
  
## 需求  
 **Header:** atlmem.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)