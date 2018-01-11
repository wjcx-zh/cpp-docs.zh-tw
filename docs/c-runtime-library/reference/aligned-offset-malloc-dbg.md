---
title: _aligned_offset_malloc_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
dev_langs: C++
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d06092e33fb9cf13fb4ca39e19841fa3bb7fc42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg
在指定的對齊界限上配置記憶體 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
void * _aligned_offset_malloc_dbg(  
   size_t size,   
   size_t alignment,   
   size_t offset,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `size`  
 要求的記憶體配置的大小。  
  
 [in] `alignment`  
 對齊值，必須是 2 的整數冪。  
  
 [in] `offset`  
 記憶體配置中要強制對齊的位移。  
  
 [輸入] `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 NULL。  
  
 [in] `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 NULL。  
  
## <a name="return-value"></a>傳回值  
 已配置之記憶體區塊的指標，或為 `NULL` (作業失敗時)。  
  
## <a name="remarks"></a>備註  
 `_aligned_offset_malloc_dbg` 是 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 函式的偵錯版本。 當 [_DEBUG](../../c-runtime-library/debug.md) 未定義時，每個 `_aligned_offset_malloc_dbg` 的呼叫會降至 `_aligned_offset_malloc` 的呼叫。 `_aligned_offset_malloc` 和 `_aligned_offset_malloc_dbg` 都會配置基底堆積中的記憶體區塊，但 `_aligned_offset_malloc_dbg` 還提供數種偵錯功能：在區塊的使用者部分的任一端使用緩衝區以測試遺漏，以及追蹤特定配置類型的區塊類型參數，還有判斷配置要求來源的 `filename`/`linenumber` 資訊。  
  
 `_aligned_offset_malloc_dbg` 會使用比要求的 `size` 稍多一些的空間配置記憶體區塊。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 區塊配置後，區塊的使用者部分會填入值 0xCD，且每個覆寫緩衝區會填入 0xFD。  
  
 `_aligned_offset_malloc_dbg` 適用於巢狀元素需要對齊的情況，例如，如果巢狀類別需要對齊時。  
  
 `_aligned_offset_malloc_dbg` 是以 `malloc` 為基礎，如需詳細資訊，請參閱 [malloc](../../c-runtime-library/reference/malloc.md)。  
  
 若記憶體配置失敗，或是要求的大小大於 `errno`，則此函式會將 `ENOMEM` 設為 `_HEAP_MAXREQ`。 如需 `errno` 的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。 此外，`_aligned_offset_malloc` 也會驗證其參數。 如果 `alignment` 不是 2 的乘冪，或如果 `offset` 大於或等於 `size` 及非零值，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
 如需配置區塊類型和其使用方式的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_aligned_offset_malloc_dbg`|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)