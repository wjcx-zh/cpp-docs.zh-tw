---
title: 自訂字串管理員實作 （基本方法） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c393489b8b4d0353ae37a21132f66e0618b3b794
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884580"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>自訂字串管理員實作 （基本方法）
若要自訂記憶體配置方案，字串資料是使用 ATL 提供最簡單的方式`CAtlStringMgr`類別，但提供您自己的記憶體配置常式。 建構函式`CAtlStringMgr`接受單一參數： 指向`IAtlMemMgr`物件。 `IAtlMemMgr` 是提供成堆積的泛型介面的抽象基底類別。 使用`IAtlMemMgr`介面，`CAtlStringMgr`配置、 重新配置，並釋放用來儲存字串資料的記憶體。 您可以實作`IAtlMemMgr`介面，或使用其中一個五個的 ATL 提供的記憶體管理員類別。 ATL 提供的記憶體管理員僅會包裝現有的記憶體配置功能：  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md)包裝標準 CRT 堆積函式 ([malloc](../c-runtime-library/reference/malloc.md)，[免費](../c-runtime-library/reference/free.md)，和[realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md)包裝 Win32 堆積處理，請使用[HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)， [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)，和[HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md)包裝 Win32 Api: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)， [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)，和[LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md)包裝 Win32 Api: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)， [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)，和[GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)。  
  
-   [CComHeap](../atl/reference/ccomheap-class.md)包裝 COM 工作配置器 Api: [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)， [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)，和[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 最有用的類別是以字串的記憶體管理、`CWin32Heap`因為它可讓您建立多個獨立的堆積。 例如，如果您想要只針對字串使用不同堆積，您可以執行下列項目：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 若要使用此私用 string 管理員來管理記憶體`CString`變數中，管理員做為參數傳遞指標`CString`變數的建構函式：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)

