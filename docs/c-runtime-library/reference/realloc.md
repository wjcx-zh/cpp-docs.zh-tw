---
title: realloc
ms.date: 4/2/2020
api_name:
- realloc
- _o_realloc
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
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
ms.openlocfilehash: 964c465a95d44de9d8a4d399f23ec43f8a3a6692
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332939"
---
# <a name="realloc"></a>realloc

重新配置記憶體區塊。

## <a name="syntax"></a>語法

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
先前配置之記憶體區塊的指標。

*大小*<br/>
新的大小 (以位元組計)。

## <a name="return-value"></a>傳回值

**realloc**傳回到重新分配(並可能移動)記憶體區**塊的空指標**。

如果沒有足夠的可用記憶體將塊擴展到給定的大小,則原始塊保持不變,並且**返回 NULL。**

如果*大小*為零,則釋放*memblock*指向的塊;如果大小為零。"返回值為**NULL***NULL,memblock*被保留在已釋放的塊上。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 要取得指向**void**以外的類型的指標,請使用返回值上強制轉換的類型。

## <a name="remarks"></a>備註

**realloc**函數更改已分配記憶體區塊的大小。 *memblock*參數指向記憶體塊的開頭。 如果*memblock*為**NULL,****則 realloc**的方法來與**malloc**相同的方式,並分配一個新的*大小*位元組塊。 如果*memblock*不是**NULL,** 它應該是前一個調用 call 傳回的指向**calloc、malloc**或**realloc**的指標。 **realloc**

*大小*參數提供塊的新大小(以位元組為單位)。 區塊的內容維持為新舊大小的較短者，不過新區塊可能在不同的位置。 由於新塊可以位於新的記憶體位置,因此**Realloc**返回的指標不能保證是通過*memblock*參數傳遞的指標。 在緩衝區增長的情況下 **,realloc**不會為新分配的記憶體。

如果記憶體分配失敗或請求的記憶體量超過 **_HEAP_MAXREQ,realloc**將**errno**設置**ENOMEM。** **realloc** 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**realloc**調用**malloc**以使用[C++_set_new_mode](set-new-mode.md)函數來設置新的處理程式模式。 新的處理程式模式指示在發生故障時 **,malloc**是否將調用[由 _set_new_handler](set-new-handler.md)設置的新處理程式例程。 默認情況下 **,malloc**不會在分配記憶體失敗時調用新的處理程式例程。 您可以重寫此預設行為,以便在**Realloc**無法分配記憶體時 **,malloc**呼叫新處理程式例程的方式**與新運算符出於**相同原因失敗時相同。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

，或使用 NEWMODE.OBJ 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

當應用程式與 C 執行時庫的除錯版本連結時 **,realloc**解析為[_realloc_dbg](realloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**realloc**`__declspec(noalias)`被`__declspec(restrict)`標記 和 ,這意味著保證函數不修改全域變數,並且返回的指標不會別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**realloc**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
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

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[自由](free.md)<br/>
[malloc](malloc.md)<br/>
