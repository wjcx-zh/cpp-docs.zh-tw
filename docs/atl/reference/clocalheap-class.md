---
title: "CLocalHeap Class | Microsoft Docs"
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
  - "ATL.CLocalHeap"
  - "ATL::CLocalHeap"
  - "CLocalHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLocalHeap class"
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLocalHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 Win32 區域堆積函式，這個類別會實作 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CLocalHeap : public IAtlMemMgr  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CLocalHeap::Allocate](../Topic/CLocalHeap::Allocate.md)|呼叫這個方法會配置記憶體區塊。|  
|[CLocalHeap::Free](../Topic/CLocalHeap::Free.md)|呼叫這個方法會釋放此記憶體管理員所配置的記憶體區塊。|  
|[CLocalHeap::GetSize](../Topic/CLocalHeap::GetSize.md)|呼叫這個方法會取得此記憶體管理員所配置的記憶體區塊的配置的大小。|  
|[CLocalHeap::Reallocate](../Topic/CLocalHeap::Reallocate.md)|呼叫這個方法會重新指派此記憶體管理員所配置的記憶體。|  
  
## 備註  
 `CLocalHeap` 實作使用 Win32 區域堆積上的記憶體配置配置功能運作。  
  
> [!NOTE]
>  本機堆積函式比其他記憶體管理函式慢，而且不會提供許多功能。  因此，新的應用程式應使用 [堆積函式](http://msdn.microsoft.com/library/windows/desktop/aa366711)。  這些是適用於 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 類別。  
  
## 範例  
 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。請參閱範例。  
  
## 繼承階層架構  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## 需求  
 **Header:** atlmem.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)