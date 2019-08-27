---
title: 自訂字串管理員的實作為 (基本方法)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 92c1c46f5251980f9cefb55e052e9aff395e0e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491319"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>自訂字串管理員的實作為 (基本方法)

自訂字串資料的記憶體配置配置最簡單的方式, 就是使用 ATL 提供`CAtlStringMgr`的類別, 但提供您自己的記憶體配置常式。 的函`IAtlMemMgr`式會採用單一參數:`CAtlStringMgr`物件的指標。 `IAtlMemMgr`是提供堆積泛型介面的抽象基類。 使用介面時`CAtlStringMgr` , 會配置、重新配置和釋放用來儲存字串資料的記憶體。 `IAtlMemMgr` 您可以自行執行`IAtlMemMgr`介面, 或使用五個 ATL 提供的記憶體管理員類別其中之一。 ATL 提供的記憶體管理員只會包裝現有的記憶體配置設備:

- [CCRTHeap](../atl/reference/ccrtheap-class.md)包裝標準 CRT 堆積函數 ([malloc](../c-runtime-library/reference/malloc.md)、 [free](../c-runtime-library/reference/free.md)和[realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md)使用[HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)、 [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)和[HeapRealloc](/windows/win32/api/heapapi/nf-heapapi-heaprealloc)包裝 Win32 堆積控制碼

- [CLocalHeap](../atl/reference/clocalheap-class.md)包裝 Win32 Api:[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)、 [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)和[LocalRealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md)包裝 Win32 Api:[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)、 [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)和[GlobalRealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)。

- [CComHeap](../atl/reference/ccomheap-class.md)包裝 COM 工作配置器 Api:[CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)、 [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)和[CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

基於字串記憶體管理的目的, 最有用的類別是`CWin32Heap` , 因為它可讓您建立多個獨立的堆積。 例如, 如果您想要只針對字串使用個別的堆積, 您可以執行下列動作:

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

若要使用這個私用字串管理員來管理`CString`變數的記憶體, 請將指標傳遞給管理員, 做為`CString`變數的函式的參數:

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)
