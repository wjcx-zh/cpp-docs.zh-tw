---
title: 實作的自訂字串管理員 （基本的方法） |Microsoft 文件
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
ms.openlocfilehash: 259f9533747b266f0be0a782cdc94c98f167d2d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355721"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>實作的自訂字串管理員 （基本的方法）
若要自訂的記憶體配置方案，字串資料是使用 ATL 提供最簡單的方式**CAtlStringMgr**類別，但提供您自己的記憶體配置常式。 建構函式**CAtlStringMgr**接受單一參數： 指標`IAtlMemMgr`物件。 `IAtlMemMgr` 是提供到堆積的泛型介面的抽象基底類別。 使用`IAtlMemMgr`介面， **CAtlStringMgr**配置、 重新配置，然後釋放用來儲存字串資料的記憶體。 您可以實作`IAtlMemMgr`介面，或是使用其中一個五個 ATL 提供的記憶體管理員類別。 ATL 提供的記憶體管理員只會包裝現有的記憶體配置設備：  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md)包裝標準 CRT 堆積函式 ([malloc](../c-runtime-library/reference/malloc.md)，[可用](../c-runtime-library/reference/free.md)，和[realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md)換行的 Win32 堆積處理，請使用[HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)， [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)，和[HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md)包裝 Win32 Api: [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)， [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)，和[LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md)包裝 Win32 Api: [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)， [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)，和[GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)。  
  
-   [CComHeap](../atl/reference/ccomheap-class.md)包裝 COM 工作配置器應用程式開發介面： [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)， [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)，和[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 管理字串記憶體，是最有用的類別`CWin32Heap`因為它可讓您建立多個獨立的堆積。 例如，如果您想要只對字串使用不同的堆積，您可以執行下列項目：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 若要使用此私用 string 管理員來管理記憶體`CString`變數，來為參數，以管理員的指標傳遞`CString`變數的建構函式：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)

