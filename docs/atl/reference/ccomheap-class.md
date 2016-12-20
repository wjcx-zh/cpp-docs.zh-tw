---
title: "CComHeap Class | Microsoft Docs"
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
  - "CComHeap"
  - "ATL.CComHeap"
  - "ATL::CComHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComHeap class"
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 COM 記憶體配置配置功能，這個類別會實作 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CComHeap : public IAtlMemMgr  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComHeap::Allocate](../Topic/CComHeap::Allocate.md)|呼叫這個方法會配置記憶體區塊。|  
|[CComHeap::Free](../Topic/CComHeap::Free.md)|呼叫這個方法會釋放此記憶體管理員所配置的記憶體區塊。|  
|[CComHeap::GetSize](../Topic/CComHeap::GetSize.md)|呼叫這個方法會取得此記憶體管理員所配置的記憶體區塊的配置的大小。|  
|[CComHeap::Reallocate](../Topic/CComHeap::Reallocate.md)|呼叫這個方法會重新指派此記憶體管理員所配置的記憶體。|  
  
## 備註  
 使用 COM 配置功能，包括、、 [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)[CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)[IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)和 [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)，`CComHeap` 實作記憶體配置配置功能。  可以配置的最大記憶體數量等於 **INT\_MAX** \(2147483647 個位元組。  
  
## 範例  
 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。請參閱範例。  
  
## 繼承階層架構  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## 需求  
 **Header:** ATLComMem.h  
  
## 請參閱  
 [DynamicConsumer 範例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)