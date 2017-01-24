---
title: "CWin32Heap Class | Microsoft Docs"
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
  - "ATL::CWin32Heap"
  - "ATL.CWin32Heap"
  - "CWin32Heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWin32Heap class"
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWin32Heap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 Win32 堆積配置函式，這個類別會實作 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CWin32Heap : public IAtlMemMgr  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWin32Heap::CWin32Heap](../Topic/CWin32Heap::CWin32Heap.md)|建構函式。|  
|[CWin32Heap::~CWin32Heap](../Topic/CWin32Heap::~CWin32Heap.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWin32Heap::Allocate](../Topic/CWin32Heap::Allocate.md)|從物件堆積配置記憶體區塊。|  
|[CWin32Heap::Attach](../Topic/CWin32Heap::Attach.md)|附加至現有的堆積堆積上的物件。|  
|[CWin32Heap::Detach](../Topic/CWin32Heap::Detach.md)|中斷連結現有的堆積堆積上的物件。|  
|[CWin32Heap::Free](../Topic/CWin32Heap::Free.md)|從堆積釋放先前配置的記憶體。|  
|[CWin32Heap::GetSize](../Topic/CWin32Heap::GetSize.md)|會傳回從物件堆積配置的記憶體區塊的大小。|  
|[CWin32Heap::Reallocate](../Topic/CWin32Heap::Reallocate.md)|重新配置記憶體區塊是堆積上的物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CWin32Heap::m\_bOwnHeap](../Topic/CWin32Heap::m_bOwnHeap.md)|用於的旗標判斷堆積控制代碼目前的擁有權。|  
|[CWin32Heap::m\_hHeap](../Topic/CWin32Heap::m_hHeap.md)|對堆積物件的控制代碼。|  
  
## 備註  
 `CWin32Heap` 實作使用 Win32 的記憶體配置方法堆積配置函式，包括 [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597) 和 [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)。  不同於其他堆積類別， `CWin32Heap` ，在配置之前，需要有效的堆積控制代碼提供記憶體:其他類別預設使用處理堆積。  控制代碼可能會傳遞至建構函式 \(Constructor\) 或重新命名 [CWin32Heap::Attach](../Topic/CWin32Heap::Attach.md) 方法。  如需的詳細資訊請參閱 [CWin32Heap::CWin32Heap](../Topic/CWin32Heap::CWin32Heap.md) 方法。  
  
## 範例  
 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。請參閱範例。  
  
## 繼承階層架構  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## 需求  
 **Header:** atlmem.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)