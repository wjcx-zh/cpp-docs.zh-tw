---
title: "Implementation of a Custom String Manager (Basic Method) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlStringMgr class, 使用"
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementation of a Custom String Manager (Basic Method)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

最簡單的方式自訂字串資料的記憶體配置計劃會使用 ATL 提供 **CAtlStringMgr** 類別，但您的記憶體配置常式。  **CAtlStringMgr** 的建構函式會接受單一參數:為 `IAtlMemMgr` 物件的指標。  `IAtlMemMgr` 是提供泛型介面給堆積的抽象基底類別。  使用 `IAtlMemMgr` 介面， **CAtlStringMgr** 配置，重新配置，並釋放所使用的記憶體中儲存字串資料。  您可以實作 `IAtlMemMgr` 介面，或是使用其中一個 ATL 提供了記憶體管理員類別。  ATL 提供了記憶體管理員包裝現有的記憶體配置安裝:  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) 包裝標準 CRT 堆積函式 \([malloc](../c-runtime-library/reference/malloc.md)、 [可用](../c-runtime-library/reference/free.md)和 [realloc](../c-runtime-library/reference/realloc.md)\)  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) 使用 [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)、 [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)和 [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)，包裝 Win32 控制代碼，堆積  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) 包裝 Win32 API: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)、 [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)和 [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) 包裝 Win32 API: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)、 [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)和 [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)。  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) 包裝 COM 工作配置器 API: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)、 [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)和 [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 字串形式的記憶體管理的目的，，因為它可讓您建立多個獨立堆積，最實用的類別是 `CWin32Heap` 。  例如，在中，如果您想要對字串使用不同堆積，可以執行下列操作:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/CPP/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 若要使用這個私用字串處理常式處理 `CString` 變數的記憶體，請將指標傳遞給這個處理常式做為參數傳遞至 `CString` 變數的建構函式:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/CPP/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## 請參閱  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)