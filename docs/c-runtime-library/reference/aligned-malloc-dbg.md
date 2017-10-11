---
title: _aligned_malloc_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_malloc_dbg
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _aligned_malloc_dbg
- aligned_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: aca23722103b75c6420ed14132d1fdac9cd097f6
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg
使用額外空間為偵錯標頭及覆寫緩衝區，依指定的對齊界限配置記憶體 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
void * _aligned_malloc_dbg(  
    size_t size,   
    size_t alignment,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `size`  
 要求的記憶體配置的大小。  
  
 [in] `alignment`  
 對齊值，必須是 2 的整數冪。  
  
 [in] `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 NULL。  
  
 [in] `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 NULL。  
  
## <a name="return-value"></a>傳回值  
 已配置之記憶體區塊的指標，或為 `NULL` (作業失敗時)。  
  
## <a name="remarks"></a>備註  
 `_aligned_malloc_dbg` 是 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 函式的偵錯版本。 當 [_DEBUG](../../c-runtime-library/debug.md) 未定義時，每個 `_aligned_malloc_dbg` 的呼叫會降至 `_aligned_malloc` 的呼叫。 `_aligned_malloc` 和 `_aligned_malloc_dbg` 都會配置基底堆積中的記憶體區塊，但 `_aligned_malloc_dbg` 還提供數種偵錯功能：在區塊的使用者部分的任一端使用緩衝區以測試遺漏，以及判斷配置要求來源的 `filename`/`linenumber` 資訊。  
  
 `_aligned_malloc_dbg` 會使用比要求的 `size` 稍多一些的空間配置記憶體區塊。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。  
  
 若記憶體配置失敗，或是所需的記憶體數量 (包含之前提到的額外負荷) 超過 `_aligned_malloc_dbg`，`errno` 會將 `ENOMEM` 設定為 `_HEAP_MAXREQ`。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_malloc_dbg` 也會驗證其參數。 如果 `alignment` 不是 2 的乘冪，或 `size` 為零，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
 如需在偵錯版本的基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_aligned_malloc_dbg`|\<crtdbg.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)
