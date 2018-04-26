---
title: realloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e81f0456fd436ddb0036e0aebd0f56697c1ac213
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*size*<br/>
新的大小 (以位元組計)。

## <a name="return-value"></a>傳回值

**realloc**傳回**void**重新配置後 （且可能有移動） 記憶體區塊指標。

如果沒有足夠的可用記憶體將區塊展開為指定大小，原始區塊會保持不變，與**NULL**傳回。

如果*大小*是零，則所指向的區塊*memblock*釋放; 傳回值是**NULL**，和*memblock*保留指向釋出區塊。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得指標的類型以外**void**，使用類型，對傳回值轉型。

## <a name="remarks"></a>備註

**Realloc**函式變更配置的記憶體區塊大小。 *Memblock*引數指向的記憶體區塊開頭。 如果*memblock*是**NULL**， **realloc**的行為方式相同**malloc**而不會配置新的區塊*大小*位元組。 如果*memblock*不**NULL**，它應該是由先前呼叫所傳回的指標**calloc**， **malloc**，或**realloc**.

*大小*引數提供新的區塊大小，以位元組為單位。 區塊的內容維持為新舊大小的較短者，不過新區塊可能在不同的位置。 因為新區塊可能會在新的記憶體位置，傳回的指標**realloc**不保證是透過傳遞指標*memblock*引數。 **realloc**並不是以零新配置的記憶體在緩衝區成長的情況下。

**realloc**設定**errno**至**ENOMEM**如果記憶體配置失敗，或要求的記憶體數量超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**realloc**呼叫**malloc**才能使用 c + + [_set_new_mode](set-new-mode.md)函式可設定新的處理常式模式。 新的處理常式模式指出是否在失敗時， **malloc**是新的處理常式呼叫所設定的[_set_new_handler](set-new-handler.md)。 根據預設， **malloc**不會呼叫新的處理常式在無法配置記憶體。 您可以覆寫此預設行為，讓，當**realloc**無法配置記憶體， **malloc**呼叫新的處理常式在相同的方式來**新**運算子會當它失敗基於相同原因。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

，或使用 NEWMODE.OBJ 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

當應用程式的 C 執行階段程式庫的偵錯版本連結時**realloc**解析成[_realloc_dbg](realloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**realloc**標示`__declspec(noalias)`和`__declspec(restrict)`，也就是說，不保證函式修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
[free](free.md)<br/>
[malloc](malloc.md)<br/>
