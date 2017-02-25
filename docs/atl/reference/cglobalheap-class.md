---
title: "CGlobalHeap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CGlobalHeap"
  - "ATL::CGlobalHeap"
  - "CGlobalHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGlobalHeap class"
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CGlobalHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 Win32 全域堆積函式，這個類別會實作 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CGlobalHeap : public IAtlMemMgr  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CGlobalHeap::Allocate](../Topic/CGlobalHeap::Allocate.md)|呼叫這個方法會配置記憶體區塊。|  
|[CGlobalHeap::Free](../Topic/CGlobalHeap::Free.md)|呼叫這個方法會釋放此記憶體管理員所配置的記憶體區塊。|  
|[CGlobalHeap::GetSize](../Topic/CGlobalHeap::GetSize.md)|呼叫這個方法會取得此記憶體管理員所配置的記憶體區塊的配置的大小。|  
|[CGlobalHeap::Reallocate](../Topic/CGlobalHeap::Reallocate.md)|呼叫這個方法會重新指派此記憶體管理員所配置的記憶體。|  
  
## 備註  
 使用 Win32 全域堆積函式，`CGlobalHeap` 實作記憶體配置配置功能。  
  
> [!NOTE]
>  全域堆積函式比其他記憶體管理函式慢，而且不會提供許多功能。  因此，新的應用程式應使用 [堆積函式](http://msdn.microsoft.com/library/windows/desktop/aa366711)。  這些是適用於 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 類別。  DDE 和剪貼簿函式仍使用全域函式。  
  
## 範例  
 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。請參閱範例。  
  
## 繼承階層架構  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## 需求  
 **Header:** atlmem.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)