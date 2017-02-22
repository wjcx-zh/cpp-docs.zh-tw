---
title: "Memory Management Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "記憶體, 管理"
ms.assetid: be564a5e-577e-40a7-bfe3-25ad21e57270
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Memory Management Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別提供堆疊指標、智慧型指標和其他記憶體配置常式的支援。  
  
-   [CAutoPtr](../atl/reference/cautoptr-class.md) 這個類別表示智慧型指標物件。  
  
-   以建構一個陣列智慧型指標時，[CAutoPtrArray](../atl/reference/cautoptrarray-class.md) 這個類別會提供有用的方法。  
  
-   以建構清單智慧型指標時，[CAutoPtrList](../atl/reference/cautoptrlist-class.md) 這個類別會提供有用的方法。  
  
-   使用向量新增和刪除運算子，[CAutoVectorPtr](../atl/reference/cautovectorptr-class.md) 這個類別表示智慧型指標物件。  
  
-   使用 COM 記憶體[CComAllocator](../atl/reference/ccomallocator-class.md) 常式，這個類別會提供管理記憶體的方法。  
  
-   [CComGITPtr](../atl/reference/ccomgitptr-class.md) 這個類別會處理方法提供介面指標和全域介面表 \(GIT\)。  
  
-   使用 COM 記憶體配置[CComHeap](../atl/reference/ccomheap-class.md) 配置功能，這個類別會實作 [IAtlMemMgr](../atl/reference/iatlmemmgr-class.md) 。  
  
-   管理的堆積指標的[CComHeapPtr](../atl/reference/ccomheapptr-class.md) A 智慧型指標類別。  
  
-   處理 COM 介面指標的[CComPtr](../atl/reference/ccomptr-class.md) A 智慧型指標類別。  
  
-   使用 COM 架構的記憶體[CComPtrBase](../atl/reference/ccomptrbase-class.md) 常式，這個類別提供智慧型指標類別提供了基礎。  
  
-   處理 COM 介面指標的[CComQIPtr](../atl/reference/ccomqiptr-class.md) A 智慧型指標類別。  
  
-   使用 CRT 記憶體[CCRTAllocator](../atl/reference/ccrtallocator-class.md) 常式，這個類別會提供管理記憶體的方法。  
  
-   使用 CRT 堆積函式[CCRTHeap](../atl/reference/ccrtheap-class.md) ，這個類別會實作 [IAtlMemMgr](../atl/reference/iatlmemmgr-class.md) 。  
  
-   使用 Win32 全域堆積函式，[CGlobalHeap](../atl/reference/cglobalheap-class.md) 這個類別會實作 [IAtlMemMgr](../atl/reference/iatlmemmgr-class.md) 。  
  
-   [CHandle](../atl/reference/chandle-class.md) 這個類別提供方法來建立和使用物件控制代碼。  
  
-   管理的堆積指標的[CHeapPtr](../atl/reference/cheapptr-class.md) A 智慧型指標類別。  
  
-   這個類別[CHeapPtrBase](../atl/reference/cheapptrbase-class.md) 成為許多智慧型指標堆積類別的基礎。  
  
-   以建構清單堆積指標時，[CHeapPtrList](../atl/reference/cheapptrlist-class.md) 這個類別會提供有用的方法。  
  
-   使用 Win32 區域堆積函式，[CLocalHeap](../atl/reference/clocalheap-class.md) 這個類別會實作 [IAtlMemMgr](../atl/reference/iatlmemmgr-class.md) 。  
  
-   使用 Win32 堆積配置函式，[CWin32Heap](../atl/reference/cwin32heap-class.md) 這個類別會實作 [IAtlMemMgr](../atl/reference/iatlmemmgr-class.md) 。  
  
-   [IAtlMemMgr](../atl/reference/iatlmemmgr-class.md) 這個類別表示介面給記憶體管理員。  
  
## 請參閱  
 [Class Overview](../atl/atl-class-overview.md)