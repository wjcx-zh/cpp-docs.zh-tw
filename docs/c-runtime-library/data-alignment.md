---
title: "資料對齊 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- data.alignment
dev_langs:
- C++
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 8c1e9bceaf205f6ac324033842292fe12150df27
ms.lasthandoff: 02/24/2017

---
# <a name="data-alignment"></a>資料對齊
下列 C 執行階段函式支援資料對齊。  
  
### <a name="data-alignment-routines"></a>資料對齊常式  
  
|常式|用法|.NET Framework 同等|  
|-------------|---------|-------------------------------|  
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|釋放使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|釋放使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊 (僅限偵錯)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|針對指定的對齊界限配置記憶體。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|使用額外空間為偵錯標頭及覆寫緩衝區，依指定的對齊界限配置記憶體 (僅限偵錯版本)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|傳回堆積中所配置的記憶體區塊大小。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|傳回堆積中所配置的記憶體區塊大小 (僅限偵錯版本)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|針對指定的對齊界限配置記憶體。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|在指定的對齊界限上配置記憶體 (僅限偵錯版本)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小 (僅限偵錯版本)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0 (僅限偵錯版本)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小 (僅限偵錯版本)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|變更使用 [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊大小，並將記憶體初始化為 0 (僅限偵錯版本)。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
