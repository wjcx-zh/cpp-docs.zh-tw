---
title: realloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
dev_langs:
- C++
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e378f907c864f534173f746404f853ffa415c70c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="realloc"></a>realloc
重新配置記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```  
void *realloc(  
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>參數  
 `memblock`  
 先前配置之記憶體區塊的指標。  
  
 `size`  
 新的大小 (以位元組計)。  
  
## <a name="return-value"></a>傳回值  
 `realloc` 會傳回重新配置後 (且可能有移動) 記憶體區塊的 `void` 指標。  
  
 如果沒有足夠的可用記憶體將區塊展開為指定大小，原始區塊會保持不變，並傳回 `NULL`。  
  
 如果 `size` 是零，則會釋放 `memblock` 所指向的區塊；傳回值是 `NULL`，且 `memblock` 保持指向已釋放的區塊。  
  
 儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得 `void` 以外之類型的指標，請對傳回值使用類型轉換。  
  
## <a name="remarks"></a>備註  
 `realloc` 函式會變更已配置之記憶體區塊的大小。 `memblock` 引數指向記憶體區塊的開頭。 如果 `memblock` 是 `NULL`，則 `realloc` 的行為方式與 `malloc` 相同，並且會配置 `size` 個位元組的新區塊。 如果 `memblock` 不是 `NULL`，它應該是由先前呼叫 `calloc`、`malloc` 或 `realloc` 所傳回的指標。  
  
 `size` 引數會指定區塊的新大小，以位元組為單位。 區塊的內容維持為新舊大小的較短者，不過新區塊可能在不同的位置。 因為新區塊可能會在新的記憶體位置，所以 `realloc` 傳回的指標並不保證是透過 `memblock` 引數傳遞的指標。 `realloc` 在緩衝區成長的情況下，不會將新配置的記憶體歸零。  
  
 如果記憶體配置失敗，或所要求的記憶體數量超過 `_HEAP_MAXREQ`，則 `realloc` 會將 `errno` 設定為 `ENOMEM`。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `realloc` 會呼叫 `malloc` 以使用 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函式來設定新的處理常式模式。 此新的處理常式模式會指出失敗時，`malloc` 是否會呼叫 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 所設定的新處理常式。 根據預設，`malloc` 不會在失敗時呼叫新的處理常式來配置記憶體。 您可以覆寫這個預設行為，因此，在 `realloc` 無法配置記憶體時，`malloc` 會呼叫新的處理常式，其方法與 `new` 運算子因相同原因而失敗時所執行的方法相同。 若要覆寫預設值，請及早在程式中呼叫  
  
```  
_set_new_mode(1)  
```  
  
 ，或使用 NEWMODE.OBJ 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。  
  
 當應用程式與偵錯版本的 C 執行階段程式庫相連結時，`realloc` 會解析為 [_realloc_dbg](../../c-runtime-library/reference/realloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `realloc` 標記為 `__declspec(noalias)` 和 `__declspec(restrict)`，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`realloc`|\<stdlib.h> 和 \<malloc.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_realloc.c  
// This program allocates a block of memory for  
// buffer and then uses _msize to display the size of that  
// block. Next, it uses realloc to expand the amount of  
// memory used by buffer and then calls _msize again to  
// display the new amount of memory allocated to buffer.  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   long *buffer, *oldbuffer;  
   size_t size;  
  
   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )  
      exit( 1 );  
  
   size = _msize( buffer );  
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );  
  
   // Reallocate and show new size:  
   oldbuffer = buffer;     // save pointer in case realloc fails  
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))   
        ==  NULL )  
   {  
      free( oldbuffer );  // free original block  
      exit( 1 );  
   }  
   size = _msize( buffer );  
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",   
            size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after malloc of 1000 longs: 4000  
Size of block after realloc of 1000 more longs: 8000  
```  
  
## <a name="see-also"></a>請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)