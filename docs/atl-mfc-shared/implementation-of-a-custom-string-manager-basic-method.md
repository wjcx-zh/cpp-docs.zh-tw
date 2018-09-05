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
ms.openlocfilehash: 5c251ae73b4adaaed09e5ed654e394a130281332
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756401"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>自訂字串管理員實作 （基本方法）

若要自訂記憶體配置方案，字串資料是使用 ATL 提供最簡單的方式`CAtlStringMgr`類別，但提供您自己的記憶體配置常式。 建構函式`CAtlStringMgr`接受單一參數： 指向`IAtlMemMgr`物件。 `IAtlMemMgr` 是提供成堆積的泛型介面的抽象基底類別。 使用`IAtlMemMgr`介面，`CAtlStringMgr`配置、 重新配置，並釋放用來儲存字串資料的記憶體。 您可以實作`IAtlMemMgr`介面，或使用其中一個五個的 ATL 提供的記憶體管理員類別。 ATL 提供的記憶體管理員僅會包裝現有的記憶體配置功能：

- [CCRTHeap](../atl/reference/ccrtheap-class.md)包裝標準 CRT 堆積函式 ([malloc](../c-runtime-library/reference/malloc.md)，[免費](../c-runtime-library/reference/free.md)，和[realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md)包裝 Win32 堆積處理，請使用[HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc)， [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree)，和[HeapRealloc](/windows/desktop/api/heapapi/nf-heapapi-heaprealloc)

- [CLocalHeap](../atl/reference/clocalheap-class.md)包裝 Win32 Api: [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc)， [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree)，和[LocalRealloc](/windows/desktop/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md)包裝 Win32 Api: [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)， [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree)，和[GlobalRealloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc)。

- [CComHeap](../atl/reference/ccomheap-class.md)包裝 COM 工作配置器 Api: [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)， [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree)，和[CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

最有用的類別是以字串的記憶體管理、`CWin32Heap`因為它可讓您建立多個獨立的堆積。 例如，如果您想要只針對字串使用不同堆積，您可以執行下列項目：

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

若要使用此私用 string 管理員來管理記憶體`CString`變數中，管理員做為參數傳遞指標`CString`變數的建構函式：

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)

