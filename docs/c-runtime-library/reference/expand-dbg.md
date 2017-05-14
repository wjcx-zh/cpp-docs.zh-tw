---
title: _expand_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _expand_dbg
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
- expand_dbg
- _expand_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: e398d641cde32b90b4502b9ae38dc3918aa65704
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="expanddbg"></a>_expand_dbg
以展開或收縮區塊的方式調整堆積中的指定記憶體區塊 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
void *_expand_dbg(   
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>參數  
 `userData`  
 之前配置的記憶體區塊的指標。  
  
 `newSize`  
 要求的新區塊大小 (以位元組為單位)。  
  
 `blockType`  
 已調整大小區塊的要求類型︰`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求展開作業的來源檔案名稱指標，或為 `NULL`。  
  
 `linenumber`  
 要求展開作業的來源檔案行號，或為 `NULL`。  
  
 只有在已明確呼叫 `_expand_dbg`，或是已定義 [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 處理器常數時，才可以使用 `filename` 和 `linenumber` 參數。  
  
## <a name="return-value"></a>傳回值  
 成功完成時，`_expand_dbg` 會傳回已調整大小的記憶體區塊指標。 因為記憶體未移動，所以位址和 userData 相同。 如果發生錯誤，或區塊無法展開至要求的大小，它會傳回 `NULL`。 如果失敗，`errno` 會伴隨作業系統有關失敗類別的資訊。 如需 `errno` 的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_expand_dbg` 函式是 _[expand](../../c-runtime-library/reference/expand.md) 函式的偵錯版本。 當 [_DEBUG](../../c-runtime-library/debug.md) 未定義時，每個 `_expand_dbg` 的呼叫會降至 `_expand` 的呼叫。 `_expand` 和 `_expand_dbg` 都會調整基底堆積的記憶體區塊大小，但 `_expand_dbg` 還容納數種偵錯功能：在區塊的使用者部分的任一端使用緩衝區以測試遺漏，以及追蹤特定配置類型的區塊類型參數，還有判斷配置要求來源的 `filename`/`linenumber` 資訊。  
  
 `_expand_dbg` 會使用比要求的 `newSize` 稍多一些的空間調整指定的記憶體區塊大小。 `newSize` 可能會比原始配置的記憶體區塊大小更多或更少。 偵錯堆積管理員會使用額外的空間連結偵錯記憶體區塊，以及為應用程式提供偵錯標頭資訊和覆寫緩衝區。 展開或收縮原始記憶體區塊即可調整大小。 `_expand_dbg` 不會移動記憶體區塊，如同 [_realloc_dbg](../../c-runtime-library/reference/realloc-dbg.md) 函式一樣。  
  
 當 `newSize` 大於原始區塊大小時，就會展開記憶體區塊。 在展開時，如果記憶體區塊無法展開至可容納要求的大小，即傳回 `NULL`。 當 `newSize` 小於原時區塊大小時，記憶體區塊會收縮至取得新的大小。  
  
 如需在偵錯版本的基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。 如需配置區塊類型以及如何使用它們的資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在應用程式的偵錯組建中呼叫標準堆積函式與其偵錯版本間之差異的資訊，請參閱[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)。  
  
 這個函式會驗證它的參數。 如果 `memblock` 為 Null 指標，或如果大小大於 `_HEAP_MAXREQ`，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行， `errno` 會設為 `EINVAL` ，且此函式會傳回 `NULL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_expand_dbg`|\<crtdbg.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_expand_dbg.c  
//  
// This program allocates a block of memory using _malloc_dbg  
// and then calls _msize_dbg to display the size of that block.  
// Next, it uses _expand_dbg to expand the amount of  
// memory used by the buffer and then calls _msize_dbg again to  
// display the new amount of memory allocated to the buffer.  
//  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   long *buffer;  
   size_t size;  
  
   // Call _malloc_dbg to include the filename and line number  
   // of our allocation request in the header  
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if( buffer == NULL )  
      exit( 1 );  
  
   // Get the size of the buffer by calling _msize_dbg  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
   // Expand the buffer using _expand_dbg and show the new size  
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
   if( buffer == NULL )  
      exit( 1 );  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",  
           size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after _malloc_dbg of 40 longs: 160  
Size of block after _expand_dbg of 1 more long: 164  
```  
  
## <a name="comment"></a>註解  
 此程式的輸出取決於您的電腦能否展開所有區段。 如果所有區段都能展開，就會在 [輸出] 區段反映輸出。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)
